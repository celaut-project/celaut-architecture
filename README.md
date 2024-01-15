# CELAUT: A peer-to-peer architecture for software design and distribution

<br>

## Context
In 1970, the British mathematician John Horton Conway introduced a cellular automaton called "The Game of Life." A cellular automaton serves as a mathematical and computational model for a dynamic system that evolves in discrete steps.

The Game of Life suggests that, through a set of simple rules, complex structures can emerge. This system consists of a group of agents (or cells) that occupy a space and follow rules that dictate their interactions with other agents. In a way, this mirrors the evolution of a living ecosystem, constantly improving and optimizing processes without conscious intention.

This same principle can be applied to the capacity of competitive economic systems to enhance their processes. When a company explores new technologies to reduce costs, it does so not for the common good but to outperform rivals. Yet, unconsciously, it contributes to the common good. The market will determine whether the new approach to a task is more optimal or not.

Competition of ideas, processes, and methods is what allows us to improve our way of life. For instance, in industrial or logistical processes, if someone devises a more efficient method, they create a company to implement it. If it proves better than the traditional method, it gains a larger market share, surpassing the previous approach.

However, real-world evolution is slow to observe due to the time required for tangible results. Conversely, in simulated environments, new action proposals can be observed much faster, considering more options and allowing for the immediate application of the best approach.

The computer revolution of recent decades provides us with the ability to simulate and automate processes. A network of computers with these capabilities has been established, offering tremendous potential. Cutting-edge technologies such as artificial intelligence promise a significant improvement in our quality of life, primarily through their potential to automate tasks beyond previous imagination.

In a cellular automaton, the fewer and/or less complex the rules governing agent interactions, the broader the spectrum of complexity the automaton can achieve. In other words, more rules lead to greater limitations.

<br>

## Definition

CELAUT is a set of simple rules for software design and distribution. It is based on two main elements: nodes and services.

### Nodes

A node is a computer on the network that can find and communicate with other nodes. It has the ability to share, build, and orchestrate services between them.

A node must:

* Provide an interface for services to communicate with.
* Provide the address to which the service will make its requests.
* Load the components of a new instance from a binary file in the root of the service's file system.
* If requesting an instance from another node, ensure that the requester has access to the address it provides to communicate with the dependency.

A node can choose whether to build a new instance locally or request it from another node.

### Services

A service is software that performs a specific task, whose specification is found in a binary file. They follow the idea of a "black box" or a lambda function.

<br>

This architecture allows services to focus on their functionality, without worrying about the underlying infrastructure. Nodes, for their part, can efficiently manage the execution of instances, without worrying about their usefulness.

<br>

## Why is this necessary

CELAUT intend to solve is precisely the separation between the “*how to solve a problem*” and the “*where and who solve it*”.

Take, for example, a trading bot.

    Trading bots are automated software programs that execute buy and sell orders in financial markets based on predefined algorithms. They are important as they can operate 24/7, react quickly to market changes, and remove emotional biases, enhancing efficiency and consistency in trading strategies.


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

- You don’t need to run the infrastructure yourself or search for a cloud provider to do that, as the node takes care of this.
- You don’t need to configure anything, as the specification service covers how the container is built, his architecture, his network requirements and his interface, the user don’t need to know anything about that.
- The developers of a service cannot control, modify or extract data of the service as they don’t control the nodes that distribute and runs it. Although they could be incentivized to develop it.

<br>

## More

[Roles](roles.md)

[Service specification](service_specification.md)

[FAQ](faq.md)

[Roadmap](roadmap.svg)

[Ergo-forum conversation](https://www.ergoforum.org/t/artifical-economic-intelligence-on-ergo-blockchain/4429/2)