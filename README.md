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
Recent developments in software defined networking have seen the move from traditional networking architectures, where network services such as firewalls, load balancers, intrusion detection systems, encryption/decryption, and content filtering are typically deployed as standalone appliances or devices, to virtualized network functions (VNF). These network functions can be run on enterprise-grade hardware instead of specialized, vendor-specific machines, thereby improving resource use and extensibility. Additionally, with the increasing complexity and dynamic nature of modern networks, there is a need for more flexible and scalable approaches to service delivery. Service Function Chaining (SFC) addresses this need by allowing the creation of logical chains of virtualized network services that are applied to traffic flows in a programmable and dynamic manner to allow for a high level of customization and complex functionality, further extending the trend of software-defined networking.

### Problem description !
The challenges in this field of research consist of three stages: function chain composition (VNFs-CC), function chain embedding(VNF-FGE) and VNF scheduling(VNFs-SCH) whereby different VNFs get chained together according to a specific requirement, the chain gets embedded on the actual available service network topology, also called a substrate network (SN) and resources on this network get allocated to host the VNF function chain. [¹]

- all problems are NP-complete (find source)

When looking specifically at the embedding problem, multiple solutions have been proposed.
- online/offline (find source)
- exact / heuristic / meta heuristic (find source)
- Machine Learning / Deep Learning (find source)



[¹]: Resource_Allocation_in_NFV_A_Comprehensive_Survey,


### Research question !
The research question; describe the problem that will be worked on. This often takes the form of a reflection with regard to the “state-of-the-art” just described. As part of the research question, it is also described what the project will deliver: the product that will be delivered at the end, eg the results of a research, the source code of developed software, documentation.

While many strategies have been proposed to tackle the embedding problem, there remains to be developed a simulation framework that allows for testing models. it needs to be easy to use, so developers can easily work with it, maybe even in the form of a library for easy integration. 

Especially nouveau Machine Learning approaches need a lot of test data, so the faster we can run simulations and integrate with existing codebases the better. 

We will also check if there are areas that could benefit from a rework in a lower-level language like Rust or Go

work on a VNF resource allocation and SDN simulator called VNFnet, the project will integrate features from previous extension of CVI-sim[²],[³]. Here too, the focus will be put on evaluating machine-learning based solutions to the VNF-FGE problem.

the project will be open source

- cater to exact, heuristic or meta-heuristic solution frameworks?
- extending VNFnet
- support both offline and online scheduling?
- simulate Virtual Network Infrastructure (VNI)?
- Mijumbi et al. [68] carry out evaluations of RA algorithms considering metrics such as successful service mappings, total service processing times, revenue or cost, under varying network conditions. • Important metrics such as number of active physical nodes, node buffer capacity, function processing times and function buffer demand were also considered in [68]. • Additional metrics such as acceptance rate, resources utilization and traffic congestion, were used in [80]–[82].


[²]: Extending a simulation frame- work for virtualised networking infrastructures to leverage the potential of machine learning
[³]: On the Optimal Allocation of Virtual Resources in Cloud Computing Networks

### Related work
- cvi sim
- other network simulators simulators, how do they do it?
- VNFnet -> this is the thing I'll be working on, also no literature
- mininet -> not scalable
- cloudsim
- [networkx](https://networkx.org/documentation/latest/)



### Methods !
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
