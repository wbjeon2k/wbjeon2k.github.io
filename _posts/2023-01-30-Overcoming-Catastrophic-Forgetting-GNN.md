---
tags: ddop awesome
date: 2023-01-30 18:00 +0900
title: "Daily Dose of Paper : Overcoming Catastrophic Forgetting in Graph Neural Networks"
categories: ai
<!--author: wbjeon2k-->
---

# Overcoming Catastrophic Forgetting in Graph Neural Networks

AAAI 2021 paper.

## **TLDR**

![wsnalgo](/images/WSN/wsn_algo.png)  
Designed continual learning strategy tailored for GNN,  
where most previous works have been about CNN-based networks.  
Penalize updating important parameter in terms of loss change and attention change.


## Quick Look

- **Authors & Affiliation**: Haeyong Kang  
- **Link**: <https://arxiv.org/pdf/2012.06002.pdf>  
- **Comments**: AAAI 2021 
- **Relevance**: 4.0  

# Research Topic

- **Category** (General): Graph Neural Network, Continual Learning
- **Category** (Specific): 

# Paper Summary (What)
 
- Problem statement
  - Previous continual learning approaches were not for GNN-based models.
  
- Solutions
  - Define two importance metrics, $I_{loss}$ and $I_{attention}$.
  - $I_{loss}$ : $\sum_{m} \frac{\partial L}{\partial w_m} \Delta w_m$
  - $I_{attention}$ : Given graph attention between node $i$ and $j$ as $e^{(l)}_{ij} = a(H^{(l-1)}_{i,j} ; W^{(l)})$,  
  $e^{(l)}_{i} = [e^{(l)}_{i1}, \cdots , e^{(l)}_{i N_i}]$,  
  $g_m(H^{(l-1)}) = \frac{\partial ([e^{(l)}_{1}, \cdots , e^{(l)}_{D}])}{\partial w_m}$,  
  $I_{attention} = [|| g_m(H^{(l-1)}) ||]$
  - In short, $I_{attention}$ is the L2 norm of change of attention.

1. Penalize updating important parameters with loss term.

![eq1](/images/ocfgnn/ocfgnn.png)

# Notable References

# Thoughts

As it is said in the paper, no objective function for attention change.  
Thus, it is just penalizing the attention change as a whole,  
which is not 'topology preserving' way to freeze,  
but rather a way to freeze all graph structure.  
Is it really a desirable way of freezing? May be more clever topological aware design?

# Footnote
아래와 같은 양식을 활용한다.  

```text
# 
## Quick Look
- **Authors & Affiliation**: [Authors][Affiliations]
- **Link**: [Paper link]
- **Comments**: [e.g. Published at X / arXiv paper / in review.]
- **TLDR**: [One or at most two line summary]
- **Relevance**: [Score between 1 and 5, stating how relevant this paper is to your work. Usually filled in at the end.]
# Research Topic
- **Category** (General):
- **Category** (Specific):
# Paper Summary (What)
[Summary of the paper - a few sentences with bullet points. What did they do?]
```
