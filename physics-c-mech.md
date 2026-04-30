# AP Physics C: E&M — Complete Mastery Guide

> **Philosophy:** In AP Physics C E&M, the math *is* the physics. Every formula is a compressed argument about how nature behaves. This guide unpacks those arguments so you can reconstruct any result, not just recall it.

---

# UNIT 1: Electrostatics

## 1. Core Concepts

Electrostatics studies charges **at rest** and the fields and potentials they create. The foundational insight is that charges exert forces on each other through an **electric field** — a vector field that exists in space regardless of whether a test charge is present.

The two pillars are:
- **Coulomb's Law** — the force between point charges
- **Gauss's Law** — a geometrically powerful restatement of Coulomb's Law for symmetric distributions

**Electric potential** $V$ is the scalar cousin of the vector field $\vec{E}$. It encodes the same physics but is often far easier to work with for complex distributions.

---

## 2. The Calculus Connection

### Coulomb's Law → Superposition Integral

For a **continuous charge distribution**, the electric field is built by summing infinitesimal contributions:

$$\vec{E} = \int \frac{k \, dq}{r^2} \hat{r}$$

where $\hat{r}$ points **from the source element $dq$ to the field point**.

**Setting up $dq$:**

| Geometry | Charge density | $dq$ |
|---|---|---|
| Line (1D) | $\lambda$ (C/m) | $\lambda \, dl$ |
| Surface (2D) | $\sigma$ (C/m²) | $\sigma \, dA$ |
| Volume (3D) | $\rho$ (C/m³) | $\rho \, dV$ |

**Critical technique — canceling components by symmetry:** For a uniformly charged ring of radius $R$, field contributions in the plane of the ring cancel by symmetry. Only the axial component survives:

$$E_x = \int \frac{k \, dq}{r^2} \cos\theta = \frac{kQx}{(x^2 + R^2)^{3/2}}$$

where $r = \sqrt{x^2 + R^2}$ and $\cos\theta = \frac{x}{r}$.

### Gauss's Law — Integral Form

$$\oint_{\mathcal{S}} \vec{E} \cdot d\vec{A} = \frac{Q_{\text{enc}}}{\varepsilon_0}$$

The left side is a **closed surface integral** (flux). The strategy is always:

1. Identify the symmetry (spherical, cylindrical, planar)
2. Choose a Gaussian surface where $|\vec{E}|$ is **constant** and $\vec{E} \parallel d\vec{A}$
3. Pull $|\vec{E}|$ outside the integral; the remaining integral is just the surface area

