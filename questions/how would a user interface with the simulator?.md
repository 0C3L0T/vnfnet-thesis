the simulator needs to communicate its state and apply policy changes on-the-fly, but what do those policy changes look like? Are they forwarding tables, or direct commands like 'chain these services together', 'make new service'?


a remote agent will :
1. create a substrate network topology
2. request the state of the environment (SN topology and also probably all the VMs and VNFs) and a 'service request' (see [[what is traffic generation]])
3. find some embedding for the service request on the current state
4. communicate to the environment how to embed the function chain

from Tom Wassings paper: ![[Pasted image 20240416115237.png]]

SCHEMA: ![[Pasted image 20240417114519.png]]
