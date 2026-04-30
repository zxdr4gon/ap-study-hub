# AP Calculus BC: Complete Mastery Guide for a 5

---

## Units 1 & 2: Limits, Continuity & Differentiation Foundations

### Core Concepts

Limits form the logical backbone of all of calculus. You must understand limits not merely as a computational tool but as a rigorous statement about the behavior of a function near a point. Continuity is defined entirely in terms of limits, and differentiability is a stronger condition than continuity.

**The Three-Part Definition of Continuity:** A function $f$ is continuous at $x = c$ if:
1. $f(c)$ exists
2. $\displaystyle\lim_{x \to c} f(x)$ exists
3. $\displaystyle\lim_{x \to c} f(x) = f(c)$

Differentiability implies continuity, but **not** vice versa. The classic counterexample is $f(x) = |x|$ at $x = 0$.

### The BC Extension

The primary BC extension in these units is the rigorous and complete treatment of **L'Hôpital's Rule**, including the non-obvious indeterminate forms.

### Essential Formulas & Theorems

**Formal Definition of the Derivative:**

$$f'(x) = \lim_{h \to 0} \frac{f(x+h) - f(x)}{h}$$

**Alternate (Point) Definition:**

$$f'(a) = \lim_{x \to a} \frac{f(x) - f(a)}{x - a}$$

**L'Hôpital's Rule:** If $\displaystyle\lim_{x \to c} \frac{f(x)}{g(x)}$ produces the indeterminate form $\dfrac{0}{0}$ or $\dfrac{\pm\infty}{\pm\infty}$, then:

$$\lim_{x \to c} \frac{f(x)}{g(x)} = \lim_{x \to c} \frac{f'(x)}{g'(x)}$$

**Handling Non-Standard Indeterminate Forms:** These require algebraic manipulation *before* applying L'Hôpital's Rule.

| Form | Strategy |
|---|---|
| $0 \cdot \infty$ | Rewrite as $\dfrac{0}{1/\infty}$ or $\dfrac{\infty}{1/0}$ to get $\dfrac{0}{0}$ or $\dfrac{\infty}{\infty}$ |
| $\infty - \infty$ | Find a common denominator or multiply by a conjugate |
| $1^\infty,\ 0^0,\ \infty^0$ | Take the natural log: let $L = \lim f^g$, then evaluate $\lim g \ln f$ |

**The $1^\infty$ Form — Full Procedure:**

To evaluate $L = \displaystyle\lim_{x \to \infty} \left(1 + \frac{1}{x}\right)^x$:

Let $y = \left(1 + \frac{1}{x}\right)^x$, so $\ln y = x \ln\left(1 + \frac{1}{x}\right) = \dfrac{\ln(1 + 1/x)}{1/x}$

This is now $\dfrac{0}{0}$. Apply L'Hôpital's Rule $\Rightarrow \ln y \to 1$, so $L = e^1 = e$.

**Squeeze Theorem:** If $g(x) \leq f(x) \leq h(x)$ near $c$ and $\displaystyle\lim_{x \to c} g(x) = \lim_{x \to c} h(x) = L$, then $\displaystyle\lim_{x \to c} f(x) = L$.

**Two Essential Trigonometric Limits:**

$$\lim_{x \to 0} \frac{\sin x}{x} = 1 \qquad \lim_{x \to 0} \frac{1 - \cos x}{x} = 0$$

### FRQ Strategy

L'Hôpital's Rule rarely appears as a standalone FRQ, but it frequently appears in:
- **Series FRQs**: Confirming that $\displaystyle\lim_{n\to\infty} a_n = 0$ as a necessary condition.
- **Differential Equations FRQs**: Analyzing long-run behavior.
- **Table-based FRQs**: Using the alternate definition of the derivative from a table of values.

When using the alternate definition from a table, always average the slopes on either side for an approximation: $f'(a) \approx \dfrac{f(b) - f(a)}{b - a}$.

### The "Trap" List

- **Applying L'Hôpital's Rule to a non-indeterminate form.** You *must* verify the form is $\dfrac{0}{0}$ or $\dfrac{\infty}{\infty}$ first. Applying it to $\dfrac{2}{0}$ is an illegal move.
- **Differentiating the quotient instead of the numerator and denominator separately.** L'Hôpital's Rule is *not* the quotient rule. You differentiate $f$ and $g$ independently: $\dfrac{f'}{g'}$, not $\left(\dfrac{f}{g}\right)'$.
- **Confusing removable discontinuities with holes in domain vs. jump discontinuities.** Be precise: a function with a hole (removable discontinuity) can be *redefined* to be continuous; a jump discontinuity cannot.
- **Forgetting that differentiability requires equal left-hand and right-hand derivatives.** For piecewise functions, verify both the function value and the derivative agree at the boundary point.

---

## Units 3, 4 & 5: Advanced Differentiation & Applications

### Core Concepts

These units transform the derivative from a definition into a powerful analytical tool. The key ideas are: applying differentiation rules to complex functions, using derivatives to understand the *relationship* between changing quantities (Related Rates), and the profound theoretical guarantee of the **Mean Value Theorem (MVT)**.

