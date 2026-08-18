---
title: "A Fast Path to Modern Physics"
date: 2023-08-18T13:44:49-07:00
math: true
markup: "mmark"
---

One of my favorite physics books is [Einstein Gravity in a Nutshell](https://press.princeton.edu/books/hardcover/9780691145587/einstein-gravity-in-a-nutshell) by Anthony Zee.  A subplot of the book that is spread over several sections is a line of thinking that discovers a wide range of physics from a simple starting point, guided by a couple of simple intuitions:
1. Could what we know be seen as a low velocity approximation of something more general?
2. If new symmetries show up in the new, more general form, take them seriously and see what happens!

I've never seen this approach used in other physics books or papers, and it doesn't line up with the historical order of discoveries, but it's pedagogically intriguing.  So in this post, I attempt to recreate it, filling in some details and extending it to a few additional "discoveries" motivated by the same line of thinking.

We'll imagine ourselves as physicists from the 1700s who know Newtonian mechanics and look for a path by which we could have plausibly discovered much of 19th- and 20th-century physics, mostly just by recognizing the structure of various equations as possible low-velocity approximations of other more structured forms, and then taking seriously the symmetries we discover in those new forms.  In the prologue, we'll just reformulate $F=ma$ in a way well known in the 1700s. Then we'll make some more educated guesses to discover the rest of this physics.

Along the way, we'll "discover" all of the following:
* The speed of light
* Lorentz covariance
* $E = mc^2$
* Electromagnetic vector potential
* Lorentz force law
* Gauge invariance
* Maxwell's equations
* Dynamic spacetime metric
* Curved spacetime
* Geodesic equation
* Curvature tensor
* Einstein-Hilbert Action
* Einstein Field Equations

Let's dig in!

## Part 0: Prologue

## Start with Newton's 2nd Law

Let's start with the one physics equation that every high school student knows - Newton's 2nd law, known since at least 1687:

$$F = ma$$

We can make this a little more explicit in a few steps. First, this is an equation about the force, mass and acceleration of an object at a point in space and time.

$$F(x(t)) = m a(t)$$

It also applies in three dimensions as a vector equation.

$$\vec{F}(\vec{x}(t)) = m\vec{a}(t)$$

And the acceleration $\vec{a}(t)$ is the second derivative of the path of the body $\vec{x}(t)$.

$$\vec{F}(\vec{x}(t)) = m\frac{d^2 \vec{x}(t)}{dt^2}$$

This equation is true for *any* force $\vec{F}(x)$, but for the purposes of this post, we'll focus on a specific class of forces called [conservative forces](https://en.wikipedia.org/wiki/Conservative_force). These are forces that depend only on the position of the object.  Effectively all the fundamental forces we commonly think about are conservative, like gravity and electromagnetism. But things like friction, when treated as an external force, are not conservative (they transfer energy into a body that is not included in the analysis).  For conservative forces, instead of specifying a vector (three numbers) at every point, we can specify a single number called the potential $V$ at every point, and express the force as the gradient of the potential $\vec{F}(x) = - \vec{\nabla} V(\vec{x}(t))$.  With this, we can give our $F=ma$ equation in terms of the potential $V$ as:

$$ - \vec{\nabla} V(\vec{x}(t)) = m\frac{d^2 \vec{x}(t)}{dt^2}$$

Or, in the final form we'll use:

$$ 0 = m\frac{d^2 \vec{x}(t)}{dt^2} + \vec{\nabla} V(\vec{x}(t))$$

This expresses that the force of a conservative potential is equal to the mass times the acceleration of a particle.

### Least Action Principle

We can express this same statement that $F=ma$ in a quite different form that happens to generalize well.  That form is known as the Principle of Least Action, and was known in the mid-1700s by Euler and Maupertuis.

We can derive this directly from the form of $F = ma$ we ended up with above, but instead we'll state the answer and just show that it does indeed imply that $F = ma$ for a conservative force $F$.

Let $S[x(t)]$ be the *action* associated with a given function $x(t)$.  It is a single number for each function, or a *functional*.

$$ S[x(t)] = \int dt \left[\frac{m}{2} \left(\frac{dx}{dt}\right)^2 - V(x(t)) \right] $$

The principle of least action says that the path $x(t)$ followed by the object will be the one for which $S[x(t)]$ is a minimum.  We know that one way to find the minimum is to take the derivative and set it to zero.  In this case "take the derivative" means "vary the functional with respect to small changes to the path $x(t)$".  We take a path $x(t)$ between a start and end point, and vary it slightly, holding both ends fixed.  This is expressed as:

$$ 0 = \delta S[x(t)] $$

Let's quickly show that this statement is equivalent for the action $S[x(t)]$ we defined above.

$$ 0 = \delta \int dt \left[\frac{m}{2} \left(\frac{dx}{dt}\right)^2 - V(x(t)) \right] $$
$$ 0 = \int dt \left[m \frac{dx}{dt} \frac{\delta dx}{dt} - \frac{dV(x(t))}{d\vec{x}}\delta x \right] $$
$$ 0 = \int dt \left[m \frac{dx}{dt} \frac{d \delta x}{dt} - \vec{\nabla} V(x(t)) \delta x \right] $$

Then partial integration on the first term:

$$ 0 = \int dt \left[\frac{d}{dt}\left[m\frac{dx}{dt}\delta x \right] - m\frac{d^2 \vec{x}(t)}{dt^2} \delta x - \vec{\nabla} V(x(t)) \delta x \right] $$

The first term is a total derivative, so it is equal to the difference in the inner square bracket term between the endpoints of the integration.  But because our $\delta x(t)$ is $0$ at the two ends, this is zero.  So we are left with:

$$ 0 = \int dt \left[ m\frac{d^2 \vec{x}(t)}{dt^2}  \delta x + \vec{\nabla} V(x(t)) \delta x \right] $$
$$ 0 = \int dt \left[ m\frac{d^2 \vec{x}(t)}{dt^2} + \vec{\nabla} V(x(t)) \right] \delta x  $$

This must be $0$ for any variation $\delta x(t)$, so that the term inside the integrand itself must be $0$.

$$ 0 =  m\frac{d^2 \vec{x}(t)}{dt^2} + \vec{\nabla} V(x(t)) $$

This is the same as $F = ma$ as we established in the first section.

Note that in the Prologue we haven't introduced anything more to our physics than $F = ma$, we've just reformulated how we express it in a way that was well known in the 1700s.

## Part 1: To Special Relativity

As a reminder, the action we have for Newtonian mechanics is:

$$ S[x(t)] = \int dt \left[\frac{m}{2} \left(\frac{dx}{dt}\right)^2 - V(x(t)) \right] $$

We can try doing something that isn't quite "legal" calculus, but helps highlight how $dx$ and $dt$ are treated differently in this equation:

$$ S[x(t)] = \int \left[\frac{m \left(dx\right)^2}{2 dt} - V(x(t)) dt \right] $$

We see that we have a square of distance divided by the time. Let's try to express this more evenly.

An identity we can use is that:

$$ \sqrt{a^2 - b^2} \approx a - \frac{b^2}{2a} - ... $$

When  $b \ll a$, we can ignore the $...$.

$$ \left(a - \frac{b^2}{2a}\right)\left(a - \frac{b^2}{2a}\right) = a^2 - b^2 + \frac{b^4}{4a^2} + ...$$

So this is correct up to fourth order in the small $b$.

So for $b \ll a$ we have $\frac{b^2}{2a} = a - \sqrt{a^2-b^2}$.

We can use this to rewrite the first term in our action above.  It is almost the case that we could set $b=dx$ and $a=dt$.  However, we can't add distance and time, so we can't use this formula which assumes a and b have the same units.  Instead, we can introduce a constant $c$ into our original action arbitrarily, with units of velocity.

$$ S[x(t)] = \int \left[m c \left[\frac{ \left(dx\right)^2}{2 (c dt)}\right] - V(x(t)) dt \right] $$

This $c$ is so far an entirely arbitrary constant, but if we select it to be a very large velocity, larger than any velocity at which we have tested $F=ma$ in practice, then it will be the case that $ \frac{dx}{dt} \ll c $ or $ dx \ll  c dt $.

We can now choose $b = dx$ and $a = cdt$, and then we have that $b \ll a$ because $dx \ll cdt$ or $\frac{dx}{dt} \ll c$.  We then have:

$$ S[x(t)] = \int \left[m c \left[ cdt -  \sqrt{c^2dt^2 - dx^2}  \right] - V(x(t)) dt \right] $$

$$ S[x(t)] = \int m c^2 dt - \int mc \sqrt{c^2dt^2 - dx^2} - \int V dt $$

$$ S[x(t)] =  m c^2 \int dt - mc \int  \sqrt{c^2dt^2 - dx^2} - \int V dt $$

The first term is just a constant, varying $x(t)$ will not change it so we can ignore it.  But we'll see shortly that this is very suggestive (you might be able to guess already from the constant value!).

So our action is:

$$ S[x(t)] =  - mc \int  \sqrt{c^2dt^2 - dx^2} - \int V dt $$

As long as we pick $c$ much larger than all velocities we have tested, this should produce the same predictions for the path $x(t)$ of an object as were predicted by $F=ma$.

### Taking this Seriously

We can invert the logic so far to posit that potentially the *real* action for mechanics is $ S =  - mc \int  \sqrt{c^2dt^2 - dx^2} - \int V dt $ and that the earlier $ S = \int dt \left[\frac{m}{2} \left(\frac{dx}{dt}\right)^2 - V(x(t)) \right] $ is actually just a low-velocity approximation.  When $\frac{dx}{dt}$ is *small* (relative to $c$), these make the same predictions.  But when velocities get closer to $c$ these produce different predictions about the path that bodies will take within the same potential $V$.

This is the first major *educated guess* we will make about physics - that the new action is correct and the earlier action is the approximation, instead of the opposite.

### Speed of Light

But if this is the real action, instead of just an approximation, it has some additional requirements.  To keep the first term real, we must have:

$$ c^2 dt^2 - dx^2 >= 0 $$
$$ \frac{dx}{dt} <= c $$

That is, this equation requires that there is an absolute maximum velocity $c$ that is allowed for any body.  We don't yet know what value it has, but we know there must be a maximum, and by testing how objects move at large velocities, we can do experiments to discover what value it must have.

**We've discovered the speed of light!**  (Though we haven't yet shown that light attains this fastest possible speed).

