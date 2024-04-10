---
tags:
  - thesis
---
# VNFNet: a simulation framework for orchestration virtualised infrastructures

### Supervisor: Anestis Dalgkitsis, Cyril Hsu (a.dalgkitsis@uva.nl, s.h.hsu@uva.nl)

This Thesis is focused on enhancing a Python-based [[software defined networking]] and [[network function virtualization]] network simulator called VNFNet, originally developed to simulate Virtual Network Function (VNF) migration and orchestration for 5G networks.

The primary objective involves extending the traffic generation and propagation modules of the simulator to support multiple patterns of traffic. Your contribution will empower researchers to harness the power of your traffic generation module for developing and evaluating solutions on large-scale simulated networks. The key objectives are to:

1. Study and understand how resource allocation works in multi-domain, SDN and NFV networks.
2. Analyze and understand a model network simulator made with Python, and finally
3. Contribute to the traffic generation functionality or modelling of the network infrastructure

### On grading
>The final result should be in the form of a research report (“thesis”) plus any appendices, such as code, and a public presentation. The whole is assessed on the quality of the insights acquired in the study and the ability to interconnect these and to give shape to a project to be carried out independently.

---

GitHub repo: [link](https://github.com/anestisdalgkitsis/vnfnet/tree/main).

---
On a very high level, your project tasks should include:

- Exploring advanced networking concepts in multi domain networks, such as NFV, SDN and SFC.
- Study and understand how the resource allocation and networking simulator VNFnet works.
- Contribute to the development of the advanced networking functions of the simulator in Python, specifically the Service Graph request embedding.
- Explore the use of Rust for large scale NFV/SDN simulation in HPC environments.

# Refactor code base
- dividing the project up into modules
- adding types
- remove comments
- add doc strings
- replace logging library

# Implement new features
- something with displaying the network
- service graph request embedding
- porting features from java application
- traffic generation

# Rust
- identify 'hot code' trough a profiler
- replace with optimized rust code
- maybe even port the entire project
- possibly create a library with [[PyO3]]