### The BC Extension

BC extends implicit differentiation into **parametric and vector contexts** (formalized in Unit 9) and demands deeper fluency with:
- **Implicit differentiation** of complex multivariable expressions
- **Derivatives of inverse functions**
- **Derivatives of inverse trigonometric functions** with full chain rule fluency

### Essential Formulas & Theorems

**Chain Rule:**

$$\frac{d}{dx}[f(g(x))] = f'(g(x)) \cdot g'(x)$$

**Implicit Differentiation** — Differentiate both sides with respect to $x$; every $y$ term picks up a $\dfrac{dy}{dx}$ factor via the chain rule:

$$\frac{d}{dx}[y^n] = n y^{n-1} \frac{dy}{dx}$$

**Derivative of an Inverse Function:**

$$\left(f^{-1}\right)'(a) = \frac{1}{f'(f^{-1}(a))}$$

**Key Inverse Trig Derivatives:**

$$\frac{d}{dx}[\arcsin u] = \frac{u'}{\sqrt{1-u^2}} \qquad \frac{d}{dx}[\arctan u] = \frac{u'}{1+u^2}$$

$$\frac{d}{dx}[\text{arcsec}\, u] = \frac{u'}{|u|\sqrt{u^2-1}}$$

**Mean Value Theorem:** If $f$ is continuous on $[a,b]$ and differentiable on $(a,b)$, then there exists at least one $c \in (a,b)$ such that:

$$f'(c) = \frac{f(b) - f(a)}{b - a}$$

**Rolle's Theorem** (special case of MVT): If additionally $f(a) = f(b)$, then $\exists\, c$ such that $f'(c) = 0$.

**Extreme Value Theorem (EVT):** If $f$ is continuous on $[a,b]$, then $f$ attains both an absolute maximum and minimum on $[a,b]$.

**Candidates Test for Absolute Extrema:** Evaluate $f$ at all critical points in $[a,b]$ *and* at the endpoints. The largest value is the absolute max; the smallest is the absolute min.

**Second Derivative Test:**
- $f'(c) = 0$ and $f''(c) > 0 \Rightarrow$ local minimum
- $f'(c) = 0$ and $f''(c) < 0 \Rightarrow$ local maximum
- $f''(c) = 0 \Rightarrow$ test is inconclusive

### FRQ Strategy

**The Related Rates FRQ** is nearly guaranteed on the AP exam. The procedure is invariant:

1. Draw and label a diagram.
2. Write an equation relating the relevant variables (geometric formula, Pythagorean theorem, similar triangles, etc.).
3. Differentiate *implicitly* with respect to time $t$.
4. Substitute the known values of rates and quantities at the specific instant.
5. Solve for the unknown rate. **Include units on your final answer.**

**Common Related Rates Setups:**

- Ladder sliding down a wall: $x^2 + y^2 = L^2$, differentiate to get $2x\dfrac{dx}{dt} + 2y\dfrac{dy}{dt} = 0$
- Expanding circle: $A = \pi r^2 \Rightarrow \dfrac{dA}{dt} = 2\pi r \dfrac{dr}{dt}$
- Conical tank draining: $V = \dfrac{1}{3}\pi r^2 h$ with a similar triangles relationship $\dfrac{r}{h} = \text{const}$

**The MVT FRQ:** College Board loves asking you to *justify* that a certain average rate of change must equal an instantaneous rate somewhere. Your justification must explicitly state: (1) $f$ is continuous on $[a,b]$, (2) $f$ is differentiable on $(a,b)$, (3) therefore by the MVT, there exists $c \in (a,b)$ such that $f'(c) = \dfrac{f(b)-f(a)}{b-a}$.

### The "Trap" List

- **In Related Rates: substituting values BEFORE differentiating.** You must differentiate the general equation first, then substitute.
- **Sign errors in implicit differentiation.** When differentiating $x^2 + y^2 = 25$ for a related rates problem and $x$ is *decreasing*, $\dfrac{dx}{dt}$ must be entered as a **negative** value.
- **Misquoting the MVT.** The theorem guarantees a $c$ exists; it does not tell you what $c$ is. Also, the conclusion is about the *derivative*, not the function value. On FRQs, incomplete hypothesis statements ("because $f$ is differentiable") without mentioning continuity lose points.
- **Applying Rolle's Theorem without verifying $f(a) = f(b)$.** This is a hypothesis, not a conclusion.
- **The inverse function derivative trap.** Students compute $f'(a)$ and take its reciprocal, forgetting to first find $f^{-1}(a)$ and evaluate $f'$ *there*.

---

## Unit 6: Integration and Accumulation of Change

### Core Concepts

Integration is understood through two lenses: the **Riemann Sum** (as a limit of accumulation) and the **Fundamental Theorem of Calculus (FTC)** (as the inverse of differentiation). For BC, you must master a toolkit of integration techniques well beyond simple $u$-substitution.

### The BC Extension

This is one of the most heavily weighted BC-only sections:

- **Integration by Parts (IBP)**
- **Integration by Partial Fractions**
- **Improper Integrals** (both Type I: infinite limits, and Type II: discontinuous integrands)

### Essential Formulas & Theorems

**Fundamental Theorem of Calculus, Part 1:**

$$\frac{d}{dx}\int_a^{g(x)} f(t)\, dt = f(g(x)) \cdot g'(x)$$

**Fundamental Theorem of Calculus, Part 2:**

$$\int_a^b f(x)\, dx = F(b) - F(a), \quad \text{where } F' = f$$

**Net Change Theorem:**

$$\int_a^b f'(x)\, dx = f(b) - f(a)$$

**Integration by Parts:**

$$\int u\, dv = uv - \int v\, du$$

**LIATE Rule for choosing $u$:** Logarithms, Inverse trig, Algebraic (polynomials), Trigonometric, Exponential. Choose $u$ as whichever appears earliest in this list.

**Classic IBP Examples:**

$$\int x e^x dx: \quad u = x,\ dv = e^x dx \Rightarrow xe^x - e^x + C$$

$$\int \ln x\, dx: \quad u = \ln x,\ dv = dx \Rightarrow x\ln x - x + C$$

For $\int e^x \sin x\, dx$: Apply IBP *twice*, then solve algebraically for the integral (the "boomerang" technique).

**Partial Fractions** — for a rational function $\dfrac{P(x)}{Q(x)}$ where $\deg P < \deg Q$:

$$\frac{1}{(x-a)(x-b)} = \frac{A}{x-a} + \frac{B}{x-b}$$

$$\frac{1}{(x-a)^2} = \frac{A}{x-a} + \frac{B}{(x-a)^2}$$

**Improper Integrals — Type I (Infinite Limits):**

$$\int_a^{\infty} f(x)\, dx = \lim_{b \to \infty} \int_a^b f(x)\, dx$$

**Improper Integrals — Type II (Discontinuous Integrand at $x = c \in [a,b]$):**

$$\int_a^b f(x)\, dx = \lim_{t \to c^-} \int_a^t f(x)\, dx + \lim_{t \to c^+} \int_t^b f(x)\, dx$$

**$p$-Integral Test Results** (critical to memorize):

$$\int_1^{\infty} \frac{1}{x^p}\, dx \begin{cases} \text{converges to } \dfrac{1}{p-1} & \text{if } p > 1 \\ \text{diverges} & \text{if } p \leq 1 \end{cases}$$

**Key Antiderivative Table:**

$$\int \frac{1}{x}\, dx = \ln|x| + C \qquad \int e^{kx}\, dx = \frac{1}{k}e^{kx} + C$$

$$\int \frac{1}{x^2 + a^2}\, dx = \frac{1}{a}\arctan\left(\frac{x}{a}\right) + C$$

$$\int \frac{1}{\sqrt{a^2 - x^2}}\, dx = \arcsin\left(\frac{x}{a}\right) + C$$

### FRQ Strategy

**The Accumulation FRQ:** Given a rate function $r(t)$, you are asked to find total accumulation via $\displaystyle\int_a^b r(t)\, dt$, or a running total via $Q(t) = Q(0) + \displaystyle\int_0^t r(s)\, ds$. This is the most common FRQ structure across all of Unit 6 and 7.

**IBP on the FRQ:** When you see $\displaystyle\int x \cdot (\text{trig or exp})\, dx$ or $\displaystyle\int \ln(x)\, dx$, reach for IBP immediately. Show the $u$ and $dv$ selection explicitly — readers award method points.

**Partial Fractions on the FRQ:** After decomposing, always show the step where you solve for $A$ and $B$ (either by cover-up or expanding and matching coefficients). Do not skip to the answer.

### The "Trap" List

- **Forgetting $+C$ on indefinite integrals.** This is an automatic point deduction on every AP exam FRQ, every time.
- **IBP: algebraic sign errors in $-\int v\, du$.** The negative sign distributes. Rewrite $uv - \int v\, du$ carefully each time.
- **Improper integrals: not using limit notation.** Writing $\displaystyle\int_1^\infty \frac{1}{x}\, dx = [\ln x]_1^\infty = \infty$ earns no credit. You *must* write $\displaystyle\lim_{b\to\infty}[\ln x]_1^b$.
- **Partial fractions: attempting the technique when $\deg P \geq \deg Q$.** You must perform polynomial long division first to get a proper rational function.
- **The absolute value trap in $\ln$.** The antiderivative of $\dfrac{1}{x}$ is $\ln|x| + C$, not $\ln x + C$. Miss the absolute value bars on an FRQ and lose a point.

---

## Unit 7: Differential Equations

### Core Concepts

A differential equation describes a relationship between a function and its derivatives. The two major solution strategies are **separation of variables** (for separable ODEs) and **slope fields** (for qualitative analysis). BC adds the numerical approach of **Euler's Method** and the modeling power of the **Logistic Growth Model**.

### The BC Extension

- **Euler's Method**: a numerical/iterative approximation for solving differential equations
- **Logistic Growth Model**: a more realistic population model than pure exponential growth

### Essential Formulas & Theorems

**Separation of Variables:**

$$\frac{dy}{dx} = f(x)g(y) \Rightarrow \int \frac{dy}{g(y)} = \int f(x)\, dx$$

**General Solution of $\dfrac{dy}{dx} = ky$:**

$$y = Ce^{kt}$$

**Euler's Method:** Given $\dfrac{dy}{dx} = F(x, y)$, starting from $(x_0, y_0)$, with step size $h$:

$$x_{n+1} = x_n + h$$

$$y_{n+1} = y_n + h \cdot F(x_n, y_n)$$

Euler's method is a **linear approximation** along the tangent line at each step. It is an **overestimate** when the solution is concave down ($f'' < 0$) and an **underestimate** when the solution is concave up ($f'' > 0$).

**Logistic Growth Differential Equation:**

$$\frac{dP}{dt} = kP\left(1 - \frac{P}{L}\right)$$

where $k$ is the growth rate constant and $L$ is the **carrying capacity** (the equilibrium population).

**Logistic Growth Solution:**

$$P(t) = \frac{L}{1 + Ae^{-kt}}, \quad \text{where } A = \frac{L - P_0}{P_0}$$

**Key Logistic Behaviors:**

- $\dfrac{dP}{dt}$ is maximized when $P = \dfrac{L}{2}$ (the **inflection point** of the logistic curve)
- As $t \to \infty$, $P(t) \to L$ (the population approaches the carrying capacity)
- The graph of $P(t)$ is **S-shaped (sigmoidal)**
- $\dfrac{d^2P}{dt^2} = 0$ at $P = \dfrac{L}{2}$

**Maximum Rate of Change of Logistic Growth:**

At $P = \dfrac{L}{2}$: $\dfrac{dP}{dt}\bigg|_{\max} = \dfrac{kL}{4}$

### FRQ Strategy

**The Differential Equations FRQ** (typically Part 4 of the FRQ section) almost always has the following parts:

1. **Slope field sketch**: Draw short tangent segments consistent with the sign/magnitude of $\dfrac{dy}{dx}$ at specified points.
2. **Euler's Method approximation**: Two or three steps, showing each computation. Always make a table: $x_n$, $y_n$, $F(x_n, y_n)$, $h \cdot F$.
3. **Solving the separable ODE**: Full separation, integration, apply initial condition, solve for $y$ explicitly.
4. **Logistic model analysis**: Identify $L$ and $k$ from a given equation, state when growth is fastest, describe long-run behavior.

**Euler's Method Table Template:**

| $n$ | $x_n$ | $y_n$ | $F(x_n, y_n)$ | $h \cdot F$ |
|---|---|---|---|---|
| 0 | $x_0$ | $y_0$ | computed | $h \cdot F_0$ |
| 1 | $x_0+h$ | $y_0 + h F_0$ | computed | $h \cdot F_1$ |

### The "Trap" List

- **Euler's Method: using the updated $x$ or $y$ in the same step.** Each step uses the *current* values $(x_n, y_n)$, not the values from the next step.
- **Forgetting the constant of integration during separation.** After integrating both sides, write $+C$ on *one* side only. Then apply the initial condition to solve for $C$ before any rearranging.
- **Logistic growth: misidentifying $L$.** Students often confuse the value of $k$ and $L$. Given $\dfrac{dP}{dt} = 0.3P(1 - P/500)$, we have $k = 0.3$ and $L = 500$, not $k = 0.3$ and $L = 1/500$.
- **Not recognizing that $\dfrac{dP}{dt}$ is maximum at $P = L/2$, not at $t = L/2$.** The inflection point is a *population value*, not a time value.
- **Slope fields: drawing slopes inconsistent with sign.** If $\dfrac{dy}{dx} > 0$ at a point, the segment must slope upward. A sign error in reading the ODE leads to an entirely wrong slope field.

---

## Unit 8: Applications of Integration

### Core Concepts

Integration gives us a machinery for computing geometrically meaningful quantities: area, volume, and arc length. The overarching principle is that every such computation reduces to an integral by thinking about **accumulating infinitesimally thin slices**.

### The BC Extension

- **Arc Length formula** (BC only)
- More complex volume setups involving non-standard axes of rotation

### Essential Formulas & Theorems

**Area Between Two Curves (integrating with respect to $x$):**

$$A = \int_a^b \left[f(x) - g(x)\right] dx, \quad \text{where } f(x) \geq g(x) \text{ on } [a,b]$$

**Area Between Two Curves (integrating with respect to $y$):**

$$A = \int_c^d \left[R(y) - L(y)\right] dy, \quad \text{where } R(y) \text{ is the right curve}$$

**Volume — Disk Method** (solid formed by rotating a region about the $x$-axis):

$$V = \pi \int_a^b \left[f(x)\right]^2\, dx$$

**Volume — Washer Method** (rotation with a hole):

$$V = \pi \int_a^b \left[\left(f(x)\right)^2 - \left(g(x)\right)^2\right] dx$$

where $f(x)$ is the **outer radius** and $g(x)$ is the **inner radius**.

**Volume — Shell Method** (rotation about a vertical axis, integrating with respect to $x$):

$$V = 2\pi \int_a^b x \cdot f(x)\, dx$$

**Volume — Cross-Sections (General):**

$$V = \int_a^b A(x)\, dx$$

where $A(x)$ is the area of the cross-sectional shape at position $x$.

| Cross-Section | $A(x)$ |
|---|---|
| Square | $[s(x)]^2$ |
| Equilateral Triangle | $\dfrac{\sqrt{3}}{4}[s(x)]^2$ |
| Semicircle (diameter on base) | $\dfrac{\pi}{8}[s(x)]^2$ |
| Right Isoceles Triangle (leg on base) | $\dfrac{1}{2}[s(x)]^2$ |

**Arc Length** (BC only) — for $y = f(x)$ on $[a,b]$:

$$L = \int_a^b \sqrt{1 + \left[f'(x)\right]^2}\, dx$$

**Arc Length** (parametric form, covered further in Unit 9):

$$L = \int_{t_1}^{t_2} \sqrt{\left(\frac{dx}{dt}\right)^2 + \left(\frac{dy}{dt}\right)^2}\, dt$$

**Average Value of a Function:**

$$f_{\text{avg}} = \frac{1}{b-a}\int_a^b f(x)\, dx$$

### FRQ Strategy

**The Volume FRQ** appears on nearly every AP exam and is typically a 9-point question. The format:

1. Find the area of the region (requires finding intersection points — show your algebra).
2. Find the volume when the region is rotated about a horizontal or vertical line.
3. Find the volume of a solid with cross-sections perpendicular to an axis.

**Rotating about a line other than the $x$-axis** (e.g., $y = -2$, or $y = 5$): The radius is no longer simply $f(x)$. You must compute the *distance* from the curve to the axis of rotation.

- Rotating about $y = k$ (below the region): outer radius $= f(x) - k$, inner radius $= g(x) - k$
- Rotating about $y = k$ (above the region): outer radius $= k - g(x)$, inner radius $= k - f(x)$

**Arc Length FRQ:** This is typically a short part of a larger FRQ (often the parametric/polar question). Set up the integral correctly; a calculator-active portion often just requires evaluating it numerically.

### The "Trap" List

- **Washer Method: squaring the difference vs. difference of squares.** The formula is $\pi\displaystyle\int[(R)^2 - (r)^2]\, dx$, *not* $\pi\displaystyle\int[(R - r)^2]\, dx$. These are different and the latter is always wrong.
- **Axis of rotation errors.** When rotating about $y = 3$ and the region is *below* $y = 3$, students forget to negate: outer radius $= 3 - g(x)$, not $g(x) - 3$. A negative radius gives a negative volume, which is a red flag.
- **Cross-section formula errors.** Forgetting the $\sqrt{3}/4$ for equilateral triangles or the $\pi/8$ for semicircles (diameter, not radius) costs easy points.
- **Arc length setup: squaring the derivative inside the radical.** The formula is $\sqrt{1 + (f')^2}$. A very common error is writing $\sqrt{1 + f'}$ or $\sqrt{(f')^2}$.
- **Not finding the correct limits of integration.** Always *solve* for intersection points algebraically. Do not guess from a graph.

---

## Unit 9: Parametric, Polar & Vector-Valued Functions

### Core Concepts

Unit 9 extends calculus to curves and motion described in systems beyond $y = f(x)$. A **parametric curve** describes position as a pair of functions of a parameter $t$. A **polar curve** describes position using a radius as a function of angle $\theta$. **Vector-valued functions** unify parametric motion with vector language.

### The BC Extension

This entire unit is BC-exclusive and is one of the most conceptually rich parts of the course.

### Essential Formulas & Theorems

**Parametric Calculus:**

First derivative (slope of tangent line):

$$\frac{dy}{dx} = \frac{dy/dt}{dx/dt}$$

Second derivative:

$$\frac{d^2y}{dx^2} = \frac{\dfrac{d}{dt}\!\left(\dfrac{dy}{dx}\right)}{dx/dt}$$

**Speed** of a particle in parametric motion:

$$\text{speed} = \sqrt{\left(\frac{dx}{dt}\right)^2 + \left(\frac{dy}{dt}\right)^2}$$

**Arc Length** (parametric):

$$L = \int_{t_1}^{t_2} \sqrt{\left(\frac{dx}{dt}\right)^2 + \left(\frac{dy}{dt}\right)^2}\, dt$$

**Vector-Valued Functions:**

Position vector: $\vec{r}(t) = \langle x(t),\, y(t) \rangle$

Velocity vector: $\vec{v}(t) = \vec{r}\,'(t) = \langle x'(t),\, y'(t) \rangle$

Acceleration vector: $\vec{a}(t) = \vec{v}\,'(t) = \langle x''(t),\, y''(t) \rangle$

**Displacement vs. Distance:**

$$\text{Displacement vector} = \vec{r}(b) - \vec{r}(a) = \left\langle \int_a^b x'(t)\, dt,\, \int_a^b y'(t)\, dt \right\rangle$$

$$\text{Total distance} = \int_a^b \left|\vec{v}(t)\right| dt = \int_a^b \sqrt{[x'(t)]^2 + [y'(t)]^2}\, dt$$

**Polar Coordinates:**

Conversion: $x = r\cos\theta$, $y = r\sin\theta$, $r^2 = x^2 + y^2$

**Slope of a polar curve** (using parametric interpretation):

$$\frac{dy}{dx} = \frac{\dfrac{dr}{d\theta}\sin\theta + r\cos\theta}{\dfrac{dr}{d\theta}\cos\theta - r\sin\theta}$$

**Area in Polar Coordinates** (BC only):

$$A = \frac{1}{2}\int_\alpha^\beta \left[r(\theta)\right]^2 d\theta$$

**Area between two polar curves:**

$$A = \frac{1}{2}\int_\alpha^\beta \left[\left(r_{\text{outer}}\right)^2 - \left(r_{\text{inner}}\right)^2\right] d\theta$$

**Common Polar Curves:**

| Curve | Equation |
|---|---|
| Circle | $r = a$ |
| Cardioid | $r = a(1 \pm \cos\theta)$ or $r = a(1 \pm \sin\theta)$ |
| Rose (n petals if n odd, 2n if n even) | $r = a\cos(n\theta)$ or $r = a\sin(n\theta)$ |
| Lemniscate | $r^2 = a^2\cos(2\theta)$ |
| Limaçon | $r = a + b\cos\theta$ |

### FRQ Strategy

**The Particle Motion FRQ** is one of the most reliable FRQ archetypes across the entire exam:

1. **Position, velocity, acceleration**: Given $\vec{r}(t) = \langle x(t), y(t)\rangle$, find $\vec{v}(t)$ and $\vec{a}(t)$ by differentiating component-wise.
2. **Speed at a specific time**: Compute $|\vec{v}(t)| = \sqrt{[x'(t)]^2 + [y'(t)]^2}$ at the given $t$.
3. **Direction of motion**: Examine the signs of $x'(t)$ and $y'(t)$.
4. **Is the particle moving left/right/up/down?** Moving left means $x'(t) < 0$; moving down means $y'(t) < 0$.
5. **Total distance** over an interval: Set up $\displaystyle\int_a^b |\vec{v}(t)|\, dt$ — this almost always requires a calculator.

**The Polar Area FRQ:**

1. Graph the curve (or describe it from the equation form).
2. Determine the correct $\theta$-interval by finding where $r = 0$ or where the curves intersect.
3. For a rose curve $r = a\cos(n\theta)$: petals traced from $\theta = -\pi/(2n)$ to $\pi/(2n)$.
4. Apply the formula $\dfrac{1}{2}\displaystyle\int_\alpha^\beta r^2\, d\theta$.

### The "Trap" List

- **Parametric second derivative: the most error-prone formula in BC.** $\dfrac{d^2y}{dx^2} \neq \dfrac{d^2y/dt^2}{d^2x/dt^2}$. You must differentiate $\dfrac{dy}{dx}$ with respect to $t$, then divide by $\dfrac{dx}{dt}$.
- **Polar area: using $r$, not $r^2$.** The formula is $\dfrac{1}{2}\displaystyle\int r^2\, d\theta$. Writing $\dfrac{1}{2}\displaystyle\int r\, d\theta$ is a fundamental error.
- **Polar area: wrong limits of integration.** The limits must capture exactly one full sweep of the region. For $r = \sin(2\theta)$, one petal is swept from $\theta = 0$ to $\theta = \pi/2$, not $0$ to $2\pi$.
- **Confusing distance and displacement.** Displacement is a vector (or signed scalar); distance is always non-negative and uses $|\vec{v}(t)|$.
- **Forgetting that speed is a scalar, not a vector.** Speed $= |\vec{v}(t)|$. Direction of motion requires examining both components of $\vec{v}(t)$.
- **Horizontal/vertical tangents in polar.** For a horizontal tangent, set $\dfrac{dy}{d\theta} = 0$ (not $\dfrac{dy}{dx} = 0$, which is a ratio). For a vertical tangent, set $\dfrac{dx}{d\theta} = 0$.

---

## Unit 10: Infinite Sequences and Series

### Core Concepts

This is the intellectual heart of BC Calculus and the most heavily tested BC-only topic. Series theory asks: when can we represent a function as an infinite sum of simpler terms? How do we know if an infinite sum converges to a finite value? The answers require mastering **convergence tests**, **power series**, and **Taylor/Maclaurin series**.

### The BC Extension

The entirety of Unit 10 is BC-exclusive and typically comprises 17–18% of the exam score.

### Essential Formulas & Theorems

**Geometric Series:**

$$\sum_{n=0}^{\infty} ar^n = \frac{a}{1-r}, \quad |r| < 1$$

Diverges if $|r| \geq 1$.

**$p$-Series:**

$$\sum_{n=1}^{\infty} \frac{1}{n^p} \begin{cases} \text{converges} & p > 1 \\ \text{diverges} & p \leq 1 \end{cases}$$

The harmonic series $\displaystyle\sum \dfrac{1}{n}$ is the boundary case: it **diverges** ($p = 1$).

**Convergence Tests Summary:**

| Test | When to Use | Condition for Convergence |
|---|---|---|
| $n$-th Term (Divergence) | Always check first | $\lim_{n\to\infty} a_n \neq 0 \Rightarrow$ diverges |
| Geometric | Terms have form $ar^n$ | $\|r\| < 1$ |
| $p$-Series | Terms have form $1/n^p$ | $p > 1$ |
| Integral Test | $a_n = f(n)$, $f$ pos., dec., cts. | $\int_1^\infty f(x)\,dx$ converges |
| Comparison Test (DCT) | Compare to known series | $0 \leq a_n \leq b_n$; if $\sum b_n$ conv., so does $\sum a_n$ |
| Limit Comparison Test (LCT) | Rational-type terms | $\lim_{n\to\infty} \frac{a_n}{b_n} = L > 0$; both conv. or both div. |
| Alternating Series Test (AST) | Alternating signs | $a_n \to 0$ and $a_n$ is decreasing |
| Ratio Test | Factorials, exponentials | $\lim_{n\to\infty} \left\|\frac{a_{n+1}}{a_n}\right\| < 1 \Rightarrow$ conv.; $> 1 \Rightarrow$ div.; $= 1 \Rightarrow$ inconclusive |
| Root Test | Terms of form $(b_n)^n$ | $\lim_{n\to\infty} \sqrt[n]{|a_n|} < 1 \Rightarrow$ conv. |

**Alternating Series Estimation Theorem (Alternating Series Error Bound):**

For a convergent alternating series $S = \displaystyle\sum_{n=1}^\infty (-1)^{n+1} a_n$:

$$|S - S_N| \leq a_{N+1}$$

The error of a partial sum approximation is **bounded by the first omitted term**, and the true sum lies between consecutive partial sums.

**Power Series:**

$$\sum_{n=0}^{\infty} c_n (x-a)^n$$

**Radius of Convergence** — found via the Ratio Test:

$$R = \lim_{n\to\infty} \left|\frac{c_n}{c_{n+1}}\right|$$

The series converges absolutely on $(a - R,\, a + R)$. **Endpoints must be tested separately** by substituting $x = a \pm R$ into the series.

**Taylor Series** centered at $x = a$:

$$f(x) = \sum_{n=0}^{\infty} \frac{f^{(n)}(a)}{n!}(x-a)^n = f(a) + f'(a)(x-a) + \frac{f''(a)}{2!}(x-a)^2 + \cdots$$

**Maclaurin Series** (Taylor centered at $a = 0$) — **Memorize all of these:**

$$e^x = \sum_{n=0}^{\infty} \frac{x^n}{n!} = 1 + x + \frac{x^2}{2!} + \frac{x^3}{3!} + \cdots \quad \text{for all } x$$

$$\sin x = \sum_{n=0}^{\infty} \frac{(-1)^n x^{2n+1}}{(2n+1)!} = x - \frac{x^3}{3!} + \frac{x^5}{5!} - \cdots \quad \text{for all } x$$

$$\cos x = \sum_{n=0}^{\infty} \frac{(-1)^n x^{2n}}{(2n)!} = 1 - \frac{x^2}{2!} + \frac{x^4}{4!} - \cdots \quad \text{for all } x$$

$$\frac{1}{1-x} = \sum_{n=0}^{\infty} x^n = 1 + x + x^2 + x^3 + \cdots \quad \text{for } |x| < 1$$

$$\ln(1+x) = \sum_{n=1}^{\infty} \frac{(-1)^{n+1} x^n}{n} = x - \frac{x^2}{2} + \frac{x^3}{3} - \cdots \quad \text{for } -1 < x \leq 1$$

$$\arctan x = \sum_{n=0}^{\infty} \frac{(-1)^n x^{2n+1}}{2n+1} = x - \frac{x^3}{3} + \frac{x^5}{5} - \cdots \quad \text{for } |x| \leq 1$$

**Manipulating Known Series** (far more efficient than computing derivatives):

$$e^{-x^2} = \sum_{n=0}^{\infty} \frac{(-1)^n x^{2n}}{n!} \quad \text{(substitute } x \to -x^2 \text{ into } e^x)$$

$$\int_0^x e^{-t^2}\, dt = \sum_{n=0}^{\infty} \frac{(-1)^n x^{2n+1}}{n!(2n+1)} \quad \text{(integrate term by term)}$$

**Lagrange Error Bound:**

If $f$ is approximated by its $n$-th degree Taylor polynomial $P_n(x)$ centered at $a$, then:

$$|f(x) - P_n(x)| \leq \frac{M}{(n+1)!}|x-a|^{n+1}$$

where $M$ is the maximum value of $|f^{(n+1)}|$ on the interval between $a$ and $x$.

### FRQ Strategy

**The Series FRQ** (always in the calculator-inactive section) is typically structured as:

**Part (a):** Write the first three or four nonzero terms and the general term of a Taylor series. The most efficient method is **substituting into a known Maclaurin series** rather than computing derivatives.

**Part (b):** Find the **interval of convergence**. Always: (1) apply the Ratio Test to find $R$, (2) state the open interval $(a-R, a+R)$, (3) test each endpoint separately using a named convergence test, (4) state the final interval with correct bracket/parenthesis notation.

**Part (c):** Use the series for **approximation**. Identify whether the series is alternating to use the Alternating Series Error Bound, or use the Lagrange Error Bound.

**Part (d):** Find a **related series** (e.g., use the series for $f(x)$ to find the series for $f'(x)$, $f(x^2)$, or $\displaystyle\int f(x)\, dx$) by differentiating or integrating term-by-term.

**Distinguishing the Two Error Bounds:**

- **Alternating Series Error Bound**: Use when the series is alternating AND converges by AST. The error $\leq$ first omitted term. *Simple and always preferred when applicable.*
- **Lagrange Error Bound**: Use when the series is NOT alternating, or when you need an upper bound with a specific value of $M$. Requires finding a bound on the $(n+1)$-th derivative.

### The "Trap" List

- **The $n$-th Term Test proves convergence? No.** If $\lim a_n = 0$, the test is **inconclusive** — the series may still diverge (harmonic series). The test only proves **divergence** when the limit is nonzero.
- **Ratio Test equals 1 → conclusion?** When $L = 1$, the Ratio Test is **completely inconclusive**. You must use a different test.
- **Forgetting to check endpoints of the interval of convergence.** The Ratio Test gives an open interval. Each endpoint is a separate convergence question requiring a separate test. Losing both endpoint points is a common 2-point loss on the FRQ.
- **Using the Lagrange Error Bound with the wrong $n$.** If you use a 3rd-degree polynomial, then $n = 3$ and the bound uses $\dfrac{M}{4!}|x-a|^4$.
- **Alternating Series Error Bound: the series must actually converge first.** You must verify the AST conditions (terms decrease to zero) before applying the error bound.
- **Term-by-term differentiation/integration changes the radius of convergence? Not for open intervals.** The radius $R$ stays the same after differentiation or integration, but **endpoint behavior can change** — recheck endpoints.
- **Computing Taylor series from scratch via derivatives when a known series can be substituted.** Deriving the Taylor series for $\cos(x^2)$ by taking eight derivatives of $\cos(x^2)$ is unnecessary and error-prone. Substitute $x^2$ for $x$ in the cosine Maclaurin series in 10 seconds.
- **Misidentifying the general term.** When writing $\sin x = x - \dfrac{x^3}{6} + \cdots$, the general term is $\dfrac{(-1)^n x^{2n+1}}{(2n+1)!}$ starting at $n = 0$. Off-by-one errors in the starting index are extremely common.

---

## Master Quick-Reference: The Non-Negotiable Memorization List

These are the items that appear on virtually every AP Calculus BC exam. If you do not have these memorized cold, you will lose points on time-pressure calculations.

**Derivatives to Know Instantly:**

$$\frac{d}{dx}[\tan x] = \sec^2 x \qquad \frac{d}{dx}[\sec x] = \sec x \tan x$$

$$\frac{d}{dx}[\arctan x] = \frac{1}{1+x^2} \qquad \frac{d}{dx}[\arcsin x] = \frac{1}{\sqrt{1-x^2}}$$

**The Five Maclaurin Series:** $e^x$, $\sin x$, $\cos x$, $\dfrac{1}{1-x}$, $\ln(1+x)$. Know the general term, the first four nonzero terms, and the interval of convergence for each.

**Convergence Test Decision Tree:**
1. Check $n$-th term first — if limit $\neq 0$, diverges immediately.
2. Is it geometric? Use geometric series test.
3. Is it a $p$-series? Use $p$-series test.
4. Does it alternate? Try AST.
5. Does it have factorials or exponentials? Use Ratio Test.
6. Does it look like a rational function? Use LCT with a $p$-series.

**Area Formula Checklist:**
- Area (Cartesian): $\displaystyle\int [f(x) - g(x)]\, dx$
- Area (Polar): $\dfrac{1}{2}\displaystyle\int r^2\, d\theta$
- Disk: $\pi\displaystyle\int [f(x)]^2\, dx$
- Washer: $\pi\displaystyle\int [(R)^2 - (r)^2]\, dx$
- Arc Length: $\displaystyle\int \sqrt{1 + [f'(x)]^2}\, dx$
- Speed (parametric): $\displaystyle\int \sqrt{(x')^2 + (y')^2}\, dt$

---

