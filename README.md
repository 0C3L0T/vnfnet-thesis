
# VNFnet - Design Requirements

## 1. How does VNFnet work currently?
the current simulator has a couple of classes:
- Service -> Service Level Agreement
- Host -> hosts services, uses resources
- User -> traffic pattern, has chain of VMs
- Link -> source/destination and connection characteristics
- VM -> has Host, also Service?
- Chain -> Has SLA and list of VMs
- Domain -> collection of hosts and links
- Connection -> path of nodes and User object, node path vs. chain?
- Network -> used to interact with the network as a whole, I guess this could be seen as the simulation 'engine'.

I think this python file is supposed to be used as a library in other programs. 


## 2. How should VNFnet work after the project?
- simplify substrate network and add abstractions
- generate traffic
- report environment state and update according to commands -> ==formulate commands==
- visualize the network -> grave?

## What do we want to simulate?

### Substrate Network
- nodes and edges
	- nodes have resources in the form of cpu, storage, ram, etc
	- edges have resources in the form of bandwidth, delay, etc

- generate random / according to config -> would actually be useful to do this with networkX
- provide interfaces for sending and receiving
- handle resource allocation (nodes will have a predetermined amount of resources)

### Substrate class:
- ```nodes``` hash map of Node class
- ```edges``` hash map of Edge class
- ```create_topology()``` create substrate topology according to model or configuration
- ```insert_function()```  update available resources of nodes and edges, or error if no resources are available
- ```remove_function()``` update available resources of nodes and edges

##### Host class (node)
- ```uid``` index in Substrate class hash table
- ```cpu_avail``` available cpu resources according to topology
- ```memory_avail``` available memory resources according to topology
- ```storage_avail``` available storage according to topology
##### Link class (edge)
- ```uid``` index in substrate hash table
- ```avail_bandwidth``` available bandwidth according to topology
- ```latency``` latency of the connection according to topology
 
### Virtual Network Functions
- ==does every SFC have its own VNFs or can they share== -> they would be able to share in theory but our simulation will have only one VNF per SFC.
- ==will the remote agent be able to allocate/remove/migrate VNFs?==
- model resources consumed per unit of traffic
- ==find factors to simulate resource usage==

### FunctionAllocator
- ```functions``` hash map of ```NetworkfFunction``` classes
- ```allocate_function()``` add function to ```Substrate``` class and insert into ```functions```
- ```free_function()``` remove function from ```Substrate``` and ```functions```
##### NetworkFunction class
- ```uid``` index in Allocator hash map
- ```cpu_usage``` function of traffic
- ```memory_usage``` function of traffic
- ```storage_usage``` function of traffic
- ```processing_time``` time it takes to process request
- ```host_id``` on which function is hosted 

### Service Function Chains
- latency -> every link between VNFs will add propagation and processing time
- chain -> vector of nodes, ==I guess each node will have to have a forwarding table, so we know which edge will be taken==
- source / destination
- requested according to Poissant distribution (see paper)
 - removed based on lifetime

### ChainAllocator
- ```chains``` hash map of ```ServiceChain``` class
- ```allocate_chain()```
- ```calculate_latency()``` calculate the total latency of the chain

#### ServiceChain
- ```functions``` list of ```NetworkFunction``` classes
- ```lifetime``` duration that the chain should be active




### Traffic
It seems to me that SFC and the concept of traffic are very much related.

Network traffic has multiple aspects:
1. source/destination
2. SLA requirements

- static vs. mobile vs. dynamic traffic?

We can say that traffic is only generated along a SFC. Or maybe the creation of the SFC *is* the traffic, since resources have to be allocated.

is the SLA static though? I can imagine that if a VNF is not using all of its allocated resources, the resources can be "multi-threaded".

### Scheduler -> Environment?
- handle orchestration
- interface for remote agent -> communicate environment state, apply policy commands
- allocates, removes, migrates VNFs
- ==so the job of the remote agent is not to allocate resources, but to optimize the service chains?==
- or the network would have a list of service chains that are not yet embedded and the remote agent decides where to embed them
- 'step' the simulation
- generate Service Function Chain requests?
- maybe do migration here, since VNFs and SFCs will need to be updated
- generate 'unembedded' SFC requests

### How will users interact with it?
- VNFnet seems to be used as a library, so we should maybe keep it a python library
- Cyril wrote "Roughly speaking, the environment should be able to report its state to the implementation and apply the returned embedding policy on-the-fly".

## How should it work?
- if we clearly define the interfaces, implementation doesn't matter and we can freely switch implementations
- by making the modules communicate in the form of protobufs, we make the framework easily extendable
- scheduling -> we could do discrete time, but real networks don't do that.

Illustration in SFCsim paper: ![[Pasted image 20240413001256.png]]
SFCsim schefuling: ![[Pasted image 20240416133522.png]]
from Tom Wassings paper: ![[Pasted image 20240416115237.png]]

![[Pasted image 20240417114519.png]]


Recommendation:
1. document current functionality
2. document classes and functionality we want to develop
3. propose how to develop service graph embedding -> place vnf from sfc on sn randomly
4. propose network traffic generation strategy
5. describe a technical architecture
