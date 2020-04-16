---
title: Multiple View Geometry - Lecture 1 정리
use_math: true
tags: MVG
---


해당 포스트은 뮌헨 공과대학교(TU München)의 Prof. Dr. Daniel Cremers 께서 진행하신 Multiple View Geometry 강의를 정리한 내용입니다.

Multiple View Geometry 과목의 첫번째 강의는 이후 내용의 이해를 위한 수학적 배경(선형대수)에 대한 내용으로 이루어져 있습니다.

[Video](https://www.youtube.com/watch?v=RDkwklFGMfo)

[강의자료](https://drive.google.com/file/d/19vI3xbLeXcQuJz15UtwHp-YNsT5gZxEm/view?usp=sharing)

## Vector Space
어떤 set V가 다음과 같은 vector summation과 scalar multiplication에 대해 닫혀있을 때, set V를 linear space 또는 vector space (over the field R)이라고 합니다.

$$
 + : V \times V \rightarrow V
$$

$$
 \cdot :R \times V \rightarrow V
$$

이를 통해 0과 음의 원소의 존재 (+연산을 이용), $\alpha(\beta u) = (\alpha\beta)u$ 와 같은 결합법칙(scalar multiplication을 이용) 등을 유추할 수 있으며, $(\alpha + \beta)v = \alpha v + \beta v, and \alpha(v + u) = \alpha v + \alpha u$ 와 같은 분배법칙 또한 두 연산의 조합으로 유추할 수 있습니다.

이러한 vector space V의 subset인 W가 V와 마찬가지로 vector summation과 scalar multiplication에 대해 닫혀있으며 0을 포함하고 있을때 W를 subspace라고 합니다.

## Linear Independence and Basis
Vector들의 집합 $S = \{ v_1, ... , v_k \} \subset V$에 의해 span 되는 subspace는 S에 속해있는 vector들로 구성할 수 있는 모든 linear combinations으로 이루어진 subspace를 의미하며, 다음과 같이 표현할 수 있습니다.

$$
 span(S) = \{ v \in V | v = \sum_{i=1}^{k}{\alpha_i v_i} \}
$$

또한 set S가 다음을 만족하면 linearly independent하다고 하며, 이는 S에 속해있는 어떤 vector v를 나머지 다른 vector들의 linear combination으로 나타낼 수 없다는 의미이다.

$$
 \sum_{i=1}^{k}{\alpha_i v_i} = 0 \rightarrow \alpha_i = 0 \;\; \forall i
$$

Vector들의 집합 $B = \{ v_1, ..., v_n \}$이 linearly independent하며 space V를 span할 수 있을 때 B를 space V의 basis라고 하며, basis는 linearly independent vector들의 최대 집합입니다.

이러한 basis는 아래와 같은 성질을 가지고 있습니다.(아래에서 B와 B'은 linear space V의 basis들입니다.)

- B와 B'은 같은 수의 원소(vector)를 포함하고 있으며, 이 숫자 n을 space V의 dimension(차원)이라고 합니다.

- V에 속해있는 모든 vector v는 basis vector들(B에 속해있는 vector들)의 linear combination에 의해 unique하게 표현됩니다.(즉 basis vector들로 해당 vector v를 표현하는 방법은 한가지 뿐입니다.)

- B의 모든 vector들은 또다른 basis인 $ b'_i \in B' $의 linear combination으로 다음과 같이 표현될 수 있습니다.

$$
 b'_i = \sum_{j=1}^{n}{\alpha_{ji} b_j}
$$

위의 세번째 성질에서 나타나는 coefficient $\alpha_{ji}$를 이용하여 basis transform을 나타내는 matrix A를 만들 수 있으며, $B' = BA \Leftrightarrow B=B'A^{-1}$이라고 할 수 있습니다.


## Inner Product
Vector space에서는 다음과 같은 inner product라는 연산을 정의할 수 있습니다.

$$
 \langle \cdot, \cdot \rangle : V \times V \rightarrow R
$$

이러한 inner product는 다음과 같은 세가지 성질을 갖습니다.

- $\langle u, \alpha v + \beta w \rangle = \alpha \langle u, v \rangle + \beta \langle u, w \rangle$ (linear)

- $\langle u, v \rangle = \langle v, u \rangle$ (symmetric)

- $\langle v, v \rangle \geq 0 \; , and \; \langle v, v \rangle = 0 \Leftrightarrow v = 0 $ (positive definite)

내적을 통해 다음과 같이 vector의 norm(vector의 길이를 계산)과 metric(두 vector간 거리를 계산)을 계산할 수도 있습니다.

$$
 | \cdot | : V \rightarrow R, \; |v| = \sqrt{\langle v, v \rangle} \; \; (norm)
$$

$$
 d : V \times V \rightarrow R, \; d(v,w) = |v-w| = \sqrt{\langle v-w, v-w \rangle} \; \; (metric)
$$

이와 같이 space V에서 scalar product로 생성되는 metric을 Hilbert space라고 합니다.

$V = R^n$에서 basis가 canonical basis $B = I_n$일 경우 아래와 같이 canonical inner product를 정의할 수 있습니다.(해당 강의에서는 $I_n$을 identity matrix(단위행렬)에서 대각성분들이 n인 행렬로 정의하고 있습니다.)

$$
 \langle x, y \rangle = x^T y = \sum_{i=1}^{n}{x_i y_j}
$$

또한 이로부터 L2-norm(또는 Euclidean norm)을 정의할 수 있습니다.

$$
 |x|_2 = \sqrt{x^T x} = \sqrt{x_1^2 + \cdot \cdot \cdot + x_n^2}
$$

그리고 위에서 정의했던 basis transform A를 이용하여 다른 coordinate에서의 cannonical inner product를 계산할 수 있습니다.

Canonical basis B에서 B'사이의 basis transform가 A일때, $I=B' A^-1$이라고 할 수 있으며, 새로운 coordinate x', y'의 cannonical inner product는 다음과 같습니다.

$$
 \langle x, y \rangle = x^T y = (Ax')^T(Ay') = x'^T A^T A y' \equiv \langle x', y' \rangle_{A^T A}
$$

위의 식에서 두번째 term과 세번째 term 사이에 $x=Ax', y=Ay'$의 관계가 존재하는데 이 부분에 대한 설명이 강의자료에는 나와있지 않습니다.

이 부분에 대해서는 다음과 같이 이해를 하면 좋을 것 같습니다.(2차원의 예시에 한정된 설명이지만 임의의 차원으로 확장시켜도 무리가 없을 것 같습니다.)

---

어떤 point를 basis $B' = \{ b'_1, b'_2 \}$의 coordinate에서 바라본 좌표가 $x'=(\alpha', \beta')^T$이라고 하면, 이 point의 정확한 위치는 $\alpha' b'_1 + \beta' b'_2$라고 할 수 있고, 이를 정리하면 다음과 같습니다.

$$
 B' = 
\begin{bmatrix}
b'_1 & b'_2
\end{bmatrix} 
$$

$$
\alpha' b'_1 + \beta' b'_2 = B'
\begin{pmatrix}
\alpha' \\ \beta' 
\end{pmatrix} = B'x'
$$

이때, $B' = BA$이므로 위의 수식은 다음과 같이 정리될 수 있습니다.

$$
B'x'= BAx'
$$

만약 해당 point를 B의 coordinate에서 보았을 때, 해당 point의 위치는 $Bx$의 형태로 나타날 것으므로 위의 식에서 $Ax'$ 부분이 x에 해당함을 알 수 있습니다.

즉, basis transform matrix가 주어졌을 때, 이를 주어진 vector에 곱함으로써 다른 좌표계에서의 해당 vector의 좌표값을 얻을 수 있습니다.

---

추가적으로 내적을 이용하여 두 vector의 orthogonal(직교)를 다음과 같이 정의할 수 있습니다.

$$
\langle v, w \rangle = 0
$$


## Kronecker Product and Stack of a Matrix

두 matrix $A \in R^(m \times n)$과 $A \in R^(k \times l)$이 주어졌을때 이들의 Kronecker product를 다음과 같이 정의할 수 있습니다.

$$
A \otimes B \equiv 
\begin{pmatrix}
a_{11}B & \cdots & a_{1n}B\\ 
\vdots & \ddots & \vdots\\ 
a_{m1}B & \cdots & a_{mn}B 
\end{pmatrix}
\in R^{mk \times nl}
$$

또한 주어진 $A \in R^(m \times n)$의 stack $A^s$는 다음과 같이 A에 속해있는 n개의 column vector들을 쌓은 것으로 정의할 수 있습니다.

$$
A^s \equiv 
\begin{pmatrix}
a_1\\ 
\vdots\\ 
a_n
\end{pmatrix} \in R^{mn}
$$

위의 두 notation을 통해 아래와 같이 기존의 식으로 새롭게 표현할 수 있습니다.

$$
u^TAv = (v \otimes u )^T A^s
$$

## Linear Transformations and Matrices

Linear transform은 두 linear space V, W 사이의 map $L : V \rightarrow W$로 정의되며, 다음과 같은 성질을 가지고 있어야 한다.

$$
L(x+y) = L(x) + L(y) \;\;\; \forall x, y \in V \\
L(\alpha x) = \alpha L(x) \;\;\; \forall x \in V, \alpha \in R
$$


## The Linear Groups GL(n) and SL(n)

## Matrix Representation of Groups

## Range, Span, Null Space and Kernel

## Eigenvalues and Eigenvectors

## Symmetric Matrices

## Norms of Matrices

## Skew-symmetric Matrices

## The Singular Value Decomposition (SVD)

## The Generalized (Moore Penrose) Inverse


<!--more-->

---
