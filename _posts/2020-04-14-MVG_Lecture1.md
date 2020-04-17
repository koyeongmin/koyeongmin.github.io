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

또한 주어진 $A \in R^{m \times n}$의 stack $A^s$는 다음과 같이 A에 속해있는 n개의 column vector들을 쌓은 것으로 정의할 수 있습니다.

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

Linear transform은 두 linear space V, W 사이의 map $L : V \rightarrow W$로 정의되며, 다음과 같은 성질을 가지고 있어야 합니다.

- $L(x+y) = L(x) + L(y) \;\;\; \forall x, y \in V$
- $L(\alpha x) = \alpha L(x) \;\;\; \forall x \in V, \alpha \in R$

또한 space V에 적용되는 linear transform L은 V의 basis vector들로 정의 될 수 있으며, canonical basis $\{ e_1 , cdots, e_n \}$의 경우에는 다음과 같습니다.

$$
L(x) = Ax \;\;\; \forall x \in V \\
A = (L(e_1), \cdots , L(e_n)) \in R^(m \times n)
$$

이때 실수로 정의되는 모든 m x n matrix들은 $M(m,n)$으로 표시하며, m=n인 경우 $M(m,n) \equiv M(n)$으로 field R에서 ring(환)의 형태를 갖습니다.(ring에 대한 내용은 [link](https://freshrimpsushi.tistory.com/587)를 참조하시면 좋을 것 같습니다.)


## The Linear Groups GL(n) and SL(n)

여러가지 linear transformation 중 몇몇은 집합 G와 함께 group을 이루기도 합니다.

group은 연산 $\circ : G \times G \rightarrow G$와 set G가 함께 구성하며, 다음과 같은 성질을 가지고 있어야 합니다.

- closed: $g_1 \circ g_2 \in G \;\;\; \forall g_1, g_2 \in G$
- assoc: $(g_1 \circ g_2) \circ g_3 = g_1 \circ (g_2 \circ g_3) \;\;\; \forall g_1, g_2, g_3 \in G$
- neutral: $\exists e \in G: e \circ g = g \circ e = g \;\;\; \forall g \in G$
- invers: $\exists g^{-1} \in G: g \circ g^{-1} = g^{-1} \circ g = e \;\;\; \forall g \in G$

이러한 정의에 몇가지 특성을 추가하여 다음과 같은 group들을 정의할 수도 있습니다.

- 모든 invertible(non-singular) real n x n matrix들은 matrix multiplication과 함께 group을 이루며, 이러한 group을 general linear group(일반선형군) GL(n)이라고 합니다. 즉 GL(n)은 $det(a) \neq 0$인 모든 $A \in M(n)$을 포함하고 있습니다.

- 이러한 $A \in GL(n)$ 중 det(a) = 1 인 matrix들이 이루고 있는 group을 special linear group(특수선형군) SL(n)이라고 합니다.

또한 어떤 group G와 GL(n) 사이에 injective(단사) transformation, $R:G \rightarrow GL(n)$이 존재할 경우 G는 matrix representation을 가지고 있다고 하며, 다음과 같은 연산도 가능합니다.

$$
R(e) = I_{n \times n} \;\;\;\;\;\; R(g \circ h) = R(g)R(h) \;\;\; \forall g,h \in G
$$

이때, map R을 group homomorhphism이라고도 합니다.

이러한 matrix representation은 추상적인 group을 분석할 때 이에 해당하는 matrix group의 성질을 살핌으로써 좀 더 직관적인 분석이 가능하도록 합니다.

예를 들어 어떤 객체의 회전에 대한 group의 경우 neutral element는 회전이 없는 변환, inverse는 역회전, 여러 matrix의 곱은 회전의 반복 등에 대응합니다.

다음은 몇가지 자주 등장하는 group에 대한 설명입니다.

#### The Affine Group A(n)

Affine transformation $L: R^n \rightarrow R^n$은 matrix $A \in GL(n)$과 vector $b \in R^n$에 의해 다음과 같이 정의됩니다.

$$
L(x) = Ax + b
$$

이와 같은 affine transformation의 set을 affine group of dimentsion n이라고 하며, A(n)으로 나타냅니다.

위의 정의된 식에 따르면 b=0이 아닌 이상 L은 linear하지 않지만 $x \in R^n$을 $
\begin{pmatrix}
x\\ 
1
\end{pmatrix} \in R^{n+1}$과 같이 나타내는 homogeneous coordinates를 사용하면 다음과 같이 linear mapping으로 표현할 수 있습니다.

$$
L: R^{n+1} \rightarrow R^{n+1} \;\;\;\;\;\; 
\begin{pmatrix}
x\\ 
1
\end{pmatrix} \rightarrow
\begin{pmatrix}
A&b\\ 
0&1
\end{pmatrix}
\begin{pmatrix}
x\\ 
1
\end{pmatrix}
$$

이때 A와 b로 이루어진 matrix를 affine matrix라고 하며, 이는 GL(n+1)에 속하고, 이러한 affine matrix들의 집합은 GL(n+1)의 subgroup입니다.


#### The Orthogonal Group O(n)

Matrix $A \in M(n)$이 다음과 같이 inner product를 보존하는 경우 orthogonal 하다고 합니다.

$$
\langle Ax, Ay \rangle = \langle x, y \rangle \;\;\; \forall x, y \in R^n
$$

모든 orthogonal matrix들의 set은 othogonal group O(n)를 이루며, 이는 GL(n)의 subgroup입니다.

Othogonal matrix R을 cononical inner product에 적용할 경우 $\langle Rx, Ry \rangle = x^T R^T R y = x^T y \;\;\; \forall x,y \in R^n$가 되어야 하므로 $R^T R = R R^T = I$라는 결론이 나오며, 이를 이용하면 O(n)을 다음과 같이 정의할 수도 있습니다.

$$
O(n) = \{ R \in GL(n) | R^t R = I \}
$$

이로부터 $det(R) \in \{ \pm 1 \}$을 만족할 경우 $det(R^T R) = (det(R))^2 = det(I) = 1$을 유추할 수 있고, O(n)의 subgroup이 $det(R) \in \{ \pm 1 \}$를 만족할 경우 이 subgroup을 special orthogonal group SO(n)이라고 하며, $SO(n) = O(n) \cap SL(n)$ 입니다.(특히 SO(3)은 3차원에서의 모든 회전 변환 matrix의 group입니다.)


#### The Euclidean Group E(n)

Euclidean transformation은 다음과 같이 orthogonal matrix와 vector로 정의 됩니다.

$$
L: R^n \rightarrow R^n \;\;\;\;\;\; x \rightarrow Rx + T
$$

이러한 transformation의 집합을 Eculidean group E(n)이라고 하며, 이는 affine group A(n)의 subgroup입니다.

Eucliean transformation을 homogeneous coordinates로 나타내면 다음과 같습니다.

$$
E(n) = \left\{ 
\begin{pmatrix}
R&T\\ 
0&1
\end{pmatrix} | R \in O(n), T \in R^n
\right\}
$$

이때 $R \in SO(n)$이면 special Euclidean group SE(n)이라고 하고, 특히 SE(3)은 rigid-body motion을 나타냅니다.


## Range, Span, Null Space and Kernel, and Rank

$A \in R^{m \times n}$을 $R^n$에서 $R^m$으로의 linear map을 정의하는 matrix라고 할 때, A의 range 또는 span은 A에 의해 변환되어 도달할 수 있는 $R^m$의 subspace로 정의되며, 즉, matrix A의 range는 A의 column vector들의 span이라고 할 수 있고, 다음과 같이 나타낼 수 있습니다.

$$
range(A) = \{ y \in R^m | \exists x \in R^n : Ax = y \}
$$

Matrix A의 null space 또는 kernel은 A에 의해 0으로 mapping되는 vector들의 집합이며, 즉, A의 row vector들에 orthogonal한 vector의 집합이고, 다음과 같이 나타낼 수 있습니다.

$$
null(A) \equiv ker(A) = \{ x \in R^n | Ax = 0 \}
$$

Matrix A의 rank는 range의 dimension입니다.

$$
rank(A) = dim(range(A))
$$

Matrix $A \in R^{m \times n}$의 rank는 다음과 같은 성질을 갖습니다.

- $rank(A) = n - dim(ker(A))$

- $0 \leq rank(A) \leq min(m,n)$

- $rank(A)$는 A의 row vector 중 서로 linearly independent한 vector들의 최대 갯수와 같습니다.

- rank(A)는 A의 minor 중 0이 아닌 것들의 hightest order와 같으며, 여기서 minor of order k는 A의 k x k submatrix의 determinant입니다.

- Sylvester's inequality: $B \in R^{n \times k}$일때 $AB \in R^{m \times k}$이며, $rank(A) + rank(B) -n \leq rank(AB) \leq min(rank(A), rank(B))$

- 모든 nonsigular matrix $C \in R^{m \times m}$, $D \in R^{n \times n}$에 대해 $rank(A) = rank(CAD)$



## Eigenvalues and Eigenvectors

$A \in C^{n \times n}$이 complex matrix라고 할 때, 다음을 만족하는 0이 아닌 vector $v \in C^n$을 A의 (right) eigenvector라고 하며, $\lambda$를 A의 eigenvalue라고 합니다.

$$
Av = \lambda v \;\;\;\;\;\; with \;\; \lambda \in C
$$

이와 비슷하게 $v^T A = \lambda v^T$를 만족하는 v를 A의 left eigenvector라고 하기도 하며, matrix A의 모든 eigenvalue들의 집합을 spectrum $\sigma (A)$라고 합니다.

또한 D가 matrix A의 eigenvalue들을 포함하는 diagonal matrix(대각행렬)이고, V가 각 eigenvalue에 대응하는 eigenvector를 column으로 가지고 있는 matrix라고 할 때, 위의 정의로부터 AV=VD 가 만족함을 유추할 수 있습니다.

그리고 $A \in R^{n \times n}$인 square matrix일 경우 다음과 같은 성질을 갖습니다.

- $Av = \lambda v$인 $\lambda \in R$이 존재할 경우, left-eigenvector $\eta \in R^n$ 또한 존재합니다.(즉, $\eta ^T A = \lambda \eta ^T$를 만족하는 $\eta$가 존재하며, $\sigma (A) = \sigma (A^T)$입니다.)

- 서로 다른 eigenvalue에 대응하는 eigenvector들은 서로 linearly independent합니다.

- 모든 eigenvector $\sigma (A)$는 characteristic polynomial(특성방정식) $det(\lambda I - A) = 0$의 해이며, 따라서 det(A)는 모든 eigenvalue의 곱과 같습니다.(이때, 중근이 발생하는 경우 해당 eigenvalue는 여러번 곱해주어야 합니다.)

- 어떤 nonsigular matrix P에 대해 $B = PAP^{-1}$일 경우 $\sigma (B) = \sigma (A)$입니다.

- Eigenvalue가 복소수일 경우, 해당 eigenvalue의 conjugate 또한 eigenvalue입니다. 

또한 matrix A를 하나의 좌표 변환으로 사용한다면, eigenvector는 A를 통해 좌표변환을 하여도 방향이 바뀌지 않고 크기만 변하는(스칼라 배만 되는) vector, eigentvalue는 vector의 크기 변화율로 이해할 수도 있습니다.


## Symmetric Matrices

어떤 matrix $S \in R^{n \times n}$이 $S^T = S$를 만족할 경우 matrix S를 symmetric하다고 합니다.

이때 symmetric matrix S가 $x^T S x \geq 0$라면 이를 positive semi-definite라고 하고($S \geq 0$라고 표시), $x^T S x \gt 0 \;\; if \; \forall x \ne 0$이면 positive definte($S \gt 0$라고 표시)라고 합니다.

$S \in R^{n \times n}$가 real symmetric matrix라고 하면 다음의 성질을 갖습니다.

- S의 모든 eigenvalue들은 실수입니다.

- 서로 다른 eigenvalue에 대응하는 eigenvector들은 서로 othogonal합니다.

- 언제나 $R^n$의 basis 형태의 n개의 orthonormal한 eigenvector들의 존재하며, $V = (v_1, \cdots, v_n) \in O(n)$을 eigenvector들이 이루는 orthogonal matrix, $\Lambda = diag(\lambda_1, \cdots, \lambda_n)$을 eigenvalue들이 이루는 diagonal matrix라고 할때, $S = V\Lambda V^T$입니다.

- 모든 eigenvalue가 positive(nonnegative)라면 S는 positive (semi-)definite입니다.

- S가 positive semi-definite이고, $ \lambda_1, \lambda_n $이 각각 최대, 최소의 eigenvalue라면,
$ \lambda_1 = max_{|x|=1} \langle x, Sx \rangle \;\;\; \lambda_n = min_{|x|=1} \langle x, Sx \rangle $ 


## Norms of Matrices

어떤 matrix $A \in R^{m \times n}$의 norm을 정의하는 방법은 여러가지가 있지만 대표적인 방법으로 2가지 정도를 생각해 볼 수 있습니다.

첫번째로 induced 2-norm의 경우 다음과 같이 정의됩니다.

$$
\parallel A \parallel_2 \equiv \max_{|x|_2 = 1}{|Ax|_2} = \max_{|x|_2 = 1}{\sqrt{\langle x, A^T A x \rangle}}
$$

다음으로 Frobenius norm은 다음과 같이 정의됩니다.

$$
\parallel A \parallel_f \equiv \sqrt{\sum_{i, j}{A^2_{ij}}} = \sqrt{trace(A^T A)}
$$

일반적으로는 위의 두 norm이 서로 같지 않음에 주의하여야 합니다.

또한 $A^T A$는 symmetric, positive semi-definite하기 때문에 $A^T A = V diag(\sigma^2_1, \cdots, \sigma^2_n) V^T, \;\;\; \sigma^2_1 \geq \sigma^2_n \geq 0 $이며, 다음을 유추할 수 있습니다.

$$
\parallel A \parallel_2 = \sigma_1 \;\;\;\;\;\; \parallel A \parallel_f = \sqrt{trace(A^T A)} = \sqrt{ \sigma^2_1 + \cdots + \sigma^2_n}
$$

## Skew-symmetric Matrices

어떤 matrix $A \in R^{n \times n}$이 $A^T = -A$를 만족하는 경우, A를 skew-symmetric 또는 anti-symmetric하다고 합니다.

만약 A가 real skew-symmetric일 때, 다음과 같은 성질을 갖습니다.

- A의 모든 eigenvalue은은 0이거나 복소수 성분만 가지고 있는 수(purely imaginary)입니다.

- $A = V \Lambda V^T$를 만족하는 orthogonal matrix V가 존재하며, 이때 $\Lambda$는 block-diagonal matrix이고 $\Lambda=diag(A_1, \cdots , A_m, 0, \cdots, 0)$, 각 $A_i$는 다음과 같은 형태의 skew-symmetric matrix입니다.

$$
A_i = 
\begin{pmatrix}
0&a_i\\ 
-a_i&0
\end{pmatrix} \in R^{2 \times 2} \;\;\;\;\;\; i = 1, \cdots, m
$$

특히, 모든 skew-symmetric matrix의 rank는 짝수입니다.


## The Singular Value Decomposition (SVD)



## The Generalized (Moore Penrose) Inverse




<!--more-->

---
