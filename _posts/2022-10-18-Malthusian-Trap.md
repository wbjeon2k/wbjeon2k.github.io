---
tags: misc
date: 2022-10-18 16:00 +0900
title: "Malthusian Trap in Academia"
categories: misc
<!--author: wbjeon2k-->
---

### Malthusian Trap

모르는 것은 exponential 하게 증가하는데, 아는 것은 linear 하게 증가한다.  
이는 맬서스의 함정과 자연스럽게 연결된다.  

### Malthusian Trap in Academia

Continual Learning, self-supervised learning, ViT, diffusion models, etc ...  
해당 키워드만 해도 알아야 할 내용이 매우 방대하다.  
하지만 현실적으로는 하루에 D2L 한 챕터 나가기에도 힘들다.  
이에 내가 알아야 한다고 인지하는 범위는 exponential 하게 증가하는데,  
실제로 내가 아는 범위는 시간에 정비례 하게 늘어난다.  

### 실제로 함정은 존재하는가?

맬서스의 함정은 식량 생산이 폭발적으로 증가하면서 해결이 되었다.  
하지만 공부 량이 폭발적으로 증가 할 수 있는가? 그렇지는 않다.  
하나 기대 해볼 수 있는 부분은, 지식은 어느정도 단계가 되면 서로 연관되는 경우가 있다는 사실이다.  
맬서스의 함정과 공부가 힘든 이유가 연결되는 것 처럼 말이다.  

### 해결책?
그렇다면 공부라는 것을 '전체 지식 범위 탐색을 위한 조합 최적화 문제' 로 해석 할 수 있다고 생각한다.  
그런데 생각하면 이 문제가 익숙하다.  
지식 정점들을 이리저리 돌아다니는 최소한의 비용을 구하는건 TSP 문제와 같은 것 아닌가?  
TSP 문제는 NP-hard 이므로 실용적인 해결책은 무엇일까?  
nearest neighbour algorithm 으로 greedy 하게 접근하는게 suboptimal 하더라도 실용적으로 보인다.  
공부하는 주제와 연관된 가장 가까운 지식 정점으로 계속 이동하는게 포인트

### Conclusion
애초에 TSP 처럼 모델링 할 수도 없는 문제다. 모든 정점들이 밝혀지지 않은 상태이기 때문이다.  
따라서 현재 아는 정점에서 greedy 하게 접근을 하다가,  
서로 연관되는 정점들의 수가 exponential 하게 증가하는 것을 기대하는 수 밖에 없다.  
따라서 그냥 하는 수 밖에 없다...