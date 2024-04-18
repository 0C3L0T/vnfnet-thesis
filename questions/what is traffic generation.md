Traffic generation, in the context of VNFnet, consists of generating 'service requests'. Service requests are [[service function chaining | SFCs]] consisting of unembedded [[virtual network functions | VNFs]]. It is up to the remote agent to receive these service requests, together with a state of the current simulation, and come up with an embedding strategy.

A service request would consist of a couple things:
- a chain of network functions of a variable length, each function having its own resource characteristics
- a lifetime of how long the chain should be active
- a service level agreement in the form of a max latency

The frequency of the traffic would be simulated according to a [[Poisson distribution]] (see paper)

==how long is a normal function chain?==
==how many resources does a normal VNF consume?==