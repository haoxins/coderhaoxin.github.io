---
title: 费曼物理学讲义 (卷二) 中
description: 又闻子规啼夜月, 愁空山. 蜀道之难, 难于上青天! 使人听此凋朱颜.
date: 2022-05-14
---

## 矢量场的微分运算

```
真正理解一个方程式 -- 即不仅在严格的数学意义上 -- 意味着什么, 狄拉克对此早就有所评述.
他说: "如果我没有实际解一个方程而对其解的特性已有一种估计办法, 那我就懂得了该方程的意义."
因此, 若我们无须实际解那个方程而对在给定情况下会发生什么便已有一种了解的办法,
则我们便算"理解"了应用到这些情况上去的那个方程了.
物理上的理解乃是一种完全非数学性, 不精确和不严格的事,
但对于一个物理学家来说却是绝对必需的.
```

- 下面列举一些来自矢量代数的等式, 并假定你们都已知道了.

$$
\begin{cases}

\mathbf{A} · \mathbf{B} & = 标量 \\
                        & = A_x B_x + A_y B_y + A_z B_z \\

\mathbf{A} \times \mathbf{B} & = 矢量 \\

(\mathbf{A} \times \mathbf{B})_z & = A_x B_y - A_y B_x \\

(\mathbf{A} \times \mathbf{B})_x & = A_y B_z - A_z B_y \\

(\mathbf{A} \times \mathbf{B})_y & = A_z B_x - A_x B_z \\

\mathbf{A} \times \mathbf{A} & = 0 \\

\mathbf{A} · (\mathbf{A} \times \mathbf{B}) & = 0 \\

\mathbf{A} · (\mathbf{B} \times \mathbf{C}) & =
(\mathbf{A} \times \mathbf{B})·\mathbf{C} \\

\mathbf{A} \times (\mathbf{B} \times \mathbf{C}) & =
\mathbf{B} (\mathbf{A} · \mathbf{C}) -
\mathbf{C} (\mathbf{A} · \mathbf{B})

\end{cases}
$$

- 我们也要用到从微分学方面得来的下列两个等式:
  - $$
      Δf(x, y, z) =
      \frac{\partial f}{\partial x} Δx +
      \frac{\partial f}{\partial y} Δy +
      \frac{\partial f}{\partial z} Δz
    $$
  - $$
      \frac{\partial ^2 f}{\partial x \partial y} =
      \frac{\partial ^2 f}{\partial y \partial x}
    $$
  - 当然, 第一个等式只有在
    $$ Δx $$,
    $$ Δy $$,
    $$ Δz $$
    都趋于零的极限时才正确.

---

- 现在我们将不加证明地陈述两个数学定理.
  它们是物理学家已经知道的十分有趣而又有用的定理.
- 在一个物理问题中, 我们经常发现某一个量, 比如矢量场
  $$ \mathbf{A} $$
  的旋度为零.
  - 我们已看到, 一个梯度的旋度为零, 这是很容易记住的, 因为这种情形是矢量造成的.
  - 于是, 有可能肯定
    $$ \mathbf{A} $$
    是某一个量的梯度, 这样它的旋度才必然等于零.
- 这个有趣的定理说明, 如果
  $$ curl \mathbf{A} $$
  等于零, 则
  $$ \mathbf{A} $$
  总是某种东西的梯度, 存在某一标量场
  $$ \psi $$
  使得
  $$ \mathbf{A} $$
  等于
  $$ grad \psi $$.
  - 换句话说, 我们有`定理`: 如果
    $$ \boldsymbol{\nabla} \times \mathbf{A} = 0 $$,
    就有一个
    $$ \psi $$
    使得
    $$ \mathbf{A} = \boldsymbol{\nabla} \psi $$.
    (`2.50`)
- 若
  $$ \mathbf{A} $$
  的散度为零, 则有一个相似的定理.
  - 我们已看到, 某个矢量旋度的散度总是零.
- 如果你遇到
  $$ div \mathbf{D} $$
  为零的一个矢量场
  $$ \mathbf{D} $$,
  那你就可以得出结论,
  $$ \mathbf{D} $$
  是某个矢量场
  $$ \mathbf{C} $$
  的旋度.
  - `定理`: 如果
    $$ \boldsymbol{\nabla} · \mathbf{D} = 0 $$,
    就有一个
    $$ \mathbf{C} $$
    使得
    $$ \mathbf{D} = \boldsymbol{\nabla} \times \mathbf{C} $$.
    (`2.51`)

