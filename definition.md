CELAUT is a set of simple rules for software design and distribution. It is based on two main elements: nodes and services.

## Nodes

A node is a computer on the network that can find and communicate with other nodes. It has the ability to share, build, and orchestrate services between them.

A node must:

* Provide an interface for services to communicate with.
* Provide the address to which the service will make its requests.
* Load the components of a new instance from a binary file in the root of the service's file system.
* If requesting an instance from another node, ensure that the requester has access to the address it provides to communicate with the dependency.

A node can choose whether to build a new instance locally or request it from another node.

## Services

A service is software that performs a specific task, whose specification is found in a binary file. They follow the idea of a "black box" or a lambda function.

## Conclusions

This architecture allows services to focus on their functionality, without worrying about the underlying infrastructure. Nodes, for their part, can efficiently manage the execution of instances, without worrying about their usefulness.
