---
title: Multiple View Geometry - Lecture 3 정리
use_math: true
tags: MVG
---


해당 포스트은 뮌헨 공과대학교(TU München)의 Prof. Dr. Daniel Cremers 께서 진행하신 Multiple View Geometry 강의를 정리한 내용입니다.

Multiple View Geometry 과목의 세번째 강의는 투영 기하학과 관련된 내용이 포함되어 있습니다.

[Video](https://www.youtube.com/watch?v=H6WEt3xOyPU)

[강의자료](https://drive.google.com/file/d/19vI3xbLeXcQuJz15UtwHp-YNsT5gZxEm/view?usp=sharing)


## Mathematics of Perspective Projection

<p align="center">
  <img src="https://raw.githubusercontent.com/koyeongmin/koyeongmin.github.io/master/_posts/MVG_lecture3_figure/1.png">
</p>

위의 그림은 point P가 image p에 투영되는 상황을 보여주고 있습니다.

이때 P는 좌표 $\textbf{X} = (X, Y, Z) \in R^3$를 가지고 있으며, 이는 z축이 lens의 optical axis이고 optical center에 대한 reference frame에 대한 좌표입니다.

위의 그림에 따르면, 실제로 맺히는 상 image p는 랜즈 뒤에 생기게 되지만 이를 대칭이동하여 랜즈 앞(point P와 같은 방향)으로 옮겨 아래 그림과 같이 생각한다면 앞으로의 계산이 한결 쉬워집니다.

<p align="center">
  <img src="https://raw.githubusercontent.com/koyeongmin/koyeongmin.github.io/master/_posts/MVG_lecture3_figure/2.png">
</p>

이를 이용하여 perspective transformation $\pi$를 다음과 같이 나타낼 수 있습니다.

$$
\pi : R^3 \rightarrow R^2 \;\;\;\;\;\; \textbf{X} \rightarrow x = \pi (\textbf{X}) = 
\begin{pmatrix}
f \frac{X}{Z}\\ 
f \frac{Y}{Z}
\end{pmatrix}
$$


## An Ideal Perspective Camera


## Intrinsic Camera Parameters


## Spherical Perspective Projection


## Radial Distortion


## Preimage of Points and Lines


## Projective Geometry

