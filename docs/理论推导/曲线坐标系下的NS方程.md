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
\end{equation}\tag {1}
$$

where $$\vec{v} = {u_i} \vec{e}_i = {U^i} \vec{g}_i$$ is the velocity vector, $$p$$ is the static pressure divided by density $$\rho$$, $$Re$$ is the Reynolds number of the flow based on a characteristic length and velocity scales, $$\tau = 2 \mu S$$ is the shear stress tensor, and $$S = \frac{1}{2}(\nabla\vec{v}+\vec{v}\nabla)$$ is the strain rate tensor. Some of notation we adopt in this work is introduced as follows:

<div align="center">
    <table>
    <caption>Some of notation we adopt in this work.</caption>
    <tr>
        <td> $$x_i$$ </td> <td> Cartesian coordinates </td> <td> $$\xi^i$$ </td> <td> Curvilinear coordinates </td>
    </tr>
    <tr>
        <td>$$\vec{e}_i$$</td> <td>Cartesian base vectors</td> <td>$$\vec{g}_i$$ </td> <td>Covariant base vectors</td>
    </tr>
    <tr>
        <td> $$u_i$$ </td> <td> Cartesian velocity components </td> <td> $$U^i$$ </td> <td> Contravariant velocity components </td>
    </tr>
    <tr>
        <td>   </td> <td>   </td> <td> $$\vec{g}^i$$ </td> <td> Contravariant base vectors </td>
    </tr>
    <tr>
        <td>   </td> <td>   </td> <td> $$U_i$$ </td> <td> Covariant velocity components </td>
    </tr>
    </table>
</div>

There are two approaches one can adopt to implement such a coordinate transformation, i.e. the partial transformation and the full transformation[1]. We will derive them in the next two sections. We review something about transformation of coordinates here.

$$
\begin{equation}
\begin{aligned}
    \vec{g}_i &= \frac{\partial{\vec{r}}}{\partial{\xi^i}} = \frac{\partial{\vec{r}}}{\partial{x^j}} \frac{\partial{x^j}}{\partial\xi^i} = \frac{\partial{x^j}}{\partial\xi^i} \vec{e}_j,\\
    \vec{e}_i &= \frac{\partial{\vec{r}}}{\partial{x^i}} = \frac{\partial{\vec{r}}}{\partial{\xi^j}} \frac{\partial{\xi^j}}{\partial{x}^i} = \xi^j_i \vec{g}_j,
\end{aligned}
\end{equation}\tag {2}
$$

where $$\xi^j_i = \frac{\partial{\xi^j}}{\partial{x}^i}$$ is the element of Jacobian matrix. In this way, we obtain the relationship between the contravariant velocity components and Cartesian velocity components as follows:

$$
\begin{equation}
\begin{aligned}
    U^j &= \xi^j_i u_i,\\
    u_j &= \frac{\partial{x_j}}{\partial\xi^i} U^i,
\end{aligned}
\end{equation}\tag{3}
$$

## The partial transformation

In the partial transformation approach only the independent $${x_i}$$ are transformed to curvilinear coordinates while the dependent variables, the components of the velocity field, are retained in terms of their Cartesian components $${u_i}$$. The partially transformed equations can be derived as follows:

$$
\begin{equation}
\begin{aligned}
    &J \frac{\partial}{\partial\xi^i}\left( \frac{\xi^i_j}{J} \cdot u_j \right) = 0,\\
    &\frac{\partial{u_j}}{\partial{t}} + C(u_j) + G_j(p) - \frac{1}{Re} D(u_j) = 0,
\end{aligned}
\end{equation}\tag{4}
$$

where $$C$$, $$G$$, and $$D$$ are the convective, gradient, and viscous operators defined in curvilinear coordinates as follows:

$$
\begin{equation}
\begin{aligned}
    C(u_j) &= (\vec{v}\cdot\nabla{\vec{v}})\cdot{\vec{e}_j} = U^i\vec{g}_i\cdot\vec{g^k}\frac{\partial}{\partial{\xi}^k}(u_l\vec{e}_l)\cdot{\vec{e}_j} = U^i\frac{\partial{u_j}}{\partial\xi^i} = J \frac{\partial}{\partial\xi^i}\left(\frac{U^i}{J}\cdot{u_j}\right),\\
    G_j(p) &= (\nabla{p})\cdot\vec{e}_j = \vec{g^i}\frac{\partial{p}}{\partial{\xi^i}}\cdot \vec{e}_j = \xi^i_k\vec{e}_k\frac{\partial{p}}{\partial{\xi^i}}\cdot \vec{e}_j = \xi^i_j \frac{\partial{p}}{\partial\xi^i} = J \frac{\partial}{\partial{\xi^i}}\left(\frac{\xi^i_j}{J}\cdot p\right),\\
    D(u_j) &= (\nabla\cdot\nabla\vec{v})\cdot\vec{e}_j = \nabla\cdot{G(u_j)} = J \frac{\partial}{\partial\xi^i}\left( \frac{\xi^i_l}{J} \cdot \xi^k_l\frac{\partial{u_j}}{\partial\xi^k} \right) = J \frac{\partial}{\partial\xi^i}\left( \frac{\xi^i_l\xi^k_l}{J}\frac{\partial}{\partial\xi^k}  \cdot{u_j}\right).
