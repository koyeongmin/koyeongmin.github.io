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

이와 같이 rigid-body motion은 길이와 orientation을 보존하므로, rigid-body motion $g_t$는 물체의 origin과 orthonormal oriented vector($e_1, e_2, e_3 \in R^3$)로 구성되는 Cartesian coordinate frame의 motion으로 충분히 정의될 수 있습니다.

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

Exponential Coordinates of Rotation는 infinitesimal rotation(매우 작은 각도의 회전)의 표현을 위해 사용됩니다.

우선 rotation matrix들의 family R(t)가 한 point를 orginal location(R(0) = I)를 다른 지점으로 continuously transform한다고 합시다.

$$
X_{trans}(t) = R(t) X_{orig}, \;\;\; with R(t) \in SO(3)
$$

$R(t)R(t)^t = I$이므로 다음과 같은 식을 유도 할 수 있습니다.

$$
\frac{d}{dt}(RR^T) = \dot{R}R^T = R\dot{R}^T = 0 \;\;\; \Rightarrow \;\;\; \dot{R}R^T = -(\dot{R}R^T)^T   
$$

따라서 $\dot{R}R^T$는 skew-symmetric matrix이며 다음과 같이 $\hat{}$ operator와 어떤 vector $w(t) \in R^3$을 이용하여 다음과 같이 나타낼 수 있습니다.

$$
\dot{R}(t)R^t(t) = \hat{w}(t) \;\;\; \Leftrightarrow \dot{R}(t) = \hat{w}R(t)
$$

이때 $R(0) = I$이므로 $\dot{R}(0) = \hat(w)(0)$이며, 이러한 skew-symmetric matrix $\hat{w}(0) \in so(3)$으로 부터 rotation의 first order approximation을 다음과 같이 찾을 수 있습니다.

$$
R(dt) = R(0) + dR = I + \hat{w}(0)dt
$$

## Lie Group and Lie Algebra

위에서 infintesimal roation $R \in SO(3)$은 어떤 skew-symmetric matrix $so(3) = {\hat{w} \mid w \in R^3}$ 에 의해 근사될 수 있음을 보였고, 이러한 rotation group SO(3)는 Lie group, so(3)는 Lie algebra라고 하며, Lie algebra는 rotation group SO(3)의 identity에서의 tangent space 

Lie algebra에서 사용되는 연산 중 하나인 Lie bracket은 다음과 같습니다.

$$
\lbrack ., . \rbrack \; : \; so(3) \times so(3) \; \rightarrow \; so(3) \;\;\;\;\;\; \lbrack \hat{w}, \hat{v} \rbrack \equiv \hat{w}\hat{v} - \hat{v}\hat{w}
$$

skew symmetric matrix $\hat{w}$가 시간 t에 대해 constant하다고 하면, infinitesimal formulation은 다음과 같이 differential equation system으로 생각 할 수 있습니다.

$$
\begin{cases}
\dot{R}(t) & = \hat{w} R(t)\\ 
\dot{R}(0) & = I  
\end{cases}
$$

위의 differential equation system의 해는 다음과 같습니다.

$$
R(t) = e^{\hat{w}t} = \sum_{n=0}^{\infty}{\frac{(\hat{w}t)^n}{n!}} = I + \hat{w}t + \frac{(\hat{w}t)^2}{2!} + \cdots
$$

이는 $\mid w \mid = 1$일 경우 $w \in R^3$을 축으로 하는 t만큼의 회전을 의미하며, 이때 t는 scalar이므로 $\hat{v} = \hat{w} t$와 같이 하나의 vector로 표현될 수 있습니다.

이러한 matrix exponetial을 통해 다음과 같은 Lie algebra에서 Lie group으로의 mapping을 표현 할 수 있습니다.

$$
exp : so(3) \rightarrow SO(3) \;\;\; \hat{w} \rightarrow e^{\hat{w}}
$$

