---
title: "A Fast Path to Modern Physics"
date: 2020-02-25T13:44:49-07:00
math: true
markup: "mmark"
---

One of my favorite physics books is [Einstein Gravity in a Nutshell](https://press.princeton.edu/books/hardcover/9780691145587/einstein-gravity-in-a-nutshell) by A. Zee.  A subplot of the book that is spread over several sections, is a line of thinking that discovers a wide range of physics from a simple starting point, guided by a couple simple intuitions (1) could what we know be seen as a low velocity approximation of something more general? (2) if new symmetries show up in the new more general form take them seriously and see what happens.

I've never seen this this approach used in other physics books or papers, but I think back to it frequently.  So in this post, I attempt to recreate it, filling in some details and extending to a few additional "discoveries" motivated by the same line of thinking.

We'll imagine ourselves a physicist from the 1700s who knows Newtonian mechanics, and see a path where we could have reasonably discovered much of 19th and 20th centuty physics, mostly just by recognizing the structure of various equations as possible low-velocity approximations of other more structured forms, and then taking seriously the symmetries we discover in those new forms.  In the prologue, we'll just reformulate $F=ma$ in a way well known in the 1700s. Then we'll make some more educated guesses to discover the rest of this physics.

Along the way - we'll "discover" all of the following:
* The speed of light
* Lorentz  covariance
* $E = mc^2$
* Electromegnetic vector potential
* Lorentz force law
* Gauge invariance
* Maxwell's equations
* Dynamic spacetime metric
* Curved spacetime
* Geodesic equation
* Curvature tensor
* Einstien-Hilbert Action
* Einstein Field Equations

Let's dig in!

## Part 0: Prologue

## Start with Newton's 2nd Law

Let's start with the one phyiscs equation that every high-school student knows - Newton's 2nd law, known since at least 1687:

$$F = ma$$

We can make this a little more explicit in a few steps. First, this is an equation about the force, mass and acceleration of an object at a point in space and time.

$$F(x(t)) = m a(t)$$

It also applies in three dimensions as a vector equation.

$$\vec{F}(\vec{x}(t)) = m\vec{a}(t)$$

And the acceleration $\vec{a}(t)$ is the second derivative of the path of the body $\vec{x}(t)$.

$$\vec{F}(\vec{x}(t)) = m\frac{d^2 \vec{x}(t)}{dt^2}$$

This equation is true for *any* force $\vec{F}(x)$, but for the purposes of this post, we'll focus on a specific class of forces called [conservative forces](https://en.wikipedia.org/wiki/Conservative_force). These are forces that depend only on the position of the object.  Effectively all the fundamental forces we commonly think about are conservative, like gravity and electromagnetism. But things like friction when treated as an external force are not conservative (they transfer energy into a body that is not included in the analysis).  For conservative forces, instead of specifying a vector (3 numbers) at every point, we can specify a single number called the potential $V$ at every point, and express the force as the gradient of the potential $\vec{F}(x) = - \vec{\nabla} V(\vec{x}(t))$.  With this, we can give our $F=ma$ equation in terms of the potential $V$ as:

$$ - \vec{\nabla} V(\vec{x}(t)) = m\frac{d^2 \vec{x}(t)}{dt^2}$$

Or, in the final form we'll use:

$$ 0 = m\frac{d^2 \vec{x}(t)}{dt^2} + \vec{\nabla} V(\vec{x}(t))$$

This expresses that the force of a conservtive potential is equal to the mass times the acceleration of a p

### Least Action Principle

We can express this same statement that $F=ma$ in a quite different form that happens to generalize well into.  That form is known as the Principle of Least Action, and was known in the mid-1700's by Euler and Maupertuis.

we can derive this directly from the form of $F = ma$ we ended up with above, but instead we'll state the answer and just show that it does indeed imply that $F = ma$ for a conservative force $F$.

Let $S[x(t)]$ be the *action* associated with a given function $x(t)$.  It is a single number for each function, or a *functional*.

$$ S[x(t)] = \int dt \left[\frac{m}{2} \left(\frac{dx}{dt}\right)^2 - V(x(t)) \right] $$

The the principle of least action says that the path $x(t)$ followed by the object will be the one for which $S[x(t)]$ is a minimum.  We know that one way to find the minimum is to take the derivative and set it to zero.  In this case "take the derivative" means "vary the functional with respect to small changes to the path $x(t)$".  We take a path $x(t)$ between a start and end point, and vary it slightly, holding both ends fixed.  This is expressed as:

$$ 0 = \delta S[x(t)] $$

Let's quickly show that this statement is equivalent for the action $S[x(t)]$ we defined above.

$$ 0 = \delta \int dt \left[\frac{m}{2} \left(\frac{dx}{dt}\right)^2 - V(x(t)) \right] $$
$$ 0 = \int dt \left[m \frac{dx}{dt} \frac{\delta dx}{dt} - \frac{dV(x(t))}{d\vec{x}}\delta x \right] $$
$$ 0 = \int dt \left[m \frac{dx}{dt} \frac{d \delta x}{dt} - \vec{\nabla} V(x(t)) \delta x \right] $$

Then partial integration on the first term:

$$ 0 = \int dt \left[\frac{d}{dt}\left[m\frac{dx}{dt}\delta x \right] - m\frac{d^2 \vec{x}(t)}{dt^2} \delta x - \vec{\nabla} V(x(t)) \delta x \right] $$

The first term is a total derivative, so is equal to the diference in the inner square bracket term between the endpoints of the integration.  But because our $\delta x(t)$ is $0$ at the two ends, this is zero.  So we are left with:

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

We can use this to rewrite the first term in our action above.  It is almost the case that we could set $b=dx$ and $a=dt$.  However, we can't add distance and time, so we can't use this formula which assumes a and b have the same units.  Instead - we can introduce a constant $c$ into our original action arbitrarily, with units of velocity.

$$ S[x(t)] = \int \left[m c \left[\frac{ \left(dx\right)^2}{2 (c dt)}\right] - V(x(t)) dt \right] $$

This $c$ is so far entirely abritrary constant, but if we select it to be a very large velocity, larger than any velocity we have tested $F=ma$ on in practice, then it will be the case that $ \frac{dx}{dt} \ll c $ or $ dx \ll  c dt $.

We can now choose $b = dx$ and $a = cdt$, and then we have that $b \ll a$ becaue $dx \ll cdt$ or $\frac{dx}{dt} \ll c$.  We then have:

$$ S[x(t)] = \int \left[m c \left[ cdt -  \sqrt{c^2dt^2 - dx^2}  \right] - V(x(t)) dt \right] $$

$$ S[x(t)] = \int m c^2 dt - \int mc \sqrt{c^2dt^2 - dx^2} - \int V dt $$

$$ S[x(t)] =  m c^2 \int dt - mc \int  \sqrt{c^2dt^2 - dx^2} - \int V dt $$

The first term is just a constant, varying $x(t)$ will not change it so we can ignore it.  But we'll see shortly that this is very suggestive (you might be able to guess already from the constant value!).

So our action is:

$$ S[x(t)] =  - mc \int  \sqrt{c^2dt^2 - dx^2} - \int V dt $$

As long as we pick $c$ much larger than all velocities we have tested, this should prouce the same predictions for the path $x(t)$ of an object as were predicted by $F=ma$.

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

We saw a constant term $mc^2$ that appeared in the derivation of the action.  If we take our new action as being the true one, then we see that our total action is indeed a large constanct $mc^2$ plus the term that approximates $\frac{dx}{dt}^2$ (plus additional terms for the corrections).  This large constant energy doesn't affect the dynamics because it doesn't change while varying the action for a given mass $m$.  We could think of this instead as being an additional component of the potential, giving us an addition $mc^2$ of potential energy.  We can't observe this, but it is very suggestive of this fixed large amount of energy associated with a mass, and that if there were a way to convert this mass into energy, we might be able to observe this (which quantum mechanics, the physics of the atom, and ultimately the atomic bomb did indeed discover was possible).

**We've discovered one of the most famous equations in physics - that there is $E=mc^2$ rest energy assocaited with a mass $m$.**

### Lorentz  Covariance

If we ignore the potential term, and focus only the kinematics, we have just;

$$ S =  - mc \int  \sqrt{c^2dt^2 - dx^2} $$

Let's introduce a new differntial quantity $ds$:

$$ ds^2 = c^2dt^2-dx^2 $$

So that:

$$ S =  - mc \int ds $$

This is a notion of "distance" in both space and time.  It is similar to $dx$ which measures the distance in 3 spatial dimensions, but negated, and combined with $dt$ which measures distance in a single time dimension.

Expressing the action in this form makes it perhaps feel more clear why this is a "simpler" way to formulate mechanics.  The action is simply the distance along the curve in this spacetime metric, multiplied by $mc$ to convert into an energy.

This can also be written in another form that puts $dt$ and $dx$ even more clearly on equal footing.  Let $\mu=0,1,2,3$ and $dx_{\mu}=(cdt,dx_1,dx_2,dx_3)$.  Then we can write $S$ in a third form as:

$$ S =  - mc \int \sqrt{\eta_{\mu\nu}dx^{\mu}dx^{\nu}} $$

Where there is an implicit sum over repeated indices ($\mu$ and $\nu$):

$$ \eta_{\mu\nu} = \begin{pmatrix} 1 & 0 & 0 & 0 \cr 0 & -1 & 0 & 0 \cr 0 & 0 & -1 & 0 \cr 0 & 0 & 0 & -1 \end{pmatrix} $$

Our "vectors" are now 4d spacetime vectors with greek indices, and the metric for computing the length of a vector is $\eta_{\mu\nu}$.

There might be some class of ways we can transform $x_\mu \rightarrow x^\prime_\mu$ which keep $S$ the same.  Such a transform would be a symmetry of physics implied by this equation, since it would not affect the solutions to the least action equations.

There are several transformations that were symmteries of $\vec{F}=m\vec{a}$ that we can try.  We can translate in either space or time, $x^\prime_\mu = x_\mu + (T,0,0,0) $ or $ x^\prime_\mu = x_\mu + (0,0,0,Z) $.  In both cases, $dx_\mu$ is unchanged, and so $S$ is unchanged.  We can also rotate in space:

$$ x^\prime_\mu = \left(\begin{matrix} 1 & 0 & 0 & 0 \cr 0 & -1 & 0 & 0 \cr 0 & 0 & -cos \theta & sin \theta \cr 0 & 0 & -sin \theta & -cos \theta \end{matrix}\right) x_\nu $$

If you multiply this out, you can see that it leaves $S$ unchanges as well.  (Note that this is a symmetry of $\vec{F}=m\vec{a}$ because that is an equation written in terms of vectors, which implies both $F$ and $a$ rotate in the same way as vectors).

More generally we can see from quick inspection of the action that, for $dx^\prime_\mu = \Lambda_{\mu\nu}dx_\nu$, this will be a symmetry for any $\Lambda_{\mu\nu}$ such that:

$$ \Lambda_{\mu\nu} \eta_{\nu\rho} \Lambda_{\rho\gamma} = \eta_{\mu\gamma}  $$

These transformations $\Lambda_{\mu\nu}$ are called Lorentz transformations. As well as the rotations which were symmetries of $\vec{F}=m\vec{a}$, there is another class of symmetries allowed called *boosts*.  With $\beta=\frac{v}{c}$ and $\gamma = \frac{1}{\sqrt{1-\beta^2}}$ :

$$ x^\prime_\mu = \begin{pmatrix} \gamma & -\gamma\beta & 0 & 0 \cr -\gamma\beta & \gamma & 0 & 0 \cr 0 & 0 & 1 & 0 \cr 0 & 0 & 0 & 1 \end{pmatrix} x_\nu $$

These "rotate" between a spatial dimension and the time dimension, boosting our speed by $v$.  This is not the same additive veclocity transformation of Newtonian/Gallilean physics.  The rules for boosting into relative motion, and the symmetry of the phsyics representing this, is now expressed by this transformation matrix in the spacetime vector space.

**We have discovered Lorentz covariance of our physics**.  There are new symmetries to our physics, and the previous Gallilean symmetries are only an approximation.

## Part 2: To Electromagnetism

We discovered the Lorentz symmetry of the kinnematic term in our action, but that symmetry does not appear to apply to the dynamic term of our action which includes the potential $V$.

$$ S =  - mc \int\sqrt{\eta_{\mu\nu}dx^{\mu}dx^{\nu}} - \int V dt $$

There's no way to make $Vdt$ into a Lorentz covariant quantity if $V$ is a scalar quantity, since boosts would mix the $dt$ component with a $dx$ component.

### (Electormagnetic) vector potential

A solution is to treat the above action as only a low velocity approximation again.

One way we can do that is to introduce a new vector $A_\mu=(\frac{V}{c}, A_1, A_2, A_3)$ so that:

$$ \int \eta_{\mu\nu}A^\mu dx^\nu =  \int \left[Vdt - \vec{A}\vec{dx}\right] \approx \int V dt  $$

Where the last approximate equality is because $\vec{dx} \ll c dt$ for normal speeds, so that the first term dominates.  For speeds closer to the speed of light, or vector potentials $A_\mu$ dominated by their spatial terms, we might see different physics, but for the low velocity approximation results will match the scalar potential we started with from Newton.

This leads to a full action:

$$ S =  - mc \int\sqrt{\eta_{\mu\nu}dx^{\mu}dx^{\nu}} - \int \eta_{\mu\nu}A^\mu dx^\nu $$

We'll introduce the lowering notation of moving greek indices downstairs to indicate multiplication by a factor of $\eta_{\mu\nu}$.  So that $A_\nu = \eta_{\mu\nu}A^\mu$.  This can be used in both terms of the above to simplify it's notation:

$$ S =  - mc \int\sqrt{dx_{\mu}dx^{\mu}} - \int A_\mu dx^\mu $$

This is manifestly Lorentz invariant - all components are Lorentz vectors, and the inner product of vectors produces Lorentz scalar values that must transform covariantly under Lorentz transofmations, so that the value of $S$ is the same in any Lorentz frame of reference.  It's notable the the additional symmetry of Lorentz invariance of the action puts significant constraints on the shape and structure of this equation.

### Equations for Motion for the Vector Potential

Let's apply $\delta S = 0$ to discover the equations of motion for this new action incorporating the vector potential.

$$ 0 = \delta S$$

$$ 0 = \delta \left[ - mc \int\sqrt{\eta_{\mu\nu}dx^{\mu}dx^{\mu}} - \int A_\mu(x(t)) dx^\mu \right]$$

$$ 0 = - mc \int \delta \left[ \sqrt{\eta_{\mu\nu}dx^{\mu}dx^{\mu}} \right] - \int \left[ \partial_\mu A_\nu(x(t)) \delta x^\mu dx^\nu + A_\mu(x(t)) d\delta x^\mu\right] $$

$$ 0 = - mc \int \delta \left[ \sqrt{\eta_{\mu\nu}dx^{\mu}dx^{\mu}} \right] - \int \left[ \partial_\mu A_\nu(x(t)) \delta x^\mu dx^\nu - \partial_\nu A_\mu(x(t)) \delta x^\mu dx^\nu \right] $$

We'll introduce $F_{\mu\nu}(x(t)) =  \partial_\mu A_\nu(x(t)) - \partial_\nu A_\mu(x(t)) $ so that we have:

$$ 0 = \int  d\tau \left[ m \frac{d^2x^{\mu}}{d\tau^2} - F^\mu_\nu \frac{dx^\nu}{d\tau}\right] \delta x^\mu $$

**TODO**: how does $d\tau$ end up here, steps for first part.

Or, since $ \delta x^\mu $ is arbitary:

$$ 0 =  m \frac{d^2x^{\mu}}{d\tau^2} - F^\mu_\nu \frac{dx^\nu}{d\tau} $$

$$  m \frac{d^2x^{\mu}}{d\tau^2} = F^\mu_\nu \frac{dx^\nu}{d\tau} $$

This looks a lot like $ma = F$ that we started with!  But the structure of the action requires the force to be proportional to the veclocity $\frac{dx^\nu}{d\tau}$, and propotional to the tensor $F_{\mu\nu}$ derived from the derivative of the vector potential $A_\mu$.

### Lorentz Force Law

We know that $F_{\mu\nu}$  must be antisymmetric ($F_{\mu\nu} = - F_{\nu\mu}$) from it's definition.   That means there are only 6 unique values, and we can name them as follows:

$$F_{\mu\nu} = \begin{pmatrix} 0 & E_1 / c & E_2 / c & E_3 / c \cr - E_1 / c & 0 & -B_3 & B_2 \cr - E_2 / c & B_3 & 0 & - B_1 \cr - E_3 / c & -B_2& B_1& 0 \end{pmatrix} $$

This introduces two vectors $\vec{E} = (E_1,E_2,E_3)$ and  $\vec{B} = (B_1,B_2,B_3)$ that together define $F_{\mu\nu}$ (and vice versa).

We can expand out our equations of motion in terms of $\vec{E}$ and $\vec{B}$ instead to see what they say in a more familiar notation.

For $\mu = 1$ we have:

$$ m \frac{d^2x^1(t)}{dt^2} = F_{1 0} + F_{1 1} dx^1 + F_{1 2} dx^2 + F_{1 3} dx^3$$

$$ m \frac{d^2x^1(t)}{dt^2} = E_1 + B_3 dx^2 - B_2 dx^3$$

$$ m \frac{d^2x^1(t)}{dt^2} = E_1 + B_3 \frac{dx^2}{dt} - B_2 \frac{dx^3}{dt}$$

Or, generalizing to $\mu = 1,2,3$ we have:

$$ m \frac{d^2\vec{x}(t)}{dt^2} = \vec{E} + \frac{d\vec{x}}{dt}  \times \vec{B} $$

**We have discovered the Lorentz Force Law.**

We can of course measure and observe the two 3 dimensonal vector fields $\vec{E}$ and $\vec{B}$ as the electric and magnetic fields.  These are just the components of the much more symmetrical $F_{\mu\nu}$ which itself is formed from derivatices of the vector potential $A_\mu$.  If we know any of these, we know the rest.  The unique structure of the electromagnetic fields and their force on an object turns out to be effectively the only structure allowed for a Lorentz-covariant potential.  So we didn't have to "guess" this form, the simple assumption that we should take Lorentz invariance seriously while incorporating a potential into the equations required us to have the form of the Lorentz force law.

### Gauge Invariance

We have introduced a vector potential $A_\mu$, but we have so far not said anything about the form it must take, or the dynamics of the $A_\mu$ field itself (how it evolves from a given state).  We have only spoken to the impact it has on other objects.

We can observe an intersting fact about $A_\mu$.  If we change our $A_\mu$ to $A^\prime_\mu = A_\mu + \partial_\mu\Lambda$ then the the term $\int A_\mu dx^\mu$ changes by the following:

$$ \int \partial_\mu\Lambda(x) dx^\mu  = \int d\Lambda(x) $$

If we take $\Lambda(x)$ to go to $0$ at infinity, then this value goes to $0$ and doesn't affect the equations of motion.

So even though we were able to specify the vector potential $A_\mu$ arbirarily, it is actually overspecified, any change by $\partial_\mu \Lambda(x)$ for any $\Lambda(x)$ will represent the same physics.

**We have discovered gauge invariance of the vector potential.**

This gauge freedom is similar to how the potential $V$ for gravity has no absolute value, shifting the value by a fixed quantity throughout spacetime results in the same physics (because it is doesn't change $\nabla \vec{V}(x)$).  But in this case, we can shift by a different value at every point in spacetime, making the gauge invariance extremely flexible.

### Maxwell's Action

As we've done several times before in this path to modern physics, let's take the new found symmetry/invariance very seriously.  What if guage invariance of the vector potential is fundamental?

To discover the equations of motion for the vector potential field, we must add a term to the action for the existence of the potential $A_\mu(x)$.  We need three things to be true about this term for it to capture the dynamics of the field:

* It must contain two powers of the time derivative of $A_\mu(x)$.
* It must be gauge invariant.
* It must be a Lorentz scalar to be a term in the action.

To capture the dynamics of the potential, it must involve two powers of the time derivtives of $A_\mu(x)$ just like the term $\frac{m}{2} \left(\frac{dx}{dt}\right)^2$ in the point particle equations of motion contains two powers of the time derivative of $x$.

We also though now expect this term to be gauge invariant.  There is in fact only one gauge invariant quantity we can build from derivaties of $A_\mu(x)$, which we stumbled upon earlier:

$$ F_{\mu\nu} = \partial_\mu A_\nu - \partial_\nu A_\mu$$

Under a guage tranformation, the value of $F_{\mu\nu}$ is unchanged, which explains why this value could show up in the equations of motion (and be equivalent to the measurable $\vec{E}$ and $\vec{B}$), even though $A_\mu(x)$ itself isn't measurable.

So if $F_{\mu\nu}$ contains first derivatives, then the square of $F_{\mu\nu}$ will contain second powers of time derivatives.  And since $F$ is a 2-tensor, we can turn it into a Lorentz scalar by contracting both indices.  This field exists over all of spacetime, so the term it adds to the action is (with a conventional factor in front - that we can introduce by scaling $A$ by a constant factor):

$$ \int d^4x \left(-\frac{1}{4}F_{\mu\nu}(x)F^{\mu\nu}(x)\right) $$

This is the action that specifies all the dynamics of the field $A_\mu(x)$.

The full action for an interacting object and the vector potential field is:

$$ S = - mc \int\sqrt{\eta_{\mu\nu}dx^{\mu}dx^{\nu}} - \int A(x)_\mu dx^\mu - \int d^4x \frac{1}{4}F_{\mu\nu}(x)F^{\mu\nu}(x) $$

The first and second terms involve the object traversing the path $x_\mu(t)$ and the second and third terms involve the vector field $A_\mu(x)$ defined at all points in spacetime.  We have seen how the object behaves within this field.  How does the field behave in response to the obejct?

### The equations of motion of the vector field

As we've done twice before, we vary the action, but this time we vary it wrt $A_\mu(x)$ instead of wrt $x_\mu(t)$.

The first time above doesn't include $A_\mu(x)$ so it doesn't contribute.

The third time is:

$$ \delta \int d^4x -\frac{1}{4}F^{\mu\nu}(x)F_{\mu\nu}(x)$$
$$ = \int d^4x -\frac{1}{4}\delta \left(F^{\mu\nu}(x)F_{\mu\nu}(x)\right)$$
$$ = \int d^4x -\frac{1}{4}\left(2F^{\mu\nu}(x)\delta F_{\mu\nu}(x)\right)$$
$$ = \int d^4x -\frac{1}{4}\left(4F^{\mu\nu}(x)\partial_\mu\delta A_\nu(x)\right)$$
$$ = \int d^4x -F^{\mu\nu}(x)\partial_\mu\delta A_\nu(x)$$

And, integrating by parts again:

$$ = \int d^4x \left[\partial_\mu F^{\mu\nu}(x)\right]\delta A_\nu(x)$$

And, since this applies for any $\delta A_\nu(x)$, the term inside the $[...]$ must be 0.

So, if there were no interaction with any objects, the field's dynamics would be:

$$ \partial_\mu F^{\mu\nu} = 0 $$

Let's vary the second term as well though - representing the interaction.  We'll write it more precisely in terms of the actual path $X$ of the object, so that we can keep $x$ as a value that ranges over all of spacetime.

$$ \delta \int A(X)_\mu dX^\mu $$
$$ = \delta \int \left[  \int d^4x \delta^{(4)}(x - X) A_\mu(x) \right]dX^\mu $$
$$ = \delta \int d^4x \int \delta^{(4)}(x - X) A_\mu(x) dX^\mu $$
$$ = \int d^4x \int \delta^{(4)}(x - X) dX^\mu \delta A(x)_\mu  $$
$$ = \int d^4x J^{\mu}(x) A_\mu(x) $$

For $J^{\mu}(x) = \int \delta^{(4)}(x - X) dX^\mu$ which is a vector field that is non-zero only on the path of the object, and tangent to the path at all points.

**TODO**: Charge.

So, putting these two pieces together, when the field interacts with an object, we have:

$$ \partial_\mu F^{\mu\nu}(x) = - J^\nu(x) $$

### Maxwell's Equations

If we name $J_0 = \rho$ and the other terms $\vec{J}$, and use the previous breakdown of $F_{\mu\nu}$ as $\vec{E}$ and $\vec{B}$ then we have a few terms of this equation:

$$ \partial_i F^{i 0} = -\partial_i E^i = - \vec{\nabla} \cdot \vec{E} = - J^0  = -\rho$$

Or:

$$ \vec{\nabla} \cdot \vec{E} = \rho $$

**We've discovered one of Maxwell's equations - Gauss's Law.**

And:

$$ \partial_\mu F^{\mu 3} = \partial_0 F^{0 3} + \partial_1 F^{1 3} + \partial_2 F^{2 3} $$
$$ = \partial_0 E^3 - \partial_1 B^2 + \partial_2 B^1$$

Which if we complete for the other vector indices, generalizes into:

$$ \frac{\partial \vec{E}}{\partial t} - \vec{\nabla} \times \vec{B} = -\vec{J}$$

Or:

$$ \vec{\nabla} \times \vec{B} = \frac{\partial \vec{E}}{\partial t} + \vec{J}$$

**We've discovered another of Maxwell's equations - Ampere's Law.**

The other two Maxwell equations are actually even simpler, they are just identities that must be true because $F_{\mu\nu}$ is not just an arbitrary antisymmetric tensor, but is $F_{\mu\nu}(x(t)) =  \partial_\mu A_\nu(x(t)) - \partial_\nu A_\mu(x(t)) $.

**We discovered Maxwell's equations.**

This was of writing the equations of motion also implies current conservation, because $F_{\mu\nu} is antisymetric and partial derivatives commute):

$$ \partial_\mu F^{\mu\nu}(x) = - J^\nu(x) $$
$$ \partial_\nu \partial_\mu F^{\mu\nu}(x) = - \partial_\nu J^\nu(x) $$
$$ 0 = - \partial_\nu J^\nu(x) $$
$$ \partial_\nu J^\nu(x) = 0$$

We already knew that from the way we defined $J^\nu(x)$, but this reaffirms how much information is in these equations of motion.

### Summary of Part 2

By taking Lorentz symmetry seriously, we promoted the potential $V(x)$ to a vector potential $A_\mu(x)$, and discovered that it must interact with objects according to the Lorentz force law.

We then discovered a new symmetry, gauge invariance, in the action of the vector potential, and taking that seriously fixed the form of the action for the vector field $A_\mu(x)$ itself.  Solving the equations of motion for this fields, we discovered that its dynamics are those of the Maxwell equations.

As a result, these two assumptions that these symmetries are real lead to discovering all of the properties of electromagnetism.

**TODO**: Speed of light?

## Part 3: To Gravity

We started Part 2 by looking at this action and trying to make the second term Lorentz invariant:

$$ S =  - mc \int\sqrt{\eta_{\mu\nu}dx^{\mu}dx^{\nu}} - \int V dt $$

In Part 2, we did this by promoting $V$ to a Lorentz vector.

Instead of interpreting the potential as a vector potential, there's another way we could have incorporated it intot he action, which is to absorb it into the first term, underneath the square root.  We can do that with the action:

$$ S =  - mc \int\sqrt{g_{\mu\nu}(x)dx^{\mu}dx^{\nu}} $$

Where:

$$ g_{\mu\nu}(x) = \begin{pmatrix} 1 + \frac{2V(x)}{m}& 0 & 0 & 0 \cr 0 & -1 & 0 & 0 \cr 0 & 0 & -1 & 0 \cr 0 & 0 & 0 & -1 \end{pmatrix} $$

We could expand this out, and use the low velocity approximation twice, to see that it ends up introducing the $Vdt$ term we started with.

What if we again take this idea very seriously?  What if this $g_{\mu\nu}$ is actually the true metric of spacetime, and that $\eta_{\mu\nu}$ is just the low-order limit when this new potential is small.  What if the length of a veector is actually measured by $g_{\mu\nu}$.  Then everywhere we contract Lorentz indices, we must do so with $g_{\mu\nu}$.

This also means that spacetime is fundamentally curved.  Similar to how the surface of a sphere is a fundamentally curved 2-dimensional surface, spacetime itself is a fundamentally curved 4-dimenstional surface (unless $V = 0$).

###  Curved Spacetime

This introduces a few new concepts.  First, the potential is now the metric itself, and it is a tensor instead of a scalar or vector. Second, the metric which determines "distance" in spacetime is no longer a constant, and no longer the "flat" metric we discovered for special relativity above.  Instead, the metric depends on the potential, and is different at every point of space.  That means that spacetime is curved, and curved by the presence of this potential.

**We have discovered curved spacetime!**

Just like with the vector potential where we realized there could have been non-zero terms elsewhere in the vector, but that the time dimension would have been the only term that dominated at low velocity, similarly, here we see that $g_{\mu\nu}(x)$ could actually have non-constannt values in every position, but again for the low velocity case, the time-time value will dominate, and the perceived scalar potential will be $V(x) = \frac{m}{2}(g_{0 0}(x) - 1)$.  The only constraint is that only the symmetric part of $g_{\mu\nu}$ will matter because of how it is incoporated into the action, so we constrain our attention to $g_{\mu\nu}(x) = g_{\nu\mu}(x)$, which means 10 independent functions of spacetime.

### Motion of an object in curved spacetime

Whenever we have an action, we know that we can vary it to discover the equations of motion.  Let's try that with our new $S$.

$$ S =  - mc \int\sqrt{g_{\mu\nu}(x)dx^{\mu}dx^{\nu}} $$

Or, for an arbitrary parameter along the curve $x^\mu(\lambda)$:

$$ S =  - mc \int d\lambda \sqrt{g_{\mu\nu}(x)\frac{dx^{\mu}}{d\lambda}\frac{dx^{\nu}}{d\lambda}} $$

Verying it is different than it was when we had the metric $\eta_{\mu\nu}$ because now the metric depends on the path $x^\mu(t)$ that we are varying.

Varying it - and defining $L = \sqrt{g_{\mu\nu}(x)\frac{dx^{\mu}}{d\lambda}\frac{dx^{\nu}}{d\lambda}}$ we have:

$$ 0 =  \delta S $$
$$ = \int \frac{1}{L} \left[ -\frac{\partial g_{\alpha\beta}}{\partial^\delta}\delta x^\delta \frac{dx^{\alpha}}{d\lambda}\frac{dx^{\beta}}{d\lambda} -2g_{\alpha\beta} \frac{d\delta x^{\alpha}}{d\lambda}\frac{dx^{\beta}}{d\lambda} \right] d\lambda  $$

Integrating the second term by parts gives:

$$ 0 = \int \frac{1}{L} \delta x^\delta \left[ -\frac{\partial g_{\alpha\beta}}{\partial^\delta} \frac{dx^{\alpha}}{d\lambda}\frac{dx^{\beta}}{d\lambda} + 2\frac{d}{d\lambda}g_{\delta\beta}\frac{dx^{\beta}}{d\lambda} \right] d\lambda  $$

Since this must vanish for any $\delta x^\mu$, the piece inside the square brackets must be $0$.  Using the proper time $\tau$ instead of $\lambda$ we have:

$$ \frac{1}{2}\frac{\partial g_{\alpha\beta}}{\partial^\delta} \frac{dx^{\alpha}}{d\tau}\frac{dx^{\beta}}{d\tau} = \frac{d}{d\tau}g_{\delta\beta}\frac{dx^{\beta}}{d\tau}  $$

$$ \frac{1}{2}\frac{\partial g_{\alpha\beta}}{\partial^\delta} \frac{dx^{\alpha}}{d\tau}\frac{dx^{\beta}}{d\tau} = \frac{\partial g_{\delta\beta}}{\partial x^\delta} \frac{dx^\delta}{d\tau}\frac{dx^\beta}{d\tau} + g_{\delta\mu}\frac{d^2 x^\mu}{d\tau^2} $$

$$ \frac{d^2 x^\mu}{d\tau^2} =  g^{\delta\mu} \frac{1}{2}\frac{\partial g_{\alpha\beta}}{\partial x^\delta} \frac{dx^{\alpha}}{d\tau}\frac{dx^{\beta}}{d\tau} - g^{\delta\mu} \frac{\partial g_{\delta\beta}}{\partial x^\delta} \frac{dx^\delta}{d\tau}\frac{dx^\beta}{d\tau}  $$

$$ \frac{d^2 x^\mu}{d\tau^2} = \frac{1}{2}g^{\mu\delta} \left(\frac{\partial g_{\alpha\beta}}{\partial x^\delta}  -2 \frac{\partial g_{\delta\beta}}{\partial x^\alpha}    \right) \frac{dx^{\alpha}}{d\tau}\frac{dx^{\beta}}{d\tau} $$

$$ \frac{d^2 x^\mu}{d\tau^2} = \frac{1}{2}g^{\mu\delta} \left(\frac{\partial g_{\alpha\beta}}{\partial x^\delta}  - \frac{\partial g_{\delta\beta}}{\partial x^\alpha} - \frac{\partial g_{\beta\delta}}{\partial x^\alpha}    \right) \frac{dx^{\alpha}}{d\tau}\frac{dx^{\beta}}{d\tau} $$

$$ \frac{d^2 x^\mu}{d\tau^2} = \frac{1}{2}g^{\mu\delta} \left(\frac{\partial g_{\alpha\beta}}{\partial x^\delta}  - \frac{\partial g_{\delta\alpha}}{\partial x^\beta} - \frac{\partial g_{\beta\delta}}{\partial x^\alpha}    \right) \frac{dx^{\alpha}}{d\tau}\frac{dx^{\beta}}{d\tau} $$

$$ \frac{d^2 x^\mu}{d\tau^2} = -\Gamma^\mu_{\alpha\beta} \frac{dx^{\alpha}}{d\tau}\frac{dx^{\beta}}{d\tau} $$

For $ \Gamma^\mu_{\alpha\beta} = \frac{1}{2}g^{\mu\delta} \left(  \frac{\partial g_{\delta\alpha}}{\partial x^\beta} + \frac{\partial g_{\beta\delta}}{\partial x^\alpha} -\frac{\partial g_{\alpha\beta}}{\partial x^\delta}    \right)$, known as the Christoffel symbols.

This is again reminisent of $m\frac{d\vec{x}}{dt} = \vec{F}$ for the classical Newtonian scalar potential and $ m \frac{d^2x^{\mu}}{d\tau^2} = F^\mu_\nu \frac{dx^\nu}{d\tau} $ for the electromagnetic vector potential.  Here though, the acceleration is propotional to two factors of the velocity, and the potential is expressed as a tensor $ \Gamma^\mu_{\alpha\beta} $.

**We have discovered the Geodesic Equations.**

When $g_{\mu\nu} = \eta_{\mu\nu}$, that is there is no curvature, then these equations produce the idea that there is no accelration: $\frac{d^2 x^\mu}{d\tau^2} = 0 $.  But this is also true for other $g_{\mu\nu}$ which also represent flat spacetime (just in less obvious coordinate systems). However, for $g_{\mu\nu}$ which produce non-zero $ \Gamma^\mu_{\alpha\beta} $, object will feel acceleration due to the curvature of spacetime.  Note that this is not due to an external force or potential, the potential is actually now just part of the shape of spacetime which causes objects to accelerate as they "fall" within this curved spacetime.

### Curvature

The Geodesic equation above was derived in the coordinate system using the proper time $\tau$ of the object moving in the curved spacetime.  But for another observer, we would get a different tensor here.  However, there is a value we can derive from $ \Gamma^\mu_{\alpha\beta}$ that truly is a unique description of the curvature of the spacetime.

It's a little too involved to fully "discover" it here, but if we played around with curved spaces enough, we could discover that there is a unique tensor $R_{\mu\nu\delta\rho}$ we can build out of derivates of the metric $g_{\mu\nu}$ that encodes all of the information about the curvature.

$$ R^{\rho}_{\sigma\mu\nu} = \partial_\mu \Gamma^{\rho}_{\nu\sigma} - \partial_\nu \Gamma^{\rho}_{\mu\sigma} + \Gamma^{\rho}_{\mu\lambda}\Gamma^{\lambda}_{\nu\sigma} - \Gamma^{\rho}_{\nu\lambda}\Gamma^{\lambda}_{\mu\sigma} $$

This expresses how much two geodesics (paths $x^\mu(t)$ in curved spacetime that follow the geodesic equations which are "as straight as possible" in the curved spacetime) will accelerate toward each other, as well as measuring the change in a vector as it is translated around an infinitesimal loop in spacetime (since in a surved space, vectors do not stay pointing the same direction when moved around a loop).

**We've discovered the Riemann Curvature Tensor.**

If we try to contract inices by multipling by $g_{\alpha\beta}$ we find that there are a quite a few symmteries of $R^{\rho}_{\sigma\mu\nu}$ so tht many of the contractions are $0$.  All the non-zero contractions are the same up to a minus sign;

$$ R_{\mu\nu} = R^{\rho}_{\rho\mu\nu} $$

And similarly, we can contract again to form:

$$ R  = R^\mu_\mu $$

These are the Ricci tensor and scalar respectively.  These values are $0$ for flat space(time) and non-zero for curved spacetimes.

### Dynamics of the metric tensor

Just like we did in Part 2, we can ask whether there are constraints on the structure and dynamics of $g_{\mu\nu}$ beyond it being a symmetric tensor.  Similar to how we couldn't anwer that question directly for $A^\mu(x)$ due to its gauge invariance, we similarly can't answer directly in terms of $g_{\mu\nu}(x)$ due to it's overspecification of the geometry (many different $g$ define the same structure of the geometry, just with different coordinates).  We need a quantity which is "generally covriant", which means that it doesn't change under changes to the coordinates (as long as the gemoetry/shape of the space is unchanged).

Again, we are looking for a term satisfying

* It must contain two powers of the time derivative of $g_{\mu\nu}(x)$.
* It must be generally covariant.
* It must be a Lorentz scalar to be a term in the action.

It turns out we already have a quantity that meets these requirements - the Ricci scalar $R$.  It contains two powers of the derivatives of $g_{\mu\nu}(x)$ because it contains two powers of the Christoffel symbol which is built out of derivates fo the metric.  It is generally covariant because it captures the curvature of the space independent of the coordinates used for the space.  And it is a Lorentz scalar quantity.

And this is almost the full answer, except that to integrate this over spacetime for the action, we can't just use $d^4 x$ because that isn't Lorentz invaraint.  Instead, we must use $\sqrt{-g} d^4x$ as the integration measure where $g = det(g_{\mu\nu}(x))$ which is negative.  For flat spacetime,  $\sqrt{-g} = 1$ so this term is not needed, but for general $g_{\mu\nu}$ it is needed to ensure a Lorentz invariant integral.

The result is we can add a term to our action:

$$ S \sim  \int R \sqrt{-g} d^4x $$

**We've discovered the Einstien-Hilbert Action.**

## Einstein Field Equations

We know what to do when we find a new term in our action - we vary it!

This one is even more messy than the variation of the vector potential action to get to Maxwell's equations.  But if we work through it in full, we get the following:

TODO: Not done...


<!--
# OLD

Thie section contains some alterantive derivations, not yet complete.

### Motion of an object in curved spacetime

Given that there is no external force/potential, and that instead we have changed the shape of spacetime, we expect that relative to this new coordinates, on object does not accelerate.

$$ \frac{d^2 X^\mu}{dT^2} = 0$$

Where $X^\mu$ is the spacetime position of the object, and $T = X_0$.  This says that the object itself perceived no acceleration (and hence no force) in it's own local coordinates.

With this - we can do a few lines of algebra to get:

$$ \frac{dX^\mu}{dT} = \frac{dx^\nu}{dT}\frac{\partial X^\mu}{\partial x^\nu} $$
$$ \frac{d^2 X^\mu}{dT^2} = \frac{d^2 x^\nu}{dT^2}\frac{\partial X^\mu}{\partial x^\nu} + \frac{dx^\nu}{dT}\frac{dx^\alpha}{dT}\frac{\partial^2 X^\mu}{\partial x^\nu\partial x^\alpha} $$
$$ 0 = \frac{d^2 x^\nu}{dT^2}\frac{\partial X^\mu}{\partial x^\nu} + \frac{dx^\nu}{dT}\frac{dx^\alpha}{dT}\frac{\partial^2 X^\mu}{\partial x^\nu\partial x^\alpha} $$
$$ \frac{d^2 x^\nu}{dT^2}\frac{\partial X^\mu}{\partial x^\nu} = - \frac{dx^\nu}{dT}\frac{dx^\alpha}{dT}\frac{\partial^2 X^\mu}{\partial x^\nu\partial x^\alpha} $$
$$ \frac{d^2 x^\lambda}{dT^2} = - \frac{dx^\nu}{dT}\frac{dx^\alpha}{dT}\left[\frac{\partial^2 X^\mu}{\partial x^\nu\partial x^\alpha}\frac{\partial x^\lambda}{\partial X^\mu} \right]$$

Calling the term in square brackets $\Gamma^\lambda_{\nu\alpha} = \frac{\partial^2 X^\mu}{\partial x^\nu\partial x^\alpha}\frac{\partial x^\lambda}{\partial X^\mu}$ we get:

$$ \frac{d^2 x^\lambda}{dT^2} = - \Gamma^\lambda_{\nu\alpha} \frac{dx^\nu}{dT}\frac{dx^\alpha}{dT}$$

-->