\end{aligned}
\end{equation}\tag{5}
$$

Substituting operators above into equation (4), we have:

$$
\begin{equation}
\begin{aligned}
    &J \frac{\partial}{\partial\xi^i}\left( \frac{\xi^i_j}{J} \cdot u_j \right) = 0,\\
    &\frac{\partial{u_j}}{\partial{t}} = J\left(-\frac{\partial}{\partial\xi^i}\left(\frac{U^i}{J}\cdot{u_j}\right) -  \frac{\partial}{\partial{\xi^i}}\left(\frac{\xi^i_j}{J}\cdot p\right) + \frac{1}{Re}\frac{\partial}{\partial\xi^i}\left( \frac{\xi^i_l\xi^k_l}{J}\frac{\partial}{\partial\xi^k}  \cdot{u_j}\right)\right).
\end{aligned}
\end{equation}\tag{6}
$$

Selecting the surface volume fluxes $V^i = U^i/J$ as the dependent variables in left hand side of equation (6), the transport equation for the volume fluxes read as follows:

$$
\begin{equation}
\begin{aligned}
    &J \frac{\partial{V^i}}{\partial\xi^i} = 0,\\
    &\frac{1}{J}\frac{\partial{V^l}}{\partial{t}} = \frac{\xi^l_j}{J}\left(-\frac{\partial}{\partial\xi^i}\left(V^i{u_j}\right) -  \frac{\partial}{\partial{\xi^i}}\left(\frac{\xi^i_j p}{J}\right) + \frac{1}{Re}\frac{\partial}{\partial\xi^i}\left( \frac{\xi^i_l\xi^k_l}{J}\frac{\partial{u_j}}{\partial\xi^k}  \right)\right).
\end{aligned}
\end{equation}\tag{7}
$$

## The full transformation

In the full transformation approach both the independent variables are transformed in generalized curvilinear coordinates. The fully transformed governing equations read as follows[1]:

$$
\begin{equation}
\begin{aligned}
    &J\frac{\partial{V^j}}{\partial\xi^j}=0,\\
    &\frac{1}{J}\frac{\partial{V^j}}{\partial{t}}+\textbf{C}(V^j) + \textbf{G}_j (p) - \frac{1}{Re}\textbf{D}(V^j)=0.
\end{aligned}
\end{equation}\tag{8}
$$

The fully transformed convective $$ \textbf{C} $$ read as follow:

$$
\begin{equation}
\begin{aligned}
    \textbf{C}(V^j) &= \frac{1}{J^2}(\vec{v}\cdot\nabla{\vec{v}}) \cdot\vec{g^j}= V^i\vec{g}_i\cdot\vec{g^k}\frac{\partial}{\partial{\xi}^k}(V^q\vec{g}_q)\cdot{\vec{g^j}}\\
    &= V^i\frac{\partial}{\partial{\xi^i}}(V^q\vec{g}_q) \cdot\vec{g^j}\\
    &= \frac{\partial}{\partial\xi^i}\left(V^iV^q\vec{g}_q\right) \cdot \vec{g^j}\\
    &= (V^i V^q)_{,i} \vec{g}_q\cdot\vec{g^j}\\
    &= (V^i V^j)_{,i}.
\end{aligned}
\end{equation}\tag{9}
$$

The covariant derivative operator that appears in the above equations is defined as [2]:

$$
\begin{equation}
    (f^i)_{,j} = \frac{\partial{f^i}}{\partial{\xi^j}} + f^k\Gamma_{kj}^i,
\end{equation}\tag{10}
$$

where $$\Gamma_{ij}^k$$ is the Christoffel symbols of the second kind defined as equation (20) in appendix A. The fully transformed gradient $$\textbf{G}_j$$ operator read as follows:

