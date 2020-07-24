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

이를 이용하여 perspective transformation $\pi$를 다음과 같이 나타낼 수 있으며, 이는 위의 그림에서 point와 image 사이에 매칭되는 점에 대한 비례를 통해 유도될 수 있습니다.

$$
\pi : R^3 \rightarrow R^2 \;\;\;\;\;\; \textbf{X} \rightarrow x = \pi (\textbf{X}) = 
\begin{pmatrix}
f \frac{X}{Z}\\ 
f \frac{Y}{Z}
\end{pmatrix}
$$


## An Ideal Perspective Camera

위의 perspective transformation은 homogeneous coordinate에서  다음과 같이 표현될 수 있습니다.

$$
Z \textbf{x} = Z 
\begin{pmatrix}
x \\ 
y \\
1
\end{pmatrix} = 
\begin{pmatrix}
f & 0 & 0 & 0 \\ 
0 & f & 0 & 0 \\
0 & 0 & 1 & 0 
\end{pmatrix}
\begin{pmatrix}
X \\ 
Y \\
Z \\
1
\end{pmatrix} = K_f \Pi_0 \textbf{X}
$$

이때, $\textbf{x}$는 image의 좌표, $\textbf{X}$는 point의 좌표이며 $K_f, \Pi_0$는 다음과 같습니다.

$$
K_f \equiv 
\begin{pmatrix}
f & 0 & 0 \\ 
0 & f & 0 \\
0 & 0 & 1 
\end{pmatrix} \;\;\;\;\;\;
\Pi_0 \equiv 
\begin{pmatrix}
1 & 0 & 0 & 0 \\ 
0 & 1 & 0 & 0 \\
0 & 0 & 1 & 0 
\end{pmatrix}
$$

여기서 matrix $\Pi_0$는 standard projection matrix라고 하며, $Z$가 0 이상의 상수, $\lambda$라고 하면 다음과 같습니다.

$$
\lambda \textbf{x} = K_f \Pi_0 \textbf{X}
$$

이전에 나왔던 camera의 rigid motion을 통해 다음과 같이 world 좌표계의 point $\textbf{X}_0$에서 camera 좌표계의 point $\textbf{X}$를 얻을 수 있습니다.

$$
\textbf{X} = R \textbf{X}_0 + T
$$

Homogeneous 좌표계 $\textbf{X} = (X, Y, Z, 1)^T$ 로 표현하는 경우에는 다음과 같습니다.

$$
\textbf{X} = g \textbf{X}_0 =
\begin{pmatrix}
R & T \\ 
0 & 1
\end{pmatrix}
\textbf{X}_0
$$

이들을 결합하면, 다음과 같이 world 좌표계에서 image 좌표계로의 transformation을 얻을 수 있습니다.

$$
\lambda \textbf{x} = K_f \Pi_0 g \textbf{X}_0
$$

또한 focal length $f$ 가 알려져 있어 이를 1로 normalize(image 좌표계의 unit을 바꿈으로써 normalize 할 수 있음) 할 수 있는 경우 다음과 같이 표현됩니다.

$$
\lambda \textbf{x} = \Pi_0 \textbf{X} = K_f \Pi_0 g \textbf{X}_0
$$


## Intrinsic Camera Parameters

만약 카메라의 중심이 optical center와 일치하지 않거나, pixel 좌표가 unit scale이 아니거나, 또는 pixel이 정사각형이 아닐 경우 이를 처리하기 위한 transformation parameter가 더 필요합니다.

이를 고려하여 pixel 좌표 $(x', y', 1)$을 homogeneous camera coordinate $\textbf{X}$의 함수로 나타내면 다음과 같습니다.

$$
\lambda 
\begin{pmatrix}
x' \\ 
y' \\
1
\end{pmatrix} = 
\begin{pmatrix}
s_x & s_{\theta} & o_x \\ 
0 & s_y & o_y \\
0 & 0 & 1 
\end{pmatrix}
\begin{pmatrix}
f & 0 & 0 \\ 
0 & f & 0 \\
0 & 0 & 1 
\end{pmatrix}
\begin{pmatrix}
1 & 0 & 0 & 0 \\ 
0 & 1 & 0 & 0 \\
0 & 0 & 1 & 0 
\end{pmatrix}
\begin{pmatrix}
X \\ 
Y \\
Z  \\
1
\end{pmatrix}
$$ = K_s K_f \Pi_0 \textbf{X}

이때, $K_s$가 위에서 설명한 추가적인 transformation이며, perspective projection $\Pi_0$ 이후에 적용되는 transformation인 $K = K_s K_f$를 intrinsic parameter matrix라고 하며, 다음과 같이 정리할 수 있습니다.

$$
K \equiv K_s K_f = 
fs_x & fs_{\theta} & o_x \\ 
0 & fs_y & o_y \\
0 & 0 & 1 
\end{pmatrix}
$$

위에 표기된 각 기호의 의미는 다음과 같습니다.

- $o_x$ : x-coordinate of principal point in pixels (카메라의 중심이 optical center와 일치하지 않을 때 필요한 parameter)
- $o_x$ : y-coordinate of principal point in pixels (카메라의 중심이 optical center와 일치하지 않을 때 필요한 parameter)
- $fs_x = \alpha_x$ : size of unit length in horizontal pixels (pixel 좌표가 unit scale이 아닐 때 필요한 parameter)
- $fs_y = \alpha_y$ : size of unit length in vertical pixels (pixel 좌표가 unit scale이 아닐 때 필요한 parameter)
- $\alpha_x / \alpha_y$ : aspect ratio $\sigma$
- $fs_{\theta}$ : skew of the pixel, often close to zero (pixel이 정사각형이 아닐 경우 필요한 parameter)


그리고 위의 식을 world coordinate $\textbf{X}_0$로 나타내면 다음과 같습니다.

$$
\lambda \textbf{x}' = K \Pi_0 \textbf{X} = K \Pi_0 g \textbf{X}_0 \equiv \Pi \textbf{X}_0
$$

여기서 $3 \times 4$ matrix $\Pi \equiv K \Pi_0 g = (KR, KT)$를 genreal projection matrix라고 합니다.

그리고 아직 남아있는 scale parameter $\lambda$ 를 나누어 다음의 식을 얻을 수 있습니다.

$$
x' = \frac{\pi^T_1 \textbf{X}_0}{\pi^T_3 \textbf{X}_0} \;\;\;\;\;\; y' = \frac{\pi^T_2 \textbf{X}_0}{\pi^T_3 \textbf{X}_0}
$$

여기서 $\pi^T_1, \;\; \pi^T_2, \;\; \pi^T_3 \in R^4$는 projection matrix $\Pi$의 3가지 row입니다.



## Spherical Perspective Projection


## Radial Distortion


## Preimage of Points and Lines


## Projective Geometry

