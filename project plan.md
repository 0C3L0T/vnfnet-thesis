---
tags:
  - thesis
---
The project plan is submitted via Canvas after it has been approved by the project supervisor(s) (both in the case of an external
project). It takes an average of four pages of A4 and consists of the following parts:

# VNFnet
Merijn Laks

Supervisors: Anestis Dalgkitsis, Cyril Hsu

### Introduction
Recent developments in software defined networking have seen the move from traditional networking architectures, where network services such as firewalls, load balancers, intrusion detection systems, encryption/decryption, and content filtering are typically deployed as standalone appliances or devices, to virtualized network functions (VNF). These network functions can be run on enterprise-grade hardware instead of specialized, vendor-specific machines, thereby improving resource use and extensibility. Additionally, with the increasing complexity and dynamic nature of modern networks, there is a need for more flexible and scalable approaches to service delivery. Service Function Chaining (SFC) addresses this need by allowing the creation of logical chains of virtualized network services that are applied to traffic flows in a programmable and dynamic manner to allow for a high level of customization and complex functionality, effectively extending the control plane of regular software-defined networking solutions.

### Problem description
what is the relevant literature associated with the research question? This often takes the form of a description of the “state-of-the-art”: a summary of results previously achieved by others and on which the research question builds.



- CVI sim
- VNFnet (how does it differ from CVI-sim?)
- allocating resources
- SFC embedding problem
- testing out strategies -> need for simulator
- simulations to train ML models

### Research question
The research question; describe the problem that will be worked on. This often takes the form of a reflection with regard to the “state-of-the-art” just described. As part of the research question, it is also described what the project will deliver: the product that will be delivered at the end, eg the results of a research, the source code of developed software, documentation.

- how to best help researchers evaluate their models
- are there any significant performance increases to be made in simulator


### Related work
- cvi sim
- other simulators
- VNFnet?


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
