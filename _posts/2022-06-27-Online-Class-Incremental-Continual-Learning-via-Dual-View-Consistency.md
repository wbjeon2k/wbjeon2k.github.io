---
tags: ddop
date: 2022-06-27 18:00 +0900
title: "Daily Dose of Paper : Online Class-Incremental Continual
Learning via Dual View Consistency"
categories: ai
<!--author: wbjeon2k-->
---


# Not Just Selection, but Exploration: Online Class-Incremental Continual Learning via Dual View Consistency

CVPR 2022 paper.

## **TLDR**

![pedigree](/images/ddop0627/img4.png)  
Memory-based continual learning that maintains memory bank that makes maximum loss changes (maximum gradient).  
Maximum gradient is consist of CE loss, mutual information and distribution loss similar to FSLL's triplet loss.  


## Quick Look

- **Authors & Affiliation**: Yanan Gu  
- **Link**: <https://openaccess.thecvf.com/content/CVPR2022/papers/Gu_Not_Just_Selection_but_Exploration_Online_Class-Incremental_Continual_Learning_via_CVPR_2022_paper.pdf>  
- **Comments**: CVPR 2022  
- **Relevance**: 3.5  

# Research Topic

- **Category** (General): Contrastive Learning, Continual Learning
- **Category** (Specific): Contrastive Learning

# Paper Summary (What)
 
- Problem statement
  - Information from images in the memory buffer is under-utilized.
  
- Solutions
  - Select images from buffer w.r.t maximum loss change.
  - Representation of augmented image and original image should be consistent. Adopt Mutual Information Loss.

1. Maximum Gradient

![pedigree](/images/ddop0627/img3.png)  
Select a training batch, and for each images in the memory buffer, calculate gradient for both the original parameter $$\theta$$ and parameter (virtually) updated with trainig batch $$\theta_v$$

2. Mutual Information Loss.



# Notable References

# Thoughts

Mutual Information loss is very similar with the GIT from Chelsea Finn ICLR22.  
Maximum gradient implies a sample that is closest to the decision boundary? What is the relationship between the maximum gradient sample and prototype sample?

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
