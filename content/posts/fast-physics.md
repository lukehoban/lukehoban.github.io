---
title: "A Fast Path to Modern Physics"
date: 2023-08-18T13:44:49-07:00
math: true
markup: "mmark"
---

One of my favorite physics books is [*Einstein Gravity in a Nutshell*](https://press.princeton.edu/books/hardcover/9780691145587/einstein-gravity-in-a-nutshell), by Anthony Zee. A subplot spread across several chapters follows an unusual route through physics. It begins with two questions:

1. Could a familiar theory be the low-velocity approximation to something more general?
2. If the more general theory reveals a new symmetry, what happens if we take that symmetry seriously?

This is not the historical order in which the ideas were discovered, nor is symmetry alone enough to derive every law below. It is, however, a compelling pedagogical path. In this post I reconstruct it, fill in some details, and point out where an additional physical assumption enters.

We will imagine a physicist who knows Newtonian mechanics and the principle of stationary action. From there we will find a route toward:

* an invariant maximum speed;
* Lorentz invariance and special relativity;
* rest energy, $E_0=mc^2$;
* the electromagnetic four-potential and Lorentz force;
* gauge invariance and Maxwell's equations;
* a dynamical spacetime metric;
* geodesic motion and spacetime curvature;
* the Einstein--Hilbert action; and
* Einstein's field equations.

## Part 0: Newtonian mechanics in action form

### Newton's second law

For a particle of constant mass $m$ moving in a conservative, time-independent potential energy $V(\vec x)$, Newton's second law is

$$
m\frac{d^2\vec x}{dt^2}=-\vec\nabla V(\vec x),
$$

or

$$
m\frac{d^2\vec x}{dt^2}+\vec\nabla V(\vec x)=0.
$$

Not every force is conservative, and even electromagnetic forces are not generally described by a position-only scalar potential. For now, this restricted system is enough.

### The principle of stationary action

Define the action of a path $\vec x(t)$ by

$$
S[\vec x]=\int_{t_1}^{t_2}dt\,
\left[\frac{m}{2}\left|\frac{d\vec x}{dt}\right|^2-V(\vec x)\right].
$$

The physical path makes the action **stationary** under small variations that vanish at the endpoints:

$$
\delta S=0,\qquad \delta\vec x(t_1)=\delta\vec x(t_2)=0.
$$

"Stationary" is more accurate than "least": the physical path need not be a minimum of the action.

Varying the action gives

$$
\begin{aligned}
\delta S
&=\int dt\left[
m\frac{d\vec x}{dt}\cdot\frac{d(\delta\vec x)}{dt}
-\vec\nabla V\cdot\delta\vec x
\right] \\
&=\left[m\frac{d\vec x}{dt}\cdot\delta\vec x\right]_{t_1}^{t_2}
-\int dt\left[
m\frac{d^2\vec x}{dt^2}+\vec\nabla V
\right]\cdot\delta\vec x.
\end{aligned}
$$

The boundary term vanishes. Because the remaining expression must vanish for every allowed $\delta\vec x(t)$,

$$
m\frac{d^2\vec x}{dt^2}+\vec\nabla V=0.
$$

So far we have added no new physics; we have only rewritten Newton's law in a form that generalizes particularly well.

## Part 1: From Newtonian mechanics to special relativity

The free-particle part of the Newtonian action is

$$
S_{\mathrm N}=\int dt\,\frac{m}{2}v^2,
\qquad
v=\left|\frac{d\vec x}{dt}\right|.
$$

The expansion

$$
\sqrt{1-z}=1-\frac{z}{2}-\frac{z^2}{8}-\cdots
$$

suggests

$$
-mc^2\sqrt{1-\frac{v^2}{c^2}}
=-mc^2+\frac{m}{2}v^2+O\left(\frac{v^4}{c^2}\right),
$$

where $c$ is, for the moment, an undetermined constant with units of velocity. The constant term $-mc^2$ does not affect the path of a particle of fixed mass, so the relativistic-looking action

$$
S_{\mathrm{free}}
=-mc^2\int dt\,\sqrt{1-\frac{v^2}{c^2}}
$$

has the Newtonian free-particle action as its low-velocity limit.

This is an educated guess, not an algebraic derivation: many theories share the same low-velocity approximation. We now ask what follows if this particular completion is fundamental.

### An invariant maximum speed

For the action to remain real along a massive particle's path,

$$
c^2dt^2-d\vec x^{\,2}>0,
$$

and hence $v<c$. The limiting case $v=c$ describes a null path and requires a separate, massless-particle treatment.

At this point we have discovered an invariant candidate for a maximum speed, not yet the speed of light. Maxwell's equations will later show that electromagnetic waves propagate at this same invariant speed. Experiment identifies it with the measured speed of light.

### Spacetime and Lorentz invariance

Introduce spacetime coordinates

$$
x^\mu=(ct,x^1,x^2,x^3)
$$

and the Minkowski metric, using the signature $(+,-,-,-)$,

$$
\eta_{\mu\nu}
=\operatorname{diag}(1,-1,-1,-1).
$$

The invariant interval is

$$
ds^2=\eta_{\mu\nu}dx^\mu dx^\nu
=c^2dt^2-d\vec x^{\,2},
$$

so the free action becomes

$$
S_{\mathrm{free}}=-mc\int ds.
$$

It is the invariant spacetime length of the worldline multiplied by $mc$, which gives the action the correct units.

A linear transformation $x'^\mu=\Lambda^\mu{}_\nu x^\nu$ preserves this interval when

$$
\Lambda^T\eta\Lambda=\eta.
$$

These are Lorentz transformations. They include ordinary spatial rotations and boosts. A boost of speed $u$ in the $x^1$ direction is

$$
\Lambda^\mu{}_\nu=
\begin{pmatrix}
\gamma & -\gamma\beta & 0 & 0 \cr
-\gamma\beta & \gamma & 0 & 0 \cr
0 & 0 & 1 & 0 \cr
0 & 0 & 0 & 1
\end{pmatrix},
\qquad
\beta=\frac{u}{c},
\qquad
\gamma=\frac{1}{\sqrt{1-\beta^2}}.
$$

Unlike a Galilean boost, a Lorentz boost mixes space and time while preserving $ds^2$. Galilean transformations reappear as the approximation for $u\ll c$.

### Rest energy

The relativistic Lagrangian is

$$
L=-mc^2\sqrt{1-\frac{v^2}{c^2}}.
$$

Its conserved energy is

$$
E=\vec p\cdot\vec v-L=\gamma mc^2.
$$

At rest, $\gamma=1$, so

$$
E_0=mc^2.
$$

The constant discarded in the Newtonian equations was therefore the particle's rest energy, not potential energy. It is dynamically irrelevant only when the particle's mass is fixed and no process converts rest mass into other forms of energy.

## Part 2: From Lorentz invariance to electromagnetism

A position-only interaction,

$$
-\int V(\vec x)\,dt,
$$

is not Lorentz invariant by itself. A natural Lorentz-invariant generalization couples the particle's worldline to a four-vector field $A_\mu(x)$:

$$
S_{\mathrm{particle}}
=-mc\int ds-q\int A_\mu(x)\,dx^\mu.
$$

Here $q$ is a property of the particle that we call electric charge. The time component of $A_\mu$ reproduces a scalar-potential interaction at low velocity, while its spatial components produce an interaction that depends on velocity.

For readability, this part uses units in which $c=1$ and absorbs the conventional vacuum constants into the definitions of the fields and sources. They can be restored by dimensional analysis.

### The field strength and Lorentz force

Parameterize a massive worldline by proper time $\tau$, for which $ds=d\tau$ in these units, and define the four-velocity

$$
u^\mu=\frac{dx^\mu}{d\tau}.
$$

Varying the worldline while holding its endpoints fixed gives

$$
m\frac{du^\mu}{d\tau}
=qF^\mu{}_\nu u^\nu,
$$

where

$$
F_{\mu\nu}
=\partial_\mu A_\nu-\partial_\nu A_\mu.
$$

To see where this comes from, the variation of the interaction term is

$$
\begin{aligned}
\delta\int A_\mu dx^\mu
&=\int d\tau\left(
\partial_\nu A_\mu\,u^\mu\delta x^\nu
+A_\mu\frac{d(\delta x^\mu)}{d\tau}
\right)\\
&=\int d\tau\,
(\partial_\nu A_\mu-\partial_\mu A_\nu)
u^\mu\delta x^\nu,
\end{aligned}
$$

after integrating by parts. Combining this with the variation of the free action yields the equation above.

Because $F_{\mu\nu}$ is antisymmetric, it has six independent components. We identify three with the electric field $\vec E$ and three with the magnetic field $\vec B$. The spatial part of the covariant equation is

$$
\frac{d\vec p}{dt}
=q\left(\vec E+\vec v\times\vec B\right),
$$

where $\vec p=\gamma m\vec v$. Its low-velocity limit is the familiar Lorentz force law,

$$
m\frac{d^2\vec x}{dt^2}
=q\left(\vec E+\vec v\times\vec B\right).
$$

Lorentz invariance has not uniquely proved that nature must contain this field. It has shown that, if a particle couples locally and linearly to a four-vector potential, the interaction has the form of electromagnetism.

### Gauge invariance

The potential is not unique. Under

$$
A_\mu\longrightarrow A_\mu+\partial_\mu\Lambda,
$$

the interaction changes by an endpoint term:

$$
q\int\partial_\mu\Lambda\,dx^\mu
=q\left[\Lambda(x_{\mathrm f})-\Lambda(x_{\mathrm i})\right].
$$

With fixed endpoints, this does not change the equations of motion. Equivalently,

$$
F_{\mu\nu}\longrightarrow F_{\mu\nu}.
$$

This is gauge invariance. A constant shift of a Newtonian potential is a special, much smaller redundancy; here $\Lambda$ may vary across spacetime.

### The Maxwell action

We now need dynamics for $A_\mu$ itself. If we require a local, Lorentz-invariant, gauge-invariant action whose equations contain no more than two derivatives, the simplest field term is

$$
S_{\mathrm{field}}
=-\frac14\int d^4x\,F_{\mu\nu}F^{\mu\nu}.
$$

"Simplest" matters: symmetry alone does not forbid higher-order terms such as $(F_{\mu\nu}F^{\mu\nu})^2$, but they are suppressed in the low-energy theory.

For charged matter with four-current $J^\mu$, the complete electromagnetic action can be written

$$
S=S_{\mathrm{matter}}
-\int d^4x\,J^\mu A_\mu
-\frac14\int d^4x\,F_{\mu\nu}F^{\mu\nu}.
$$

For a point charge following $X^\mu(\tau)$,

$$
J^\mu(x)
=q\int d\tau\,
\frac{dX^\mu}{d\tau}
\delta^{(4)}\!\left(x-X(\tau)\right).
$$

This form makes $-\int J^\mu A_\mu\,d^4x$ equal to the worldline coupling $-q\int A_\mu dX^\mu$.

Varying the action with respect to $A_\nu$ gives

$$
\begin{aligned}
\delta S
&=\int d^4x\,
\left(\partial_\mu F^{\mu\nu}-J^\nu\right)\delta A_\nu,
\end{aligned}
$$

after an integration by parts. Therefore,

$$
\partial_\mu F^{\mu\nu}=J^\nu.
$$

These four equations contain Gauss's law and the Ampère--Maxwell law:

$$
\vec\nabla\cdot\vec E=\rho,
$$

$$
\vec\nabla\times\vec B
=\frac{\partial\vec E}{\partial t}+\vec J.
$$

The definition $F=dA$ supplies the other two equations through the identity

$$
\partial_{[\lambda}F_{\mu\nu]}=0:
$$

$$
\vec\nabla\cdot\vec B=0,
$$

$$
\vec\nabla\times\vec E
=-\frac{\partial\vec B}{\partial t}.
$$

Together these are Maxwell's equations in our normalized units.

Taking a divergence of the sourced equation gives

$$
\partial_\nu J^\nu
=\partial_\nu\partial_\mu F^{\mu\nu}=0,
$$

because partial derivatives commute while $F^{\mu\nu}$ is antisymmetric. Gauge-invariant electrodynamics therefore requires conservation of charge.

In vacuum, Maxwell's equations imply wave equations for both fields:

$$
\left(\frac{\partial^2}{\partial t^2}-\nabla^2\right)\vec E=0,
\qquad
\left(\frac{\partial^2}{\partial t^2}-\nabla^2\right)\vec B=0.
$$

Restoring units, the propagation speed is $c$. We can now identify the invariant speed introduced in Part 1 with the speed of electromagnetic waves---and, experimentally, with the speed of light.

## Part 3: From a universal potential to gravity

There is another way a Newtonian potential can enter the relativistic particle action. Write the Newtonian gravitational potential energy as

$$
V=m\Phi,
$$

where $\Phi$ is the gravitational potential per unit mass. The fact that $m$ factors out is essential: gravitational free fall is universal. A generic potential does not have this property and cannot be absorbed into one spacetime metric shared by every particle.

Consider a weak, static metric

$$
g_{\mu\nu}\approx
\begin{pmatrix}
1+\dfrac{2\Phi}{c^2} & 0 & 0 & 0 \cr
0 & -1 & 0 & 0 \cr
0 & 0 & -1 & 0 \cr
0 & 0 & 0 & -1
\end{pmatrix}.
$$

Then

$$
\begin{aligned}
-mc\int ds
&=-mc^2\int dt\,
\sqrt{
\left(1+\frac{2\Phi}{c^2}\right)-\frac{v^2}{c^2}
}\\
&\approx\int dt\left(
-mc^2+\frac12mv^2-m\Phi
\right).
\end{aligned}
$$

Apart from the constant rest-energy term, this is exactly the Newtonian action for gravity.

Once again we invert the logic. Suppose the position-dependent $g_{\mu\nu}(x)$ is fundamental and the Minkowski metric is only its local, weak-field limit:

$$
S_{\mathrm{particle}}
=-mc\int
\sqrt{g_{\mu\nu}(x)\,dx^\mu dx^\nu}.
$$

The gravitational potential has become part of spacetime geometry. A general symmetric metric in four dimensions has ten independent components, and the same metric governs every freely falling test body.

### Geodesic motion

For an affinely parameterized path, the square-root action has the same trajectories as the simpler Lagrangian

$$
L_{\mathrm g}
=\frac12g_{\mu\nu}(x)
\frac{dx^\mu}{d\lambda}
\frac{dx^\nu}{d\lambda}.
$$

Applying the Euler--Lagrange equations gives

$$
\frac{d}{d\lambda}
\left(g_{\rho\nu}\frac{dx^\nu}{d\lambda}\right)
-\frac12\partial_\rho g_{\mu\nu}
\frac{dx^\mu}{d\lambda}
\frac{dx^\nu}{d\lambda}=0.
$$

Expanding the total derivative, multiplying by the inverse metric, and symmetrizing the two velocity factors yields

$$
\frac{d^2x^\rho}{d\lambda^2}
+\Gamma^\rho{}_{\mu\nu}
\frac{dx^\mu}{d\lambda}
\frac{dx^\nu}{d\lambda}=0,
$$

with

$$
\Gamma^\rho{}_{\mu\nu}
=\frac12g^{\rho\sigma}
\left(
\partial_\mu g_{\sigma\nu}
+\partial_\nu g_{\sigma\mu}
-\partial_\sigma g_{\mu\nu}
\right).
$$

This is the geodesic equation. For a massive particle, proper time $\tau$ is an affine parameter.

The Christoffel symbols can be nonzero even in flat spacetime when curvilinear coordinates are used, so they are not themselves a measure of curvature. At any one point they can be made to vanish by a suitable choice of coordinates. Tidal effects, which cannot be transformed away over a finite region, require the curvature tensor.

### Curvature

The Riemann curvature tensor is

$$
R^\rho{}_{\sigma\mu\nu}
=\partial_\mu\Gamma^\rho{}_{\nu\sigma}
-\partial_\nu\Gamma^\rho{}_{\mu\sigma}
+\Gamma^\rho{}_{\mu\lambda}\Gamma^\lambda{}_{\nu\sigma}
-\Gamma^\rho{}_{\nu\lambda}\Gamma^\lambda{}_{\mu\sigma}.
$$

It describes, among other things, geodesic deviation and the change in a vector after parallel transport around an infinitesimal loop. Spacetime is locally flat throughout a region exactly when the Riemann tensor vanishes there.

Contracting the first and third indices gives the Ricci tensor,

$$
R_{\sigma\nu}=R^\rho{}_{\sigma\rho\nu},
$$

and contracting once more gives the Ricci scalar,

$$
R=g^{\sigma\nu}R_{\sigma\nu}.
$$

Unlike the full Riemann tensor, the Ricci tensor can vanish in a curved spacetime; gravitational waves and the exterior of a gravitating body are important examples. Thus $R_{\mu\nu}=0$ does not imply flatness.

### The Einstein--Hilbert action

We now seek dynamics for the metric itself. Requiring a local, generally covariant action built from the metric and containing no more than second-order field equations leaves, in four dimensions, the Ricci scalar and a cosmological constant as the relevant lowest-order terms. This is the content of Lovelock's theorem under its stated assumptions; symmetry by itself does not exclude higher-curvature corrections.

The coordinate volume $d^4x$ is not invariant on its own. The invariant volume element is

$$
\sqrt{-g}\,d^4x,
\qquad
g=\det(g_{\mu\nu}),
$$

for our $(+,-,-,-)$ signature. The gravitational action is therefore

$$
S_{\mathrm{gravity}}
=\frac{c^3}{16\pi G}
\int d^4x\,\sqrt{-g}\,(R-2\Lambda),
$$

where $G$ is Newton's constant and $\Lambda$ is the cosmological constant. Matter contributes a separate action $S_{\mathrm{matter}}[g,\text{matter}]$.

Strictly, a spacetime with a boundary also requires an appropriate boundary term for a well-posed metric variation. That detail does not alter the bulk field equations below.

### Einstein's field equations

Define the stress--energy tensor by

$$
T_{\mu\nu}
=-\frac{2c}{\sqrt{-g}}
\frac{\delta S_{\mathrm{matter}}}{\delta g^{\mu\nu}}.
$$

The metric variations needed for the gravitational action are

$$
\delta\sqrt{-g}
=-\frac12\sqrt{-g}\,g_{\mu\nu}\delta g^{\mu\nu}
$$

and, after discarding the boundary contribution,

$$
\delta\left(\sqrt{-g}\,R\right)
=\sqrt{-g}
\left(R_{\mu\nu}-\frac12Rg_{\mu\nu}\right)
\delta g^{\mu\nu}.
$$

Varying the total action with respect to $g^{\mu\nu}$ and requiring $\delta S=0$ gives

$$
R_{\mu\nu}
-\frac12Rg_{\mu\nu}
+\Lambda g_{\mu\nu}
=\frac{8\pi G}{c^4}T_{\mu\nu}.
$$

These are Einstein's field equations. Their left-hand side describes spacetime geometry; their right-hand side describes matter and energy. The coefficient is fixed by demanding that the weak-field, slow-motion limit reproduce Newtonian gravity,

$$
\nabla^2\Phi=4\pi G\rho.
$$

The contracted Bianchi identity,

$$
\nabla^\mu
\left(R_{\mu\nu}-\frac12Rg_{\mu\nu}\right)=0,
$$

then implies

$$
\nabla^\mu T_{\mu\nu}=0.
$$

As in electromagnetism, a symmetry of the action is tied to a conservation law: gauge invariance accompanies charge conservation, while diffeomorphism invariance accompanies covariant stress--energy conservation.

## What this path did---and did not---show

Starting with Newtonian mechanics, we guessed a Lorentz-invariant completion of its free-particle action. Taking the resulting symmetry seriously led naturally to relativistic kinematics. A local coupling to a four-vector field produced the Lorentz force, and gauge invariance plus a lowest-derivative assumption produced Maxwell's theory. The universality of gravity then allowed its potential to be reinterpreted as spacetime geometry, and general covariance plus another lowest-derivative assumption led to the Einstein--Hilbert action and Einstein's equations.

This is not a proof that these are the only conceivable laws of nature. At each stage we chose the simplest local action compatible with the new symmetry and retained only the leading terms in a derivative or low-energy expansion. Nature could, and in effective field theory does, include higher-order corrections. The striking fact is that a small set of experimental clues and symmetry principles constrains the leading theories so tightly.
