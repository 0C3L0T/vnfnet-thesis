---
tags:
  - thesis
---
# VNFnet project plan
Merijn Laks

Supervisors: Anestis Dalgkitsis, Cyril Hsu

## Introduction
Recent developments in software defined networking have seen the move from traditional networking architectures, where network services such as firewalls, load balancers, intrusion detection systems, encryption/decryption, and content filtering are typically deployed as standalone appliances or devices, to virtualized network functions (VNF). These network functions can be run on enterprise-grade hardware instead of specialized, vendor-specific machines, thereby improving resource use and extensibility. Additionally, with the increasing complexity and dynamic nature of modern networks, there is a need for more flexible and scalable approaches to service delivery. Service Function Chaining (SFC) addresses this need by allowing the creation of logical chains of virtualized network services that are applied to traffic flows in a programmable and dynamic manner to allow for a high level of customization and complex functionality, further extending the trend of software-defined networking.

## Problem description
The challenges in this field of research consist of three stages: VNF chain composition (VNFs-CC), VNF graph embedding(VNF-FGE) and VNF scheduling(VNFs-SCH) whereby different VNFs get chained together according to a specific requirement, the chain gets embedded on the actual available service network topology, also called a substrate network (SN) and resources on this network get allocated to host the VNF function chain [¹].
VNF-FGE, in being a generalization of the virtual network embedding (VNE) problem, is NP-hard [²]. Therefore, multiple solution approaches have been proposed based on heuristic and meta heuristic, and more recently machine- and deep reinforcement learning models ([³], [⁴]).

[¹]: Resource_Allocation_in_NFV_A_Comprehensive_Survey,
[²]: vne complexity
[³]: solve vne problems
[⁴]: Service Function Chain Embedding for NFV-Enabled IoT Based on Deep Reinforcement Learning

## Research question
A Java-based simulator has been used in past literature to evaluate analytical solutions to the VNF resource allocation problem [⁵]. The framework has later been extended to better integrate with machine-learning methods [⁶]. While this framework has been successfully used, the need for more extensive traffic-generation and better extensibility has arisen. Additionally, some non-free resources were used, limiting the open use of the project. In this project we want to answer the following question:

"How can we extend previous work on VNF simulators to accommodate future machine learning solutions to the VNF-FGE problem on large scales, improving traffic generation and extensibility?"

This project will deliver a completely open-source, well documented, highly-scalable and extendable simulation framework that can generate vast volumes of traffic to test VNF resource allocation on massive networks. Additionally, a small literature study will be performed to determine which traffic generation schemes will be implemented. Since most machine-learning frameworks and libraries are situated in the Python ecosystem, the simulator will be implemented in Python. To increase performance, a study will be performed into replacing parts of the simulator with optimized modules written in the more performant programming languages.


[⁵]: Extending a simulation frame- work for virtualised networking infrastructures to leverage the potential of machine learning
[⁶]: On the Optimal Allocation of Virtual Resources in Cloud Computing Networks

## Related work

Some work has already been done on simulating Virtual Network Functions and their chaining and orchestration.

The Alevin framework [⁷] uses a sophisticated application of visitor design pattern to decouple implementations from the objects they operate on, increasing modularity and allowing for an arbitrary amount of parameters. The concept of modularity is further explored in SFCsim[⁸], which is based on the NetworkX framework and splits up the simulation infrastructure in literal components. This approach of splitting up simulator functionality should be studied more closely, as it could provide valuable insight in the implementation of the current project.

- message passing?

In terms of ML-focused simulators, an extension of the CVI-sim testbed has been described in literature ([⁵], [⁸]). Recent work in multi-domain orchestration sees the creation of custom-made Open AI Gym environments, highlighting the need for ML-focused simulators ([⁹], [7]). 
Mininet -> process virtualization, still uses actual resources, not scalable. focuses on network emulation.

- cloudsim

[⁷]: SCHE2MA: Scalable, Energy-Aware, Multidomain Orchestration for Beyond-5G URLLC Services
[⁸]: SFC-sim
[⁹]: openAI Gym

## Methods 
This project will consist of four phases; design, implementation , optimization and evaluation.
#### Design
Before any work gets done, a clear overview of requirements needs to be constructed. Interviews wil be performed with researchers to determine what interfaces would be best suitable for machine-learning implementations. Additionally, an overview of existing features that need to be ported from previous work, namely CVI-sim, has to be made and extended with new features on the front of traffic generation. The result of this phase will be a design document highlighting the current functionality of the FNVnet code base, the desired features from CVI-sim and an overview of network generation algorithms to be implemented.

#### Implementation
The existing code base from [⁷] will be refactored, after which the desired features from [⁵] will be ported and any additional traffic generation schemes will be implemented. The focus here should be on an extensible and - highly scalable architecture, allowing for quick extensibility by splitting the program up in several modules. The result of this phase will be a functional code base.

#### Optimization
When the initial functionality of the framework has been implemented, a study will be performed into replacing modules in the code base with implementations in more performant programming language. This will result in a more performant simulator for the high-scalability aspirations of this project.

#### Evaluation
At the end of the project, the correctness of the program should be tested. This can be achieved by comparison with similar pieces of software or, if traffic generation is the only concern, a comprehensive visualization into the inner workings of the simulation.

## Planning
The schedule; Describe how the available time is expected to be spent. It is often difficult to identify all activities in advance, let alone to indicate accurately on the day what will be completed on which date. In general, it is possible to identify a number of phases (eg literature research, design,
implementation, experiments, writing a thesis, etc.) and to make a weekly schedule.
Also consider the interim results, the dependencies that may exist and whether there are critical dependencies that prevent the project from proceeding and what the alternative plan is in that case. A Gantt or Pert chart is often used for this.

- talk about hours
- https://forum.obsidian.md/t/automatic-gantt-chart-from-obsidian-tasks-dataview/50512
