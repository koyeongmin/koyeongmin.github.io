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

이를 통해 0과 음의 원소의 존재 (+연산을 이용), $\alpha(\beta u) = (\alpha\beta)u 와 같은 결합법칙(scalar multiplication) 등을 유추할 수 있으며, $(\alpha + \beta)v = \alpha v + \beta v, and \alpha(v + u) = \alpha v + \alpha u$ 와 같은 분배법칙 또한 두 연산의 조합으로 유추할 수 있습니다.

이러한 vector space V의 subset인 W가 V와 마찬가지로 vector summation과 scalar multiplication에 대해 닫혀있으며 0을 포함하고 있을때 W를 subspace

<!--more-->

---
