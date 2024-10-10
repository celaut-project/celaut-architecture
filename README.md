# CELAUT: A peer-to-peer architecture for software design and distribution

<br>


## Context
In the 1940s, mathematician John von Neumann, in collaboration with Stanislaw Ulam, introduced the concept of cellular automata. Their initial work sought to create a mathematical model for self-replicating systems, laying the groundwork for later explorations of how simple rules could lead to complex behaviors. Building on this foundation, in 1970, mathematician John Horton Conway introduced a well-known cellular automaton called "The Game of Life." A cellular automaton serves as a mathematical and computational model for a dynamic system that evolves in discrete steps.

The Game of Life, like von Neumann's earlier models, suggests that complex structures can emerge from a set of simple rules. This system consists of a group of agents (or cells) that occupy a space and follow rules that dictate their interactions with other agents. In a way, this mirrors the evolution of a living ecosystem, constantly adapting and optimizing processes without conscious intention.

This same principle can be applied to the capacity of competitive economic systems to enhance their processes. When a company explores new technologies to reduce costs, it does so not for the common good but to outperform rivals. Yet, unconsciously, it contributes to the common good. The market will determine whether the new approach to a task is more optimal or not.

Competition of ideas, processes, and methods is what allows us to improve our way of life. For instance, in industrial or logistical processes, if someone devises a more efficient method, they create a company to implement it. If it proves better than the traditional method, it gains a larger market share, surpassing the previous approach.

However, real-world evolution is slow to observe due to the time required for tangible results. Conversely, in simulated environments, new action proposals can be observed much faster, considering more options and allowing for the immediate application of the best approach.

The computer revolution of recent decades provides us with the ability to simulate and automate processes. A network of computers with these capabilities has been established, offering tremendous potential. Cutting-edge technologies such as artificial intelligence promise a significant improvement in our quality of life, primarily through their potential to automate tasks beyond previous imagination.

In a cellular automaton, the fewer and/or less complex the rules governing agent interactions, the broader the spectrum of complexity the automaton can achieve. In other words, more rules lead to greater limitations.

<br>


## Definition

*CELAUT is a set of simple rules for software design and distribution.*

<br>


### Principles

1. Descentralization
2. Simplicity
3. Determinism

<br>

*CELAUT is based on two main elements: nodes and services.*

### Nodes

A *node* is a **computer** on the network that can find and communicate with other nodes. It has the ability to share, build, and orchestrate services between them.

#### Node responsabilities:

1. **Service Execution**: Handles service instance requests, balancing the load between running them 
locally or on its peer nodes. This ensures an efficient distribution of tasks and resources across the network, optimizing system performance.

2. **Communication Interface**: Provides a robust and flexible interface that enables the services that it executes to communicate seamlessly with it, ensuring efficient data exchange and coordination.

3. **Address and Token Provisioning**: Offers a streamlined process for obtaining the communication address and authentication token of a service required for interaction, enhancing security and accessibility.

4. **Dependency Management**: Takes care of ensuring that services have access to the addresses of their dependencies, irrespective of the node on which they are executed, promoting a smooth and efficient service ecosystem.