### Mass-energy equivalence $E = mc^2$

We saw a constant term $mc^2$ that appeared in the derivation of the action.  If we take our new action as being the true one, then we see that our total action is indeed a large constant $mc^2$ plus the term that approximates $\frac{dx}{dt}^2$ (plus additional terms for the corrections).  This large constant energy doesn't affect the dynamics because it doesn't change while varying the action for a given mass $m$.  We could think of this instead as being an additional component of the potential, giving us an additional $mc^2$ of potential energy.  We can't observe this, but it is very suggestive of this fixed large amount of energy associated with a mass, and that if there were a way to convert this mass into energy, we might be able to observe this (which quantum mechanics, the physics of the atom, and ultimately the atomic bomb did indeed discover was possible).

**We've discovered one of the most famous equations in physics - that there is $E=mc^2$ rest energy associated with a mass $m$.**

### Lorentz Covariance

If we ignore the potential term and focus only on the kinematics, we have:

$$ S =  - mc \int  \sqrt{c^2dt^2 - dx^2} $$

Let's introduce a new differential quantity $ds$:

$$ ds^2 = c^2dt^2-dx^2 $$

So that:

$$ S =  - mc \int ds $$

This is a notion of "distance" in both space and time.  It is similar to $dx$ which measures the distance in 3 spatial dimensions, but negated, and combined with $dt$ which measures distance in a single time dimension.

