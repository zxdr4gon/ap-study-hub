# AP Physics C: Mechanics — Complete Mastery Guide

> **Target: Score 5 | Based on Latest College Board CED**
> This guide assumes calculus fluency. Every concept is treated at the depth required for full FRQ credit.

---

# Unit 1: Kinematics

## 1. Core Concepts

**Kinematics** describes *how* objects move without asking *why*. The foundational insight is that position, velocity, and acceleration are not independent — they are linked by the operations of differentiation and integration.

**1D Motion** is fully described by three kinematic quantities:
- **Position** $x(t)$: where the object is
- **Velocity** $v(t)$: rate of change of position
- **Acceleration** $a(t)$: rate of change of velocity

The constant-acceleration equations (the "Big Four") are special cases derived by integrating constant $a$.

**2D Motion** (including **projectile motion**) treats horizontal and vertical components as *completely independent* 1D problems sharing only time as a common variable. There is no horizontal acceleration (assuming no air resistance), and vertical acceleration is always $-g$.

**Relative motion** requires careful vector addition: $\vec{v}_{A/C} = \vec{v}_{A/B} + \vec{v}_{B/C}$.

---

## 2. The Calculus Connection

This is the heart of the AP Physics C approach.

$$\boxed{a(t) = \frac{dv}{dt} = \frac{d^2x}{dt^2}}$$

Reading this in both directions gives you the two fundamental tools:

**Differentiation (position → velocity → acceleration):**

$$v(t) = \frac{dx}{dt}, \qquad a(t) = \frac{dv}{dt}$$

**Integration (acceleration → velocity → position):**

