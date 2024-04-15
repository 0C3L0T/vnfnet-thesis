
# VNFnet - Design Requirements

## How does VNFnet work currently?
the simulator has a couple of classes:
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

## How should VNFnet work after the project?
### How will users interact with it?
- VNFnet seems to be used as a library, so we should maybe keep it a python library
- Cyril wrote "Roughly speaking, the environment should be able to report its state to the implementation and apply the returned embedding policy on-the-fly".

## What do we want to simulate?
In terms of nodes and edges, VNFnet simulates the following properties:
### Nodes
nodes have some ==resources== in the form of cpu, storage, ram, etc. By hosting services on these nodes (Hosts), the resources get used.

### Edges
edges have all the properties you would expect from a connection: ==bandwidth, delay==

By linking services on nodes trough edges, we can create a chain of services. These services get described by Service Level Agreements. ==Every user has an SLA?==

## How should it work?
- I found this illustration in the paper for SFCsim: ![[Pasted image 20240413001256.png]]
- we can module the substrate network with only nodes and edges -> good contestant to port to Rust -> what about network topology?
- on top of those nodes and edges we have a VNF (service) layer
- on top of the VNG layer we have a SFC layer
- each layer has its own interfaces, so the higher you get the higher the abstraction layer
- the 'scheduler' part would communicate the state of the network and apply policy changes
- SFC uses discrete-time event scheduling, though is that realistic?
- remote agents need to be supported
- every module could have its interfaces in the form of protobuf messages, making it easy to drop-in replace modules.