$$
\begin{equation}
\begin{aligned}
    \textbf{G}_j(p) = \frac{1}{J^2}\nabla{p}\cdot\vec{g^j} = \frac{1}{J^2}\vec{g^i}\frac{\partial{p}}{\partial{\xi^i}}\cdot \vec{g^j} = \frac{g^{ij}}{J^2}\frac{\partial{p}}{\partial{\xi^i}}=\frac{\xi^j_k}{J}\frac{\partial}{\partial{\xi^i}}\left(\frac{\xi^i_k}{J}\cdot{p}\right),
\end{aligned}
\end{equation}\tag{11}
$$

where $$g^{ij}=\vec{g^i}\cdot\vec{g^j}=\xi^i_k\xi^j_k$$ is contravariant component of the metric tensor. The fully transformed viscous $$ \textbf{D} $$ operator read as follows:

$$
\begin{equation}
\begin{aligned}
    \textbf{D}(V^j) & = \frac{1}{J^2}[ \nabla \cdot (\nabla\vec{v}+\vec{v}\nabla) ] \cdot \vec{g^j}\\
    &=\frac{1}{J}\left[\vec{g^i}\frac{\partial}{\partial\xi^i} \cdot \left( \vec{g^k}\frac{\partial}{\partial\xi^k}(V^l\vec{g}_l) \right) \right] \cdot \vec{g^j} + \frac{1}{J}\left[\vec{g^i}\frac{\partial}{\partial\xi^i} \cdot \left( \frac{\partial(V^l\vec{g}_l)}{\partial\xi^k} \vec{g^k}\right) \right] \cdot \vec{g^j}\\
    &=\left[\frac{\partial}{\partial\xi^i}\left( \frac{g^{ik}}{J}\frac{\partial}{\partial\xi^k}(V^l\vec{g}_l) \right) \right] \cdot \vec{g^j} + \frac{1}{J}\left[\vec{g^i}\frac{\partial}{\partial\xi^i} \cdot \left( (V^l)_{,k}\vec{g}_l \vec{g^k}\right) \right] \cdot \vec{g^j}\\
    &=\frac{1}{J}\left[\frac{\partial}{\partial\xi^i}\left(g^{ik} (V^l)_{,k}\vec{g}_l \right) \right] \cdot \vec{g^j} + \frac{1}{J}\left[\frac{\partial}{\partial\xi^l}\left( g^{km}(V^l)_{,k} \vec{g}_m\right) \right] \cdot \vec{g^j}\\
    &=\frac{1}{J}\left[\frac{\partial}{\partial\xi^i}\left(g^{ik} (V^l)_{,k}\vec{g}_l \right) + \frac{\partial}{\partial\xi^i}\left( g^{kl}(V^i)_{,k} \vec{g}_l\right) \right] \cdot \vec{g^j}\\
    &=\frac{1}{J}\left[ g^{ik} (V^l)_{,k} +  g^{kl}(V^i)_{,k}  \right]_{,i} \vec{g}_l\cdot \vec{g^j}\\
    &=\frac{1}{J}\left( g^{ik} (V^j)_{,k} +  g^{kj}(V^i)_{,k}  \right)_{,i}
\end{aligned}
\end{equation}\tag{12}
$$

Substituting equation (9), (11) and (12) into equation (8), we obtain:

$$
\begin{equation}
\begin{aligned}
    &J\frac{\partial{V^j}}{\partial\xi^j}=0,\\
    &\frac{\partial{V^j}}{\partial{t}} = - J(V^i V^j)_{,i} - \frac{g^{ij}}{J}\frac{\partial{p}}{\partial{\xi^i}} + \frac{1}{Re}\left( g^{ik} (V^j)_{,k} +  g^{kj}(V^i)_{,k}  \right)_{,i}.
\end{aligned}
\end{equation}\tag{13}
$$

## Two-phase incompressible flow

The VFS-Wind code solves the spatially-filtered Navier-Stokes equations governing incompressible flows of two immiscible fluids. The equations adopt a two-fluid formulation based on the level set method[3] and are expressed in generalized curvilinear coordinates as follows( $$i,j,k,l=1,2,3$$ ):

$$
\begin{equation}
\begin{aligned}
    &J \frac{\partial{V^i}}{\partial\xi^i} = 0,\\
    &\frac{1}{J}\frac{\partial{V^l}}{\partial{t}} = \frac{\xi^l_j}{J}\bigg[ -\frac{\partial}{\partial\xi^i}\left(V^i{u_j}\right) + \frac{1}{\rho(\phi)Re}\frac{\partial}{\partial\xi^i}\left( \mu(\phi)\frac{\xi^i_l\xi^k_l}{J}\frac{\partial{u_j}}{\partial\xi^k}  \right) -  \frac{1}{\rho(\phi)}\frac{\xi^i_j}{J}\frac{\partial{p}}{\partial{\xi^i}}\\
    &\qquad\qquad\qquad -\frac{\xi^i_k}{\rho(\phi)}\frac{\partial\tau_{kj}}{\partial\xi^i}- \frac{\kappa}{\rho(\phi)}\frac{\xi^i_j}{JWe^2}\frac{\partial{h}(\phi)}{\partial{\xi^i}}+\frac{\delta_{j2}}{Fr^2}\bigg].
