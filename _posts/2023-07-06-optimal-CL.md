---
tags: ddop
date: 2023-07-06 18:00 +0900
title: "Daily Dose of Paper : Optimal Continual Learning has Perfect Memory and is NP-HARD"
categories: ai
<!--author: wbjeon2k-->
---

# Optimal Continual Learning has Perfect Memory and is NP-HARD

ICML 2020 paper.

## **TLDR**

- Acquiring optimal CL algorithm is at least as hard as $A \cap B = \phi$
- Which is a NP-Hard problem
- Existing CL algorithms are polynomial heuristic to find optimal CL algorithm.
- Perfect memory : For previously observed tasks $1 \cdots t$,  
  with a perfect memory, we can find $\Theta$ such that  
  $\Theta \in \{ E(\Theta_i) \cap E(\Theta_j)\}_{i,j \in 1 \cdots t}$
- i.e. (Re)Training with 'perfect memory' leads to $\Theta$ that preserves performance  
  for all previously trained tasks $1 \cdots t$

## Quick Look

- **Authors & Affiliation**: Jeremias Knoblauch  
- **Link**: <https://proceedings.mlr.press/v119/knoblauch20a/knoblauch20a.pdf>  
- **Comments**: ICML 2020  
- **Relevance**: 4.5  

# Research Topic

- **Category** (General): Continual Learning
- **Category** (Specific): Continual Learning, Set Theory

# Thoughts

- Optimal은 바라지도 않음. Suboptimal 해도 좋으니까 relaxation을 하는게 현실적이지 않나?
- $A \cap B = \phi$ --> at least as hard as 2-SAT problem --> NP-Hard 자명
- 전체 $SAT(\Theta)$ ($SAT$은 본 논문에서 제시하는 solution set) 구하는건 (당연히) intractable  
  (search space 2 to the power of million/billion parameters)
- loss landscape 에서 solution set region을 찾는거는 $SAT(\Theta)$ 의 relaxation  
  i.e. $\text{our\_solution\_set} \in SAT(\Theta)$
- 아래와 같은 자료가 있는걸 확인.  
  `Rehearsal revealed: The limits and merits of revisiting samples in continual learning(ICCV2021)`[link](https://openaccess.thecvf.com/content/ICCV2021/papers/Verwimp_Rehearsal_Revealed_The_Limits_and_Merits_of_Revisiting_Samples_in_ICCV_2021_paper.pdf)
  `REPRESENTATIONAL CONTINUITY FOR UNSUPERVISED CONTINUAL LEARNING(ICLR 2022)`[link](https://arxiv.org/pdf/2110.06976.pdf)
- `Rehearsal revealed...` 는 우리의 문제 해석과 거의 똑같음. 다만 해법을 제시하지는 않고 observation만 제시
- `REPRESENTATIONAL CONTINUITY...` 는 unsupervised 방법을 쓰면 'smoother' loss landscape 나온다는 내용. 다만 flatness를 언급하거나 보이지는 않음.

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