Expressing the action in this form makes it perhaps feel more clear why this is a "simpler" way to formulate mechanics.  The action is simply the distance along the curve in this spacetime metric, multiplied by $mc$ to convert into an energy.

This can also be written in another form that puts $dt$ and $dx$ even more clearly on equal footing.  Let $\mu=0,1,2,3$ and $dx_{\mu}=(cdt,dx_1,dx_2,dx_3)$.  Then we can write $S$ in a third form as:

$$ S =  - mc \int \sqrt{\eta_{\mu\nu}dx^{\mu}dx^{\nu}} $$

Where there is an implicit sum over repeated indices ($\mu$ and $\nu$):

$$ \eta_{\mu\nu} = \begin{pmatrix} 1 & 0 & 0 & 0 \cr 0 & -1 & 0 & 0 \cr 0 & 0 & -1 & 0 \cr 0 & 0 & 0 & -1 \end{pmatrix} $$

Our "vectors" are now 4D spacetime vectors with Greek indices, and the metric for computing the length of a vector is $\eta_{\mu\nu}$.

There may be a class of transformations $x_\mu \rightarrow x^\prime_\mu$ which keep $S$ the same.  Such a transformation would be a symmetry of physics implied by this equation, since it would not affect the solutions to the least action equations.

There are several transformations that were symmetries of $\vec{F}=m\vec{a}$ that we can try.  We can translate in either space or time, $x^\prime_\mu = x_\mu + (T,0,0,0) $ or $ x^\prime_\mu = x_\mu + (0,0,0,Z) $.  In both cases, $dx_\mu$ is unchanged, and so $S$ is unchanged.  We can also rotate in space:

$$ x^\prime_\mu = \left(\begin{matrix} 1 & 0 & 0 & 0 \cr 0 & -1 & 0 & 0 \cr 0 & 0 & -cos \theta & sin \theta \cr 0 & 0 & -sin \theta & -cos \theta \end{matrix}\right) x_\nu $$

If you multiply this out, you can see that it leaves $S$ unchanged as well.  (Note that this is a symmetry of $\vec{F}=m\vec{a}$ because that is an equation written in terms of vectors, which implies both $F$ and $a$ rotate in the same way as vectors).

More generally we can see from quick inspection of the action that, for $dx^\prime_\mu = \Lambda_{\mu\nu}dx_\nu$, this will be a symmetry for any $\Lambda_{\mu\nu}$ such that:

$$ \Lambda_{\mu\nu} \eta_{\nu\rho} \Lambda_{\rho\gamma} = \eta_{\mu\gamma}  $$

These transformations $\Lambda_{\mu\nu}$ are called Lorentz transformations. As well as the rotations which were symmetries of $\vec{F}=m\vec{a}$, there is another class of symmetries allowed called *boosts*.  With $\beta=\frac{v}{c}$ and $\gamma = \frac{1}{\sqrt{1-\beta^2}}$ :

$$ x^\prime_\mu = \begin{pmatrix} \gamma & -\gamma\beta & 0 & 0 \cr -\gamma\beta & \gamma & 0 & 0 \cr 0 & 0 & 1 & 0 \cr 0 & 0 & 0 & 1 \end{pmatrix} x_\nu $$