마찬가지로 exponetial의 역인 logarithm을 사용하면, Lie group에서 Lie algebra으로의 mapping을 $\hat{w} = log(R)$과 같이 찾을 수 있습니다.

$R = (r_{ij}) \ne I$라면 $w$는 다음과 같습니다.

$$
\mid w \mid cos^{-1} (\frac{trace(R)-1}{2}) \;\;\;\;\;\; \frac{w}{\mid w \mid} = \frac{1}{2sin(\mid w \mid)}
\begin{pmatrix}
r_{32} - r_{23}\\ 
r_{13} - r_{31}\\ 
r_{21} - r_{12}
\end{pmatrix}
$$

$R=I$일 경우 $\mid w \mid = 0$이며, 위의 식으로 부터 rotation R은 $\mid w \mid$만큼의 각도로 $\frac{w}{\mid w \mid}$의 축을 기준으로 회전하는 변환임을 알 수 있습니다.(해당 강의 자료에서는 이에 대한 증명을 진행하지 않음)

또한 각도에 $2\pi$를 곱하여도 같은 ratation이 되므로 위의 표현은 uniqe하지 않습니다.


## Rodrigues’ Formula

$e^{i\phi} = \cos(\phi) + i \sin(\phi), \;\; \forall \phi \in R $와 같은 Euler equation은 exponential을 삼각함수로 표현해줍니다.

Skew-symmetric matrix의 경우에도 다음과 같은 표현식이 있으며, 이를 Rodrigues' formula라고 합니다.

$$
e^{\hat{w}} = I + \frac{\hat{w}}{\mid w \mid}\sin(\mid w \mid) + \frac{\hat{w}^2}{\mid w \mid^2}(1 - \cos(\mid w \mid))
$$

증명은 다음과 같습니다.

- $t = \mid w \mid, \;\;\; v = w/\mid w \mid$
- $\hat{v}^2 = vv^T - I, \;\;\; \hat{v}^3 = - \hat{v}, \cdots $
- $e^{\hat{w}} = e^{\hat{v}t} = I + (t - \frac{t^3}{3!} + \frac{t^5}{5!} - \cdots)\hat{v} + (\frac{t^2}{2!} - \frac{t^4}{4!} + \frac{t^6}{6!} - \cdots)\hat{v}^2 $
- $e^{\hat{w}} = e^{\hat{v}t} = I + \sin(t)\hat{v} + (1 - \cos(t))\hat{v}^2$


## Representation of Rigid-body Motions SE(3)

Rigid-body motion은 translation과 rotation에 의해 unique하게 결정됩니다. 따라서 rigid-body motion의 space를 하나의 special Euclidean transformation의 group으로 볼 수 있으며, 이는 다음과 같습니다.

$$
SE(3) \equiv \{g = (R, T) \mid R \in SO(3),\; T \in R^3 \}
$$

Homogeneous coordinate에 대해서는 다음과 같이 쓸 수 있습니다.

$$
SE(3) \equiv \left\{g = 
\begin{pmatrix}
R & T\\ 
0 & 1 
\end{pmatrix} \mid R \in SO(3), \; T \in R^3 \right\} \subset R^{4 \times 4}
$$


## The Lie Algebra of Twists

Rigid-body transformation $g$에 대해서 다음과 같이 계산할 수 있습니다.

$$
\dot{g}(t)g^{-1}(t) = 
\begin{pmatrix}
\dot{R}R^T & \dot{T}-\dot{R}R^TT\\ 
0 & 0
\end{pmatrix} \in R^{4 \times 4}
$$

이때, 위에서 보았듯이 SO(3)의 경우 $\dot{R}R^T$는 알맞는 skew-symmetric matrix $\hat{w} \in so(3)$로 나타낼 수 있으며, $v(t) = \dot{T}(t) - \hat{w}(t) T(t)$라고 하면 다음과 같이 쓸 수 있습니다.

$$
\dot{g}(t)g^{-1}(t) = 
\begin{pmatrix}
\hat{w}(t) & v(t)\\ 
0 & 0
\end{pmatrix} \equiv \hat{\xi}(t) \in R^{4 \times 4}
$$

