
# VNFnet - Design Requirements

# 1. How does VNFnet work currently?
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


# 2. How should VNFnet work after the project?
- simplify substrate network and add abstractions
- generate traffic
- report environment state and update according to commands -> ==formulate commands==
- visualize the network -> grave?

## Substrate Network
- generate random / according to config -> would actually be useful to do this with networkX

#### Substrate class:
- ```nodes```: hash map of ```Node``` class
- ```edges```: hash map of ```Edge``` class
- ```insert_vm(target_node: host_id, virtual_machine: VM)```:  decrease resources of ```Node``` with ```host_id``` and update available resources of nodes and edges and return node_id, or error if no resources are available
- ```remove_vm(target_node: Node, virtual_machine: VM)```: update available resources of nodes and edges
##### Host class (node)
- ```uid```: index in ```nodes```  hash table
- ```cpu_avail``` available cpu resources according to topology
- ```memory_avail``` available memory resources according to topology
- ```storage_avail``` available storage according to topology
##### Link class (edge)
- ```uid```: index in ```edges``` hash table
- ```avail_bandwidth```: available bandwidth according to topology
- ```latency```: latency of the connection according to topology

## Virtual Network Functions
- optionally support VNFs being shared by multiple SFCs
- ==find factors to simulate resource usage==

### VNFManager
- ```virtual_machines```: hash map of ```VirtualMachine``` classes
- ```allocate_function(target_vm: VirtualMachine, function: NetworkFunction) -> function_id```: add ```function``` to ```functions``` of ```target_vm``` and return ```function_id``` or error if no resources available
- ```free_function(target_vm: VirtualMachine, function_id: uid)```: remove function with ```function_id``` from ```functions``` of ```target_vm```
#### VirtualMachine
- ```uid```: index in ```virtual_machines``` hash map
- ```host_id```: index of ```Host``` in ```Substrate``` hash map
- ```functions```: hash map of ```NetworkFunction``` class
- ```cpu_base```: base cpu utilization of virtual machine
- ```memory_base```: base memory utilization of virtual machine
- ```storage_base```: base storage utilization of virtual machine
- ```bandwidth_base```: base bandwidth utilization of virtual machine
##### NetworkFunction class
- ```uid```: index in ```functions``` hash map
- ```cpu_usage```: function of traffic
- ```memory_usage```: function of traffic
- ```storage_usage```: function of traffic
- ```processing_time```: time it takes to process request

## Service Function Chains
- ==how do we know what edges are used in the chain?==
- requested according to [[[Poissant distribution]] (see paper)
 - 'service request'
- static vs. mobile vs. dynamic?

### ChainAllocator
- ```chains``` hash map of ```ServiceChain``` class
- ```allocate_chain()```

#### ServiceChain
- ```functions``` list of ```NetworkFunction``` classes that make up the chain
- ```lifetime``` duration that the chain should be active, after which it will be deallocated
- ```calculate_latency()``` calculate the total latency of a chain

## Scheduler -> Environment?
- handle orchestration
- interface for remote agent -> communicate environment state, apply policy commands
- allocates, removes, migrates VNFs
- ==so the job of the remote agent is not to allocate resources, but to optimize the service chains?==
- or the network would have a list of service chains that are not yet embedded and the remote agent decides where to embed them
- 'step' the simulation
- maybe do migration here, since VNFs and SFCs will need to be updated
- generate 'unembedded' SFC requests
- have a small database to store environment state
- visualize current environment state
- create / delete / migrate VM

#### Environment
- ```create_topology()``` create substrate topology according to model or configuration
- ```embed_sfc()``` 
- ```step()``` decrease all lifetimes by 1

# Dependency Graph
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
