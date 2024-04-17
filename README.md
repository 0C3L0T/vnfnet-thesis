
# VNFnet - Design Requirements

## 1. How does VNFnet work currently?
the current simulator has a couple of classes:
- Service -> Service Level Agreement
- Host -> hosts services, uses resources
- User -> traffic pattern, has chain of VMs
- Link -> source/destination and connection characteristics
- VM -> has Host, also Service? groups VNFs on host
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
- generate random / according to config -> would actually be useful to do this with networkX

#### Substrate class:
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
- in theory every VNF could be shared by multiple SFCs, but in this simulator it is not required.
- ==find factors to simulate resource usage==

#### FunctionAllocator
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
- ==how do we know what edges are used in the chain?==
- requested according to Poissant distribution (see paper)
 - 'service request'
- static vs. mobile vs. dynamic?

### ChainAllocator
- ```chains``` hash map of ```ServiceChain``` class
- ```allocate_chain()```

#### ServiceChain
- ```functions``` list of ```NetworkFunction``` classes that make up the chain
- ```lifetime``` duration that the chain should be active, after which it will be deallocated
- ```calculate_latency()``` calculate the total latency of a chain

### Scheduler -> Environment?
- handle orchestration
- interface for remote agent -> communicate environment state, apply policy commands
- allocates, removes, migrates VNFs
- ==so the job of the remote agent is not to allocate resources, but to optimize the service chains?==
- or the network would have a list of service chains that are not yet embedded and the remote agent decides where to embed them
- 'step' the simulation
- maybe do migration here, since VNFs and SFCs will need to be updated
- generate 'unembedded' SFC requests

#### Environment
- 
- ```step()``` decrease all lifetimes by 1

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
