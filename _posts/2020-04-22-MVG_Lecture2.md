---
title: Multiple View Geometry - Lecture 2 정리
use_math: true
tags: MVG
---


해당 포스트은 뮌헨 공과대학교(TU München)의 Prof. Dr. Daniel Cremers 께서 진행하신 Multiple View Geometry 강의를 정리한 내용입니다.

Multiple View Geometry 과목의 두번째 강의는 카메라 등의 움직임을 나타내기 위한 수학적 표현 등을 포함하고 있습니다.

[Video](https://www.youtube.com/user/cvprtum/videos)

[강의자료](https://drive.google.com/file/d/19vI3xbLeXcQuJz15UtwHp-YNsT5gZxEm/view?usp=sharing)


## Three-dimensional Euclidean Space

Three-dimensional Euclidean Space $E^3$은 다음과 같이 $R^3$에서 정의되는 point들을 포함하는 space입니다.

$$
X \equiv (X_1, X_2, X_3)^T \in R^3 
$$

만약 두 point X와 Y가 주어질 경우 다음과 같이 bound vector를 정의할 수 있으며, 이는 시작점과 도작점이 정해져있는 vector를 의미합니다.

$$
v = Y - X \in R^3
$$

또한 만약 vector가 시작점과 무관하게, 즉 크기와 방향 만을 고려하는 vector가 있을 때 이를 free vector라고 하며 이러한 free vector의 set은 linear vector space입니다.

## Cross Product & Skew-symmetric Matrices

$R^3$에서는 다음과 같이 cross product를 정의할 수 있습니다.

$$
\times \;\;\; : \;\;\; R^3 \times R^3 \;\;\; : \;\;\; u \times v = 
\begin{pmatrix}
u_2 v_3 - u_3 v_2 \\ 
u_3 v_1 - u_1 v_3 \\ 
u_1 v_2 - u_2 v_1 
\end{pmatrix} \in R^3
$$

또한 이전에 소개되었던 skew-symmetric matrix를 이용하여 $v \rightarrow u \times v$의 mapping을 표현할 수 있습니다.

$$
\hat{u} =
\begin{pmatrix}
0 & -u_3 & u_2 \\ 
u_3 & 0 & -u_1 \\ 
-u_2 & u_1 & 0 
\end{pmatrix} \in R^{3 \times 3} \;\;\;\;\;\; u \times v = \hat{u}v
$$

위에서 사용된 $\hat{}$ operator는 $R^3$와 so(3)사이의 isomorphism이며, 이것의 역연산은 $\check{}:so(3) \rightarrow R^3$로 표현합니다.


## Rigid-body Motion

Rigid-body motion은 $g_t : R^3 \rightarrow R^3$과 같은 mapping으로 norm과 cross product를 보존합니다.

$$
\mid g_t (v) \mid = \mid v \mid, \;\;\; \forall v \in R^3
$$

$$
g_t(u) \times g_t(v) = g_t(u \times v), \;\;\; \forall u, v \in R^3
$$

또한 norm과 scalar product사이에는 다음과 같은 polarization identity가 존재하므로, rigid-body motion은 inner product와 cross product를 보존한다고 할 수도 있습니다.

$$
\langle u, v \rangle = \frac{1}{4} (\mid u+v \mid^2 - \mid u-v \mid^2)
$$

그리고 이러한 성질을 조합하면 다음과 같은 triple product 또한 보존됨을 알 수 있으며, 이는 부피의 보존성을 의미합니다.

$$
\langle g_t(u), g_t(v) \times g_t(w) \rangle = \langle u, v \times w \rangle, \;\;\; \forall u, v, w \in R^3
$$

이와 같이 regid-body motion은 길이와 orientation을 보존하므로, regid-body motion $g_t$는 물체의 origin과 orthonormal oriented vector($e_1, e_2, e_3 \in R^3$)로 구성되는 Cartesian coordinate frame의 motion으로 충분히 정의될 수 있습니다.

여기서 origin의 motion은 translation $T \in R^3$로 표현되고, vector $e_i$의 transformation은 $r_i = g_t(e_i)$와 같은 새로운 vector로 주어집니다.

이때, vector들의 scalar product와 croos product는 다음과 같이 보존됩니다.

$$
r_i^T r_j = g_t(e_i)g_t(e_j) = e_i^T e_j = \delta_{ij}, \;\;\;\;\;\; r_1 \times r_2 = r_3
$$

위의 첫번째 constraint는 matrix $R = (r_1, r_2, r_3)$이 orthogonal (rotation) matrix, $R^T R = RR^T = I$임을 의미하며, 두번째 constraint는 $det(R) = \pm 1$임을 의미합니다.

이는 R이 group SO(3)의 element라는 의미이기도 하며, 최종적으로 rigid body motion $g_t$는 다음과 같이 쓰여집니다.

$$
g_t(x) = Rx + T
$$

## Exponential Coordinates of Rotation




## Lie Group and Lie Algebra

## Rodrigues’ Formula

## Representation of Rigid-body Motions SE(3)

## The Lie Algebra of Twists

## Exponential Coordinates for SE(3)

## Representing the Motion of the Camera

## Rules of Velocity Transformation

## Transfer Between Frames: The Adjoint Map

## Alternative Representations: Euler Angles

























