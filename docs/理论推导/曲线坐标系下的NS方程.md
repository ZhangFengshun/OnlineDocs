---
sort: 2
---

# 曲线坐标系下的NS方程

## Introduction
The incompressible Navier-Stokes equations for a Newtonian fluid read as follows:

$$
\begin{equation}
\begin{aligned}
    &\nabla \cdot \vec{v} = 0, \\
    &\frac{\partial\vec{v}}{\partial{t}} + \vec{v}\cdot\nabla\vec{v} = -\nabla{p} + \frac{1}{Re}\nabla\cdot\tau,
\end{aligned}
\end{equation}
$$

where $$\vec{v} = {u_i} \vec{e}_i = {U^i} \vec{g}_i$$ is the velocity vector, $$p$$ is the static pressure divided by density $$\rho$$, $$Re$$ is the Reynolds number of the flow based on a characteristic length and velocity scales, $$\tau = 2 \mu S$$ is the shear stress tensor, and $$S = \frac{1}{2}(\nabla\vec{v}+\vec{v}\nabla)$$ is the strain rate tensor. Some of notation we adopt in this work is introduced as follows:

|       |                       |          |                        |
|-------|-----------------------|----------|------------------------|
| $$x_i$$ | Cartesian coordinates |  $$\xi^i$$ | curvilinear coordinates|
|  | | $$\vec{g}_i$$ |  |
|$$u_i$$ | Cartesian velocity components | $$U^i$$ | contravariant velocity components |
|      |                      | $$\vec{g}^i$$ | contravariant base vectors |
|     |                       | $$U_i$$ | covariant velocity components |
<div align="center">
<table>
    <caption>Some of notation we adopt in this work.</caption>
    <tr>
        <td> $$x_i$$ </td>
        <td> Cartesian coordinates </td>
        <td> $$\xi^i$$ </td>
        <td> Curvilinear coordinates </td>
    </tr>
    <tr>
        <td>$$\vec{e}_i$$</td>
        <td>Cartesian base vectors</td>
        <td>$$\vec{g}_i$$ </td>
        <td>Covariant base vectors</td>
    </tr>
</table>
</div>