These "rotate" between a spatial dimension and the time dimension, boosting our speed by $v$.  This is not the same additive velocity transformation of Newtonian/Galilean physics.  The rules for boosting into relative motion, and the symmetry of the physics representing this, are now expressed by this transformation matrix in the spacetime vector space.

**We have discovered Lorentz covariance of our physics**.  There are new symmetries to our physics, and the previous Galilean symmetries are only an approximation.

## Part 2: To Electromagnetism

We discovered the Lorentz symmetry of the kinematic term in our action, but that symmetry does not appear to apply to the dynamical term of our action which includes the potential $V$.

$$ S =  - mc \int\sqrt{\eta_{\mu\nu}dx^{\mu}dx^{\nu}} - \int V dt $$

There's no way to make $Vdt$ into a Lorentz covariant quantity if $V$ is a scalar quantity, since boosts would mix the $dt$ component with a $dx$ component.

To keep the notation focused in this part, we'll use units where $c=1$.  We will restore $c$ when we connect the resulting field equations back to the speed of light.

### Electromagnetic vector potential

A solution is to treat the above action as only a low velocity approximation again.

One way we can do that is to introduce a new four-vector $A^\mu=(V, A_1, A_2, A_3)$ so that:

$$ \int \eta_{\mu\nu}A^\mu dx^\nu =  \int \left[Vdt - \vec{A}\vec{dx}\right] \approx \int V dt  $$

The last approximate equality holds at low velocity when the spatial term is small.  At higher velocities, or for vector potentials dominated by their spatial components, we should expect different physics.

We should also allow different objects to couple to this new potential with different strengths.  We call this independent property the electric charge $q$.  The scalar potential energy in the low velocity action is then $qV$, and a neutral object has $q=0$ even though it may have non-zero mass.

This leads to the action:

$$ S =  - m \int\sqrt{\eta_{\mu\nu}dx^{\mu}dx^{\nu}} - q \int \eta_{\mu\nu}A^\mu dx^\nu $$

We'll introduce the lowering notation of moving Greek indices downstairs to indicate multiplication by a factor of $\eta_{\mu\nu}$, so that $A_\nu = \eta_{\mu\nu}A^\mu$.  This can be used in both terms above to simplify their notation:

$$ S =  - m \int\sqrt{dx_{\mu}dx^{\mu}} - q \int A_\mu dx^\mu $$

This is manifestly Lorentz invariant - all components are Lorentz vectors, and the inner product of vectors produces Lorentz scalar values that must transform covariantly under Lorentz transformations, so that the value of $S$ is the same in any Lorentz frame of reference.  It's notable that the additional symmetry of Lorentz invariance of the action puts significant constraints on the shape and structure of this equation.

### Equations of Motion for the Vector Potential

Let's apply $\delta S = 0$ to discover the equations of motion for this new action incorporating the vector potential.

First, let's fill in how proper time enters the variation of the free-particle term.  Along the path, $ds^2 = dx_\mu dx^\mu = d\tau^2$ in our $c=1$ units.  Varying the square root, integrating by parts, and fixing the endpoints gives:

$$ \delta \left(-m\int ds\right)
 = -m\int \frac{dx_\mu}{ds}d\delta x^\mu
 = m\int d\tau \frac{d^2x_\mu}{d\tau^2}\delta x^\mu $$

For the interaction term, the same integration by parts gives:

$$ \delta \left(-q\int A_\mu dx^\mu\right)
 = -q\int \left(\partial_\nu A_\mu - \partial_\mu A_\nu\right)dx^\mu\delta x^\nu $$

We'll introduce:

$$ F_{\mu\nu} = \partial_\mu A_\nu - \partial_\nu A_\mu $$

Combining the two variations gives:

$$ 0 = \int d\tau \left[m\frac{d^2x^\mu}{d\tau^2}
 - qF^\mu{}_\nu\frac{dx^\nu}{d\tau}\right]\delta x_\mu $$

Or, since $ \delta x^\mu $ is arbitrary:

$$  m \frac{d^2x^{\mu}}{d\tau^2} = qF^\mu{}_\nu \frac{dx^\nu}{d\tau} $$

This looks a lot like $ma = F$ that we started with!  But the structure of the action requires the force to be proportional to the charge $q$, the four-velocity $\frac{dx^\nu}{d\tau}$, and the tensor $F_{\mu\nu}$ derived from the vector potential $A_\mu$.

### Lorentz Force Law

We know that $F_{\mu\nu}$  must be antisymmetric ($F_{\mu\nu} = - F_{\nu\mu}$) from its definition.   That means there are only six unique values, and we can name them as follows:

$$F_{\mu\nu} = \begin{pmatrix} 0 & E_1 & E_2 & E_3 \cr - E_1 & 0 & -B_3 & B_2 \cr - E_2 & B_3 & 0 & - B_1 \cr - E_3 & -B_2& B_1& 0 \end{pmatrix} $$

This introduces two vectors $\vec{E} = (E_1,E_2,E_3)$ and  $\vec{B} = (B_1,B_2,B_3)$ that together define $F_{\mu\nu}$ (and vice versa).

