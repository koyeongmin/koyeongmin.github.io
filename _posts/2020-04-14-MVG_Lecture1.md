---
title: Multiple View Geometry - Lecture 1 정리
use_math: true
tags: MVG
---


해당 포스트은 뮌헨 공과대학교(TU München)의 Prof. Dr. Daniel Cremers 께서 진행하신 Multiple View Geometry 강의를 정리한 내용입니다.

Multiple View Geometry 과목의 첫번째 강의는 이후 내용의 이해를 위한 수학적 배경(선형대수)에 대한 내용으로 이루어져 있습니다.


## Vector Space
어떤 set V가 다음과 같은 vector summation과 scalar multiplication에 대해 닫혀있을 때, set V를 linear space 또는 vector space (over the field R)이라고 합니다.

$$
 + : V \times V \rightarrow V
$$

$$
 \bullet :R \times V \rightarrow V
$$

이를 통해 0과 음의 원소의 존재 (+연산을 이용), $\alpha(\beta u) = (\alpha\beta)u$ 와 같은 결합법칙(scalar multiplication을 이용) 등을 유추할 수 있으며, $(\alpha + \beta)v = \alpha v + \beta v, and \alpha(v + u) = \alpha v + \alpha u$ 와 같은 분배법칙 또한 두 연산의 조합으로 유추할 수 있습니다.

이러한 vector space V의 subset인 W가 V와 마찬가지로 vector summation과 scalar multiplication에 대해 닫혀있으며 0을 포함하고 있을때 W를 subspace라고 합니다.

##Linear Independence and Basis
Vector들의 집합 $S = \{ v_1, ... , v_k \} \subset V$에 의해 span 되는 subspace는 S에 속해있는 vector들로 구성할 수 있는 모든 linear combinations으로 이루어진 subspace를 의미하며, 다음과 같이 표현할 수 있습니다.

$$
 span(S) = \{ v \in V | v = \sum_{i=1}^{k}{\alpha_i v_i} \}
$$

또한 set S가 다음을 만족하면 linearly independent하다고 하며, 이는 S에 속해있는 어떤 vector v를 나머지 다른 vector들의 linear combination으로 나타낼 수 없다는 의미이다.

$$
 \sum_{i=1}^{k}{\alpha_i v_i} = 0 \rightarrow \alpha_i = 0 \forall i
$$

Vector들의 집합 $B = \{ v_1, ..., v_n \}$이 linearly independent하며 space V를 span할 수 있을 때 B를 space V의 basis라고 하며, basis는 linearly independent vector들의 최대 집합


<!--more-->

---
