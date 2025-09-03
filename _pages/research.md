---
layout: archive
title: "Research"
permalink: /research/
author_profile: true
redirect_from:
  - /projects
---

**Please also check my [publications](/publications/) or [CV](/cv/) for updates on my research activities. Feel free to reach out for collaborations!**

In the pursuit of ever-higher accuracy in machine learning (ML), two critical dimensions consistently shape the design and deployment of systems: efficiency and reliability. Performance gains in ML are no longer determined solely by new algorithms or larger datasets; they increasingly rely on whether systems can train and serve models within feasible resource budgets and with dependable correctness. Efficiency directly impacts scalability and accessibility, as an accurate model that is too computationally expensive to train or deploy limits its full potential. Likewise, reliability is also indispensable: even the most accurate model loses its value if its predictions or training outcomes are undermined by system faults, data corruptions, or hardware uncertainty. 

In my research, I aim to advance efficiency and reliability through three complementary fronts as follows:  
- **Approximate computing (AxC)**: for controllable efficiency, reliability and performance trade-off in ML.  
- **Hyperdimensional computing (HDC)**: for developing a novel bio-inspired computing paradigm for efficient ML.
- **(Mitigating) Silent Data Corruption (SDC)**: for enhancing reliability under the scaling-up and -out trends of ML. 


## Approximate Computing (AxC)

Modern ML models are powerful but notoriously resource-hungry. Fortunately, ML workloads often exhibit intrinsic error tolerance: they can abide small amounts of noise or errors with only minor accuracy loss. This opens the possibility of intentionally trading performance for efficiency gains in a controlled manner by introducing approximation.  

**Context-aware AxC Modeling.** At the hardware and architecture level, approximation can be realized by approximate designs. They have reduced computation cost, but with reduced precision. Conventional error modeling mostly rely only on statistical metrics such as error rate (ER), mean absolute error (MAE), or mean absolute percentage error (MAPE), and thus often fails to capture how errors behave in practice. For example, my research showed that error behavior of a circuit is strongly influenced by dynamic context including voltage, temperature, and most importantly, the dynamic inputs that sensitize different paths (TCAD'20). To address this, weproposed context-aware, learning-based models that incorporate these valuable contexts (TCAD'21). Compared to baseline methods, this approach significantly improves the accuracy of AxC error modeling, especially at the application level.  

**Sensitivity-aware AxC Configurations.** ML models are heterogeneous as different layers and components vary in their sensitivity to approximation. A key challenge is to identify where approximation can be safely applied and where not. My research explores AxC techniques related to data locality in ML. In computation reuse, weperformed design space exploration (DSE) to assign optimized approximation settings to different neural network layers (GLSVLSI'20). This layer-aware strategy achieves lower accuracy drop while saving more computation compared to uniform approximation. In computation bypass, we investigated how trivial computations can be aggressively skipped without violating accuracy requirements, further reducing the computation cost (DSD'20).  

## Hyperdimensional Computing (HDC)

While approximate computing advances efficiency by trading controlled accuracy for reduced cost, another promising direction is to explore alternative computing paradigms that complement deep learning under efficiency constraints. One such paradigm is hyperdimensional computing (HDC), a vector-symbolic computing approach inspired by brain functions and neural patterns. HDC models are typically smaller, more computationally efficient, and capable of one-shot learning, making them particularly attractive for deployment in resource-constrained environments.  

**Reliability of HDC.** I established a comprehensive line of research on the reliability of HDC. I conducted the first systematic study of adversarial attacks and defenses for HDC across white-box, gray-box, and black-box scenarios (DAC'21, TCAD'23). This work revealed that the fundamental architectural differences between HDC and neural networks lead to distinct responses to adversarial threats, highlighting the need for specialized defense mechanisms tailored to HDC.  

**Promising Applications of HDC.** Beyond reliability, I have demonstrated the versatility of HDC across multiple application domains, particularly when efficiency is a notable requirement. In drug discovery, I showed that HDC can represent molecular structures more effectively for drug property prediction (BIBM'22). In natural language processing, I demonstrated that HDC achieves comparable performance in text spam detection while requiring significantly less memory (ISVLSI'21). Furthermore, I developed methods to encode neural network architectures into hyperdimensional representations, enabling faster performance prediction for neural architecture search (NAS) (CVPRW'23).  

## Silent Data Corruption (SDC)

Silent data corruptions (SDCs) refer to errors in hardware modules (e.g., memory) that propagate silently through the system, remaining undetected until they trigger notable disruptions or failures. As ML systems scale up and scale out, SDCs are becoming an increasingly pronounced threat. 

**Fast Error Injection.** To better understand the impact of SDC in ML, I developed and open-sourced PyTEI, a framework for fast, flexible, and user-friendly error injection (ISSRE'25). PyTEI runs significantly faster than related tools, and can be flexibly scaled to larger models thanks to its parallelized design. This efficiency enables large-scale error injection campaigns that capture a broader range of error patterns and evaluate their impact on state-of-the-art models. For example, applying PyTEI to deep recommender systems (DRS), I discovered that SDCs affect different components inconsistently: multi-layer perceptrons (MLPs) are significantly more vulnerable than embedding tables. This insight highlights the importance of targeted protection strategies rather than one-size-fits-all defenses.  

**Cross-layer SDC Detection and Mitigation.** Building on these insights, I proposed Dr. DNA, a cross-layer framework that leverages unique SDC signatures derived from the distribution of neuron activations in intermediate deep neural network (DNN) layers (ASPLOS'24). Dr. DNA enables early detection and mitigation of SDCs during inference. Across diverse tasks, datasets, DNN architectures, and error scenarios, Dr. DNA outperforms existing methods in both detection and mitigation, offering a versatile and low-overhead solution. Importantly, it is effective against stealthy and delayed manifestations of SDCs, which are particularly challenging to address.  