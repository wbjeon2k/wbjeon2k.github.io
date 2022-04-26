---
tags: ddop
date: 2022-03-15 12:00 +0900
title: "Daily Dose of Paper : 2022-03-15 Hierarchical Temporal Learning (HTM)"
categories: ai
<!--author: wbjeon2k-->
---

# Hierarchical Temporal Learning (HTM)

## **TLDR**

Biomimicry of brain dendrites(수상돌기).  
Hebbian learning, binary activation (0 or 1), clustered and hierarchical.  

## Quick Look

- **Authors & Affiliation**: Mohammed Terry-Jack
- **Link**: <https://arxiv.org/pdf/2202.00263.pdf](https://medium.com/wluper/nlp-with-biologically-inspired-neural-networks-ac36b3170b90)>
- **Comments**: Online Article
- **Relevance**: 4, relevant enough.  

# Research Topic

- **Category** (General): Hebbian Learning, Hierarchical Temporal
- **Category** (Specific): Hebbian Learning, Artificial Neural Network

# Paper Summary (What)

- [Wikipedia](https://en.wikipedia.org/wiki/Hierarchical_temporal_memory) 에 의하면 2004년 처음 제시 되었다고 한다.  
- Dendrite : 가지돌기/축삭돌기 in Kor. "가지돌기는 활동전위보다 강한 신호만 신경세포체로 전달한다." ([KorWikiLink](https://ko.wikipedia.org/wiki/%EA%B0%80%EC%A7%80%EB%8F%8C%EA%B8%B0))  
- 활동전위 보다 강한 신호를 전달 시키기에 fire or not, binary activation 사용.  
- 심지어 Yann LeCun 도 HTM에 대해서 알고 있다! [AMALink](https://www.reddit.com/r/MachineLearning/comments/25lnbt/ama_yann_lecun/chisjsc/)  
- Quote from Yann LeCun:
> But the difficulty is to instantiate these concepts and reduce them to practice. Another difficulty is grounding them on sound mathematical principles (is this algorithm minimizing an objective function?).
- Comparison with normal neural networks  
![img1](/images/ddop0315/img1.png)  
Below is the HTM artificial neurons.  
![img2](/images/ddop0315/img2.png)  
- Parameters  
![img3](/images/ddop0315/img3.png)  
- 내가 생각(상상)했던 neural network 와 거의 흡사하다. 하지만 Yann LeCun 도 지적했듯, theoretical basis가 약하다.  
- 하지만 hierarchical 한 접근은 눈여겨볼만 하다. Simple MLP를 HTM column처럼 만들거나, GNN을 이용한다면?  
- 사람은 날아다니는 새 에서 '비행' 이라는 개념을 얻었지만, 실제로 비행기를 만들기 위해서는 유체역학과 내연기관의 발전이 필요했다.
어찌 보면 HTM은 비행을 구현하기 위해서 '날개를 더 열심히 펄럭거리는' 것을 시도하는 것 아닐까?  
- 역시 Yann LeCun이 언급했듯, HTM의 아이디어 자체는 Deep Learning의 최종 목표와 맞닿아 있다.  
> Jeff Hawkins has the right intuition and the right philosophy. Some of us have had similar ideas for several decades. Certainly, we all agree that AI systems of the future will be hierarchical (it's the very idea of deep learning) and will use temporal prediction.



# Notable References

- Avoiding Catastrophe: Active Dendrites Enable Multi-Task Learning in Dynamic Environments
- A Mathematical Formalization of Hierarchical Temporal Memory's Spatial Pooler
- Hierarchical temporal memory using memristor networks: A survey

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