>An implementation of a node using Python3 and Rust: [Nodo](https://github.com/celaut-project/nodo)

<br>


### Services

A *service* is **deterministic** software container that performs a specific task, whose specification is found in a binary file. They follow the idea of a "black box" or a lambda function. Could be called "bots" too.

When a user wants to execute a service, it sends it to a node. Every execution instance is for one client.

Generally, services are run as containers (isolated processes) or virtual machines, depending on how the node in question works with the service architecture, if it supports it.

>For example, a node with the architecture linux/arm64v8 can execute services with that architecture using Docker containers. If it wants to execute a windows/x86 service, it must execute it using a virtual machine. However, this is transparent to the services.

A characteristic property of services is that they can request the node that is executing them to execute another service, that is, a child service. This allows for certain very interesting software patterns.

>An implementation example of a service that classifies and test other services: [Sort sat solver](https://github.com/copa-ai/sort-sat-solver)

<br>

**This architecture allows services to focus on their functionality, without worrying about the underlying infrastructure. Nodes, for their part, can efficiently manage the execution of instances, without worrying about their usefulness.**

<br>


##  How a service is specified?

<br>

The specification of a service in CELAUT consists of three main components:


### Container | *BOX*
This component defines the environment in which the service will run, including the hardware and software requirements. It specifies the architecture, entry point, filesystem, and environment variables of the service.


### Interface | *API*
This component defines how the service can be interacted with, including the ports it listens on, the communication protocols it supports, and the methods it defines. It specifies the application protocol, the slots, and the cost function (optional).


### Network | *NET*

<br><br>

The specification of a service is a key part of the CELAUT architecture, as it allows services to be deployed and executed in a consistent and predictable manner. 

It also allows for services to be shared and reused across the network, which can help to reduce development costs and improve the overall efficiency of the system.

<br>

The node will load the service from the binary and provide it with the resources it needs to run.

There is no single way to define a service.
For example, [Proto3 implementation](https://github.com/celaut-project/service-lib/blob/master/node-driver/src/node_driver/gateway/protos/celaut.proto#L66) is one of many possible variations.

<br>

Not all nodes will accept all possible variations of a service specification.

>For example, node A understands a specific proto3 specification and one in JSON. Another node B understands the JSON specification and another in JSON+zip file system. Both nodes can transmit services of the specification they have in common, in this case, JSON.

<br>

## Different types of role users on the system

As users, we can play three types of roles:

- Node maintainer (similar to someone maintaining a miner in a blockchain).
- Service developer. These can be run by anyone on any node (any compatible node, in terms of architecture, etc.).
- Users who launch services on nodes.

Therefore, the person maintaining a node (type 1 user) doesn’t concern themselves with whether it’s mining PoW, running a trading bot, analyzing a DNA sequence, or whatever the services it runs do. They simply execute the services that type 3 users request, in exchange for proof of payment (on a blockchain or whatever method of payment is accepted). The developer (type 2 user) only needs to send it to one or multiple nodes, and these will handle distributing the service among others and/or uploading it to a reputation system,  so that users (or other services) know if use it and when and why to use it.

>This is a simple view of the system, by introducing more complexity the amount of possible user roles could also grow

<br>


## Following Nature's Footsteps in Digital Ecosystems

Imagine CELAUT as a digital ecosystem, mirroring the dynamics of a biological ecosystem found in nature. In this analogy:

1. Nodes as Organisms: Nodes within CELAUT can be likened to organisms in a natural ecosystem. Each node represents a distinct entity with its own capabilities and functions, akin to different species occupying various niches in the environment. These nodes interact with each other, forming a network akin to the interconnected web of life found in ecosystems.

2. Services as Biological Functions: Services within CELAUT are analogous to biological functions or processes found in organisms. Each service performs a specific task, similar to how organs in living organisms carry out specialized functions. Just as organs work together harmoniously to sustain life, services collaborate within nodes to fulfill diverse computational needs.

3. Decentralization as Diversity: The decentralization principle of CELAUT can be equated with biodiversity in natural ecosystems. In nature, biodiversity ensures resilience and adaptability, as diverse species contribute to ecosystem stability and functionality. Similarly, decentralization in CELAUT mitigates risks associated with single points of failure and enhances the system's ability to adapt to changing conditions.

4. Efficiency as Energy Optimization: Efficiency in CELAUT mirrors the energy optimization observed in natural systems. In biological ecosystems, energy flows through food webs, with organisms optimizing energy expenditure to maximize survival and reproduction. Likewise, CELAUT optimizes computational resources, distributing tasks across nodes to minimize latency and resource wastage.

5. Simplicity and Determinism as Natural Laws: The principles of simplicity and determinism in CELAUT resonate with the underlying laws governing natural systems. Just as physical laws dictate the behavior of matter and energy in the universe, CELAUT's simple rules govern the interactions between nodes and services. This deterministic framework ensures consistency and predictability, analogous to the predictability of natural phenomena governed by fundamental laws.

<br>


## Trust systems

In CELAUT, the different parts of the system, nodes and services, do not trust each other, therefore it is a trustless system. This is why it is unlikely that a node will execute services for free, or that a service will not work without making a payment in a contract and receiving proof of it (although obviously they can do it if they want, in the case of services it is economically feasible because they have a marginal cost of zero). 
<br>However, to allow interaction between these parts without trust between them, contracts, social contracts (in a society of nodes and services), are needed to transmit value and assign reputation to each part. Therefore, we have two types of systems (from a relatively abstract point of view): payment systems and reputation systems.

> A possible strategy for a node is to offer the execution of services without exchanging value at the beginning, to increase its reputation and, when it has reputation from others, start to increase its cost.

> Unlike nodes, the nature of services is to have a marginal cost of zero, this means that they do not have a limit on the number of simultaneous units in which they are executed (since the cost of executing them falls on the nodes), so it is quite likely that many services will start with a cost of zero to gain reputation, require a cost when they have reputation and remain competitive, and return to a cost of zero when they cease to be competitive.


### Payment systems

Payment systems allow for the transfer of value between entities in CELAUT. Here are some possible types:

#### License Smart Contracts

A contract system that allows for the issuance of usage licenses for services and nodes, where Ledger is the network where truth is agreed upon. In this way, if A wants to execute a method of B, it will check its contract, execute the defined command (connecting to the Ledger), and the Ledger's contract will issue a license, which A will send to B to enable it to execute the desired method.

There are four distinct types of licenses based on two different classifications. On one hand, whether the license is elastic or static, and on the other, whether it is interactive or non-interactive.

- **Elastic licenses** are those that allow for the restriction of their usage based on certain parameters (number of requests, time, methods, environment variables, etc.).

- **Static licenses** are those that do not restrict usage. B knows the license keys, and the contract provides the license without being able to limit its usage.

- **Interactive licenses** require B to connect to the Ledger to verify the validity of the provided license.

- **Non-interactive** licenses do not require B to connect to the Ledger to verify the validity of the provided license.

<br>

This results in the four types of licenses:

- Interactive static (Very straightforward - Not very useful)
- Non-interactive static (Better for services)
- Interactive elastic (Better for nodes)
- Non-interactive elastic (Quite complex - Versatile)

<br>

> Ledgers can be public and permissionless networks like Bitcoin or Ergo, or private closed platforms like Stripe. The only requirement is that all participants must support them.

<br>


### Reputation systems

Reputation systems allow users, nodes, and services to create a social ecosystem upon which to make decisions. For nodes, they need to know which peers they can trust to request the execution of services. 
For users, who execute services, it helps them determine which services will perform best for the task they wish to carry out.

In Celaut, reputation is represented as records on Ledgers, which represent an opinion.

In the case of services, their deterministic nature provides a different perspective on their reputation compared to nodes. 
A reputation proof (a record) published some time ago may hold the same value as a current one regarding a service (this is true when the service does not interact with networks, which is the default form of a service, completely isolated). 
If it does interact with any network, its reputation may depend on the reputation of the networks it connects to, which does not have that deterministic property, as it can change over time. This is because the service itself has not changed.

However, the reputation of a node is more valuable the more recent it is, as its behavior can vary over time. 
When nodes present themselves to each other, they show proofs of their reputation, and others may opine non-consensually on whether they are more or less trustworthy.

Each node, service, or other type of actor in a reputation system trusts various sources to varying degrees, and these sources, in turn, trust different sources, nodes, services, or other entities to varying degrees. Thus, when a certain actor is presented with an unknown entity, they will check the opinions of their trusted sources.

For a more specific understanding of how a reputation system works, you can read: [Sigma Reputation Panel Documentation](https://github.com/reputation-systems/sigma-reputation-panel/blob/master/README.md)

<br>


## Why is this necessary

CELAUT intend to solve is precisely the separation between the “*how to solve a problem*” and the “*where and who solve it*”.

Take, for example, a trading bot.

>Trading bots are automated software programs that execute buy and sell orders in financial markets based on predefined algorithms. They are important as they can operate 24/7, react quickly to market changes, and remove emotional biases, enhancing efficiency and consistency in trading strategies.


<br>

In this context, if you want to use a trading bot right now, You will go to the web and can:

1. Look for a web service that will manage your asset portfolio, which has:
    1. Advantages:
        1. You don’t need to run the infrastructure yourself.
        2. You don’t need to configure anything.
    2. Disadvantages:
        1. You can’t attribute reputation to it because the developer of the web
        service is unable to prove that the system hasn’t changed (for example,
        when a bot has gained a large number of users, they might reduce
        its performance to encourage you to use a newer one).
        2. The developers of the web service can’t assure you that they aren’t
        misusing the data from your requests (in this case, the
        movements of your portfolio).
2. Search for a source code (on GitHub, etc.) that you can run on your PC (or in the cloud) on your own.
    1. Advantages:
        1. It’s deterministic, in the sense that (if it can’t connect to the
        internet) you’ll be sure that its behavior and/or performance won’t change in the future, because the developer can't modify the source that you previously downloaded.
        2. The developer of the service has no control over the data of your requests.
    2. Disadvantages:
        1. You need to possess equipment (infrastructure) capable of running the code.
        2. You have to deal with system configuration issues (which are often
        significant enough for an average user to opt for a web service).

In contra part of this two options, CELAUT allows to take the advangates of the two previous solutions without their disadvantages. There’s why:



- Infrastructure management is unnecessary, as the nodes handle it. There is no need to seek out a cloud provider.

- No configuration is required. The specification service covers how the container is built, its architecture, its network requirements, and its interface. Users do not need to be concerned about any of this.

- Service developers cannot control, modify, or extract data from the service. They do not control the nodes that distribute and run it. However, they may be incentivized to create it.

<br>


## System behavior

This section describes the system behavior, which includes interactions between the parts of the system, 
in order to show the nature of the architecture with greater clarity.

- [Execution of a service](execution_of_a_service.md)
- [Service load balancing](service_balancer.md)
- [Node handshake]()

<br>


## Design patterns

Design patterns are common solutions to common problems in software development. They are a way to share knowledge and experience among developers.


- [Classifier pattern]()
- [Mirror pattern]()
- [Genetic pattern]()

<br>


## Possible Asked Questions

### How do multiple clients make requests to a specific service?

Based on the architecture developed earlier, if a client wants to use a service, it requests the creation of an instance of it on a node. Therefore, if n clients want to use the service, n instances of it will be needed. In the end, an instance of a service, a container, is nothing more than an isolated thread. Therefore, the client/server paradigm is altered when talking about services on a trustless distributed system. Instead of one server serving multiple clients, a client requests the deployment of a service. In terms of performance, there should not be a big difference between one scheme and another, since the centralized server ends up executing n threads for n client requests. In distributed services, these threads are isolated (<span style="color: gray">which can be a negative point regarding shared memory usage, but this is solved with some other patterns</span>) and are distributed among the nodes in the network.

To create a web service that can be connected to a frontend in a browser, a new service is required to handle incoming requests from clients and deploy and use the classification service. This service, as shown in *Figure 118*, can be understood as a bridge between the "traditional web" and a distributed service network.

![cealut_bridge_to_common_web](assets/188c27-cealut_bridge_to_common_web.excalidraw.svg)*__Figure 118__: Celaut service bridge to a common web pattern*

<br>


### Multiple instances cannot share dependencies

The nature of the network creates a hierarchy of service instances distributed across the nodes of the same. 
This means that when an instance (parent) requests an instance of another service (child or dependency), the latter will become dependent on the former, with the parent assuming the right to decide when the child should be stopped and the responsibility for its resource consumption (in case a node tracks the consumption of each instance, it must take into account that of its dependencies). 

In this way, if the parent is stopped, the node where its child is running can stop it. If it were not so, a node would not know which instances are in a 'zombie' state since none of its clients (parent instances) would be responsible.

<br>


### Why include the entire filesystem in the specification of a service?

The specification of a service must define it completely and comprehensively to avoid redundancy among different services. 

This can lead to problems such as the size of the specification, but these problems can be solved in a higher abstraction layer, such as the 
[pee-rpc protocol](https://github.com/pee-rpc-protocol/pee-rpc#using-blocks-buffer-containers)
does.

>Using Dockerfiles to define a service would not be possible to verify the authenticity of the container, since the Dockerfile defines how to build the container and, generally, are download instructions from central repositories, and they can change the result over the time. A node can accept a specification that uses Dockerfiles, but it would not be in line with the principles of the architecture.

<br>


### Hash Algorithm Identification

To avoid collisions when identifying different hash algorithms, they are identified by applying their own algorithm to an empty input, that is, an empty bit string. 

For example:
- **Sha2562-256 utf-8**: e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855

- **Sha3-256 uft-8**: a7ffc6f8bf1ed76651c14756a061d662f580ff4de43b49fa82d80a4b80f8434a

- **Shake-256 utf-8 of 256 bits**: 46b9dd2b0ba88d13233b3feb743eeb243fcd52ea62b81b82b50c27646ed5762f

- **Sha2562-256 utf-8 over Sha256-256 utf-8**: cd372fb85148700fa88095e3492d3f9f5beb43e555e5ff26d95f5a6adc36f8e6

<br>

In this way, the word "*CELAUT*" would be:
- Sha2562-256 utf-8:

    - type: e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855
    - value: d7f901be75b36a2ccef2fcc61f9c0665af4155ccee1eda8c4afa1a4f994e825c 
    
- Sha3-256 utf-8:
    - type: a7ffc6f8bf1ed76651c14756a061d662f580ff4de43b49fa82d80a4b80f8434a
    - value: de1a91208f7c6d320cbc50e45952fe40cb18a949f8a4daae0f8428fc60523f09

- Shake-256 utf-8 of 256 bits:
    - type: 46b9dd2b0ba88d13233b3feb743eeb243fcd52ea62b81b82b50c27646ed5762f
    - value: d10ca3f8a2ab79a8b841876780d232770e70a22cbcc8769a0a1a44194702ee7c

<br>

To avoid collisions with similar algorithms 
<span style="color: gray">(or variations of one, is the same)</span> 
double algorithm identification could be used, for example:
- Sha2562-256 utf-8 over Sha256-256 utf-8:

    - type: cd372fb85148700fa88095e3492d3f9f5beb43e555e5ff26d95f5a6adc36f8e6
    - value: 22bcde154d5f214fe34a5e2b862c0b5aee07d04f62b293b749727ce4b2bea9ad 


<br>

In this way, no centralized registry is required to agree on which identifier corresponds to a specific algorithm.

>In the same way as in the case described in the question regarding the file system, a node is not required to use this hash identification format. This solution is presented because it is in line with the CELAUT principles.


Other way to solve the problem could be 
[multihash from Protocol Labs](https://github.com/multiformats/multihash#format).
But it needs to have a consensus to say what algorithms has what identifier codes.


### How does CELAUT's peer-to-peer network architecture relate to orchestrators like Kubernetes or  Apache Mesos ?

The primary distinction lies in the hierarchical structure of both 
[Kubernetes](https://kubernetes.io/docs/concepts/architecture/nodes/)  and 
[Apache Mesos](https://mesos.apache.org/documentation/latest/architecture/)
, where a single master node oversees a collection of subordinate nodes, or minions. 
In contrast, CELAUT employs a decentralized approach, where no individual node holds authority over another, fostering a trustless environment that can support a vast and globally distributed computational network.

CELAUT offers several integration and utilization possibilities with existing systems:

- Evolving them so that the node operates as a master node in these systems and treats the other peers as subordinate minions (even if they are not, meaning compensating them).

- Operating as standalone services within the distributed network, assuming responsibility for load balancing and coordinating other child services in a centralized fashion. This role can prove beneficial for applications requiring centralized control and orchestration.

- Employing them within traditional centralized server environments, recognizing that CELAUT's inherent trustlessness may not be essential when all nodes are under the control of a single organization. In such scenarios, the master node assumes the responsibility of connecting to external nodes via the CELAUT architecture.

<br>
<br>

## Roadmap

This section covers the past and future development of the project by the initial development team (it is updated over time)

[Link to the roadmap](roadmap.md)

<br>


## Links

[Proof of Concept: CELAUT over IPFS, Feb '21](https://discuss.ipfs.tech/t/proof-of-concept-interplanetary-service-system/10245)

[Ergo-forum conversation, Aug '23](https://www.ergoforum.org/t/artifical-economic-intelligence-on-ergo-blockchain/4429/2)

>IPFS or Ergo are not platforms on which the architecture is based, although both are aligned with the CELAUT principles.

<br>
