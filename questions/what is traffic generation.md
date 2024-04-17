what does traffic generation mean in the context of Virtual network functions? just generate a bunch of random functions and chains and then let it run?

- do we also need to generate network topology?

After taking a look at vnfnet, it looks like traffic generation means being able to query a service or user and get their current traffic characteristics. I could take a look if there are papers on this topic. Maybe something like "simulating network usage".
	Also, different nodes would probably have different network traffic characteristics.


### Traffic
It seems to me that SFC and the concept of traffic are very much related.

Network traffic has multiple aspects:
1. source/destination
2. SLA requirements


We can say that traffic is only generated along a SFC. Or maybe the creation of the SFC *is* the traffic, since resources have to be allocated.

is the SLA static though? I can imagine that if a VNF is not using all of its allocated resources, the resources can be "multi-threaded".
