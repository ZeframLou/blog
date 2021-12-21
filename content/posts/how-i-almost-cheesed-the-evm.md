---
title: "How I Almost Cheesed the EVM"
date: 2021-12-21T14:13:31-08:00
draft: false
---

## Genesis

Using Ethereum is expensive. Us smart contract developers are eternally doomed to the fate of locking ourselves in dank dark basements every day to optimize gas usage, so that our fancy DeFi protocols won’t make our users bankrupt.

Of all the operations done by smart contracts, storage writes & reads usually take up most of the gas usage. EVM storage is made intentionally expensive, because it’s expensive for Ethereum nodes to store data for the rest of time.

Or so you’d think.

It turns out that permanent data are not made equal. Ethereum smart contracts have access to two types of permanent data: storage, where you put all the persistant variables of your contract; and code, where you put the logic of the contract.

Writing to the storage is expensive: setting the value of a single 32-byte storage variable costs 2900 gas, or 20000 gas if you’re setting a variable with zero-value to a non-zero value. Reading from the storage is also expensive: reading the value of a single 32-byte  variable costs 2100 gas. For comparison, computing a single addition costs 3 gas, and a single multiplication costs 5 gas.

Accessing code, on the other hand, is much cheaper. Exactly how much cheaper I don’t want to explain, because it’s pretty messy, but the TL;DR is it’s several times cheaper ([read the yellow paper to learn more](https://ethereum.github.io/yellowpaper/paper.pdf)). The rationale is that code and storage are structured differently: code is just a big blob of bytes that can’t be modified after writing, whereas storage allows contracts to write to any slot in its $2^{256}$ address space however many times as desired, so there’s quite a bit of overhead.

This cost difference led to [the SLOAD2 library by 0xsequence](https://github.com/0xsequence/sstore2), which allows contracts to store data by deploying a new contract and putting the data in its code region, thereby saving on gas costs. The gas savings are pretty dramatic: if you wanted to read 1024 bytes from storage, the cost is 71659 gas, whereas if you used `SLOAD2` the cost would only be 3296 gas. The downside of `SLOAD2` is that you can only write to the same key once, so your contract needs to keep track of which key it’s currently using to store its state, either by using storage, which increases the gas cost, or by tracking the key offchain, which makes `SLOAD2` only suitable for a small subset of applications.

Ever since I saw the release of `SLOAD2`, I’ve been wondering if it’s possible to make some modifications to it in order to enable writing to the same key multiple times. If it was possible, I would’ve effectively created an alternative method for persistant data storage for smart contracts that’s much cheaper but still has roughly the same features & developer experience, thus cheesing the EVM and saving tons of gas fees for Ethereum users.

Excited by this prospect, I forked `SLOAD2` and got to work.

## First idea: selfdestruct and reinit at the same pointer

The vanilla `SLOAD2` library automatically generated the key after you store a piece of data, which necessitates key-tracking, but the author also wrote `SLOAD2Map`, which provided a key-value map interface allowing you to store data to a custom key. Of course, you can still only write to the key once. I decided to base my work on `SLOAD2Map` rather than `SLOAD2`, since it’s closer to what I want to achieve.

`SLOAD2Map` works in the following way: when you want to store a piece of data to a key, the library first deploys a *proxy contract* using the `CREATE2` opcode, which allows you to compute the address of the resulting contract deterministically given the key & the hash of the proxy’s creation code (which is a known constant). The library calls the proxy contract with your data, and the the proxy contract will deploy a *child contract* that stores your data in its code region, using the `CREATE` opcode. The address of the child contract can also be computed deterministically given the key. After you’ve stored the data, whenever you want to read it back you would compute the address of the child contract given your key, and then simply read from the code region of the child contract.

(The proxy contract stuff is done using another library by 0xsequence called [CREATE3](https://github.com/0xsequence/create3), which emulates a new opcode that [EIP-3171](https://github.com/ethereum/EIPs/pull/3171) is trying to add to the EVM. We will come back to this later.)

My first idea for how to achieve rewritability was this: what if I made the child contract a bit fancier, such that whenever I want to rewrite to the same key, I can call the child contract to let it self-destruct, then deploy a new child contract at the same address that stores the updated data?

I quickly cobbled together a minimal child contract that self-destructs whenever it’s called by the main contract and does nothing whenever it’s called by someone else:

```
The bytecode of the created child contract.
When called, the child contract check whether the sender is equal to the preset owner address
(in our case it's this contract), if so then the data-contract selfdestructs, allowing for
reiniting a new contract at the same address. If the sender is not the owner, then the
execution halts.
The data is stored from 0x1E onwards.

0x00  0x33  0x33                                          CALLER        sender
0x01  0x73  0x73XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX  PUSH20 owner  owner sender
0x16  0x14  0x14                                          EQ            isOwner
0x17  0x60  0x601B                                        PUSH1 0x06    0x06 isOwner
0x19  0x57  0x57                                          JUMPI                       % branch based on isOwner
0x1A  0x00  0x00                                          STOP                        % not owner, halt
0x1B  0x5B  0x5B                                          JUMPDEST                    % is owner, selfdestruct
0x1C  0x32  0x32                                          ORIGIN        origin        % use tx.origin for cheaper gas
0x1D  0xFF  0xFF                                          SELFDESTRUCT
```

Once I implemented this idea and tested it out, I realized two flaws in my idea:

1. The `SELFDESTRUCT` opcode only destroys the contract at the end of the current transaction. Therefore, it’s not possible to destroy a contract and reinit a new one at the same address within the same transaction. This is more of an UX issue though, which I might be able to get around using Flashbots bundles.
2. I misunderstood how `CREATE3` works. The reason that we can deterministically compute the address of the child contract, even though `CREATE3` is not yet an opcode in the EVM, is that the proxy contract is only expected to deploy a single child contract. The proxy contract uses the `CREATE` opcode to deploy the child contract, so the address of the child contract is the lower 20 bytes of `keccak256(rlp(proxyAddress, nonce))`. Therefore, the first contract deployed by the proxy has the address `keccak256(rlp(proxyAddress, 1))`, where the nonce is known to be 1 since we know this is the first transaction originating from the proxy contract. Therefore, it’s not possible for me to deploy another contract at the same address as the first child contract, since the nonce value will be 2, resulting in a different address. Using `CREATE2` in the proxy contract for deploying the child contract doesn’t work either, since the child contract’s address would be dependent on its creation code, meaning you can only redeploy to the same address if you’re storing the same data as before, which is quite pointless.

So yeah, this idea has no way of working until `CREATE3` becomes an actual opcode. However, my deep dive into the workings of the `CREATE3` library gave me another idea.

## Second idea: deterministically shifting pointer

If you think about it, we don’t actually need the child contract to always use the same address after we modify its data, we just need some *deterministic* way to compute its address, so that we don’t need to resort to using the native storage to keep track of it. If the child contract’s address changes when we reuse the same proxy contract, due to its account nonce being incremented, then what if we just keep track of the proxy contract’s nonce value somehow? This would allow us to compute the child contract’s address using `keccak256(rlp(proxyAddress, nonce))` instead of `keccak256(rlp(proxyAddress, 1))`.

If that confused you, here’s a more visual explanation (that unfortunately doesn’t have any actual pictures cause I’m lazy): the first idea I had relied on having a single deterministically computable pointer that points to where our data is stored, and updating the data involves modifying the child contract that the pointer points to. The second idea also relies on having a single pointer, but when we update the data we simply shift the pointer to point at another child contract, and we can deterministically compute the new location that the pointer points to.

Unfortunately, this idea didn’t pan out either. The EVM, it turns out, doesn’t have a `NONCE` opcode! This means a smart contract has absolutely no way of accessing the nonce of an account. You’d think something so simple and so natural would have long been included in the EVM, but that’s not the case. The `NONCE` opcode was part of [EIP-2938](https://github.com/ethereum/EIPs/blob/master/EIPS/eip-2938.md), coauthored by Vitalik no less, but the EIP has apparently been “stagnant”, whatever that means, so oh well.

At this point, I was chuckling to myself at how ridiculous this was. The one thing that prevented me from abusing cheaper storage out of the EVM was the lack of a `NONCE` opcode! The connection between them is not obvious at all, and frankly quite surprising to me. It’s like executing a complex bank heist,where you stole the keys, disabled the alarms, drugged the security guards, and so on, only to be stopped because you got tripped by a mop left on the ground by the janitor and hit your head.

## One more thing…

Frustrated, I perused through the list of EVM opcodes to see if there’s another opcode I can abuse into tracking the nonce of the proxy contract.

I did find one that half works, but the implications made me laugh even harder. The opcode I found was `BALANCE`.

Yeah, basically I’d be using the proxy contract’s ETH balance to store its nonce, and everytime I deploy a child contract, I’d send 1 wei to the proxy at the same time.

If you don’t think this is absolutely hilarious, you might not be a Real Dev™️.

Of course, this idea only half works, and the reason is obvious: anyone can send some ETH to the proxy contract and ruin everything. You could let the proxy contract revert when someone sends it ETH, but you can get around it by using `SELFDESTRUCT`, which doesn’t execute the recipient’s code when it sends ETH.

At this point, it was clear to me that what I wanted to achieve was simply not possible in the current version of the EVM. That’s why I’m here writing a blog post about it to get some sweet sweet internet points. I hope this post brought you some fun!

My code doesn’t work, but you can see what I ended up with [here](https://github.com/ZeframLou/sstore2).

P.S. If the `NONCE` opcode ever gets added to the EVM, hit me up.

{{<remarkbox>}}
