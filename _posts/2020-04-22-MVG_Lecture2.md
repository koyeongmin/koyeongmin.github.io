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

























