---
tags: misc
date: 2022-11-22 16:00 +0900
title: "Heterogeneous Graph Neural Networks : 임성수 교수님"
categories: seminar
<!--author: wbjeon2k-->
---

### Seminars

학교에서는 종종 AI 세미나가 열리고, 그 중에는 AI 대학원 에서 진행하는 세미나 수업으로 인해 열리는 경우가 대부분이다.  
그냥 흘려 보내기에는 아까우니까 정리를 하면 좋겠다는 생각이 들었다.  

### Seminar Info

- Speaker : 충남대 CSE 임성수 교수님.
- Topic : Heterogeneous Graph Neural Networks

### Memos

- graph? vertex-edge relation. eg) drug-disease
- ML with graph?
    - learn from graph data to sovle tasks!
    - example : node classification, link prediction, ...
- node classfication:
    - given partial node labels, predict missing nodes!
- link prediction:
    - given partial links, predict missing links!
- anomaly detection:
    - latent community/anomaly structure.
- graph classification/regression?
    - relatively new topic.
    - make independent predictions specific to each graph.
    - training : subset of graph
    - target : entire graph, eg: set of molecular graphs.
- representation learning on graphs?
    - find representation to encode/decode graphs into some embedding
- embedding goal: preserving graph structure/properties
- Enc-Dec framework : minimize $L(\text{Dec}(\text{Enc}(X)))$
    - Node2Vec(KDD16), random walk based similarity
- naive way : concat adj mat + feature mat.
    - why? parameter size $O|V|$, sensitive to node orders.
- solution : neural message passing:
    - for each iteration, update each node embedding using neighborhood nods $N(u)$
    - $h^{k+1} = update(h^k, aggregate(h^k_v, N(u)) \text{  when  } v \in N(u))$
    - iterative algorithm
    - local feature-aggregation in GNN $\approx$ covolutional operation in CNN
    - aggregate from adjacent nodes $\approx$ receptive field
- Check CS224W Stanford. [CS224W Link](http://web.stanford.edu/class/cs224w/)
- parameter sharing:
    - same aggregation parameters are shared for all nodes!
- neighborhood normalization:
    - basic aggregation is sensitive to node degrees
- GCNC(ICLR17):
    - symmetric-normalized aggregation
    - using a self-loop update approach
- GraphSage(NIPS 17):
    - node sampling : fixed # of $N(u)$
    - inductive capability == parameter sharing
- GAT(ICLR18) : multi-head attention.
- Taxonomy of GNNs (TIST22) : review paper.
- knowledge graph : subject, action, object eg) A rent B
- Heterogeneous? Nodes also have types. eg) Person A rent movie B
    - node type mapping func $\phi : V \rightarrow A$
    - link type mapping func $\psi : V \rightarrow R $
    - $|A| + |R| > 2$ : heterogeneous.
- metapath : sequence of node types and link types.
    - eg, given 'person a rents movie b'
    - metapath : $a \rightarrow b \rightarrow a$
    - able to augment graph!
- MAGNN(WWW20), GTNC(NIPS19): make 'useful' metapath.
- Prof's way : treat metapath instance as a node:
    - relation between metapath : link
    - merge metapath-nodes when more thatn 2 common nodes

### Questions
- acyclic / cyclic 상관 없음?
    - practically works well, theoretically open problem

### Conclusion
- GNN 관심 있던 차 적절했던 세미나.