At low velocity, proper time and coordinate time are approximately equal.  Expanding the three spatial components of the equation of motion then gives:

$$ m \frac{d^2\vec{x}(t)}{dt^2} = q\left(\vec{E} + \frac{d\vec{x}}{dt}  \times \vec{B}\right) $$

**We have discovered the Lorentz Force Law.**

We can of course measure and observe the two three-dimensional vector fields $\vec{E}$ and $\vec{B}$ as the electric and magnetic fields.  These are just the components of the much more symmetrical $F_{\mu\nu}$ which itself is formed from derivatives of the vector potential $A_\mu$.  If we know any of these, we know the rest.  The unique structure of the electromagnetic fields and their force on an object turns out to be effectively the only structure allowed for a Lorentz-covariant potential.  So we didn't have to "guess" this form; the simple assumption that we should take Lorentz invariance seriously while incorporating a potential into the equations required us to have the form of the Lorentz force law.

### Gauge Invariance

We have introduced a vector potential $A_\mu$, but we have so far not said anything about the form it must take, or the dynamics of the $A_\mu$ field itself (how it evolves from a given state).  We have only spoken to the impact it has on other objects.

We can observe an interesting fact about $A_\mu$.  If we change our $A_\mu$ to $A^\prime_\mu = A_\mu + \partial_\mu\Lambda$ then the interaction term changes only by:

$$ q\int \partial_\mu\Lambda(x) dx^\mu
 = q\int d\Lambda(x)
 = q\left[\Lambda(x_f)-\Lambda(x_i)\right] $$

This depends only on the fixed endpoints, so it doesn't affect the equations of motion.

So even though we were able to specify the vector potential $A_\mu$ arbitrarily, it is actually overspecified; any change by $\partial_\mu \Lambda(x)$ for any $\Lambda(x)$ will represent the same physics.

**We have discovered gauge invariance of the vector potential.**