여기서 양변에 g(t)를 곱하면 다음과 같은 식을 얻을 수 있습니다.

$$
\dot{g} = \dot{g}g^{-1}g = \hat{\xi}g
$$

여기서 $4 \times 4$ matrix $\hat{\xi}$은 curve g(t)의 tangent로 볼 수 있으며, $\hat{\xi}$를 twist라고 합니다.

이는 Lie algbra가 Lie group의 tangent space인 것과 같으며, 다음과 같이 하나의 group으로 볼 수 있습니다.

$$
se(3) \equiv \left\{ \hat{\xi}
\begin{pmatrix}
\hat{w} & v\\ 
0 & 0
\end{pmatrix} \mid \hat{w} \in so(3), \; v \in R^3 \right\} \subset R^{4 \times 4}
$$

그리고 skew-symmetric matrix와 비슷하게 $\hat{}$, $\check{}$ operator를 통해 twist $\hat{\xi} \in se(3)$과 twist coordinates $\xi \in R^6$ 사이의 변환을 다음과 같이 나타낼 수 있습니다.

$$
\hat{\xi} \equiv
\begin{pmatrix}
v\\ 
w
\end{pmatrix} ^{\wedge} \equiv
\begin{pmatrix}
\hat{w} & v\\ 
0 & 0
\end{pmatrix} \in R^{4 \times 4} \;\;\;\;\;\; 
\begin{pmatrix}
\hat{w} & v\\ 
0 & 0
\end{pmatrix}^{\vee} = 
\begin{pmatrix}
v\\ 
w
\end{pmatrix} \in R^{6}
$$

## Exponential Coordinates for SE(3)

위의 twist coordinate $\xi = \begin{pmatrix}
v\\ 
w
\end{pmatrix}$는 linear velocity $v \in R^3$과 angular velocity $w \in R^3$을 쌓은 형태이며, 이를 이용하여 다음과 같은 differential equation system을 얻을 수 있습니다.

$$
\begin{cases}
\dot{g}(t) & = \hat{\xi} g(t), \;\;\; \hat{\xi} = const.\\ 
\dot{g}(0) & = I  
\end{cases}
$$

위의 system의 해는 다음과 같습니다.

$$
g(t) = e^{\hat{\xi}t} = \sum_{n=0}^{\infty}{\frac{(\hat{\xi}t)^n}{n!}}
$$

따라서 $w=0$일 때는 $e^{\hat{\xi}} = 
\begin{pmatrix}
I & v\\ 
0 & 1
\end{pmatrix}$이고, $w \ne 0$일 경우 다음과 같습니다.

$$
e^{\hat{\xi}} =
\begin{pmatrix}
e^{\hat{w}} & \frac{(I-e^{\hat{w}})\hat{w} v + w w^T v}{\mid w \mid^2}\\ 
0 & 1
\end{pmatrix}
$$

이러한 사실에서 exponential map이 Lie algebra se(3)에서 Lie group SE(3)로의 transformation을 정의함을 알 수 있으며, 이때 $\hat{\xi}$를 SE(3)의 exponential coordinates라고 합니다.

$$
exp : \; se(3) \;\; \rightarrow \;\; SE(3) \;\;\;\;\;\; \hat{\xi} \rightarrow e^{\hat{\xi}}
$$

이때 주어진 $g \in SE(3)$에 대해 $g \in exp{\xi}$를 만족하는 $\xi = (v, w)$를 언제나 찾을 수 있습니다.


## Representing the Motion of the Camera

움직이는 카메라에서 어떤 장면을 관찰할 때, 어떤 point의 coordinate나 속도 등은 카메라를 따라 변화하게 됩니다.

이러한 변환은 위에서 나온 rigid-body transformation에 의해 처리 될 수 있습니다.

