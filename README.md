---
tags:
  - thesis
---


The project plan is submitted via Canvas after it has been approved by the project supervisor(s) (both in the case of an external
project). It takes an average of four pages of A4 and consists of the following parts:

# VNFnet project plan
Merijn Laks

Supervisors: Anestis Dalgkitsis, Cyril Hsu

### Introduction
Recent developments in software defined networking have seen the move from traditional networking architectures, where network services such as firewalls, load balancers, intrusion detection systems, encryption/decryption, and content filtering are typically deployed as standalone appliances or devices, to virtualized network functions (VNF). These network functions can be run on enterprise-grade hardware instead of specialized, vendor-specific machines, thereby improving resource use and extensibility. Additionally, with the increasing complexity and dynamic nature of modern networks, there is a need for more flexible and scalable approaches to service delivery. Service Function Chaining (SFC) addresses this need by allowing the creation of logical chains of virtualized network services that are applied to traffic flows in a programmable and dynamic manner to allow for a high level of customization and complex functionality, effectively extending the control plane of regular software-defined networking solutions.

- SDN and VNF complement each other, VNF does not necessarily depend on on SDN 

### Problem description !
what is the relevant literature associated with the research question? This often takes the form of a description of the “state-of-the-art”: a summary of results previously achieved by others and on which the research question builds.

determening how service function chain topology should look like is one thing, but those chains also need to be embedded on actual hardware and with limited service infrastructure. Getting the most performant service function chains and mapping them on a substrate network is called service function chain embedding and, as with most optimization problems, it is NP-complete.

multiple different approaches have been utilized, machine learning, alogirthms, q learning, deep learning. They all need the same heuristics and a way to test their strategies.

especially Machine-learning approaches need a lot of test data, so the faster we can run tests the better.

one of the main challenges of the virtual network function is the on-demand resource allocation and operation. So it's a two-part problem, first we need to figure out how many resources to allocate where for the VNFs and second, we need to figure out how to 'map' an optimal topology to the topology available to us in the form of a substrate network.

according to Resource_Allocation_in_NFV_A_Comprehensive_Survey, the problem consists of three stages: chain composition, chain embedding and VNF scheduling/orchestration.
Also this: coordinated allocation as it proposes a recursive heuristic that solves VNFs-CC and VNF-FGE in a coordinated way, that is, the VNF-FG is composed and allocated simultaneously.

To test these embedding strategies, there rises a need for a comprehensive simulation framework that allows for testing out models. it needs to be easy to use, so developers can easiliy work with it, maybe even in the form of a library for easy intergration. 

- VNF and SFC is a hot topic, but there are no good simulation frameworks
- CVI sim
- VNFnet (how does it differ from CVI-sim?)
- allocating resources
- SFC embedding problem
- testing out strategies -> need for simulator
- simulations to train ML models
- it seems there is no readily available VNF simulator -> vnfnet
- note that mapping and embedding means the same here
- we need to simulate a substrate network so that we can test the viability of our chain embedding after we have composed the chain. -> virtual nodes / links
- vnf resource allocation simulation
- cater to exact, heuristic or meta-heuristic solution frameworks?

### Research question !
The research question; describe the problem that will be worked on. This often takes the form of a reflection with regard to the “state-of-the-art” just described. As part of the research question, it is also described what the project will deliver: the product that will be delivered at the end, eg the results of a research, the source code of developed software, documentation.

- extending VNFnet
- VNF/SDN simulator
- support both offline and online scheduling?
- how to best help researchers evaluate their models
- are there any significant performance increases to be made in simulator
- simulate Virtual Network Infrastructure (VNI)?
- what about random network generation?
- Mijumbi et al. [68] carry out evaluations of RA algo- rithms considering metrics such as successful service mappings, total service processing times, revenue or cost, under varying network conditions. • Important metrics such as number of active physical nodes, node buffer capacity, function processing times and function buffer demand were also considered in [68]. • Additional metrics such as acceptance rate, resources utilization and traffic congestion, were used in [80]–[82].
- open-source

### Related work
- cvi sim
- other network simulators simulators, how do they do it?
- VNFnet -> this is the thing I'll be working on, also no literature
- mininet -> not scalable
- [networkx](https://networkx.org/documentation/latest/)



### Methods
Methods: how is the research conducted? Which subtasks can be distinguished? For example: extensive literature research, design and implementation of a program, design of an experiment.

- talking with researchers -> tailoring to their needs
- refactoring existing codebase
- extensible python framework
- design interfaces for 

### Planning
The schedule; Describe how the available time is expected to be spent. It is often difficult to identify all activities in advance, let alone to indicate accurately on the day what will be completed on which date. In general, it is possible to identify a number of phases (eg literature research, design,
implementation, experiments, writing a thesis, etc.) and to make a weekly schedule.
Also consider the interim results, the dependencies that may exist and whether there are critical dependencies that prevent the project from proceeding and what the alternative plan is in that case. A Gantt or Pert chart is often used for this.

- talk about hours
- https://forum.obsidian.md/t/automatic-gantt-chart-from-obsidian-tasks-dataview/50512