This gauge freedom is similar to how the potential $V$ for gravity has no absolute value: shifting the value by a fixed quantity throughout spacetime results in the same physics (because it doesn't change $\vec{\nabla} V(x)$).  But in this case, we can shift by a different value at every point in spacetime, making the gauge invariance extremely flexible.

### Maxwell's Action

As we've done several times before in this path to modern physics, let's take the newly found symmetry/invariance very seriously.  What if gauge invariance of the vector potential is fundamental?

To discover the equations of motion for the vector potential field, we must add a term to the action for the existence of the potential $A_\mu(x)$.  We need three things to be true about this term for it to capture the dynamics of the field:

* It must contain two powers of the time derivative of $A_\mu(x)$.
* It must be gauge invariant.
* It must be a Lorentz scalar to be a term in the action.

To capture the dynamics of the potential, it must involve two powers of the time derivatives of $A_\mu(x)$ just like the term $\frac{m}{2} \left(\frac{dx}{dt}\right)^2$ in the point particle equations of motion contains two powers of the time derivative of $x$.

We also now expect this term to be gauge invariant.  Up to a total derivative, there is only one Lorentz scalar with two powers of first derivatives of $A_\mu(x)$, built from the quantity we stumbled upon earlier:

$$ F_{\mu\nu} = \partial_\mu A_\nu - \partial_\nu A_\mu$$

Under a gauge transformation, the value of $F_{\mu\nu}$ is unchanged, which explains why this value could show up in the equations of motion (and be equivalent to the measurable $\vec{E}$ and $\vec{B}$), even though $A_\mu(x)$ itself isn't measurable.

So if $F_{\mu\nu}$ contains first derivatives, then the square of $F_{\mu\nu}$ will contain second powers of time derivatives.  And since $F$ is a 2-tensor, we can turn it into a Lorentz scalar by contracting both indices.  This field exists over all of spacetime, so the term it adds to the action is (with a conventional factor in front - that we can introduce by scaling $A$ by a constant factor):

$$ \int d^4x \left(-\frac{1}{4}F_{\mu\nu}(x)F^{\mu\nu}(x)\right) $$

This is the action that specifies all the dynamics of the field $A_\mu(x)$.

The full action for an interacting charged object and the vector potential field is:

$$ S = - m \int\sqrt{\eta_{\mu\nu}dx^{\mu}dx^{\nu}}
 - q\int A_\mu(X)dX^\mu
 - \int d^4x \frac{1}{4}F_{\mu\nu}(x)F^{\mu\nu}(x) $$

The first and second terms involve the object traversing the path $X^\mu(\tau)$, and the second and third terms involve the vector field $A_\mu(x)$ defined at all points in spacetime.  We have seen how the object behaves within this field.  How does the field behave in response to the object?

### The Equations of Motion of the Vector Field

As we've done twice before, we vary the action, but this time we vary it with respect to $A_\mu(x)$ instead of $x_\mu(t)$.

The first term above doesn't include $A_\mu(x)$ so it doesn't contribute.

The third term is:

$$ \delta \int d^4x -\frac{1}{4}F^{\mu\nu}(x)F_{\mu\nu}(x)$$
$$ = \int d^4x -\frac{1}{4}\delta \left(F^{\mu\nu}(x)F_{\mu\nu}(x)\right)$$
$$ = \int d^4x -\frac{1}{4}\left(2F^{\mu\nu}(x)\delta F_{\mu\nu}(x)\right)$$
$$ = \int d^4x -\frac{1}{4}\left(4F^{\mu\nu}(x)\partial_\mu\delta A_\nu(x)\right)$$
$$ = \int d^4x -F^{\mu\nu}(x)\partial_\mu\delta A_\nu(x)$$

And, integrating by parts again:

$$ = \int d^4x \left[\partial_\mu F^{\mu\nu}(x)\right]\delta A_\nu(x)$$

And, since this applies for any $\delta A_\nu(x)$, the term inside the $[...]$ must be 0.

The interaction term can be rewritten as an integral over all of spacetime:

$$ -q\int A_\mu(X)dX^\mu
 = -\int d^4x J^\mu(x)A_\mu(x) $$

where:

$$ J^\mu(x) = q\int d\tau\,
\frac{dX^\mu}{d\tau}\delta^{(4)}(x-X(\tau)) $$

This four-current is non-zero only on the object's path, points along that path, and has a magnitude set by the charge $q$.  Varying the interaction term therefore gives:

$$ \delta S_{\text{interaction}}
 = -\int d^4x J^\mu(x)\delta A_\mu(x) $$

Putting the field and interaction variations together, and requiring $\delta S=0$ for every $\delta A_\nu$, gives:

$$ \partial_\mu F^{\mu\nu}(x) = J^\nu(x) $$

### Maxwell's Equations

If we name $J^\mu=(\rho,\vec{J})$, then the $\nu=0$ component is:

$$ \vec{\nabla} \cdot \vec{E} = \rho $$

**We've discovered one of Maxwell's equations - Gauss's Law.**

The three spatial components give:

$$ \vec{\nabla} \times \vec{B}
 = \frac{\partial \vec{E}}{\partial t} + \vec{J} $$

**We've discovered another of Maxwell's equations - Ampere's Law with Maxwell's displacement current.**

The other two Maxwell equations are even simpler.  They are identities that must be true because $F_{\mu\nu}$ is built from a single potential.  Since partial derivatives commute:

$$ \partial_\lambda F_{\mu\nu}
 + \partial_\mu F_{\nu\lambda}
 + \partial_\nu F_{\lambda\mu} = 0 $$

Taking all three indices to be spatial gives:

$$ \vec{\nabla}\cdot\vec{B}=0 $$

Taking one time index and two spatial indices gives Faraday's Law:

$$ \vec{\nabla}\times\vec{E}
 = -\frac{\partial\vec{B}}{\partial t} $$

**We have discovered all four of Maxwell's equations.**

This way of writing the equations of motion also implies current conservation, because $F_{\mu\nu}$ is antisymmetric and partial derivatives commute:

$$ \partial_\mu F^{\mu\nu}(x) = J^\nu(x) $$
$$ \partial_\nu \partial_\mu F^{\mu\nu}(x) = \partial_\nu J^\nu(x) $$
$$ 0 = \partial_\nu J^\nu(x) $$
$$ \partial_\nu J^\nu(x) = 0$$

We already knew that from the way we defined $J^\nu(x)$, but this reaffirms how much information is in these equations of motion.

### Electromagnetic Waves

We can finally return to the maximum velocity $c$ we introduced in Part 1.  In empty space, $J^\mu=0$.  We can use our gauge freedom to choose the Lorenz gauge $\partial_\mu A^\mu=0$, after which the field equation becomes:

$$ \partial_\mu\partial^\mu A^\nu = 0 $$

Restoring $c$, this is:

$$ \left(\frac{1}{c^2}\frac{\partial^2}{\partial t^2}
 - \vec{\nabla}^2\right)A^\nu = 0 $$

This is a wave equation whose solutions propagate at exactly $c$.  The electric and magnetic fields are waves traveling at the same invariant speed that appeared in the relativistic particle action.

**We have discovered that light is an electromagnetic wave, and that its speed is the maximum speed $c$.**

### Summary of Part 2

By taking Lorentz symmetry seriously, we promoted the potential $V(x)$ to a vector potential $A_\mu(x)$, and discovered that it must interact with objects according to the Lorentz force law.

We then discovered a new symmetry, gauge invariance, in the action of the vector potential, and taking that seriously fixed the form of the action for the vector field $A_\mu(x)$ itself.  Solving the equations of motion for this field produced Maxwell's equations, current conservation, and electromagnetic waves traveling at $c$.

As a result, taking these two symmetries seriously leads to the core structure of classical electromagnetism.

## Part 3: To Gravity

We started Part 2 by looking at this action and trying to make the second term Lorentz invariant.  We now restore factors of $c$:

$$ S =  - mc \int\sqrt{\eta_{\mu\nu}dx^{\mu}dx^{\nu}} - \int V dt $$

In Part 2, we did this by promoting $V$ to a Lorentz vector.

Instead of interpreting the potential as a vector potential, there's another way we could have incorporated it into the action, which is to absorb it into the first term, underneath the square root.  We can do that with the action:

$$ S =  - mc \int\sqrt{g_{\mu\nu}(x)dx^{\mu}dx^{\nu}} $$

Where:

$$ g_{\mu\nu}(x) = \begin{pmatrix} 1 + \frac{2V(x)}{mc^2}& 0 & 0 & 0 \cr 0 & -1 & 0 & 0 \cr 0 & 0 & -1 & 0 \cr 0 & 0 & 0 & -1 \end{pmatrix} $$

The combination $V/(mc^2)$ is dimensionless, as every component of the metric must be.  Expanding at low velocity and for a weak potential:

$$ -mc\sqrt{g_{\mu\nu}dx^\mu dx^\nu}
 = -mc^2dt\sqrt{1-\frac{v^2}{c^2}+\frac{2V}{mc^2}} $$

$$ \approx -mc^2dt + \left(\frac{1}{2}mv^2-V\right)dt $$

Apart from the constant rest-energy term, this is exactly the Newtonian action we started with.

What if we again take this idea very seriously?  What if this $g_{\mu\nu}$ is actually the true metric of spacetime, and $\eta_{\mu\nu}$ is just the low-order limit when this new potential is small?  What if the length of a vector is actually measured by $g_{\mu\nu}$?  Then everywhere we contract Lorentz indices, we must do so with $g_{\mu\nu}$.

The combination $\Phi=V/m$ is the gravitational potential per unit mass, so $g_{00}=1+2\Phi/c^2$ does not depend on which test object we use.  This universality is special to gravity: every freely falling object follows the same spacetime geometry.

### Curved Spacetime

This introduces a few new concepts.  First, the potential is now the metric itself, and it is a tensor instead of a scalar or vector. Second, the metric which determines "distance" in spacetime is no longer a constant, and no longer the "flat" metric we discovered for special relativity above.  Instead, the metric depends on the potential, and is different at every point of space.  That means that spacetime is curved, and curved by the presence of this potential.

**We have discovered curved spacetime!**

Just like with the vector potential, there can be non-zero components elsewhere in the tensor even though only the time-time component dominates the low velocity limit.  In that limit, the scalar potential is:

$$ V(x) = \frac{mc^2}{2}\left(g_{00}(x)-1\right) $$

Only the symmetric part of $g_{\mu\nu}$ contributes to the action, so we focus on $g_{\mu\nu}(x)=g_{\nu\mu}(x)$.  A symmetric $4\times4$ metric has 10 independent components at every point in spacetime.

### Motion of an Object in Curved Spacetime

Whenever we have an action, we know that we can vary it to discover the equations of motion.  The square-root action above measures the length of the path.  If we parameterize the path by proper time $\tau$, it gives the same path as the simpler quadratic action:

$$ S_{\text{path}} = \frac{1}{2}\int d\tau\,
g_{\alpha\beta}(x)\frac{dx^\alpha}{d\tau}\frac{dx^\beta}{d\tau} $$

Defining $\dot{x}^\mu=\frac{dx^\mu}{d\tau}$, the two derivatives in the Euler-Lagrange equation are:

$$ \frac{\partial L}{\partial\dot{x}^\delta}
 = g_{\delta\beta}\dot{x}^\beta $$

$$ \frac{\partial L}{\partial x^\delta}
 = \frac{1}{2}\partial_\delta g_{\alpha\beta}
\dot{x}^\alpha\dot{x}^\beta $$

Taking the proper-time derivative of the first expression gives:

$$ \frac{d}{d\tau}\left(g_{\delta\beta}\dot{x}^\beta\right)
 = \partial_\alpha g_{\delta\beta}\dot{x}^\alpha\dot{x}^\beta
 + g_{\delta\beta}\ddot{x}^\beta $$

The Euler-Lagrange equation, multiplied by the inverse metric and symmetrized in $\alpha$ and $\beta$, becomes:

$$ \frac{d^2 x^\mu}{d\tau^2}
 + \Gamma^\mu_{\alpha\beta}
\frac{dx^\alpha}{d\tau}\frac{dx^\beta}{d\tau} = 0 $$

where:

$$ \Gamma^\mu_{\alpha\beta}
 = \frac{1}{2}g^{\mu\delta}
\left(\partial_\alpha g_{\delta\beta}
+\partial_\beta g_{\delta\alpha}
-\partial_\delta g_{\alpha\beta}\right) $$

These are known as the Christoffel symbols.  The equation is reminiscent of both Newton's equation and the electromagnetic equation of motion.  Here, though, the apparent acceleration is proportional to two factors of velocity, and the metric determines the coefficients.

**We have discovered the Geodesic Equations.**

When $g_{\mu\nu}=\eta_{\mu\nu}$ in Cartesian coordinates, all Christoffel symbols vanish and $\frac{d^2x^\mu}{d\tau^2}=0$.  The Christoffel symbols can be non-zero even in flat spacetime if we use curved coordinates, so they are not themselves a coordinate-independent measure of curvature.  The geodesic equation nevertheless has the same form in every coordinate system: freely falling objects follow the straightest possible paths through spacetime.

### Curvature

Although we can make the Christoffel symbols vanish at a point by choosing a freely falling coordinate system, we cannot generally make their derivatives vanish as well.  The combination that survives such coordinate changes is the Riemann curvature tensor:

$$ R^{\rho}_{\sigma\mu\nu} = \partial_\mu \Gamma^{\rho}_{\nu\sigma} - \partial_\nu \Gamma^{\rho}_{\mu\sigma} + \Gamma^{\rho}_{\mu\lambda}\Gamma^{\lambda}_{\nu\sigma} - \Gamma^{\rho}_{\nu\lambda}\Gamma^{\lambda}_{\mu\sigma} $$

This measures the change in a vector transported around an infinitesimal loop.  It also determines how nearby geodesics accelerate toward or away from each other - the tidal effect of gravity.

**We've discovered the Riemann Curvature Tensor.**

The symmetries of the Riemann tensor make many contractions vanish or repeat the same information.  The unique non-trivial contraction is the Ricci tensor:

$$ R_{\mu\nu} = R^{\rho}_{\mu\rho\nu} $$

Contracting once more gives the Ricci scalar:

$$ R = g^{\mu\nu}R_{\mu\nu} $$

The full Riemann tensor vanishes exactly when spacetime is locally flat.  The Ricci tensor and scalar contain less information: they vanish in empty regions of some curved spacetimes, but they are exactly the contractions we need to build the simplest action for the metric.

### Dynamics of the Metric Tensor

Just like we did in Part 2, we can ask whether there are constraints on the structure and dynamics of $g_{\mu\nu}$ beyond it being a symmetric tensor.  Similar to how we couldn't answer that question directly for $A^\mu(x)$ due to its gauge invariance, we similarly can't answer directly in terms of $g_{\mu\nu}(x)$ due to its overspecification of the geometry (many different $g$ define the same structure of the geometry, just with different coordinates).  We need a quantity which is "generally covariant", which means that it doesn't change under changes to the coordinates (as long as the geometry/shape of the space is unchanged).

Again, we are looking for a term satisfying:

* It must contain two powers of the time derivative of $g_{\mu\nu}(x)$.
* It must be generally covariant.
* It must be a scalar to be a term in the action.

It turns out we already have a quantity that meets these requirements - the Ricci scalar $R$.  It contains up to second derivatives of $g_{\mu\nu}(x)$, it describes curvature independently of the coordinates used, and it is a scalar.

To integrate this over spacetime, we can't use $d^4x$ alone because a general coordinate transformation changes the coordinate volume.  Instead, we use $\sqrt{-g}\,d^4x$, where $g=\det(g_{\mu\nu})$.  The factor $\sqrt{-g}$ changes in exactly the opposite way, making the full measure coordinate invariant.

Including the conventional normalization, the result is:

$$ S_{\text{gravity}}
 = \frac{c^3}{16\pi G}\int R\sqrt{-g}\,d^4x $$

**We've discovered the Einstein-Hilbert Action.**

## Einstein Field Equations

We know what to do when we find a new term in our action - we vary it!

This variation is more involved than the one that produced Maxwell's equations, but the key steps have the same structure.  First:

$$ \delta\sqrt{-g}
 = -\frac{1}{2}\sqrt{-g}\,g_{\mu\nu}\delta g^{\mu\nu} $$

The variation of $R$ contributes a term $R_{\mu\nu}\delta g^{\mu\nu}$ plus a total derivative.  As before, the total derivative is a boundary term and doesn't affect the equations of motion.  The remaining variation is:

$$ \delta S_{\text{gravity}}
 = \frac{c^3}{16\pi G}
\int d^4x\sqrt{-g}
\left(R_{\mu\nu}-\frac{1}{2}g_{\mu\nu}R\right)
\delta g^{\mu\nu} $$

We also need to describe the matter and energy producing the curvature.  We add a matter action $S_{\text{matter}}$ and define its stress-energy tensor by:

$$ \delta S_{\text{matter}}
 = -\frac{1}{2c}\int d^4x\sqrt{-g}\,
T_{\mu\nu}\delta g^{\mu\nu} $$

The stress-energy tensor includes energy density, momentum density, pressure, and stress.  It plays the same role for the metric that the current $J^\mu$ played for the electromagnetic potential.

Setting the variation of the total action to zero for every $\delta g^{\mu\nu}$ gives:

$$ R_{\mu\nu}
 - \frac{1}{2}g_{\mu\nu}R
 = \frac{8\pi G}{c^4}T_{\mu\nu} $$

The normalization is fixed by requiring the weak-field, low velocity limit to reproduce Newton's law of gravity.

**We have discovered the Einstein Field Equations.**

The left side describes the curvature of spacetime; the right side describes the matter and energy within it.  In Wheeler's famous summary: matter tells spacetime how to curve, and curved spacetime tells matter how to move.