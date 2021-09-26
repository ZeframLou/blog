---
title: 'DAOmesh: Large-scale collaboration through a network of small DAOs connected by bounties'
date: 2019-05-17T21:12:00.003-07:00
draft: false
url: /2019/05/daomesh-large-scale-collaboration.html
tags: 
- DeFi
- DAO
- Ethereum
---

Or: World Wide Web for a collaborative economy
==============================================

[![](https://1.bp.blogspot.com/-V3yeit1QR7A/XpVVo06nXqI/AAAAAAAAGJE/N9i-VhNQzssuA0_XjXBIXmlDWz5v8uWbgCLcBGAsYHQ/s320/daomesh.png)](https://1.bp.blogspot.com/-V3yeit1QR7A/XpVVo06nXqI/AAAAAAAAGJE/N9i-VhNQzssuA0_XjXBIXmlDWz5v8uWbgCLcBGAsYHQ/s1600/daomesh.png)

**1\. Intro**
-------------

**Decentralized Autonomous Organizations (DAOs)** are organizations where members collaborate through a smart contract enabled blockchain. Compared to traditional organizations, DAOs are much cheaper to create, their immutability and transparency makes them more trustworthy, and their programmability enables a wide variety of features. It is possible that DAOs are the next evolutionary step for corporations, which makes up most of today's world economy.

Some DAO researchers/developers ([DAOStack](https://medium.com/daostack/holographic-consensus-part-1-116a73ba1e1c), Colony) believe there may one day exist DAOs with thousands or even millions of members, and are working towards that vision. Others (Aragon, MolochDAO) neither support or rebuke this belief, but they implicitly (and perhaps unconsciously) support it by placing their focus on the internal mechanisms of DAOs, rather than the interactions between DAOs. It's likely the case that this belief is the mainstream.

I believe there's no conclusive evidence yet about whether such "Mega-DAO" models can produce feasible solutions for achieving complex large-scale collaboration. MakerDAO, which some claim is the most successful DAO today, has had 5000-7000 voters, but it is not remotely on the same level of complexity as corporations.

It is my belief that Mega-DAOs will not be good solutions for collaboration. The main reason I have is that I believe reputation voting is a necessary condition for a well-functioning DAO \[[my rationale](https://www.zeframlou.com/2019/02/why-voting-tokens-are-fking-horrible.html)\], and I also believe that quantifying the relative reputations of a large number of people is an intractable problem, unless your definition of reputation is very specific \[[see Betoken](https://github.com/Betoken/Whitepaper/blob/master/BetokenWhitepaper.pdf)\].

Therefore, I would like to present an alternative model to Mega-DAO: DAOmesh. It is by no means perfect, and it's certainly possible that it's also flawed in some significant way, but it definitely points to a new and interesting path that leads to a whole different set of innovations. Personally, I think it's a lot more exciting than Mega-DAO; to understand why, do read on.

**2\. DAOmesh**
---------------

### 2.1 Network of small DAOs

DAOs are hard to scale. As the number of members grow, the effort needed for sufficient communication grows, and the time it takes to make a decision also grows. Conflicts of interest, factions, bribery, voter apathy, and other messy problems we observe in existing democracies also gradually become non-negligible.

DAOStack is probably the current champion of DAO scaling following the Mega-DAO vision. Their [Holographic Consensus](https://medium.com/daostack/holographic-consensus-part-1-116a73ba1e1c) model is in my opinion an admirable attempt at designing highly-scalable-DAOs. However, I think it only solves some of the pains that come with scaling, and tricky problems like [p+epsilon attacks](https://blog.ethereum.org/2015/01/28/p-epsilon-attack/) will most likely persist. I'd of course love to see the project flourish, but as of now I'm not convinced that they will be able to solve all of the problems that come with scaling, or that Holographic Consensus will be as highly scalable as they claim.

I claim that **a better and more scalable model is to have a large network of small DAOs**. I call this model **DAOmesh**. DAOmesh has three advantages over Mega-DAO:

1.  **Painless (the most major advantage):** Since each DAO only has a small number of people (maybe a dozen), none of the pains of scaling arise.
2.  **Reputation system:** Assigning reputation to a small number of people is easy, and obviously so. Therefore, a good reputation system can be implemented within each DAO, and a good reputation voting system can thus also be achieved.
3.  **Identity assumption:** Since each DAO is small, it's safe to assume that the members would know one another on a personal basis. Therefore, each DAO effectively has an identity solution, which means innovations that require an identity solution, such as [Quadratic Voting](https://en.wikipedia.org/wiki/Quadratic_voting) and [Liberal Radicalism](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=3243656), may now be integrated into each DAO.

(Note: Each DAO doesn't have to implement a reputation system or Quadratic Voting, they are free to use whatever sort of system they'd like. I'd recommend them to do so though.)

However, these advantages would be meaningless if the DAOs live in isolation and do not interact with each other in a meaningful way; it would then be basically saying that giving up on scaling is a scaling solution. This is why the DAOmesh model places its focus not on the internal workings of each individual DAO, but on how the DAOs interact and collaborate with one another. DAOs in the DAOmesh will work for each other and assign work to each other through the use of bounties, which will be discussed in the following section.

### 2.2 Connecting DAOs using bounties

In order for an individual DAO to be able to produce products beyond the combined capabilities of its members, it needs to employ the help of others. Since the DAOs in the DAOmesh are small, this need almost always arises. The simplest solution is to give each DAO **the ability to post bounties**: a DAO can associate a financial reward with completing a task it wants done, and anyone who is capable of completing it may do so and send the result to the DAO, receiving the reward as compensation. This way, each DAO can achieve anything it wants to achieve, as long as it has the funds.

If one assume that each bounty would be taken up _by a single person_, then it's easy to see the "problem" with this set-up: the number of people who's work a DAO can utilize _only scales linearly_ with the number of bounties it posts.

*   To be able to utilize 1000 people, a DAO needs to post 1000 bounties. If each bounty costs $100, it would cost a DAO ​$100,000. If a DAO wants to utilize 1 million people, it would cost ​$100 million. That's hardly realistic or efficient.

Another problem would be that each bounty cannot be too complex, since it would be handled by just a single person.

*   If Apple's board of directors was a DAO, and it wants to achieve the task "Develop the next-gen iPhone", placing a bounty for it would be absurd, since it involves hardware development, software development, design, user-testing, and a myriad of other work, which can't possibly be handled by a single person. Thus, the board of directors would have to split the task into bite-sized chunks, which is in itself a difficult and costly task.

The two problems above can be easily solved by also giving DAOs **the ability to take on bounties**. This not only allows each bounty to be worked on by an arbitrarily large amount of people, but also allows for highly complex and/or abstract bounties to be placed.

*   If Apple's board of directors now place a bounty for developing the next-gen iPhone, this bounty could be taken up by a phone-building DAO, who would split the task into smaller tasks like "develop the new iOS" "design the chassis" "develop the new CPU" and so on.
*   The smaller tasks would then be taken on by DAOs who specialize in the respective fields, who would split the tasks down into even smaller tasks; this task-division process would continue until each task could be taken on by a single person.
*   After all the bounties placed by the phone-building DAO are completed, the DAO would work on combining the results into a coherent product (or perhaps just place another bounty to let someone else do it), and turn in the finished design to Apple.

From this example, we can see that:

1.  The number of people working on a bounty scales automatically based on the complexity of the task.
2.  A highly complex/abstract task is automatically broken up into pieces that a single person is able to take on.

These two properties of the DAOmesh means that **large-scale collaboration can be spontaneously and automatically formed whenever the need arises**, and utilizing this power is as simple as posting a bounty. I think this makes the DAOmesh an incredibly powerful tool for collaboration and producing creative work, and its fluidity & flexibility makes it superior the artificially-constructed rigid collaboration mechanisms seen in Mega-DAOs.

### 2.3 Liquid hierarchy

How would the DAOmesh come into being, and what would it look like?

Since bounty platforms already exist (Bounties Network, Gitcoin, etc.), at the DAOmesh's genesis DAOs can immediately begin placing bounties. Bounty-taking DAOs are non-existent at this point, so the bounties would be taken up by the existing individual bounty-hunters. These DAOs would form the bottom-most layer of the DAOmesh, who are in direct contact with individual workers.

As this layer of DAOs is consolidating, the next layer would begin to form on top of it. This would happen either via the creation of DAOs dealing with more complex tasks, or via existing bottom-layer DAOs evolving in task-complexity and beginning to place bounties more suitable for DAOs to take on. At this point, there would exist two levels of DAOs: DAOs who employ individuals, and DAOs who employ DAOs who employ individuals. We can call the first level level-1 and the second level level-2, based on the distance from the DAO to individual workers.

The evolution of the DAOmesh would probably look like a pyramid being built: the bottom level is built first, then the next, smaller level on top of it, then the next, even smaller level on top of this level, so on and so forth. As we go from the bottom to the top, the number of DAOs on each level decreases, the tasks that DAOs work on become increasingly complex and abstract, and the expenditures of each DAO increases, since the cost of each bounty grows exponentially as the complexity grows (because the number of people working on it grows exponentially).

Capital would seep down from the top surface of this pyramid to the bottom, each level absorbing a bit of it, while work would float up from the bottom, being combined into more and more complex products as it rises through each level, eventually culminating at the top into amazing fruits of collaboration worthy of the number of people who have contributed to it. This kind of large-scale collaboration would all be achieved not by using any explicit command hierarchy or power structure, but instead by using nothing more than simple economic links formed via bounties.

From the previous descriptions, it's obvious that hierarchy would exist in the DAOmesh, but it is formed not out of coercion or some arbitrary rules, but out of mutual benefit, and DAOs could freely (and perhaps naturally) move up and down the hierarchy as their goals & needs change over time. I think there's no name more fitting for this model than "liquid hierarchy".

### 2.4 Confederation to support public goods

In many cases, DAOs working in the same field may want to form explicit socio-political links, in order to fund public goods beneficial for everyone in the field. The need for such confederation arises when the public goods cost more than a single DAO could handle.

There are many ways that this can be implemented.

1.  We could construct meta-DAOs where all the members are DAOs. Member DAOs could pool their resources together to fund public goods, either using the MolochDAO model where members vote on funding proposals, or using Liberal Radicalism where members create a donation-matching pool.
2.  DAOs could give out reputation tokens as bounty rewards, through which a complex web of power dependencies would be formed. DAOs working on similar things would gravitate towards each other and eventually merge into a federation. (Thanks to Luke Duncan for this idea)
3.  DAOs could form bilateral partnerships where they exchange reputation tokens, which would make them gravitate towards each other in the same way as 2.

### 2.5 DAO specifications summary

Each DAO in the DAOmesh should absolutely have the following features:

*   Has around a dozen members (or some other reasonable small amount)
*   Can work on bounties as a single entity
*   Can place bounties
*   Can distribute income among members & the DAO's treasury

and most likely should have these features as well:

*   Use voting to make group decisions
*   Add & remove members
*   Reorganize how funds & power are distributed among members

and probably should choose some of these nice-to-have features:

*   Quadratic voting
*   Use Liberal Radicalism for budgeting
*   Reputation voting
*   Rage-quit (like MolochDAO)

**3\. Potential objections & replies**
--------------------------------------

### 3.1 DAOmesh can't handle protocol governance

#### **3.1.1 Objection**

There doesn't seem to be any obvious way for the DAOmesh to be used for protocol governance. The DAOmesh as a whole doesn't really have any way of representing shareholder interests of any sort, since there is no central decision-making process. Individual DAOs in the mesh only contain a small number of people, not really suitable for letting the users of a protocol to exercise any rights, unless they act as some kind of executive council; even then, DAOmesh doesn't provide any way for the users to constrain the power of this council.

Overall, DAOmesh doesn't provide any new tools for building up a protocol governance system that lets the users & shareholders of the protocol participate in the decision-making process.

#### **3.1.2 Reply**

This objection is exactly right, protocol governance is not what DAOmesh is trying to achieve.

I believe that there are two vastly different types of DAOs, each serving a different purpose:

*   One type focuses on **representation**: making decisions legitimized by the representation of the interests of some group of people, usually the users of some protocol/product.

*   Example: MakerDAO makes decisions regarding the interest rate of DAI loans, and whatever they decide on is deemed legitimate and carried out in the MakerDAO protocol, because the DAO is supposed to represent the interests of users of the protocol (which is essentially maintaining the stability of DAI).

*   The other type focuses on **collaboration**: facilitating people teaming up to work on a common goal by providing things like incentive structures, profit-splitting mechanisms, work allocation mechanisms, and decision-making processes.

*   Example: Decentralized companies, decentralized non-profits.

*   To make an analogy, the first type of DAOs are like governments, while the second type of DAOs are like companies: a constitutional republic focuses on representation and legitimacy, while a limited liability company focuses on the efficient collaboration among its employees.

DAOmesh definitely belongs to the second type. Its purpose is to make it easy for a group of like-minded people to form a team and begin working on some project, not to solve protocol governance.

Mega-DAO models usually focus on representation, but most of them also try to handle collaboration, which is one reason I don't really like them: if you haven't even solved one hard problem, what makes you think you can solve two hard problems at the same time?

### 3.2 High-level DAOs would be exploiting low-level DAOs

#### **3.2.1 Objection**

DAOmesh's division between the capital-providing DAOs on the higher levels and the work-providing DAOs on the lower levels seems suspiciously similar to capitalism. Given that there's no such thing as "market regulation" or "anti-trust laws" in DAOmesh, won't high-level DAOs become monopolistic or collude with each other, so that low-level DAOs are exploited and get paid far less than what they deserve, similar to what happened in early-stage capitalistic economies?

#### **3.2.2 Reply**

It is possible that exploitation would happen, if DAOmesh was a closed economy. However, while it is the case that DAOs can work for other DAOs, it is not the case that they _have_ to do so. Bounty-hunters provide services for everyone: individuals, companies, governments, et cetera, not just DAOs. Bounty platforms are usually not restricted to any geographical location either, so bounty-creators and bounty-hunters could come from anywhere around the globe. This means DAOmesh will be a part of the global market, rather than a walled garden, and the pricing of the goods & services provided by the bounty-hunters will be determined by it.

Therefore, in order to achieve the kind of market control necessary for commanding the rates at will, high-level DAOs would have to be powerful enough to dominate the global market itself. I doubt that will happen any time soon.

### 3.3 The number of DAOs & bounties would increase exponentially as task complexity grows

#### **3.3.1 Objection**

As DAOmesh begins to handle more complex work, the number of "level"s increases, and the number of DAOs needed grows exponentially. The number of bounties needed to be placed also grows exponentially. This means that both the underlying blockchain of DAOmesh and the bounty platform used must be quite scalable. However, all blockchains today scale terribly, and the same can be said about any bounty platform built upon those unscalable blockchains. Thus, DAOmesh is impractical using today's technologies.

#### **3.3.2 Reply**

I agree that the scalability of the DAOmesh is bound by the scalability of the underlying blockchain. I don't really have a good answer to this objection, as blockchain scaling is a highly nontrivial problem, but if I had to say something, I'd probably say that we can probably move most of the bounty platform off-chain using some kind of a counter-factual dispute resolution system. Obviously the DAOs have to stay on-chain, but if they keep the frequency of voting low, maybe through budgeting on a weekly/monthly basis, it should be feasible for even existing blockchains to handle the DAOmesh.

**4\. Conclusion: the DAOmesh vision**
--------------------------------------

What do I think DAOmesh will achieve? Two world-changing things.

### One: World Wide Web for a collaborative economy

I think DAOmesh will become **the base protocol for a radically new economy**.

This economy will exist **entirely on the blockchain**, consisting of a multitude of businesses and non-profits, all of which are decentralized & autonomous. It will likely output billions of dollars' worth of digital work every year.

This economy will be global and open to a mind-boggling degree: a group of people from all over the world will be able to band together, pool some initial funding, and immediately start working together. They will be able to:

*   hire other people/DAOs from **a global labor market** to help them work on things both inside and outside of their expertise,
*   sell and promote their finished work as a single entity,
*   automatically share any profits they make,
*   make group decisions via any kind of voting system they like,
*   exit the group and get their share of the treasury instantly,
*   and utilize all the powerful tools that decentralized finance has to offer.

They will be able to do all this **without hiring a single lawyer, signing a single contract, filling out a single form, opening a single bank account**; they will probably never even meet each other in person. They will get all this by paying at most a few dollars of transaction fees.

I think the one thing that's the most analogous to this new economy is **the World Wide Web**.

*   WWW: websites connected via hyperlinks, forming a global, decentralized, permissionless network of information
*   DAOmesh: organizations connected via bounties, forming a global, decentralized, permissionless network of economic activity

I honestly would not be surprised if DAOmesh grew in the same trajectory as the WWW.

### Two: Widespread cryptocurrency adoption

In my opinion, global widespread cryptocurrency adoption will likely never come until the new economy I mentioned comes into being.

The main reason that most people don't use cryptocurrency today is that **most people get paid in fiat, so there's virtually no demand for crypto-accepting businesses**. Since there's virtually no demand for crypto-accepting businesses, it's no wonder that the supply for them is also tiny. And since few businesses accept crypto, the utility of crypto is small, which in turn causes the low demand. It's a vicious cycle borne out of a fiat-dominated world.

A decentralized economy can solve the problems on both the demand side and the supply side. DAOs not only natively accept crypto payments in exchange for their goods & services, but also provide job opportunities that natively pays in crypto.

* * *

I sincerely hope that the world will benefit from this document, even if just a little.

{{<remarkbox>}}