---

- 我们把
  $$ \nabla^2 $$
  看成一个新的算符. 这是一个标量算符. 由于它经常出现在物理学中,
  因而已被赋予一个专用名称, 即`拉普拉斯算符`.
  - $$
      拉普拉斯算符 = \nabla^2 =
      \frac{\partial ^2}{\partial x^2} +
      \frac{\partial ^2}{\partial y^2} +
      \frac{\partial ^2}{\partial z^2}
    $$.
    (`2.54`)
- 由于拉普拉斯算符是一个标量算符, 就可以用它来对一矢量进行运算,
  这意味着对在直角坐标系的每一个分量进行同一种运算:
  - $$ \nabla^{2} \mathbf{h} = (\nabla^{2} h_x, \nabla^{2} h_y, \nabla^{2} h_z) $$.

---

- (a)
  $$ \boldsymbol{\nabla} · (\boldsymbol{\nabla} T)= \nabla^2 T = 标量场 $$;
- (b)
  $$ \boldsymbol{\nabla} \times (\boldsymbol{\nabla} T) = 0 $$;
- (c)
  $$ \boldsymbol{\nabla} (\boldsymbol{\nabla} · \mathbf{h}) = 矢量场 $$;
- (d)
  $$ \boldsymbol{\nabla} · (\boldsymbol{\nabla} \times \mathbf{h}) = 0 $$;
- (e)
  $$
    \boldsymbol{\nabla} \times (\boldsymbol{\nabla} \times \mathbf{h}) =
    \boldsymbol{\nabla} (\boldsymbol{\nabla} · \mathbf{h}) -
    \nabla^2 \mathbf{h}
  $$;
- (f)
  $$
    (\boldsymbol{\nabla} · \boldsymbol{\nabla}) \mathbf{h} =
    \boldsymbol{\nabla}^2 \mathbf{h} =
    矢量场
  $$.

> 你可能会注意到, 我们从未试图发明一个新的矢量算符
  $$ (\boldsymbol{\nabla} \times \boldsymbol{\nabla}) $$.
  你看这是为什么?

## 矢量积分运算

- 这就证明, 一无限小立方体表面向外的通量等于该矢量的散度乘以该立方体的体积.
  现在我们看到了一个矢量的散度的"意义".
  - 一个矢量在 `P` 点的散度就是 `P` 点附近单位体积的通量,
    $$ \mathbf{C} $$
    的向外"流量".
- 我们已把
  $$ \mathbf{C} $$
  的散度与每个无限小体积向外的
  $$ \mathbf{C} $$
  通量联系起来了.
  - 对于任何有限体积来说, 我们可用上面证明过的事实:
    来自一体积的总通量等于从其中每一部分出来的通量之和.
  - 这就是说, 我们可遍及整个体积对散度进行积分.
  - 它向我们提供了这样一个定理:
    任何矢量的法向分量对任何闭合曲面的积分,
    也可以写成该矢量的散度对该曲面所包围的体积的积分.
  - 这个定理以高斯命名.
- __高斯定理__:
  - $$
      \int_{s} \mathbf{C} \cdot \mathbf{n} da =
      \int_{v} \nabla \cdot \mathbf{C} dV
    $$,
    (`3.18`)
  - 式中 `S` 是任一闭合曲面, 而 `V` 是这个曲面内的体积.

---

- 用任意合适的曲面 `S` 将回路填满, 并把绕这个面上一系列无限小正方形的环流加起来.
  这个和可以写成一个积分. 其结果是以斯托克斯命名的一个十分有用的定理.
  - __斯托克斯定理__:
  - $$
      \oint_{\Gamma} \mathbf{C} · d\mathbf{s} =
      \int_{s} (\nabla \times \mathbf{C})_{n} d a
    $$,
    (`3.38`)
  - 式中 `S` 是以 `Γ` 为边界的任意曲面.

---

## 矢势

## 感生电流

## 感应定律

## 麦克斯韦方程组

## 麦克斯韦方程组在自由空间中的解

## 有电流和电荷时麦克斯韦方程组的解

## 交流电路

## 空腔共振器

## 波导

## 用相对论符号表示的电动力学

## 场的洛伦兹变换

## 场的能量和场的动量

## 电磁质量

## 电荷在电场和磁场中的运动

## 张量

## 弯曲空间
