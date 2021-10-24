---
layout: post
title:  "Intro Voting Based Consensus"
category: "Distributed Systems & Consensus"
date:   2021-09-20 00:00:00 +0700
---

Now that we have an understand of the fundamentals of distributed systems and distributed consensus.

Our main focus for the next section is that of classical consensus mechanisms which have been the backbone of distributed system for decades, where file stores had to be safely and consistently shared across a network, used by large enterprises around the world. 

These mechanisms primarily had processes explicitly vote on new updates to the system, usually in a series of rounds. Based on formal distributed consensus research, these consensus mechanisms focused on backing in sound mathematical reasoning and formal proofs. They were often very difficult to implement, and when deployed, were usually run on networks with very few nodes - especially when compared to the global blockchain networks of today. 

In this section, we'll take a look at some classical consensus mechanisms and their impact.

After, we'll see their evolution and how they inspired the blockchain systems of today.