---
title: 'Self-sufficient virtual organizations, and how to build them up'
date: 2018-10-08T20:50:00.000-07:00
draft: false
url: /2018/10/self-sufficient-virtual-organizations.html
tags: 
- DAO
- Ethereum
---

I believe one of the most, if not the most, important applications of blockchain and smart contact technology will be the establishment of self-sufficient organizations that are completely virtual:

*   They will use virtual currencies like Ether and ERC-20 tokens to handle all transfers & storage of value.
*   Their collaboration & making of crucial decisions will be handled by smart contacts.
*   Their members will consist of pseudo-anonymous individuals from around the world who collaborate mostly remotely.
*   They will produce products that are purely digital in nature, and use the profits to cover their operational expenses, as well as provide their members with a non-negligible salary so that they may work for the organization on a part/full-time basis.

The main challenge of accomplishing such a feat is this: _how may we replicate the highly complex, fuzzy, and subjective business logic needed for most organizations using immutable, simple, strict, and objective smart contacts?_

Two main approaches exist:

1.  **Replication**: Using formal processes to attempt replicating the complex and fuzzy logic of existing organizations. This approach usually entails reinventing existing tools for coordinating, such as Trello, GitHub, HR software, corporate voting software, so on and so forth. Examples: Colony, Aragon, WikiGit
2.  **Mechanism design**: Designing new & novel coordination systems using the restricted set of tools that smart contract technology enables, which may look nothing like existing real-world organizations. Such systems usually try to use micro-scale incentives to create macro-scale emergent behaviors that are desirable. Examples: DAOStack, Betoken

Most projects are going down the first path, likely because it's the most intuitive & easy thing to think of. I'm not saying this approach is infeasible or unequivocally reprehensible: I built WikiGit as the manifestation of my vision of what going down this path will yield in 5-15 years. If smart contract platforms one day become almost infinitely scalable, I don't see why this approach is not capable of dominance.

It is for ideological, and frankly, aesthetical reasons that I object to this approach. As I've mentioned in previous works, smart contract technology is capable of spawning a new field of political science where mechanism design works in concert with DAO-based experimentation to generate radically new systems of decision-making, incentivization, and coordination. It would be simply a huge waste to the entire mankind if replication-focused projects captured the majority of capital, talent, and the definition of "governance" itself, and delayed the blossoming of this new field by decades, perhaps even delaying the societal evolution of all mankind by centuries.

This might sound like exaggerated bullshit, and perhaps it will turn out that it is, but given the exponential growth of technological progress and the extreme importance of blockchain technology, one seemingly innocuous wrong move has the potential of leading us to a completely divergent future.

Twenty-first century residents must tread carefully. Such is our burden.

* * *

So, what exactly can we do with mechanism design to create new and novel governance systems?

One possible approach, which is the approach I'm personally using, is to first accumulate a toolbox of cryptoeconomic primitives that serve various purposes, and try to combine some of them to see if they can be pieced together into interesting constructs. Like building castles from blocks.

My toolbox roughly has the following contents right now:

*   [Incentivized Meritocracy](https://github.com/Betoken/documents/blob/master/Incentivized%20Meritocracies/Incentivized%20Meritocracies.pdf)
*   [Harberger Tax](https://medium.com/@simondlr/what-is-harberger-tax-where-does-the-blockchain-fit-in-1329046922c6)
*   [Liberal Radicalism](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=3243656)
*   [Bonding curve token issuance](https://medium.com/@simondlr/tokens-2-0-curved-token-bonding-in-curation-markets-1764a2e0bee5)
*   [TCRs (I don't like them though, not really robust until the voting part is sorted out)](https://medium.com/@ilovebagels/token-curated-registries-1-0-61a232f8dac7)
*   [Quadratic Voting (not currently usable, since it needs a good ID system)](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=2003531)

And here are the things I usually do with them:

*   Do random combinations and see if they can be pieced together into a larger symbiotic system, or if one of them can solve problems another introduces.

*   Example: A TCR that uses bonding curve to issue its tokens and handle challenge votes using Quadratic Voting

*   Pick out one thing and see if it can be used for purposes quite distant from what it was created for.

*   Example: Say there's a decentralized organization where each member has a budget they can distribute across various projects, and there is a shared budget owned by the whole organization. Liberal Radicalism may be used here for the members to allocate their personal budgets across projects, and the shared budget would be used to match up their budgets.

*   See if some of them share the same incentive structure, and if so, try to create a generalized category that encompasses them. This is a good exercise for boiling models down into the most essential ideas.

*   Example: Bonding curves and TCRs are both models that make use of token holders' drive to increase the token's price. Thus, they may be categorized as Investor Driven Models. (Not a good example, I know)

These cryptoeconomic primitives are, as the name suggests, primitive, and certainly are not capable of enabling self-sufficient virtual organizations in isolation, but I firmly believe that in conjunction, these primitives and ones that haven't been invented yet will make such organizations into reality, likely within the next 5 years.