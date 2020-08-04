---
title: Multiple View Geometry - Lecture 4 정리
use_math: true
tags: MVG
---


해당 포스트은 뮌헨 공과대학교(TU München)의 Prof. Dr. Daniel Cremers 께서 진행하신 Multiple View Geometry 강의를 정리한 내용입니다.

Multiple View Geometry 과목의 네번째 강의는 두 frame간 동일한 지점을 매칭하는 내용이 포함되어 있습니다.

[Video](https://www.youtube.com/watch?v=WCyKnuhM1CE)

[강의자료](https://drive.google.com/file/d/19vI3xbLeXcQuJz15UtwHp-YNsT5gZxEm/view?usp=sharing)


## From Photometry to Geometry

앞선 강의에서는 point나 line을 transformation하는 법을 학습하였지만, 보통 우리가 영상에서 얻을 수 있는 정보는 각 pixel의 밝기나 색상 정보 등입니다.

이러한 photometric representation에서 각 pixel의 실제 위치를 알아낼 수 있는 geometric representation로 변환하기 위해서는 characteristic image feature으로 point들을 식별하고, 서로 다른 frame간 일치하는 point를 결합할 수 있어야 합니다.

이렇게 서로 대응되는 point들을 matching함으로써 3D 구조를 추론할 수 있지만, 그 과정에서 computing 자원의 제한으로 인해 영상에 나타나는 모든 pixel에 대해서 해당 작업을 모두 진행할 수 없고 이로 인해 정보의 손실이 발생하게 됩니다.

앞으로의 내용에서 point matching 시에 다음과 같은 두가지 고려해야할 사항이 있습니다.

- Small deformation: 하나의 frame에서 다른 frame으로의 deformation이 매우 작다고 가정합니다. 이 경우 하나의 frame에서 다른 frame으로의 displacement를 고전적인 optic flow estimation으로 계산할 수 있으며, 이를 위한 방법으로 Lucas/Kanade 또는 Horn/Schunck 방법 등이 있습니다. 이 방법은 dense deformation fielde(모든 pixel의 displacement를 표현)을 얻을 수 있지만, 속도를 빠르게 하기 위하여 적은 지점의 displacement만 추적하는 것이 좋습니다.

- Wide baseline stereo: 이 경우 displacement가 매우 크다고 가정합니다. 또한 모든 pixel에 대해 matching을 하기는 너무 오래 걸리므로, 적은 수의 feature points를 선정하고, 다른 영상에서 matching하는 효율적인 방법을 개발합니다.


## Small Deformation & Optical Flow

Small deformation의 경우 rigidly moving을 일반적으로 다음과 같이 표현할 수 있습니다.

$$
x_2 = h(x_1) = frac{1}{\lambda_2(\typebf{X}}(R\lambda_1(\typebf{X})x_1 + T)
$$

하지만 다음과 같이 몇몇 근사 방법이 존재합니다.

- Translational model : 
$$
h(x) = x + b
$$

- Affine model:
$$
h(x) = Ax + b
$$

이때 2D affine model은 다음과 같이 표현될 수 있습니다.

$$
h(x) = x + u(x)
$$

$$
u(x) = S(x)p = 
\begin{pmatrix}
x & y & 1 & 0 & 0 & 0\\ 
0 & 0 & 0 & x & y & 1
\end{pmatrix}
\begin{pmatrix}
p_1 & p_2 & p_3 & p_4 & p_5 & p_6
\end{pmatrix}^T
$$

## The Lucas-Kanade Method


## Feature Point Extraction


## Wide Baseline Matching

