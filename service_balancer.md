[*<-- Back to main page*](README.md#system-behavior)

### Sequence diagram of a service balancer process

When a node receives a request to instantiate a service, it is the node that decides on which node in the network it should be instantiated, locally or on another node. To do this, it compares the cost of executing the instance on each of its peers with the cost of executing the instance locally and chooses the one it considers best (for example, the lower one).

When clients (other peers) ask it for its cost to execute a service, it will give them the cost of executing it locally or on another of its peers.

<br>

In the following sequence diagram (Figure 4c0), the load balancing process for executing new service instances is exposed. It is assumed that a service has received the request to execute the instance of a service.

![Service balancer diagram](assets/4c0f64_service_balance_diagram.excalidraw.svg) *Figure 4c0: Service balance diagram*

<br>

The agents involved in the previous sequence diagram (figure 4c0) are as follows:

- Node A is the node that requests the cost and generation of the new instance of a service.
- Node B is another node in the network.

The following interactions are exposed during the sequence:

1. Node A requests the cost of executing an instance of the service from each of its peers in the network. It uses the cost retrieval method according to the interface of each peer.

2. Node B calculates the cost of executing the service locally.
    
3. Node A calculates the cost of executing the service locally and compares it with the costs received. In this case, it decides that the lowest cost is that of Node B.

4. Node A requests Node B to execute an instance of the service, sends the specification of this back to it, and waits for it to return its address and token.

5. Node B executes the instance of the service that Node A delivers to it, stores the instance in its registry considering that the parent is Node A and returns its address and token.
    
6. Node A receives the address and token from Node B, stores the instance in the registry as an external instance.