\end{aligned}
\end{equation}\tag{14}
$$

where $$\phi$$ is the level set function, $$\tau_{ij}$$ is the subgrid scale tensor, $$\kappa$$ is the curvature of the interface, $$\delta_{ij}$$ is the Kronecker delta, $$h$$ is the smoothed Heaviside function, and $$Re$$, $$Fr$$ and $$We$$ are the dimensionless Reynolds, Froude and Weber numbers, respectively, which can be defined as:

$$
\begin{equation}
    Re = \frac{UL\rho_{water}}{\mu_{water}}, Fr = \frac{U}{\sqrt{gL}}, We = U\sqrt{\frac{\rho_{water}L}{\sigma}},
\end{equation}\tag{15}
$$

where $$U$$ and $$L$$ are the characteristic velocity and linear dimension, $$\rho_{water}$$ and $$\mu_{water}$$, the density and dynamic viscosity of the water phase, $$g$$ the gravitational acceleration,
and $$\sigma$$ the surface tension.

The level set function $$\phi$$ is a signed distance function, adopting positive values on the water phase and negative values on the air phase. The density and viscosity are taken to be constant within each phase, and transition smoothly across the interface,
which is smeared over a distance $$2\epsilon$$, as follows:

$$
\begin{equation}
\begin{aligned}
    &\rho(\phi) = \rho_{air} + (\rho_{water}-\rho_{air})h(\phi),\\
    &\mu(\phi) = \mu_{air} + (\mu_{water}-\mu_{air})h(\phi),
\end{aligned}
\end{equation}\tag{16}
$$

where $$h(\phi)$$ is the numerically smeared-out Heaviside function defined as:

$$
\begin{equation}
h(\phi) = 
\begin{cases}
    0, \qquad\qquad\qquad\qquad\qquad\quad \phi<-\epsilon,\\
    \frac{1}{2}+\frac{\phi}{2\epsilon}+\frac{1}{2\pi}sin\left(\frac{\pi\phi}{\epsilon}\right),\quad -\epsilon\leq\phi\leq\epsilon,\\
    1,\qquad\qquad\qquad\qquad\qquad\quad  \epsilon<\phi.
\end{cases}
\end{equation}\tag{17}
$$

This removes all discontinuities across the interface, except the jump in pressure due to surface tension. Using the immersed
boundary method to smear out the pressure across the interface leads to continuity of the pressure, and loss of all surface-tension effects. This was remedied by adding a new forcing term to the right-hand side of the momentum equations. In the context of level set methods this new forcing term takes the form [3]:

$$
\begin{equation}
    \vec{f}_{\sigma} = - \frac{\sigma \kappa}{\rho(\phi)} \delta(\phi)  \vec{N} = - \frac{\sigma \kappa}{\rho(\phi)} \delta(\phi) \nabla \phi = - \frac{\sigma \kappa}{\rho(\phi)} \nabla{h(\phi)},
\end{equation}\tag{18}
$$

which leads to the last but one term in the second equation of (14).

## Appendix A: Divergence in curvilinear coordinates

Divergence in curvilinear coordinates read as follows [2]:

$$
\begin{equation}
\begin{aligned}
    \vec{g^i} \frac{\partial}{\partial{\xi^i}} \cdot \left(U^j \vec{g}_j\right) = \vec{g^i} \cdot \left(\frac{\partial{U^j}}{\partial{\xi^i}} \vec{g_j} + U^k \frac{\partial{\vec{g}_k}}{\partial{\xi^i}} \right) = \frac{\partial{U^j}}{\partial{\xi^i}}\delta_{ij} + U^k \Gamma_{ik}^j \delta_{ij} = \frac{\partial{U^i}}{\partial{\xi^i}} + U^k\Gamma_{ik}^i,
\end{aligned}
\end{equation}\tag{19}
$$

where $$\Gamma_{ij}^k$$ is the Christoffel symbols of the second kind defined as:

$$
\begin{equation}
    \frac{\partial{\vec{g}_i}}{\partial{\xi^j}} = \Gamma_{ij}^{k}\vec{g}_k \rightarrow \Gamma_{ij}^{k} = \frac{\partial{\vec{g}_i}}{\partial{\xi^j}} \cdot \vec{g}_k.
\end{equation}\tag{20}
$$

According to the definition of covariant base vector (2), we can easily get the property of this Christoffel, i.e. $$\Gamma_{ij}^k = \Gamma_{ji}^k$$. And we define $$g = |[\vec{g}_m][\vec{g}_n]^T|=|\left(\vec{g}_1 \times \vec{g}_2\right) \cdot \vec{g}_3 |^2$$, then we have: 

$$
\begin{equation}
\begin{aligned}
    \frac{\partial{\sqrt{g}}}{\partial\xi^1} & = \frac{\partial}{\partial{\xi^1}} \left| \left(\vec{g}_1 \times \vec{g}_2\right) \cdot \vec{g}_3 \right| \\
    & = \left| \left(\frac{\partial{\vec{g}_1}}{\partial{\xi^1}} \times \vec{g}_2\right) \cdot \vec{g}_3 + \left( \vec{g}_1 \times \frac{\partial{\vec{g}_2}}{\partial{\xi^1}} \right) \cdot \vec{g}_3 + (\vec{g}_1 \times \vec{g}_2) \cdot \frac{\partial{\vec{g}_3}}{\partial{\xi^1}} \right|\\
    & = (\Gamma_{11}^1 +\Gamma_{12}^2 +\Gamma_{13}^3 ) \cdot |(\vec{g}_1 \times \vec{g}_2) \cdot \vec{g}_3 |\\
    & = \Gamma_{1i}^i \sqrt{g}.
\end{aligned}
\end{equation}\tag{21}
$$

A general form of equation (21) can be written as:

$$
\begin{equation}
    \Gamma_{ij}^i = \frac{1}{\sqrt{g}}\frac{\partial{\sqrt{g}}}{\partial\xi^j}
\end{equation}\tag{22}
$$

Equation (2) can be rewritten in vectors as:

$$
\begin{equation}
    [ \vec{e}_i ] = [ \xi^j_i ] \cdot [ \vec{g}_j ],
\end{equation}\tag{23}
$$

where $$[\vec{e}_i]=[\vec{e}_1, \vec{e}_2, \vec{e}_3]^T, [\vec{g}_j]=[\vec{g}_1, \vec{g}_2, \vec{g}_3]^T$$ and $$[\xi^j_i]$$ is the Jacobian matrix. Then we have:

$$
\begin{equation}
    I = [ \vec{e}_i ] [ \vec{e}_j ]^T = \left[ \xi^m_i \right] [ \vec{g}_m ] [ \vec{g}_n ]^T \left[\xi^n_j \right]^T
\end{equation}\tag{24}
$$

The determinant of the matrix above can be written as:

$$
\begin{equation}
    1 = \left| [ \xi^m_i ] [ \vec{g}_m ] [ \vec{g}_n ]^T [ \xi^n_j ]^T \right| = J \cdot |[ \vec{g}_m ] [ \vec{g}_n ]^T|\cdot{J} = J^2\cdot{g},
\end{equation}\tag{25}
$$

so that $$J = \frac{1}{\sqrt{g}}$$. Then equation (19) can be read as follows:

$$
\begin{equation}
\begin{aligned}
    \nabla\cdot\vec{v} = \frac{\partial{U^i}}{\partial{\xi^i}} + U^k \frac{1}{\sqrt{g}}\frac{\partial{\sqrt{g}}}{\partial\xi^k} = J \frac{\partial}{\partial\xi^i}\left( \frac{U^i}{J}\right) = J \frac{\partial}{\partial\xi^i}\left( \frac{\xi^i_j}{J} \cdot u_j \right).
\end{aligned}
\end{equation}\tag{26}
$$

## Reference
[1] [Ge L, Sotiropoulos F. A numerical method for solving the 3D unsteady incompressible Navier–Stokes equations in curvilinear domains with complex immersed boundaries[J]. Journal of computational physics, 2007, 225(2): 1782-1809.](https://www.sciencedirect.com/science/article/pii/S0021999107000873)

[2] [Kezhi H, Mingde X, Mingwan L. Tensor analysis[M]. Tsinghua University Press, 2019.](https://www.amazon.com/Tensor-Analysis-Chinese-MING-HUANG/dp/7302521573)

[3] [Osher S, Fedkiw R P. Level set methods and dynamic implicit surfaces[M]. New York: Springer, 2005.](http://ndl.ethernet.edu.et/bitstream/123456789/33018/1/9.pdf.pdf)