**Differential form (Maxwell's first equation):**

$$\nabla \cdot \vec{E} = \frac{\rho}{\varepsilon_0}$$

This says the **divergence** of $\vec{E}$ equals the local charge density divided by $\varepsilon_0$ — $\vec{E}$ field lines *originate* from positive charges and *terminate* on negative charges.

### Electric Potential — Line Integral

$$V(r) = -\int_{\mathcal{C}} \vec{E} \cdot d\vec{\ell}$$

The path $\mathcal{C}$ goes from a **reference point** (usually $\infty$) to the field point. Because $\vec{E}$ is a **conservative field**, this integral is path-independent.

The inverse relationship:

$$\vec{E} = -\nabla V \quad \Rightarrow \quad E_x = -\frac{\partial V}{\partial x}, \quad E_r = -\frac{dV}{dr}$$

For a **continuous distribution**, superposition of scalar potentials is almost always easier than integrating the vector field:

$$V = \int \frac{k \, dq}{r}$$

---

## 3. Essential Formulas

### Standard Equations

$$\vec{F} = k\frac{q_1 q_2}{r^2}\hat{r} = \frac{1}{4\pi\varepsilon_0}\frac{q_1 q_2}{r^2}\hat{r}$$

$$\vec{E} = \frac{\vec{F}}{q_0} = k\frac{Q}{r^2}\hat{r} \quad \text{(point charge)}$$

$$\oint \vec{E} \cdot d\vec{A} = \frac{Q_{\text{enc}}}{\varepsilon_0}$$

$$V = k\frac{Q}{r}, \qquad U = k\frac{q_1 q_2}{r} = qV$$

### Must-Know Derived Results

| Configuration | Result |
|---|---|
| Infinite line charge (linear density $\lambda$) | $E = \dfrac{\lambda}{2\pi\varepsilon_0 r}$ |
| Infinite plane (surface density $\sigma$) | $E = \dfrac{\sigma}{2\varepsilon_0}$ (each side) |
| Uniformly charged sphere (outside, $r > R$) | $E = \dfrac{kQ}{r^2}$ (same as point charge) |
| Uniformly charged sphere (inside, $r < R$) | $E = \dfrac{kQ}{R^3}r = \dfrac{\rho r}{3\varepsilon_0}$ |
| Uniformly charged ring, on axis | $E = \dfrac{kQx}{(x^2+R^2)^{3/2}}$ |
| Uniformly charged disk, on axis | $E = \dfrac{\sigma}{2\varepsilon_0}\!\left(1 - \dfrac{x}{\sqrt{x^2+R^2}}\right)$ |
| Infinite conducting shell (outside) | $E = \dfrac{kQ}{r^2}$; inside $E = 0$ |

---

## 4. Free-Response Strategy

**Common FRQ scenarios:**

- **"Derive $\vec{E}$ using Gauss's Law"** — State the symmetry, draw the Gaussian surface, write the full integral form, then simplify. Always write $\oint \vec{E} \cdot d\vec{A} = \frac{Q_{\text{enc}}}{\varepsilon_0}$ first before simplifying — graders award method points.

- **"Find $V$ at a point given a non-uniform $\lambda(x)$"** — Use $V = \int \frac{k\,dq}{r}$. Express $dq = \lambda(x)\,dx$ and $r$ as a function of $x$.

- **"Sketch equipotential lines"** — Equipotentials are always **perpendicular to field lines**. For a point charge they are concentric spheres. Closer spacing = stronger field.

- **"Find $E$ from $V(r)$"** — Differentiate: $E_r = -\frac{dV}{dr}$. Watch signs.

---

## 5. The Trap List

> ⚠️ **$V$ vs. $U$:** Electric potential $V$ is a property of the field (J/C = V). Potential energy $U = qV$ belongs to the **charge-field system** and depends on which charge $q$ you place there.

> ⚠️ **$\hat{r}$ direction:** In Coulomb's Law and $\vec{E}$, $\hat{r}$ always points **away from the source**. The force on a negative test charge is *opposite* to $\vec{E}$.

> ⚠️ **Gauss's Law requires a closed surface:** You cannot apply Gauss's Law to an open surface. And $E$ on the surface must be exploitable by symmetry — Gauss's Law is *always* true, but it's only *useful* in symmetric situations.

> ⚠️ **Inside a conductor, $E = 0$ in electrostatic equilibrium** — not "small," exactly zero. Any field would drive current, violating the "static" assumption.

> ⚠️ **$V = 0$ does not mean $E = 0$:** At the midpoint between equal and opposite charges, $V = 0$ but $\vec{E}$ points from $+$ to $-$ and is nonzero.

---
---

# UNIT 2: Conductors, Capacitors & Dielectrics

## 1. Core Concepts

**Conductors in electrostatic equilibrium** obey four cardinal rules:
1. $\vec{E} = 0$ everywhere inside
2. Any net charge resides **entirely on the surface**
3. The surface is an **equipotential**
4. Just outside, $\vec{E} \perp$ surface and $E = \sigma/\varepsilon_0$

**Capacitors** store energy in the electric field between two conductors. **Dielectrics** are insulating materials that reduce $\vec{E}$ (and $V$) by polarizing — but the key is *how* they change each quantity depending on what's held constant.

---

## 2. The Calculus Connection

### Deriving Capacitance from Geometry

The fundamental procedure:
1. Assume charges $+Q$ and $-Q$ on the conductors
2. Use Gauss's Law to find $\vec{E}$ in the gap
3. Integrate $\vec{E}$ to find the potential difference: $V = -\int_- ^+ \vec{E} \cdot d\vec{\ell}$
4. Apply $C = Q/V$

**Parallel plate capacitor:**

$$E = \frac{\sigma}{\varepsilon_0} = \frac{Q}{\varepsilon_0 A}$$

$$V = Ed = \frac{Qd}{\varepsilon_0 A}$$

$$\boxed{C = \frac{Q}{V} = \frac{\varepsilon_0 A}{d}}$$

**Cylindrical capacitor** (inner radius $a$, outer radius $b$, length $L$):

Using Gauss's Law: $E = \dfrac{\lambda}{2\pi\varepsilon_0 r} = \dfrac{Q}{2\pi\varepsilon_0 L r}$

$$V = -\int_b^a E\,dr = \frac{Q}{2\pi\varepsilon_0 L}\ln\!\left(\frac{b}{a}\right)$$

$$\boxed{C = \frac{2\pi\varepsilon_0 L}{\ln(b/a)}}$$

**Spherical capacitor** (inner radius $a$, outer radius $b$):

$$E = \frac{kQ}{r^2}, \quad V = kQ\!\left(\frac{1}{a} - \frac{1}{b}\right)$$

$$\boxed{C = 4\pi\varepsilon_0 \frac{ab}{b-a}}$$

### Energy Stored in a Capacitor

$$U = \int_0^Q \frac{q}{C}\,dq = \frac{Q^2}{2C} = \frac{1}{2}CV^2 = \frac{1}{2}QV$$

**Energy density in the electric field:**

$$u_E = \frac{1}{2}\varepsilon_0 E^2 \quad \text{(J/m}^3\text{)}$$

This is profound: energy is stored in the **field itself**, not the charges.

---

## 3. Essential Formulas

$$C = \frac{Q}{V}, \qquad C_{\text{series}}: \frac{1}{C_{eq}} = \sum \frac{1}{C_i}, \qquad C_{\text{parallel}}: C_{eq} = \sum C_i$$

| Configuration | Capacitance |
|---|---|
| Parallel plates | $C = \varepsilon_0 A/d$ |
| Cylindrical | $C = 2\pi\varepsilon_0 L/\ln(b/a)$ |
| Spherical | $C = 4\pi\varepsilon_0 ab/(b-a)$ |
| Isolated sphere | $C = 4\pi\varepsilon_0 R$ |

**Dielectric effects** (dielectric constant $\kappa > 1$):

$$C_{\text{new}} = \kappa C_0, \qquad \varepsilon = \kappa\varepsilon_0$$

| Scenario | $Q$ | $V$ | $E$ | $C$ | $U$ |
|---|---|---|---|---|---|
| Dielectric inserted, **isolated** (constant $Q$) | same | $\div\kappa$ | $\div\kappa$ | $\times\kappa$ | $\div\kappa$ |
| Dielectric inserted, **connected to battery** (constant $V$) | $\times\kappa$ | same | same | $\times\kappa$ | $\times\kappa$ |

---

## 4. Free-Response Strategy

- **"Derive $C$ for a spherical/cylindrical capacitor"** — Go through all four steps above explicitly. Never just quote the formula.

- **"Dielectric is inserted — what happens to $U$?"** — First identify whether the battery is connected (constant $V$) or disconnected (constant $Q$). The answer is opposite in the two cases and graders specifically test this.

- **"Two capacitors, different dielectrics, connected in series/parallel"** — Use equivalent $C$ formulas. Then find $Q$ and $V$ on each.

---

## 5. The Trap List

> ⚠️ **Capacitors in series have the same $Q$**, not the same $V$. Capacitors in parallel have the same $V$, not the same $Q$.

> ⚠️ **A dielectric *always* increases $C$** regardless of the scenario. What changes is whether $Q$ or $V$ is held fixed by the circuit.

> ⚠️ **Energy decreases when dielectric is inserted at constant $Q$:** This seems to violate conservation of energy — it doesn't. The dielectric is pulled in by the fringe field and does positive work. The missing energy goes into mechanical energy of the dielectric slab.

> ⚠️ **The $E$ field between the plates points from the positive to negative plate.** For a capacitor, the Gaussian surface for $E$ must enclose only the positive plate.

---
---

# UNIT 3: Electric Circuits

## 1. Core Concepts

**Current** is the rate of charge flow: $I = dq/dt$. In a conductor, this arises from the **drift velocity** of electrons, which is surprisingly slow ($\sim$mm/s), despite the signal propagating near $c$.

**Resistance** quantifies opposition to current. **Ohm's Law** $V = IR$ is a material-dependent *approximation*, not a fundamental law — it holds when resistivity $\rho$ is constant.

**RC circuits** introduce time-dependent behavior: the charge on a capacitor cannot change instantaneously, creating an exponential approach to equilibrium.

---

## 2. The Calculus Connection

### Deriving the RC Circuit Differential Equation

For a **charging** RC circuit (battery $\mathcal{E}$, resistor $R$, capacitor $C$ in series):

Apply Kirchhoff's Voltage Law (KVL):

$$\mathcal{E} - IR - \frac{q}{C} = 0$$

Since $I = \dfrac{dq}{dt}$:

$$\mathcal{E} - R\frac{dq}{dt} - \frac{q}{C} = 0 \quad \Rightarrow \quad \frac{dq}{dt} = \frac{\mathcal{E}C - q}{RC}$$

This is a **separable first-order ODE.** Separating and integrating:

$$\int_0^q \frac{dq'}{\mathcal{E}C - q'} = \int_0^t \frac{dt'}{RC}$$

$$-\ln\!\left(\frac{\mathcal{E}C - q}{\mathcal{E}C}\right) = \frac{t}{RC}$$

$$\boxed{q(t) = C\mathcal{E}\!\left(1 - e^{-t/RC}\right) = Q_{\max}\!\left(1 - e^{-t/RC}\right)}$$

$$I(t) = \frac{dq}{dt} = \frac{\mathcal{E}}{R}e^{-t/RC} = I_0 \, e^{-t/RC}$$

For **discharging** (no battery, initial charge $Q_0$):

$$R\frac{dq}{dt} + \frac{q}{C} = 0 \quad \Rightarrow \quad \boxed{q(t) = Q_0 \, e^{-t/RC}}$$

$$I(t) = -\frac{Q_0}{RC}e^{-t/RC}$$

The **time constant** $\tau = RC$ has units of seconds and characterizes the timescale of the circuit. At $t = \tau$: the capacitor is $\approx 63\%$ charged (or $\approx 37\%$ discharged).

### Power and Ohm's Law from Microscopic Physics

$$\vec{J} = \sigma \vec{E} \quad \text{(microscopic Ohm's Law)}$$

where $\vec{J}$ is current density (A/m²) and $\sigma = 1/\rho$ is conductivity. Integrating across the cross-section gives macroscopic $I = \int \vec{J} \cdot d\vec{A}$.

Resistance from geometry:

$$R = \rho \frac{L}{A}$$

Power dissipated:

$$P = \frac{dU}{dt} = IV = I^2 R = \frac{V^2}{R}$$

---

## 3. Essential Formulas

**Resistors:**

$$R_{\text{series}} = \sum R_i, \qquad \frac{1}{R_{\text{parallel}}} = \sum \frac{1}{R_i}$$

**Kirchhoff's Laws:**
- **KCL** (junction rule): $\sum I_{\text{in}} = \sum I_{\text{out}}$ (charge conservation)
- **KVL** (loop rule): $\sum \Delta V = 0$ around any closed loop (energy conservation)

**RC Circuit Summary:**

| Quantity | Charging | Discharging |
|---|---|---|
| $q(t)$ | $Q_{\max}(1-e^{-t/\tau})$ | $Q_0 e^{-t/\tau}$ |
| $I(t)$ | $I_0 e^{-t/\tau}$ | $-\frac{Q_0}{\tau}e^{-t/\tau}$ |
| $V_C(t)$ | $\mathcal{E}(1-e^{-t/\tau})$ | $V_0 e^{-t/\tau}$ |
| $V_R(t)$ | $\mathcal{E}\,e^{-t/\tau}$ | $V_0 e^{-t/\tau}$ |

where $\tau = RC$.

---

## 4. Free-Response Strategy

- **"Derive the expression for $q(t)$ or $I(t)$"** — Write KVL, substitute $I = dq/dt$, then separate variables. Show all integration steps.

- **"Sketch $I(t)$ and $V_C(t)$"** — $I$ starts high and decays to zero. $V_C$ starts at zero and asymptotes to $\mathcal{E}$. The sum $V_R + V_C = \mathcal{E}$ at all times.

- **"At $t = 0$, what is the current?"** — At $t=0$, the uncharged capacitor acts as a **short circuit** ($V_C = 0$). A fully charged capacitor acts as an **open circuit** ($I = 0$).

- **Lab-based FRQ:** Often involves plotting $\ln(V_C)$ vs. $t$ to extract $RC$ from the slope, or finding $\tau$ from the time to reach $1/e$ of $V_0$.

---

## 5. The Trap List

> ⚠️ **At $t = 0$, the uncharged capacitor is a wire.** Replace it with a short for initial conditions. At $t = \infty$, it's an open circuit — no current flows through the capacitor branch.

> ⚠️ **KVL sign convention:** Crossing a resistor in the direction of current is a **voltage drop** ($-IR$). Crossing a battery from $-$ to $+$ is a **voltage rise** ($+\mathcal{E}$).

> ⚠️ **Power in parallel vs. series:** In parallel, the branch with **smaller** $R$ dissipates **more** power ($P = V^2/R$, same $V$). In series, the larger $R$ dissipates more ($P = I^2R$, same $I$). Students frequently confuse these.

> ⚠️ **$\tau = RC$ only when $R$ is the Thévenin equivalent resistance** seen by the capacitor — i.e., with all independent sources set to zero.

---
---

# UNIT 4: Magnetic Fields

## 1. Core Concepts

Moving charges create **magnetic fields** $\vec{B}$, and magnetic fields exert forces on moving charges — but crucially, **magnetic forces do no work** (the force is always perpendicular to velocity).

The two foundational laws for computing $\vec{B}$:

- **Biot-Savart Law** — microscopic, works for any current geometry
- **Ampere's Law** — macroscopic, works elegantly for symmetric configurations (the magnetic analog of Gauss's Law)

---

## 2. The Calculus Connection

### Biot-Savart Law

The magnetic field $d\vec{B}$ produced by an infinitesimal current element $Id\vec{\ell}$ at position $\vec{r}$ from the element:

$$d\vec{B} = \frac{\mu_0}{4\pi} \frac{I \, d\vec{\ell} \times \hat{r}}{r^2}$$

$$\vec{B} = \frac{\mu_0}{4\pi} \int \frac{I \, d\vec{\ell} \times \hat{r}}{r^2}$$

The **cross product** $d\vec{\ell} \times \hat{r}$ determines direction via the right-hand rule and magnitude $|d\vec{\ell}||\hat{r}|\sin\phi = dl\sin\phi$.

**Magnetic field at center of a circular loop of radius $R$:**

Every element $d\vec{\ell}$ is perpendicular to $\hat{r}$ (which points radially inward), so $\sin\phi = 1$ everywhere:

$$B = \frac{\mu_0}{4\pi} \int_0^{2\pi R} \frac{I \, dl}{R^2} = \frac{\mu_0 I}{4\pi R^2}(2\pi R) = \boxed{\frac{\mu_0 I}{2R}}$$

**Magnetic field of an infinite straight wire:**

Set up with the wire along the $z$-axis, field point at distance $d$:

$$B = \frac{\mu_0 I}{4\pi d} \int_{-\infty}^{\infty} \frac{\sin\theta \, dz}{r^2} = \boxed{\frac{\mu_0 I}{2\pi d}}$$

### Ampere's Law — Integral Form

$$\oint_{\mathcal{C}} \vec{B} \cdot d\vec{\ell} = \mu_0 I_{\text{enc}}$$

The line integral is over a closed loop $\mathcal{C}$ (**Amperian loop**). Strategy:

1. Identify symmetry (cylindrical → circular loop; planar → rectangular loop)
2. Choose $\mathcal{C}$ so that $|\vec{B}|$ is constant and $\vec{B} \parallel d\vec{\ell}$
3. Pull $B$ out: $B \oint d\ell = B(2\pi r) = \mu_0 I_{\text{enc}}$

**Differential form (Maxwell's fourth equation, magnetostatics):**

$$\nabla \times \vec{B} = \mu_0 \vec{J}$$

The **curl** of $\vec{B}$ equals $\mu_0$ times the local current density — $\vec{B}$ field lines **curl around** current-carrying wires.

---

## 3. Essential Formulas

**Magnetic force:**

$$\vec{F} = q\vec{v} \times \vec{B}, \qquad \vec{F} = I\vec{L} \times \vec{B}$$

Circular motion of charge in uniform $\vec{B}$:

$$qvB = \frac{mv^2}{r} \quad \Rightarrow \quad r = \frac{mv}{qB}, \quad T = \frac{2\pi m}{qB}$$

| Configuration | Magnetic Field |
|---|---|
| Long straight wire | $B = \dfrac{\mu_0 I}{2\pi r}$ |
| Center of circular loop | $B = \dfrac{\mu_0 I}{2R}$ |
| Solenoid (interior, $n$ turns/m) | $B = \mu_0 n I$ |
| Toroid (interior, $N$ turns, radius $r$) | $B = \dfrac{\mu_0 N I}{2\pi r}$ |
| On axis of circular loop | $B = \dfrac{\mu_0 I R^2}{2(x^2+R^2)^{3/2}}$ |

**Force between parallel wires** (length $L$, separation $d$):

$$\frac{F}{L} = \frac{\mu_0 I_1 I_2}{2\pi d}$$

(Attractive for parallel currents; repulsive for antiparallel)

---

## 4. Free-Response Strategy

- **"Find $\vec{B}$ inside/outside a long cylindrical wire carrying current $I$ with current density $J(r)$"** — Use Ampere's Law. Inside, $I_{\text{enc}} = \int_0^r J(r') \cdot 2\pi r' \, dr'$. This integral must be set up explicitly.

- **"Find the force on a wire segment in a non-uniform $\vec{B}$"** — Integrate $dF = I\,dl \times B(l)$.

- **"Biot-Savart for a finite wire or arc"** — Set up the integral. For an arc of angle $\theta$ (fraction of full circle): $B = \frac{\mu_0 I \theta}{4\pi R}$.

---

## 5. The Trap List

> ⚠️ **Magnetic forces do zero work:** $\vec{F}_{\text{mag}} \perp \vec{v}$ always, so $P = \vec{F} \cdot \vec{v} = 0$. The magnetic force changes direction, not speed.

> ⚠️ **Ampere's Law $I_{\text{enc}}$ is the current *piercing the surface bounded by* the Amperian loop** — not the current nearest the loop. For a hollow cylindrical shell with interior current, $I_{\text{enc}} = 0$ inside the shell.

> ⚠️ **Right-hand rule for $\vec{B}$:** Curl the right hand's fingers in the direction of the Amperian loop; the thumb points in the direction of positive current. For $d\vec{\ell} \times \hat{r}$ in Biot-Savart, use the cross-product right-hand rule — this is where signs are most often botched.

> ⚠️ **$\vec{B}$ is not zero outside a toroid** — it's approximately zero, but technically the return path creates a small exterior field. For AP purposes, $B = 0$ outside.

> ⚠️ **A solenoid's field is uniform inside and essentially zero outside.** This requires the solenoid to be infinite (or long compared to radius). The approximation is always stated on the exam.

---
---

# UNIT 5: Electromagnetism (Induction & Inductance)

## 1. Core Concepts

This unit unifies electricity and magnetism through **Faraday's Law**: a *changing* magnetic flux induces an EMF. This is the operating principle behind generators, transformers, and all of AC power.

**Lenz's Law** provides the direction: induced effects always **oppose** the change causing them (a consequence of energy conservation).

**Inductors** store energy in magnetic fields, playing the role in circuits that capacitors play with electric fields — they resist *changes* in current.

---

## 2. The Calculus Connection

### Magnetic Flux

$$\Phi_B = \int_{\mathcal{S}} \vec{B} \cdot d\vec{A} = \int B \cos\theta \, dA$$

For a uniform $\vec{B}$ and flat surface: $\Phi_B = BA\cos\theta$.

Maxwell's second equation (Gauss's Law for magnetism):

$$\oint \vec{B} \cdot d\vec{A} = 0$$

There are **no magnetic monopoles** — $\vec{B}$ field lines always form closed loops.

### Faraday's Law

$$\mathcal{E} = -\frac{d\Phi_B}{dt}$$

The **negative sign** encodes Lenz's Law. Expanding $\Phi_B = \int \vec{B} \cdot d\vec{A}$:

$$\mathcal{E} = -\frac{d}{dt}\int \vec{B} \cdot d\vec{A}$$

Three ways flux can change, each producing EMF:
1. **Changing $|\vec{B}|$** (stationary loop, changing field)
2. **Changing area $A$** (moving conductor, e.g., a sliding rod)
3. **Changing angle $\theta$** (rotating loop — this is the AC generator)

**Motional EMF** for a rod of length $L$ moving at velocity $v$ in field $B$:

$$\mathcal{E} = \int (\vec{v} \times \vec{B}) \cdot d\vec{\ell} = BLv$$

**Differential (Maxwell's third equation):**

$$\nabla \times \vec{E} = -\frac{\partial \vec{B}}{\partial t}$$

A time-varying $\vec{B}$ creates a curling $\vec{E}$ field — even in free space with no charges present.

### Inductance

**Self-inductance** $L$ relates flux to current:

$$\Phi_B = LI \quad \Rightarrow \quad \mathcal{E}_L = -L\frac{dI}{dt}$$

**Deriving $L$ for a solenoid** ($n$ turns/m, length $\ell$, area $A$, $N = n\ell$ total turns):

$$B = \mu_0 n I, \quad \Phi_B = BA = \mu_0 n I A$$

$$L = \frac{N\Phi_B}{I} = \frac{(n\ell)(\mu_0 n I A)}{I} = \boxed{\mu_0 n^2 \ell A}$$

**Mutual inductance:** $\mathcal{E}_2 = -M\dfrac{dI_1}{dt}$, where $M$ depends only on geometry.

### RL Circuit Differential Equation

**Building up current** (switch closed at $t=0$, battery $\mathcal{E}$):

$$\mathcal{E} - IR - L\frac{dI}{dt} = 0 \quad \Rightarrow \quad \frac{dI}{dt} = \frac{\mathcal{E} - IR}{L}$$

Separating variables and integrating:

$$\int_0^I \frac{dI'}{\mathcal{E}/R - I'} = \int_0^t \frac{R \, dt'}{L}$$

$$\boxed{I(t) = \frac{\mathcal{E}}{R}\!\left(1 - e^{-Rt/L}\right) = I_{\max}\!\left(1 - e^{-t/\tau_L}\right)}$$

**Decaying current** (source removed):

$$\boxed{I(t) = I_0 \, e^{-Rt/L}}$$

**Inductive time constant:** $\tau_L = L/R$

**Energy stored in inductor:**

$$U_L = \int_0^I L I' \, dI' = \frac{1}{2}LI^2$$

**Magnetic energy density:**

$$u_B = \frac{B^2}{2\mu_0}$$

---

## 3. Essential Formulas

$$\mathcal{E} = -\frac{d\Phi_B}{dt}, \qquad \Phi_B = \int \vec{B} \cdot d\vec{A}$$

$$\mathcal{E}_L = -L\frac{dI}{dt}, \qquad L_{\text{solenoid}} = \mu_0 n^2 \ell A$$

| Quantity | RL Circuit | RC Circuit |
|---|---|---|
| Time constant | $\tau = L/R$ | $\tau = RC$ |
| Energy stored | $U = \frac{1}{2}LI^2$ | $U = \frac{1}{2}CV^2$ |
| "Resists change in" | Current $I$ | Voltage $V$ |
| At $t = 0$: | Open circuit ($I = 0$) | Short circuit ($V_C = 0$) |
| At $t = \infty$: | Short circuit ($V_L = 0$) | Open circuit ($I = 0$) |

**AC Generator** (rotating loop, $N$ turns, area $A$, field $B$, angular velocity $\omega$):

$$\Phi_B = NBA\cos(\omega t) \quad \Rightarrow \quad \mathcal{E} = NBA\omega\sin(\omega t)$$

---

## 4. Free-Response Strategy

- **"Find the induced EMF in a loop as $B$ changes"** — Write $\Phi_B = B(t) \cdot A$, then $\mathcal{E} = -d\Phi_B/dt$. Apply Lenz's Law for direction.

- **"A rod slides on rails — find $\mathcal{E}$, $I$, force required to maintain speed"** — $\mathcal{E} = BLv$, $I = \mathcal{E}/R$, $F_{\text{applied}} = BIL = \frac{B^2L^2v}{R}$ (opposing motion by Lenz's Law).

- **"Derive $I(t)$ for an RL circuit"** — Show the KVL setup, the separable ODE, and the integration. Don't skip steps.

- **"Two coils, mutual inductance — find induced EMF"** — $\mathcal{E}_2 = -M\frac{dI_1}{dt}$. You may need to derive $M$ from the geometry.

---

## 5. The Trap List

> ⚠️ **Lenz's Law sign errors:** The induced EMF opposes the *change* in flux — not the flux itself. If flux is decreasing downward, the induced current creates flux *downward* (to oppose the decrease), not upward. Always ask: "Is flux increasing or decreasing? What direction of induced current would oppose that change?"

> ⚠️ **$\mathcal{E} = -L\frac{dI}{dt}$ — the sign matters:** When current is *increasing*, $\mathcal{E}_L$ is negative (opposing the increase). When current is *decreasing*, the inductor *maintains* the current — it acts like a battery in that direction.

> ⚠️ **At $t = 0$, the inductor is an open circuit** (for a previously unenergized inductor). This is the opposite of the capacitor. An inductor prevents instantaneous changes in current.

> ⚠️ **Flux through a surface, not a wire:** $\Phi_B$ is defined for a *surface* bounded by the loop. For a solenoid, $\Phi_B$ through the entire coil is $N$ times the flux through a single turn.

> ⚠️ **Faraday's Law works for any loop** — real or imaginary, moving or stationary. The loop doesn't need to be a conductor for flux to be well-defined. It *does* need to be a conductor for a real current to flow.

> ⚠️ **$u_B = \frac{B^2}{2\mu_0}$ and $u_E = \frac{1}{2}\varepsilon_0 E^2$** are both stored in the *field*. This is the deepest idea in classical electromagnetism — fields are physical entities that carry energy and momentum.

---

---

# Cross-Unit Synthesis: Maxwell's Equations

At the end of AP Physics C E&M, you have derived all four of Maxwell's equations:

$$\oint \vec{E} \cdot d\vec{A} = \frac{Q_{\text{enc}}}{\varepsilon_0} \tag{Gauss — Electric}$$

$$\oint \vec{B} \cdot d\vec{A} = 0 \tag{Gauss — Magnetic}$$

$$\oint \vec{E} \cdot d\vec{\ell} = -\frac{d\Phi_B}{dt} \tag{Faraday}$$

$$\oint \vec{B} \cdot d\vec{\ell} = \mu_0 I_{\text{enc}} \tag{Ampere}$$

Together, these four equations — plus the Lorentz force law $\vec{F} = q(\vec{E} + \vec{v}\times\vec{B})$ — completely describe **all of classical electromagnetism**. Every result in this guide is a consequence of these five relationships. When in doubt on the exam, trace any formula back to whichever Maxwell equation it comes from. That's the mark of true mastery.

**Good luck — you've got this.** 🎯