$$v(t) = v_0 + \int_{t_0}^{t} a(t')\, dt'$$

$$x(t) = x_0 + \int_{t_0}^{t} v(t')\, dt'$$

**The Chain Rule form** — used when $a$ is given as a function of position:

$$a = \frac{dv}{dt} = \frac{dv}{dx}\cdot\frac{dx}{dt} = v\frac{dv}{dx}$$

This is critical for problems like "a particle subject to a position-dependent force."

**Geometric interpretation:** On a $v$-$t$ graph, displacement = area under the curve. On an $a$-$t$ graph, $\Delta v$ = area under the curve.

**Projectile Motion in component form:**

$$x(t) = x_0 + v_{0x}t, \qquad y(t) = y_0 + v_{0y}t - \frac{1}{2}gt^2$$

$$v_x(t) = v_{0x} = \text{const}, \qquad v_y(t) = v_{0y} - gt$$

---

## 3. Essential Formulas

**On the formula sheet (constant acceleration only):**

$$v = v_0 + at$$

$$x = x_0 + v_0 t + \frac{1}{2}at^2$$

$$v^2 = v_0^2 + 2a\Delta x$$

**Derived / Not on sheet:**

| Formula | When to Use |
|---|---|
| $a = v\dfrac{dv}{dx}$ | $a$ given as $f(x)$; separable ODE |
| $\Delta x = \dfrac{v^2 - v_0^2}{2a}$ | Eliminates $t$ |
| $t_{flight} = \dfrac{2v_0\sin\theta}{g}$ | Symmetric projectile |
| $R = \dfrac{v_0^2 \sin 2\theta}{g}$ | Range on flat ground |
| $H_{max} = \dfrac{v_0^2 \sin^2\theta}{2g}$ | Maximum height |
| $|\vec{v}| = \sqrt{v_x^2 + v_y^2}$ | Speed from components |

---

## 4. Free-Response Strategy

**Common FRQ Scenarios:**

- **Given $x(t)$ or $v(t)$ as a polynomial or sinusoid** → differentiate to find $v$ and $a$; evaluate at a specific time; find when $v = 0$ to locate extrema of $x$.
- **Given $a(t)$ as a graph** → integrate graphically (area under curve) to find $\Delta v$, then $\Delta x$.
- **Given $a(v)$** (e.g., drag force problems before Unit 2) → use separation of variables: $\frac{dv}{a(v)} = dt$, integrate both sides.
- **Projectile launched from a height $h$** → set $y(t) = 0$ and use the quadratic formula; do not assume symmetric flight.
- **Two-object problems** → write separate kinematic equations, link by a shared condition (collision time, same position, etc.).

**FRQ Writing Tips:**
- Always define your coordinate system explicitly.
- Show the integral setup even if you can evaluate it quickly — scorers award setup points.
- Label the initial and final limits of all integrals.

---

## 5. The "Trap" List

- **Confusing $v = 0$ with $a = 0$.** An object at its highest point has zero velocity but full gravitational acceleration $g$ downward. These are independent.
- **Using "Big Four" when $a$ is not constant.** If $a = f(t)$ or $a = f(x)$, you *must* integrate — the constant-acceleration equations are invalid.
- **Sign errors in 2D projectile motion.** If you define upward as positive, then $a_y = -g = -9.8\ \text{m/s}^2$. Be consistent throughout.
- **Forgetting $x_0$ or $v_0$ after integration.** When integrating $a(t)$, the constant of integration is $v_0$, not zero (unless stated).
- **Range formula applicability.** $R = v_0^2\sin 2\theta / g$ only applies when the launch and landing heights are equal.
- **Speed vs. velocity.** Speed is a scalar ($|\vec{v}|$); velocity is a vector. "The speed is increasing" requires checking if $\vec{v}$ and $\vec{a}$ point in the same direction.

---

---

# Unit 2: Newton's Laws of Motion

## 1. Core Concepts

Newton's Laws are the engine of classical mechanics.

- **First Law (Inertia):** An object remains in constant velocity unless acted on by a net external force. Defines the concept of an **inertial reference frame**.
- **Second Law:** $\vec{F}_{net} = m\vec{a}$. For AP Physics C, this is often a *differential equation* when force depends on $v$ or $x$.
- **Third Law:** Forces come in equal-and-opposite action-reaction pairs acting on *different* objects. Never include both members of a pair in a single free-body diagram.

**System analysis** requires:
1. Identifying the system boundary.
2. Drawing a complete **Free-Body Diagram (FBD)** with all external forces.
3. Choosing a convenient coordinate system aligned with acceleration.

**Circular Motion:** For any object moving in a circle, the net force directed toward the center (the **centripetal force**) equals $mv^2/r$. This is *not* a new force — it is the *role* played by existing forces (tension, gravity, normal force, friction).

**Drag Forces and Terminal Velocity** introduce the concept of velocity-dependent forces, leading to solvable differential equations.

---

## 2. The Calculus Connection

**Linear drag (Stokes drag, proportional to $v$):**

Newton's second law for a falling object with linear drag (taking downward as positive):

$$m\frac{dv}{dt} = mg - bv$$

This is a **first-order linear ODE**. Separate variables:

$$\frac{dv}{mg - bv} = \frac{dt}{m}$$

Integrating both sides:

$$-\frac{1}{b}\ln(mg - bv) = \frac{t}{m} + C$$

Applying the initial condition $v(0) = 0$:

$$\boxed{v(t) = v_T\left(1 - e^{-t/\tau}\right)}, \qquad v_T = \frac{mg}{b}, \quad \tau = \frac{m}{b}$$

As $t \to \infty$, $v \to v_T$ — **terminal velocity**.

**Quadratic drag** ($F_{drag} = cv^2$): Terminal velocity found by setting net force to zero:

$$mg = cv_T^2 \implies v_T = \sqrt{\frac{mg}{c}}$$

The ODE is nonlinear and not typically solved in full on the exam, but terminal velocity and the qualitative shape of $v(t)$ are required.

**Circular motion — calculus form:** For a particle in circular motion, expressing velocity in Cartesian components and differentiating reveals:
- **Centripetal acceleration:** $a_c = \frac{v^2}{r}$ (directed inward)
- **Tangential acceleration:** $a_t = \frac{dv}{dt}$ (along the velocity)
- Total acceleration: $|\vec{a}| = \sqrt{a_c^2 + a_t^2}$

---

## 3. Essential Formulas

**On the sheet:**

$$\vec{F}_{net} = m\vec{a}, \qquad f_k = \mu_k N, \qquad f_{s,max} = \mu_s N$$

$$a_c = \frac{v^2}{r}$$

**Derived / Not on sheet:**

| Formula | Derivation/Use |
|---|---|
| $v_T = mg/b$ | Linear drag: set $ma = 0$ |
| $v_T = \sqrt{mg/c}$ | Quadratic drag: set $ma = 0$ |
| $v(t) = v_T(1-e^{-bt/m})$ | Linear drag ODE solution |
| $T = mg + mv^2/r$ | Tension at bottom of vertical circle |
| $T = mv^2/r - mg$ | Tension at top of vertical circle |
| $v_{min} = \sqrt{rg}$ | Minimum speed at top for contact |
| $\tan\theta = v^2/(rg)$ | Banking angle (frictionless banked turn) |

---

## 4. Free-Response Strategy

**Common FRQ Scenarios:**

- **Atwood Machine variants:** Two masses over a pulley. Draw separate FBDs. The tension is the same throughout a massless, frictionless string. Write $F = ma$ for each object; add equations to eliminate $T$.
- **Block on inclined plane with friction:** Resolve forces along and perpendicular to the incline. $a = g(\sin\theta - \mu_k\cos\theta)$.
- **Vertical circular motion** (ball on a string): Analyze forces at the top and bottom separately. At the top, both $T$ and $mg$ point inward; at the bottom, $T$ points inward and $mg$ points outward.
- **Terminal velocity ODE:** You will likely be asked to (a) write the differential equation, (b) solve it or verify a given solution, (c) sketch $v(t)$, and (d) find $v_T$.
- **Car rounding a banked curve:** Set up $\sum F_y = 0$ (vertical) and $\sum F_x = mv^2/r$ (horizontal). Solve simultaneously.

**FRQ Writing Tips:**
- In circular motion, *always* write the centripetal direction equation explicitly: $F_{net,\text{inward}} = mv^2/r$.
- For ODE problems, show the separation of variables step explicitly.
- Sketch $v(t)$ for drag problems: starts at $v_0$, asymptotically approaches $v_T$ — never exceeds it.

---

## 5. The "Trap" List

- **"Centrifugal force" does not exist** in an inertial frame. Never draw it on a FBD. The sensation of being "pushed outward" is inertia, not a force.
- **Confusing centripetal force with a separate force.** On the FBD, there is no arrow labeled "centripetal force." It is the *net resultant* of real forces in the inward direction.
- **Static friction isn't always $\mu_s N$.** That value is the *maximum*. Static friction can be any value from zero up to $\mu_s N$.
- **Third-law partner forces act on different objects.** If the floor pushes up on you (normal force), you push down on the floor. Neither belongs on the other's FBD.
- **Sign error in drag equations.** Drag *always opposes* motion. If velocity is positive (upward), drag is negative (downward). If falling, drag is upward. The sign must be consistent with your chosen positive direction.
- **Assuming $a = 0$ at terminal velocity but still using kinematic equations.** At terminal velocity, $a = 0$, so $v = v_T = $ constant. Use $d = v_T \cdot t$ for subsequent distance calculations.

---

---

# Unit 3: Work, Energy, and Power

## 1. Core Concepts

The **Work-Energy Theorem** provides an alternative to Newton's Laws — often far more powerful for problems involving curved paths, springs, or varying forces.

**Work** is the transfer of energy by a force through a displacement. For a constant force: $W = Fd\cos\theta$. For a variable force, integration is required.

The **Work-Energy Theorem:** The net work done on an object equals its change in kinetic energy:

$$W_{net} = \Delta K = \frac{1}{2}mv_f^2 - \frac{1}{2}mv_i^2$$

**Conservative forces** (gravity, spring force, gravity) have a potential energy function $U(x)$ associated with them and do zero net work around any closed path.

**Non-conservative forces** (friction, drag, applied forces) do not have a potential energy function. Their work removes mechanical energy from the system (usually as heat).

**Conservation of Mechanical Energy** holds when *only* conservative forces do work:

$$K_i + U_i = K_f + U_f$$

When non-conservative forces are present: $\Delta E_{mech} = W_{nc}$.

**Power** is the rate of energy transfer: $P = dW/dt$.

---

## 2. The Calculus Connection

**Work as a line integral** — the most important calculus concept in this unit:

$$W = \int_{\vec{r}_i}^{\vec{r}_f} \vec{F} \cdot d\vec{r} = \int_{x_i}^{x_f} F_x\, dx + \int_{y_i}^{y_f} F_y\, dy$$

In 1D with a force $F(x)$:

$$\boxed{W = \int_{x_i}^{x_f} F(x)\, dx}$$

Geometrically, this is the area under the $F$ vs. $x$ curve.

**Deriving potential energy from force** (conservative forces only):

$$U(x) = -\int_{x_{ref}}^{x} F(x')\, dx' \quad \Longleftrightarrow \quad F(x) = -\frac{dU}{dx}$$

This bidirectional relationship is central to the entire unit:

- **Spring:** $F = -kx \Rightarrow U = \frac{1}{2}kx^2$
- **Gravity (near surface):** $F = -mg \Rightarrow U = mgy$ (taking $y=0$ as reference)
- **Universal gravity:** $F = -\frac{GMm}{r^2} \Rightarrow U = -\frac{GMm}{r}$ (reference at $\infty$)

**Equilibrium and stability from $U(x)$:**

- **Equilibrium:** $\frac{dU}{dx} = 0$ (net force is zero)
- **Stable equilibrium:** $\frac{d^2U}{dx^2} > 0$ (minimum of $U$)
- **Unstable equilibrium:** $\frac{d^2U}{dx^2} < 0$ (maximum of $U$)

**Power:**

$$P = \frac{dW}{dt} = \vec{F} \cdot \vec{v}$$

---

## 3. Essential Formulas

**On the sheet:**

$$W = \int \vec{F} \cdot d\vec{r}, \qquad K = \frac{1}{2}mv^2, \qquad P = \frac{dW}{dt} = \vec{F}\cdot\vec{v}$$

$$U_g = mgy, \qquad U_s = \frac{1}{2}kx^2, \qquad W_{spring} = -\frac{1}{2}k(\Delta x)^2$$

**Derived / Not on sheet:**

| Formula | Source |
|---|---|
| $F(x) = -dU/dx$ | Fundamental relation |
| $E_{mech} = K + U = \text{const}$ | Conservative systems |
| $W_{nc} = \Delta K + \Delta U = \Delta E_{mech}$ | Non-conservative work |
| $W_{nc} = -f_k d$ (friction) | Energy lost to friction |
| Average power: $\bar{P} = W/\Delta t$ | Definition |
| $v_{escape} = \sqrt{2GM/R}$ | From $K + U_{grav} = 0$ |

---

## 4. Free-Response Strategy

**Common FRQ Scenarios:**

- **Force given as $F(x)$, find work over an interval:** Set up and evaluate $\int_{x_i}^{x_f} F(x)\, dx$. If $F(x)$ is given graphically, compute the area under the curve (triangles, rectangles, or trapezoids).
- **Energy conservation with a spring:** $\frac{1}{2}mv^2 + \frac{1}{2}kx^2 = E_0$. Solve for velocity at any compression/extension.
- **Potential energy function given; find equilibrium points:** Set $dU/dx = 0$; then check $d^2U/dx^2$ for stability.
- **Block on a rough incline — energy method:** $W_{friction} = -\mu_k mg\cos\theta \cdot d$ (negative, removes energy). Apply $E_{mech,f} = E_{mech,i} + W_{nc}$.
- **Power of a motor or engine:** $P = Fv$; at constant speed, $F$ equals all resistive forces.

**FRQ Writing Tips:**
- When using energy conservation, write out $K_i + U_i + W_{nc} = K_f + U_f$ explicitly before substituting numbers.
- Specify your zero-reference point for $U_g$.
- When finding $F$ from $U$: take the negative derivative, not the positive derivative.

---

## 5. The "Trap" List

- **Forgetting the negative sign: $F = -dU/dx$.** This is the single most common error in energy problems. The force points in the direction of *decreasing* potential energy.
- **Work done by a spring is NOT always $\frac{1}{2}kx^2$.** Work done by a spring is $W_{spring} = -\Delta U_s = -\left(\frac{1}{2}kx_f^2 - \frac{1}{2}kx_i^2\right)$. If both $x_i \neq 0$ and $x_f \neq 0$, use the full expression.
- **Friction is not a conservative force.** You cannot define a potential energy for friction. Always use $W_{nc} = \Delta E_{mech}$.
- **Normal force and gravity (perpendicular) do no work** on an object moving horizontally — they are perpendicular to displacement. $W = Fd\cos 90° = 0$.
- **Potential energy is defined for the system, not a single object.** Gravitational PE belongs to the Earth-object system.
- **$P = Fv$ requires $F \parallel v$.** In general, $P = \vec{F}\cdot\vec{v} = Fv\cos\theta$. Don't forget the angle if force and velocity are not parallel.

---

---

# Unit 4: Systems of Particles and Linear Momentum

## 1. Core Concepts

Shifting from single particles to **systems** introduces two powerful new quantities: **center of mass (CM)** and **linear momentum**.

The **center of mass** is the unique point that moves as if all external forces were applied there:

$$M\vec{a}_{CM} = \vec{F}_{net,ext}$$

Internal forces (between particles in the system) cancel by Newton's Third Law and do not affect the CM motion.

**Linear momentum:** $\vec{p} = m\vec{v}$. Newton's Second Law in its most general form:

$$\vec{F}_{net} = \frac{d\vec{p}}{dt}$$

This reduces to $\vec{F} = m\vec{a}$ only when $m$ is constant.

**Impulse:** The change in momentum caused by a force over time:

$$\vec{J} = \Delta\vec{p} = \int \vec{F}\, dt$$

**Conservation of Momentum:** When $\vec{F}_{net,ext} = 0$, $\vec{p}_{total}$ is conserved. This is the go-to tool for collisions.

**Collisions:**
- **Elastic:** Both $\vec{p}$ and $K$ are conserved.
- **Perfectly inelastic:** $\vec{p}$ conserved, objects stick together, $K$ is *not* conserved (some is lost to deformation/heat).
- **Inelastic:** $\vec{p}$ conserved, $K$ not fully conserved.

**Variable-mass systems** (rockets) require special treatment since $m$ changes with time.

---

## 2. The Calculus Connection

**Center of mass (continuous mass distribution):**

$$\vec{r}_{CM} = \frac{1}{M}\int \vec{r}\, dm$$

In 1D:

$$x_{CM} = \frac{1}{M}\int x\, dm$$

To evaluate, express $dm$ in terms of a spatial variable using the linear mass density $\lambda = dm/dx$, area density $\sigma = dm/dA$, or volume density $\rho = dm/dV$:

$$x_{CM} = \frac{1}{M}\int x\, \lambda(x)\, dx$$

**Momentum and impulse as integrals:**

$$\vec{J} = \int_{t_i}^{t_f} \vec{F}(t)\, dt = \Delta\vec{p}$$

If $F(t)$ is given graphically, $J$ = area under the $F$-$t$ curve.

**Rocket equation (variable mass):** Let $M(t)$ be the rocket mass and $v_{rel}$ the exhaust speed relative to the rocket. Applying momentum conservation to an infinitesimal time step:

$$M\frac{dv}{dt} = -v_{rel}\frac{dM}{dt} + F_{ext}$$

$$\boxed{F_{thrust} = -v_{rel}\frac{dM}{dt}}$$

In free space ($F_{ext} = 0$), integrating gives the **Tsiolkovsky rocket equation:**

$$\Delta v = v_{rel}\ln\left(\frac{M_i}{M_f}\right)$$

---

## 3. Essential Formulas

**On the sheet:**

$$\vec{p} = m\vec{v}, \qquad \vec{J} = \int \vec{F}\, dt = \Delta\vec{p}$$

$$x_{CM} = \frac{\sum m_i x_i}{\sum m_i}, \qquad \vec{r}_{CM} = \frac{1}{M}\int \vec{r}\, dm$$

**Derived / Not on sheet:**

| Formula | Context |
|---|---|
| $M\vec{a}_{CM} = \vec{F}_{net,ext}$ | System dynamics |
| $v_{1f} = \frac{m_1 - m_2}{m_1+m_2}v_{1i}$ | Elastic collision (target at rest) |
| $v_{2f} = \frac{2m_1}{m_1+m_2}v_{1i}$ | Elastic collision (target at rest) |
| $v_f = \frac{m_1 v_{1i} + m_2 v_{2i}}{m_1 + m_2}$ | Perfectly inelastic collision |
| $\Delta K = K_f - K_i$ | Energy lost (verify sign is negative) |
| $F_{thrust} = v_{rel}\left\|\frac{dM}{dt}\right\|$ | Rocket thrust |

---

## 4. Free-Response Strategy

**Common FRQ Scenarios:**

- **Ballistic pendulum:** Bullet embeds in block (perfectly inelastic, momentum conserved), block swings up (energy conserved). Two-stage problem — use the right tool at each stage.
- **Explosion problems:** Object initially at rest explodes into two pieces. $p_{total} = 0$, so $m_1v_1 = -m_2v_2$ (they go in opposite directions). Kinetic energy is *created* (from chemical energy).
- **CM of a rod or plate with non-uniform density:** Set up $x_{CM} = \frac{1}{M}\int x\,\lambda(x)\, dx$ where $\lambda(x)$ may be linear or polynomial. Integrate carefully.
- **Impulse from a force-time graph:** Compute the area geometrically (triangle, trapezoid). State $\Delta\vec{p} = J$ and find the final velocity.
- **2D collision:** Conserve $p_x$ and $p_y$ separately. Set up two equations; solve for unknowns.

**FRQ Writing Tips:**
- For collisions, explicitly state which conservation law applies and *why* (e.g., "no net external horizontal force, therefore horizontal momentum is conserved").
- For ballistic pendulum, clearly break the problem into Stage 1 (collision) and Stage 2 (swing).
- Don't use energy conservation during the collision phase of a perfectly inelastic collision.

---

## 5. The "Trap" List

- **Using energy conservation during a perfectly inelastic collision.** You *cannot*. Energy is lost. Use momentum conservation only for the collision itself.
- **Forgetting that elastic collision formulas require the target to be at rest.** The standard $v_{1f}$, $v_{2f}$ formulas are derived for $v_{2i} = 0$. If both objects are moving, re-derive from $p$ and $K$ conservation simultaneously.
- **Center of mass ≠ center of geometry.** For non-uniform density objects, the CM is shifted toward the denser region.
- **Internal forces do not affect the CM motion or total momentum.** In an explosion, the total momentum before and after is the same — only external forces change total $\vec{p}$.
- **Impulse direction.** The impulse vector points in the direction of $\Delta\vec{p}$, not necessarily in the direction of motion. For a ball bouncing off a wall, $\vec{J}$ points away from the wall.
- **Vector nature of momentum in 2D.** You cannot add momenta as scalars in 2D. Always resolve into components before applying conservation.

---

---

# Unit 5: Rotation

## 1. Core Concepts

Rotational mechanics is the most formula-dense unit and the most heavily tested on FRQs. The key insight is the **perfect analogy** between linear and rotational quantities:

| Linear | Rotational |
|---|---|
| $x$ (position) | $\theta$ (angle) |
| $v$ (velocity) | $\omega$ (angular velocity) |
| $a$ (acceleration) | $\alpha$ (angular acceleration) |
| $m$ (mass) | $I$ (moment of inertia) |
| $F$ (force) | $\tau$ (torque) |
| $p = mv$ | $L = I\omega$ |
| $K = \frac{1}{2}mv^2$ | $K_{rot} = \frac{1}{2}I\omega^2$ |

**Torque:** $\vec{\tau} = \vec{r} \times \vec{F}$. Magnitude: $\tau = rF\sin\theta = F\cdot\ell_\perp$ where $\ell_\perp$ is the moment arm (perpendicular distance from the pivot to the line of action of the force).

**Moment of Inertia** $I$ is the rotational analog of mass. It depends on *both* the mass distribution *and* the choice of rotation axis.

**Rolling without slipping** links linear and rotational motion: $v_{CM} = R\omega$, $a_{CM} = R\alpha$.

**Angular Momentum:** $\vec{L} = \vec{r} \times \vec{p}$ for a particle; $L = I\omega$ for a rigid body. Conserved when net external torque is zero.

---

## 2. The Calculus Connection

**Moment of inertia as an integral** — the defining calculus skill of this unit:

$$\boxed{I = \int r^2\, dm}$$

where $r$ is the perpendicular distance from each mass element $dm$ to the rotation axis. To evaluate, express $dm$ using mass density:

$$dm = \lambda\, dr \quad\text{(rod)}, \qquad dm = \sigma\, dA \quad\text{(plate)}, \qquad dm = \rho\, dV \quad\text{(solid)}$$

**Example: Solid rod of length $L$, mass $M$, rotating about one end:**

$$I = \int_0^L r^2\, \lambda\, dr = \frac{M}{L}\int_0^L r^2\, dr = \frac{M}{L}\cdot\frac{L^3}{3} = \frac{1}{3}ML^2$$

**Parallel Axis Theorem** (not derived from scratch on exam, but used constantly):

$$\boxed{I = I_{CM} + Md^2}$$

where $d$ is the distance from the CM axis to the new axis.

**Rotational analog of Newton's Second Law:**

$$\vec{\tau}_{net} = I\vec{\alpha} = I\frac{d\omega}{dt} = \frac{d\vec{L}}{dt}$$

**Angular momentum for a system:**

$$\vec{L}_{total} = \sum \vec{L}_i = \sum \vec{r}_i \times \vec{p}_i$$

If $\tau_{net,ext} = 0$, then $L = $ constant.

**Rolling without slipping — kinetic energy:**

$$K_{total} = K_{trans} + K_{rot} = \frac{1}{2}Mv_{CM}^2 + \frac{1}{2}I_{CM}\omega^2 = \frac{1}{2}\left(M + \frac{I_{CM}}{R^2}\right)v_{CM}^2$$

---

## 3. Essential Formulas

**On the sheet:**

$$\tau = r\times F,\quad I = \int r^2\,dm,\quad \tau_{net} = I\alpha,\quad L = I\omega = r\times p$$

$$K_{rot} = \frac{1}{2}I\omega^2,\quad I_{parallel} = I_{CM} + Md^2$$

$$v = R\omega,\quad a = R\alpha \quad\text{(rolling without slipping)}$$

**Standard moments of inertia (memorize — not all on sheet):**

| Object | Axis | $I$ |
|---|---|---|
| Point mass | Any | $mR^2$ |
| Thin rod | Center, $\perp$ | $\frac{1}{12}ML^2$ |
| Thin rod | End, $\perp$ | $\frac{1}{3}ML^2$ |
| Solid sphere | Diameter | $\frac{2}{5}MR^2$ |
| Hollow sphere | Diameter | $\frac{2}{3}MR^2$ |
| Solid cylinder/disk | Central axis | $\frac{1}{2}MR^2$ |
| Hollow cylinder | Central axis | $MR^2$ |
| Rectangular plate | CM, $\perp$ | $\frac{1}{12}M(a^2+b^2)$ |

**Derived / Not on sheet:**

| Formula | Context |
|---|---|
| $\ell_\perp = r\sin\theta$ | Moment arm |
| $W_{rot} = \int \tau\, d\theta$ | Rotational work |
| $P_{rot} = \tau\omega$ | Rotational power |
| $\tau_{net} = \frac{dL}{dt}$ | Most general rotational law |

---

## 4. Free-Response Strategy

**Common FRQ Scenarios:**

- **Object rolling down an incline:** Use energy conservation: $mgh = \frac{1}{2}mv^2 + \frac{1}{2}I\omega^2$. Substitute $\omega = v/R$ and solve for $v$ at the bottom. For acceleration, use Newton's Second Law + torque equation: friction provides the torque; $f = \frac{I\alpha}{R}$, combined with $mg\sin\theta - f = ma_{CM}$.
- **Atwood machine with massive pulley:** The pulley has moment of inertia $I$ and angular acceleration $\alpha = a/R$. The tensions on either side of the pulley are *not equal*. Write three equations: $m_1g - T_1 = m_1a$, $T_2 - m_2g = m_2a$, $(T_1 - T_2)R = I\alpha$.
- **Conservation of angular momentum (skater problem):** $I_1\omega_1 = I_2\omega_2$. Show explicitly that external torque is zero (why momentum is conserved).
- **Moment of inertia integral (derivation):** Set up $dm = \lambda dr$ or $\rho dV$, write $I = \int r^2 dm$, integrate with explicit limits, substitute $\lambda = M/L$.
- **Torque on a rod/beam (static equilibrium):** $\sum\tau = 0$ about a smartly chosen pivot that eliminates an unknown force; $\sum F = 0$.

**FRQ Writing Tips:**
- When applying rolling without slipping, state $v_{CM} = R\omega$ and $a_{CM} = R\alpha$ explicitly.
- For Atwood with pulley, draw three separate free-body diagrams (each mass + the pulley).
- Choose your torque pivot to eliminate unknown forces from the equation whenever possible.

---

## 5. The "Trap" List

- **Tensions in the Atwood pulley are NOT equal** when the pulley has mass/inertia. A common mistake is setting $T_1 = T_2$, which makes the pulley irrelevant.
- **Moment arm is $r\sin\theta$, not $r$.** If the force is not perpendicular to the radius vector, you must use the perpendicular component.
- **Rolling without slipping requires static friction,** which does *no work* (contact point is instantaneously at rest). Don't include friction work in energy conservation for rolling problems.
- **$I$ depends on the axis.** Forgetting to apply the Parallel Axis Theorem when the axis is not at the CM is a very common error. $I_{CM}$ is the *minimum* moment of inertia for any axis parallel to the CM axis.
- **Angular momentum is conserved only when $\tau_{net,ext} = 0$**, not when $F_{net,ext} = 0$. A net force with zero torque (force through the pivot) doesn't affect $L$.
- **Confusing $\vec{L} = I\vec{\omega}$ with $\vec{L} = \vec{r} \times \vec{p}$.** The first applies to rigid bodies rotating about a principal axis; the second is more general (particles, non-principal axes).

---

---

# Unit 6: Oscillations

## 1. Core Concepts

**Simple Harmonic Motion (SHM)** occurs whenever the restoring force is *directly proportional and opposite to displacement* from equilibrium:

$$\vec{F}_{restore} = -kx \quad\text{(Hooke's Law form)}$$

This produces sinusoidal motion. The defining condition for SHM is this linear restoring force.

**Key parameters:**
- **Amplitude $A$:** Maximum displacement from equilibrium.
- **Angular frequency $\omega$:** How fast the oscillation occurs (rad/s).
- **Period $T = 2\pi/\omega$:** Time for one complete cycle.
- **Frequency $f = 1/T = \omega/2\pi$:** Cycles per second.

**Mass-spring system:** $\omega = \sqrt{k/m}$, so $T = 2\pi\sqrt{m/k}$.

**Simple pendulum** (small angle): $\omega = \sqrt{g/L}$, so $T = 2\pi\sqrt{L/g}$.

**Physical pendulum** (extended object): $\omega = \sqrt{\tau_{net}/I\theta} = \sqrt{MgL_{CM}/I}$ where $L_{CM}$ is the distance from pivot to CM.

**Energy in SHM** oscillates between purely kinetic (at equilibrium) and purely potential (at amplitude), with total mechanical energy conserved:

$$E = \frac{1}{2}kA^2 = \frac{1}{2}mv_{max}^2 = K + U$$

---

## 2. The Calculus Connection

**Deriving SHM from Newton's Second Law:**

For a mass-spring system, $F = -kx$ and $F = ma = m\ddot{x}$:

$$m\frac{d^2x}{dt^2} = -kx$$

$$\frac{d^2x}{dt^2} = -\frac{k}{m}x = -\omega^2 x, \qquad \omega = \sqrt{\frac{k}{m}}$$

This is the **SHM differential equation.** Its general solution is:

$$\boxed{x(t) = A\cos(\omega t + \phi)}$$

where $A$ and $\phi$ are set by initial conditions.

**Velocity and acceleration by differentiation:**

$$v(t) = \frac{dx}{dt} = -A\omega\sin(\omega t + \phi)$$

$$a(t) = \frac{d^2x}{dt^2} = -A\omega^2\cos(\omega t + \phi) = -\omega^2 x(t)$$

**Maximum values:**

$$v_{max} = A\omega, \qquad a_{max} = A\omega^2$$

**Velocity as a function of position** (energy method):

$$v(x) = \omega\sqrt{A^2 - x^2}$$

**Simple pendulum derivation (small angle):**

Restoring torque: $\tau = -mgL\sin\theta \approx -mgL\theta$ (for small $\theta$)

$$I\frac{d^2\theta}{dt^2} = -mgL\theta \implies \frac{d^2\theta}{dt^2} = -\frac{mgL}{I}\theta = -\omega^2\theta$$

For a simple pendulum (point mass): $I = mL^2$, so:

$$\omega = \sqrt{\frac{mgL}{mL^2}} = \sqrt{\frac{g}{L}}$$

**Physical pendulum:**

$$\omega = \sqrt{\frac{MgL_{CM}}{I_{pivot}}}$$

---

## 3. Essential Formulas

**On the sheet:**

$$\frac{d^2x}{dt^2} = -\omega^2 x, \quad x = A\cos(\omega t + \phi), \quad T = \frac{2\pi}{\omega}$$

$$T_{spring} = 2\pi\sqrt{\frac{m}{k}}, \quad T_{pendulum} = 2\pi\sqrt{\frac{L}{g}}$$

$$U_s = \frac{1}{2}kx^2, \quad E = \frac{1}{2}kA^2$$

**Derived / Not on sheet:**

| Formula | Source |
|---|---|
| $v_{max} = A\omega$ | Differentiate $x(t)$ |
| $a_{max} = A\omega^2$ | Differentiate $v(t)$ |
| $v(x) = \omega\sqrt{A^2 - x^2}$ | Energy conservation |
| $K = \frac{1}{2}k(A^2-x^2)$ | $E - U = K$ |
| $T_{phys.pendulum} = 2\pi\sqrt{I/(MgL_{CM})}$ | Rotational SHM |
| $\phi = 0$ if $x(0) = A$ | From initial conditions |
| $\phi = \pi/2$ if $x(0) = 0, v(0) < 0$ | From initial conditions |

---

## 4. Free-Response Strategy

**Common FRQ Scenarios:**

- **Write and solve the SHM ODE:** Starting from $F = ma$ with $F = -kx$, derive $d^2x/dt^2 + \omega^2 x = 0$, state the solution $x(t) = A\cos(\omega t + \phi)$, apply initial conditions to find $A$ and $\phi$.
- **Energy analysis of SHM:** Given $A$ and $k$, find the speed at a specific $x$: use $v = \omega\sqrt{A^2 - x^2}$. Or show $E = \frac{1}{2}kA^2 = $ constant.
- **Mass on a spring with a step change** (e.g., mass is added at $x = 0$): New $\omega' = \sqrt{k/m'}$. The amplitude changes only if mass is added away from equilibrium. At equilibrium, $v_{max}$ is preserved; use $v_{max} = A'\omega'$ to find new amplitude.
- **Physical pendulum:** $I = I_{CM} + Md^2$ (Parallel Axis Theorem). Substitute into $T = 2\pi\sqrt{I_{pivot}/(MgL_{CM})}$.
- **SHM + energy:** A block on a spring on a frictionless surface is released from $x = A$. Find $v$ at $x = 0$: $\frac{1}{2}kA^2 = \frac{1}{2}mv^2$.

**FRQ Writing Tips:**
- When deriving SHM, start from Newton's Second Law — do not just quote the result.
- Explicitly identify $\omega$ before writing $T = 2\pi/\omega$.
- For initial conditions: if released from rest at $x = A$, then $\phi = 0$ (choose cosine). If released from equilibrium with initial velocity, use sine.

---

## 5. The "Trap" List

- **Period of a spring-mass system does NOT depend on amplitude.** $T = 2\pi\sqrt{m/k}$ regardless of how far you pull it. This is unique to SHM.
- **Pendulum period does not depend on mass.** $T = 2\pi\sqrt{L/g}$ — both $m_1$ and $m_2$ oscillate with the same period on the same pendulum.
- **Small angle approximation:** $T = 2\pi\sqrt{L/g}$ is only valid for $\theta \lesssim 15°$. At large angles, the period increases. Never apply it to large-angle pendulums.
- **$a_{max}$ occurs at $x = \pm A$, not at $x = 0$.** Students often think maximum speed and maximum acceleration occur at the same point — they occur at *opposite* extremes.
- **Phase angle $\phi$ must be determined from initial conditions.** Don't assume $\phi = 0$. If $x(0) = 0$ and $v(0) > 0$, then $x(t) = A\sin(\omega t)$, which corresponds to $\phi = -\pi/2$ in the cosine form.
- **When mass is added to a spring at $x \neq 0$:** The new equilibrium shifts, the amplitude changes, and the calculation requires careful energy bookkeeping. Do *not* assume the amplitude stays the same.

---

---

# Unit 7: Gravitation

## 1. Core Concepts

**Newton's Law of Universal Gravitation:** Every pair of masses attracts with a force:

$$\vec{F}_g = -\frac{GMm}{r^2}\hat{r}$$

This force is always attractive, acts along the line joining the two masses, and obeys Newton's Third Law.

**Gravitational field:** $\vec{g} = \vec{F}_g/m = -\frac{GM}{r^2}\hat{r}$. Near Earth's surface, $g \approx 9.8\ \text{m/s}^2$.

**Gravitational Potential Energy** (with reference at infinity):

$$U_g = -\frac{GMm}{r}$$

Note: This is always negative and approaches zero as $r \to \infty$.

**Escape velocity:** The minimum speed to escape to $r = \infty$ with $K_f = 0$:

$$v_{esc} = \sqrt{\frac{2GM}{R}}$$

**Orbital mechanics:** For a circular orbit, gravity provides the centripetal force:

$$\frac{GMm}{r^2} = \frac{mv^2}{r} \implies v_{orb} = \sqrt{\frac{GM}{r}}$$

**Kepler's Laws:**
1. Orbits are ellipses with the central body at one focus.
2. Equal areas in equal times (conservation of angular momentum).
3. $T^2 \propto r^3$ (for circular orbits: $T^2 = \frac{4\pi^2}{GM}r^3$).

---

## 2. The Calculus Connection

**Deriving gravitational potential energy from force:**

$$U(r) = -\int_\infty^r F_g\, dr' = -\int_\infty^r \left(-\frac{GMm}{r'^2}\right)dr' = -\frac{GMm}{r}$$

The choice of reference at $\infty$ (where $U = 0$) is essential and makes $U$ negative everywhere else.

**Gravitational field inside a uniform sphere** (Gauss's Law for gravity — advanced):

For $r < R$: Only the mass enclosed within radius $r$ contributes:

$$M_{enc} = M\cdot\frac{r^3}{R^3}$$

$$g(r) = \frac{GM_{enc}}{r^2} = \frac{GM}{R^3}r \quad \text{(linear in }r\text{)}$$

This shows gravity *increases* linearly from the center, peaks at the surface, then falls as $1/r^2$.

**Kepler's Third Law derivation (circular orbit):**

Set gravitational force equal to centripetal force:

$$\frac{GMm}{r^2} = \frac{mv^2}{r} = \frac{m(2\pi r/T)^2}{r} = \frac{4\pi^2 mr}{T^2}$$

$$\boxed{T^2 = \frac{4\pi^2}{GM}r^3}$$

**Total orbital energy:**

$$E_{total} = K + U = \frac{1}{2}mv_{orb}^2 - \frac{GMm}{r} = \frac{1}{2}m\frac{GM}{r} - \frac{GMm}{r} = -\frac{GMm}{2r}$$

The total energy is negative (bound orbit) and equals $U/2$ — a manifestation of the **Virial Theorem**.

**Angular momentum conservation (Kepler's Second Law):**

$$L = mvr = \text{const} \quad\text{(for circular orbit)}$$

For an elliptical orbit at periapsis and apoapsis (where $\vec{v} \perp \vec{r}$):

$$m v_p r_p = m v_a r_a \implies v_p r_p = v_a r_a$$

---

## 3. Essential Formulas

**On the sheet:**

$$F_g = \frac{Gm_1m_2}{r^2}, \qquad g = \frac{GM}{r^2}, \qquad U_g = -\frac{GMm}{r}$$

$$T^2 = \frac{4\pi^2}{GM}a^3 \quad\text{(Kepler's Third Law; }a\text{ = semi-major axis)}$$

**Derived / Not on sheet:**

| Formula | Source |
|---|---|
| $v_{orb} = \sqrt{GM/r}$ | Gravity = centripetal |
| $v_{esc} = \sqrt{2GM/R}$ | $K + U = 0$ |
| $E_{orbit} = -GMm/(2r)$ | $K + U$ in circular orbit |
| $v_p r_p = v_a r_a$ | Conservation of $L$ (ellipse) |
| $g(r<R) = GMr/R^3$ | Gravity inside uniform sphere |
| $g_{surface} = GM/R^2$ | Evaluated at $r = R$ |
| $E_{escape} = 0$ | Definition: $K + U = 0$ |

---

## 4. Free-Response Strategy

**Common FRQ Scenarios:**

- **Satellite in circular orbit:** Set $F_g = F_c$: $GMm/r^2 = mv^2/r$. Find orbital speed, period (use $T = 2\pi r/v$), and total energy ($E = -GMm/2r$).
- **Satellite transfers to a new orbit (Hohmann transfer, qualitative):** Apply conservation of energy and angular momentum. Speed decreases in higher orbit.
- **Escape velocity:** Set $K + U = 0$: $\frac{1}{2}mv^2 = GMm/R$, solve for $v$.
- **Kepler's Third Law comparison:** Given $T_1, r_1$ of one planet, find $T_2$ given $r_2$: use $T_1^2/r_1^3 = T_2^2/r_2^3 = 4\pi^2/(GM)$.
- **Gravitational potential energy difference:** $\Delta U = GMm(1/r_i - 1/r_f)$. This is the work required to move a mass from $r_i$ to $r_f$.
- **Finding $g$ at various heights:** $g(r) = GM/r^2$; at height $h$ above surface: $r = R_E + h$.

**FRQ Writing Tips:**
- Always use $U_g = -GMm/r$ (not $mgh$) for problems involving significant changes in altitude.
- When finding work to lift a satellite, use $W = \Delta U + \Delta K$ — the satellite changes both PE and KE.
- State Kepler's Second Law verbally and connect it to angular momentum conservation for full credit.

---

## 5. The "Trap" List

- **Using $U = mgh$ for orbital problems.** This approximation is only valid near Earth's surface. For any orbit calculation, use $U = -GMm/r$.
- **Gravitational force at the surface:** $g = GM/R^2$, not $GM/r^2$ in general. The surface value is the baseline; at height $h$, $r = R + h$.
- **Escape velocity is NOT the orbital velocity.** $v_{esc} = \sqrt{2}\ v_{orb}$. Escape requires twice the kinetic energy of a circular orbit at the same radius.
- **Orbital speed decreases with increasing radius.** $v = \sqrt{GM/r}$ — higher orbit, slower speed. This is counterintuitive to students who think "faster orbit = more energy."
- **Total orbital energy is negative.** $E = -GMm/2r < 0$ for all bound orbits. A less negative total energy means a higher orbit (more energy). To raise an orbit, you *add* energy (do positive work).
- **Kepler's Third Law uses the semi-major axis $a$**, not the orbital radius (for ellipses). For circular orbits, $a = r$, but don't confuse them for elliptical orbits.
- **"Weightlessness" in orbit does not mean zero gravity.** The gravitational force is very much present — it provides centripetal acceleration. Astronauts are in free fall, which gives the sensation of weightlessness.

---

---

# Cross-Unit Synthesis: High-Yield Connections

## The Master Analogy Table

| Concept | Linear | Rotational |
|---|---|---|
| Inertia | $m$ | $I = \int r^2\,dm$ |
| Newton's 2nd | $F = ma$ | $\tau = I\alpha$ |
| Momentum | $p = mv$ | $L = I\omega$ |
| Impulse | $J = \int F\,dt$ | $\int\tau\,dt = \Delta L$ |
| Kinetic Energy | $\frac{1}{2}mv^2$ | $\frac{1}{2}I\omega^2$ |
| Work | $\int F\,dx$ | $\int\tau\,d\theta$ |
| Power | $Fv$ | $\tau\omega$ |
| Conservation | $\vec{F}_{ext}=0 \Rightarrow \vec{p}=\text{const}$ | $\vec{\tau}_{ext}=0 \Rightarrow \vec{L}=\text{const}$ |

## Calculus Master Summary

$$a = \frac{dv}{dt} = \frac{d^2x}{dt^2} = v\frac{dv}{dx}$$

$$W = \int \vec{F}\cdot d\vec{r}, \qquad F = -\frac{dU}{dx}$$

$$\vec{J} = \int \vec{F}\,dt = \Delta\vec{p}, \qquad \vec{\tau}_{net} = \frac{d\vec{L}}{dt}$$

$$I = \int r^2\,dm, \qquad x_{CM} = \frac{1}{M}\int x\,dm$$

$$\text{SHM: } \frac{d^2x}{dt^2} = -\omega^2 x \implies x = A\cos(\omega t + \phi)$$

$$U_g = -\frac{GMm}{r}, \qquad E_{orbit} = -\frac{GMm}{2r}$$

## FRQ Attack Strategy (Universal)

1. **Read once** to identify the system, the physics principle, and what's asked.
2. **Draw a diagram** (FBD, energy bar chart, phase diagram).
3. **Identify the governing law** ($F=ma$, energy conservation, momentum conservation, $\tau = I\alpha$).
4. **Write the equation in general form** before substituting numbers.
5. **Execute algebra** cleanly; box your final answers.
6. **Dimensional check:** Verify units make sense.
7. **Sanity check:** Does the sign make sense? Is the magnitude reasonable?

> **Remember:** On AP Physics C FRQs, you earn points for *correct physics setup*, even if your algebra has an error downstream. Always show your reasoning explicitly.
