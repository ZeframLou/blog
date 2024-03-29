---
title: "Projects"
ShowToc: true
TocOpen: true
---

## Core projects

### Timeless

Timeless is a perpetual yield token protocol. It introduces two brand new financial instruments that enable people to leverage, speculate on, or hedge yield.

Launched on Ethereum Mainnet and several other networks.

[Visit](https://timelessfi.com)

### Sudoswap

Sudoswap is an Automated Market Maker (AMM) for NFTs. It is capital efficient, hyper gas-optimized, and mostly permissionless.

I expect that Sudoswap will be to NFTs what Uniswap was (and is) to tokens: a new paradigm that will dominate the trading market.

Launched on Ethereum Mainnet.

[Visit](https://sudoswap.xyz)

## Active projects

### Bunni

Bunni is an ERC-20 liquidity provider (LP) token protocol for Uniswap v3. It enables representing Uniswap v3 LP positions as fungible tokens rather than
NFTs, which unlocks new possibilities for liquidity incentivization and composability. It also makes providing liquidity on Uniswap v3 significantly cheaper, since LP tokens
for the same price ranges are reused.

[Visit](https://github.com/ZeframLou/bunni)

### Bagholder

Bagholder is an NFT loyalty protocol. It enables NFT projects to reward their holders with tokens without requiring them to stake the NFTs in a contract.

Bagholder introduces a new concept called **Optimistic Staking**. Optimistic staking uses mechanisms similar to optimistic rollups, where it optimistically assumes
that stakers are honest and won't transfer away their NFTs while receiving rewards, and slashes dishonest stakers. This is why stakers must deposit bonds when they stake; 
a bond only needs to cover the gas cost of slashing (which is low) plus a bit of reward for the slasher.

Bagholder enables NFT holders to be rewarded by the project, while retaining access to NFT-gated benefits such as private groupchats.

Launched on Ethereum Mainnet.

[Visit](https://bagholder.us)

### 88mph

88mph is a fixed interest rate lending protocol. It's super cool so take a look!

(And yes, the name is a reference to the movie _Back to the Future_. If you haven't seen it you should.)

[Visit](https://88mph.app)

### Astrodrop

Astrodrop lets users create cheap & massive ERC-20/ERC-721 token airdrops with millions of recipients, using Merkle trees.

It is completely decentralized, since it uses [IPFS](https://ipfs.io) to store & process the airdrop data.

The coolest part is its usage of [the Graph](https://thegraph.com), which allows users to view all of the airdrops they are eligible for.

[Visit](https://astrodrop.xyz)

## Inactive but still usable projects

### Pool DAI

A no-loss donation protocol enabling people to pool money together, lend it out, and donate the interest to a cause. It uses Compound to generate the interest.

[Visit](https://zeframlou.github.io/pooldai/)

### GetRichQuick

A tool for launching ICOs. It uses DAI to denominate the token price, and offers a customizable ICO page where users can buy your tokens using a nice web interface & Metamask. The ICO page's metadata is hosted on IPFS of course. Also has a referral system for max degen.

[Visit](https://betoken.fund/getrichquick/create/)

## Inactive and unusable projects

### Betoken

Betoken is a crowd-powered asset management protocol. It is essentially a decentralized hedge fund where multiple managers compete in their performance to obtain more governance power of the fund.

[Visit](https://betoken.fund)

### Fantastic12

Fantastic12 is a software suite that enables turning a Discord channel into a DAO. It consists of a Discord bot for making DAO interactions such as voting, as well as a bridge frontend that connects with the user's wallet to publish the interactions onchain.

[Visit](https://f12.network/)

### Eminem

Eminem is a cheap and dirty frontend for interacting with the Eminence contracts deployed by Andre Cronje in Summer 2020. The contracts were exploited so please don't use it anymore.

[Visit](https://zeframlou.github.io/eminem/)

### WikiGit

World's first ecosystem for decentralized innovation & cooperation, powered by Ethereum.

TL;DR: WikiGit empowers projects with governing, crowdsourcing, and crowdfunding mechanisms, which form reinforcement loops that provide projects with rapid and sustainable growth from their moments of creation.

**Comment**: This was my very first serious project that uses Ethereum. It was a framework that combines a DAO, a Git repo hosted on IPFS, and a bounty system. The idea was and probably still is ahead of its time, but it was far too ambitious for one person to build unfortunately. [Radicle](https://radicle.xyz/) is probably the closest active project to it nowadays, but it still only has the DAO and Git part, not the bounty part.

[Visit](https://github.com/Project-WikiGit/WikiGit)

## Projects by 14-year-old Zefram

They're all written in Objective-C because I was young and foolish, don't judge please.

### RevS

My attempt at a framework for building generalized peer-to-peer applications that could function without a centralized server. It's in the name: "RevS" is short for revolutionize servers. I tried to use it to build a decentralized social network called Chee, but development stalled because I had to graduate from middle school. It was never going to work since the network routing is stupid, as it literally just uses random routes to search for a piece of data (I tried to use finger tables but didn't quite understand them).

This is actually the precise reason I jumped into Ethereum dapp development: it's exactly what I wanted to achieve!

[Visit](https://github.com/ZeframLou/RevS)

### p2pLazer

This is a P2P networking library (similar in purpose to [libp2p](https://libp2p.io/)) that's taken from RevS. Looking back, it's actually insane that I dove into the weeds of P2P networking and got a pretty good understanding of NATs and techniques to get around them like TCP/UDP hole punching, when I had no business doing so.

[Visit](https://github.com/ZeframLou/p2pLazer)
