[*<--   Back to main page*](README.md)
<br><br>



##  How a service is specified?

<br>

The specification of a service in CELAUT consists of three main components:

### Container
This component defines the environment in which the service will run, including the hardware and software requirements. It specifies the architecture, entry point, filesystem, and environment variables of the service.

### API
This component defines how the service can be interacted with, including the ports it listens on, the communication protocols it supports, and the methods it defines. It specifies the application protocol, the slots, and the cost function (optional).

### Ledger
This component defines the database that the service can provide, including the class diagram and the consensus protocol (optional). It specifies the classes and the relation definitions.

<br>

>The specification of a service is stored in a binary file that can be deployed and executed on any node in the CELAUT network. 
>The node will load the service from the binary file and provide it with the resources it needs to run. The service will then start listening for requests and respond to them according to its API specification.


>The specification of a service is a key part of the CELAUT architecture, as it allows services to be deployed and executed in a consistent and predictable manner. 

>The specification of a service also allows for services to be shared and reused across the network, which can help to reduce development costs and improve the overall efficiency of the system.