고정된 world frame과 camera frame이 존재하며, 처음에는 두 frame이 일치한다고 가정하면 (g(0) = I) world 좌표의 어떤 point $X_0$를 time t의 camera frame에서는 다음과 같이 관측됩니다.

$$
X(t) = R(t)X_0 + T(t)
$$

Homogeneous 표현에서는 다음과 같습니다.

$$
X(t) = g(t)X_0
$$

Frame $t_1$에서 $t_2$로의 transformation을 $g(t_2, t_1)$라고 하면 다음이 성립합니다.

$$
g(t_3, t_2)g(t_2, t_1) = g(t_3, t_1)
$$

또한 이로부터 다음을 유추할 수 있습니다.

$$
g(t_1, t_2)g(t_2, t_1) = g(t_1, t_1) = I \;\;\;\;\;\; g^{-1}(t_2, t_1) = g(t_1, t_2)
$$


## Rules of Velocity Transformation

위의 내용을 이용하여 frame t에서의 point $X_0$의 속도를 다음과 같이 twist coordinate와 함께 나타낼 수 있습니다.

$$
\dot{X}(t) = \dot{g}(t)X_0 = \dot{g}(t)g^{-1}(t)X(t) = \hat{V}(t)X(t)
$$

따라서 $\hat{V}(t)$는 camera frame에서 보이는 world frame의 relative velocity라고 할 수 있습니다.


## Transfer Between Frames: The Adjoint Map

만약 $g_{xy}: \; Y = g_{xy}X(t)$와 같은 transformation으로 관측자가 다른 frame A로 변환된다면, 새로운 frame에서의 point의 속도는 다음과 계산될 수 있습니다.

$$
\dot{Y}(t) = g_{xy}\dot{X}(t) = g_{xy}\hat{V}X(t) = g_{xy}\hat{V}g^{-1}_{xy}Y(t)
$$

즉 camera frame A에서 관측된 point의 relative velocity는 다음과 같이 twist로 표현될 수 있습니다.

$$
\hat{V}_y = g_{xy}\hat{V}g^{-1}_{xy} \equiv ad_{g_{xy}}(\hat{V})
$$

또한 여기서 나타난 adjoint map on se(3)는 다음과 같이 정의됩니다.

$$
ad_g : se(3) \rightarrow se(3) \;\;\;\;\;\; \hat{\xi} \rightarrow g\hat{\xi}g^{-1}
$$


## Alternative Representations: Euler Angles

이제까지 나왔던 exponential parameterization에 더불어 rotation matrix를 parameterize하는 또다른 방법으로 Euler angle이 있습니다.

Lie algebra so(3)로 주어진 basis $(\hat{w}_1, \hat{w}_2, \hat{w}_3)$에 대해 다음과 같이 $R^3$에서 Lie group SO(3)로의 mapping을 정의할 수 있습니다.

$$
\alpha : (\alpha_1, \alpha_2, \alpha_3) \;\;\; \rightarrow \;\;\; exp(\alpha_1\hat{w}_1 + \alpha_2\hat{w}_2 + \alpha_3\hat{w}_3)
$$

이때 coordinate $(\alpha_1, \alpha_2, \alpha_3)$를 Lie-Cartan coordinates of the first kind라고 합니다.

Lie-Cartan coordinates of the second kind는 다음과 같습니다.

$$
\beta : (\beta_1, \beta_2, \beta_3) \;\;\; \rightarrow \;\;\; exp(\beta_1\hat{w}_1) exp(\beta_2\hat{w}_2) exp(\beta_3\hat{w}_3)
$$

이는 각 $\hat{w}_i$에 대해 $\beta_i$만큼씩의 회전은 3번 연속한 것을 의미하며, 각 basis가 z-, y-, x-axis로 나타날 경우, 즉 다음과 같이 w가 설정되었을 경우에 $\beta_1, \beta_2, \beta_3$을 Euler angles라고 합니다.

$$
w_1 = (0,0,1)^T, w_2 = (0,1,0)^T, w_3 = (1,0,0)^T
$$


















