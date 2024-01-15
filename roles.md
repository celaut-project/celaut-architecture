## Different types of role users on the system

As users, we can play three types of roles:

- Node maintainer (similar to someone maintaining a miner in a blockchain).
- Service developer. These can be run by anyone on any node (any compatible node, in terms of architecture, etc.).
- Users who launch services on nodes.

Therefore, the person maintaining a node (type 1 user) doesn’t concern themselves with whether it’s mining PoW, running a trading bot, analyzing a DNA sequence, or whatever the services it runs do. They simply execute the services that type 3 users request, in exchange for proof of payment (on a blockchain or whatever method of payment is accepted). The developer (type 2 user) only needs to send it to one or multiple nodes, and these will handle distributing the service among others and/or uploading it to a reputation system[¹],  so that users (or other services) know if use it and when and why to use it.

>This is a simple view of the system, by introducing more complexity the amount of possible user roles could also grow

[¹]: An implementation of a reputation system on the Ergo blockchain is [this](https://celaut-project.github.io/ergo-reputation-system).