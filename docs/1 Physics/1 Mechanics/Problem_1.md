# Theoretical Foundation of Projectile Motion

## Introduction
Projectile motion is a fundamental concept in classical mechanics, governed by Newton’s laws under the influence of gravity. This section establishes the theoretical framework by deriving the equations of motion from first principles, decomposing initial conditions, and solving the resulting differential equations. We assume an idealized scenario with no air resistance and constant gravitational acceleration, providing a baseline for analyzing the range as a function of the angle of projection.

---

## Newton’s Second Law Applied to Projectile Motion
Newton’s second law, $\vec{F} = m\vec{a}$, describes the motion of a projectile under gravity. For a projectile of mass $m$, the only force acting is gravity, directed vertically downward. We define a Cartesian coordinate system where $x$ is horizontal (positive to the right) and $y$ is vertical (positive upward). The gravitational force is:

$$
\vec{F} = -mg\hat{j}
$$

where $g$ is the gravitational acceleration ($g \approx 9.81 \, \text{m/s}^2$) and $\hat{j}$ is the unit vector in the $y$-direction. Since no forces act horizontally (in the absence of air resistance), the net force components are:

$$
F_x = 0, \quad F_y = -mg
$$

Applying Newton’s second law in each direction:

$$
m \frac{d^2 x}{dt^2} = 0, \quad m \frac{d^2 y}{dt^2} = -mg
$$

Simplifying by dividing through by $m$ (assuming $m \neq 0$):

$$
\frac{d^2 x}{dt^2} = 0, \quad \frac{d^2 y}{dt^2} = -g
$$

These second-order differential equations govern the projectile’s motion in two dimensions.

---

## Decomposition of Initial Velocity
The projectile is launched with an initial speed $v_0$ at an angle $\theta$ to the horizontal. Using trigonometry, the initial velocity vector $\vec{v}_0$ is resolved into horizontal and vertical components:

$$
v_{0x} = v_0 \cos\theta, \quad v_{0y} = v_0 \sin\theta
$$

At $t = 0$, assuming the launch point is at the origin $(x_0, y_0) = (0, 0)$, the initial conditions are:

$$
x(0) = 0, \quad y(0) = 0, \quad \frac{dx}{dt}(0) = v_0 \cos\theta, \quad \frac{dy}{dt}(0) = v_0 \sin\theta
$$

These components dictate the projectile’s trajectory, with $v_{0x}$ driving horizontal motion and $v_{0y}$ opposing gravity in the vertical direction.

---

## Differential Equations of Motion
The equations $\frac{d^2 x}{dt^2} = 0$ and $\frac{d^2 y}{dt^2} = -g$ are solved independently due to the decoupling of horizontal and vertical motion.

### Horizontal Motion
For the $x$-direction:

$$
\frac{d^2 x}{dt^2} = 0
$$

Integrate with respect to time:

$$
\frac{dx}{dt} = \int 0 \, dt = C_1
$$

where $C_1$ is a constant. Using the initial condition $\frac{dx}{dt}(0) = v_0 \cos\theta$:

$$
\frac{dx}{dt} = v_0 \cos\theta
$$

Integrate again:

$$
x(t) = \int (v_0 \cos\theta) \, dt = v_0 \cos\theta \cdot t + C_2
$$

With $x(0) = 0$:

$$
x(0) = 0 = v_0 \cos\theta \cdot 0 + C_2 \implies C_2 = 0
$$

Thus:

$$
x(t) = v_0 \cos\theta \cdot t
$$

### Vertical Motion
For the $y$-direction:

$$
\frac{d^2 y}{dt^2} = -g
$$

Integrate:

$$
\frac{dy}{dt} = \int -g \, dt = -gt + C_3
$$

Using $\frac{dy}{dt}(0) = v_0 \sin\theta$:

$$
v_0 \sin\theta = -g \cdot 0 + C_3 \implies C_3 = v_0 \sin\theta
$$

So:

$$
\frac{dy}{dt} = v_0 \sin\theta - gt
$$

Integrate again:

$$
y(t) = \int (v_0 \sin\theta - gt) \, dt = v_0 \sin\theta \cdot t - \frac{1}{2} g t^2 + C_4
$$

With $y(0) = 0$:

$$
y(0) = 0 = v_0 \sin\theta \cdot 0 - \frac{1}{2} g \cdot 0^2 + C_4 \implies C_4 = 0
$$

Thus:

$$
y(t) = v_0 \sin\theta \cdot t - \frac{1}{2} g t^2
$$

### General Solution
The position of the projectile as a function of time is:

$$
x(t) = v_0 \cos\theta \cdot t, \quad y(t) = v_0 \sin\theta \cdot t - \frac{1}{2} g t^2
$$

This parametric form describes a parabolic trajectory, with $x(t)$ linear and $y(t)$ quadratic in time.

---

## Key Variables and Parametric Dependence
The equations depend on several parameters:
- **Initial velocity ($v_0$)**: Scales both $x(t)$ and $y(t)$ linearly, increasing the range and height.
- **Angle of projection ($\theta$)**: Modulates the balance between horizontal and vertical components via $\cos\theta$ and $\sin\theta$.
- **Gravitational acceleration ($g$)**: Affects only the vertical motion, steepening the parabola as $g$ increases.
- **Initial height ($h$)**: If $y(0) = h \neq 0$, the vertical equation becomes:

$$
y(t) = h + v_0 \sin\theta \cdot t - \frac{1}{2} g t^2
$$

### Sensitivity Analysis
- Increasing $v_0$ amplifies the range and maximum height proportionally to $v_0^2$ (as derived later for range).
- Varying $\theta$ shifts energy between horizontal and vertical motion, with $\theta = 45^\circ$ often maximizing range (to be verified).
- Larger $g$ reduces flight time and range, compressing the trajectory.
- Non-zero $h$ extends flight time and alters the range, requiring a modified time-of-flight calculation.

---

## Discussion
These equations form a family of solutions parameterized by $v_0$, $\theta$, $g$, and $h$. The horizontal range, defined as $x(t)$ when $y(t) = 0$, depends critically on $\theta$, setting the stage for further analysis. This idealized model assumes no air resistance, a simplification to be revisited when considering real-world applications.

## References
- Goldstein, H., Poole, C., & Safko, J. (2002). *Classical Mechanics*. 3rd ed. Addison-Wesley.
- Taylor, J. R. (2005). *Classical Mechanics*. University Science Books.

# Analysis of the Range in Projectile Motion

## Introduction
The horizontal range of a projectile—the distance traveled along the ground before landing—is a key metric in understanding how launch parameters influence its trajectory. This section derives the range formula for a projectile launched from ground level, explores its dependence on the angle of projection, and examines the effects of varying initial velocity and gravitational acceleration. We aim to predict range behavior across a spectrum of angles and hypothesize the optimal angle for maximum range.

---

## Derivation of the Range Formula
For a projectile launched from ground level ($y_0 = 0$), the range $R$ is the horizontal distance $x(t)$ when the projectile returns to $y = 0$. From the theoretical foundation, the position equations are:

$$
x(t) = v_0 \cos\theta \cdot t, \quad y(t) = v_0 \sin\theta \cdot t - \frac{1}{2} g t^2
$$

where $v_0$ is the initial velocity, $\theta$ is the angle of projection, $g$ is gravitational acceleration, and $t$ is time.

### Time of Flight
The projectile lands when $y(t) = 0$. Set the vertical position to zero:

$$
v_0 \sin\theta \cdot t - \frac{1}{2} g t^2 = 0
$$

Factorize:

$$
t \left( v_0 \sin\theta - \frac{1}{2} g t \right) = 0
$$

This yields two solutions:
- $t = 0$ (launch time),
- $v_0 \sin\theta - \frac{1}{2} g t = 0$.

Solve the second:

$$
\frac{1}{2} g t = v_0 \sin\theta \implies t = \frac{2 v_0 \sin\theta}{g}
$$

This $t = \frac{2 v_0 \sin\theta}{g}$ is the time of flight, $T$, when the projectile returns to ground level.

### Horizontal Range
Substitute $T$ into the horizontal position equation:

$$
R = x(T) = v_0 \cos\theta \cdot T = v_0 \cos\theta \cdot \frac{2 v_0 \sin\theta}{g}
$$

Simplify using the trigonometric identity $2 \sin\theta \cos\theta = \sin 2\theta$:

$$
R = \frac{v_0^2 2 \sin\theta \cos\theta}{g} = \frac{v_0^2 \sin 2\theta}{g}
$$

Thus, the range formula is:

$$
R = \frac{v_0^2 \sin 2\theta}{g}
$$

This equation expresses $R$ as a function of $\theta$, $v_0$, and $g$, valid for a projectile launched and landing at the same height.

---

## Testing Projection Angles
To explore how $R$ varies with $\theta$, consider angles from $0^\circ$ to $90^\circ$:
- At $\theta = 0^\circ$: $\sin 2\theta = \sin 0^\circ = 0$, so $R = 0$ (no horizontal motion).
- At $\theta = 30^\circ$: $\sin 2\theta = \sin 60^\circ = \frac{\sqrt{3}}{2}$, so $R = \frac{v_0^2 \cdot \frac{\sqrt{3}}{2}}{g}$.
- At $\theta = 45^\circ$: $\sin 2\theta = \sin 90^\circ = 1$, so $R = \frac{v_0^2}{g}$ (potential maximum).
- At $\theta = 60^\circ$: $\sin 2\theta = \sin 120^\circ = \frac{\sqrt{3}}{2}$, so $R = \frac{v_0^2 \cdot \frac{\sqrt{3}}{2}}{g}$ (same as $30^\circ$).
- At $\theta = 90^\circ$: $\sin 2\theta = \sin 180^\circ = 0$, so $R = 0$ (straight up).

The symmetry around $45^\circ$ (e.g., $30^\circ$ and $60^\circ$ yield equal ranges) suggests a parabolic dependence of $R$ on $\theta$, peaking at $\sin 2\theta = 1$. A planned test of angles in increments (e.g., $0^\circ, 15^\circ, 30^\circ, 45^\circ, 60^\circ, 75^\circ, 90^\circ$) will confirm this trend.

---

## Influence of Other Parameters
The range depends on $v_0$ and $g$ alongside $\theta$. Analyze their effects:
- **Initial Velocity ($v_0$)**: $R \propto v_0^2$. Doubling $v_0$ quadruples $R$, as kinetic energy scales with $v_0^2$, extending both flight time and horizontal reach.
- **Gravitational Acceleration ($g$)**: $R \propto \frac{1}{g}$. Increasing $g$ reduces $R$ by shortening the flight time, $T = \frac{2 v_0 \sin\theta}{g}$, compressing the trajectory.

### Parametric Shifts
- Increasing $v_0$ stretches the range curve upward, maintaining the peak at $\theta = 45^\circ$.
- Increasing $g$ flattens the curve, reducing all ranges proportionally without altering the optimal angle.
- Combining changes (e.g., higher $v_0$, lower $g$) amplifies $R$ dramatically, useful for applications like artillery.

---

## Hypothesis for Maximum Range
The term $\sin 2\theta$ in $R = \frac{v_0^2 \sin 2\theta}{g}$ reaches its maximum of 1 when $2\theta = 90^\circ$, or $\theta = 45^\circ$. Thus, hypothesize that $\theta = 45^\circ$ maximizes $R$. Physically, this balances horizontal velocity ($v_0 \cos\theta$) and flight time (proportional to $v_0 \sin\theta$):
- At $\theta < 45^\circ$, higher $v_{0x}$ is offset by shorter $T$.
- At $\theta > 45^\circ$, longer $T$ is offset by lower $v_{0x}$.

To test, compute the derivative of $R$ with respect to $\theta$:

$$
\frac{dR}{d\theta} = \frac{d}{d\theta} \left( \frac{v_0^2 \sin 2\theta}{g} \right) = \frac{v_0^2}{g} \cdot 2 \cos 2\theta
$$

Set $\frac{dR}{d\theta} = 0$:

$$
2 \cos 2\theta = 0 \implies \cos 2\theta = 0 \implies 2\theta = 90^\circ \implies \theta = 45^\circ
$$

The second derivative, $\frac{d^2 R}{d\theta^2} = \frac{v_0^2}{g} \cdot (-4 \sin 2\theta)$, is negative at $\theta = 45^\circ$ ($\sin 90^\circ = 1$), confirming a maximum. This supports the hypothesis that $45^\circ$ optimizes range due to the interplay of horizontal and vertical motion components.

---

## Discussion
The range formula $R = \frac{v_0^2 \sin 2\theta}{g}$ encapsulates the projectile’s dependence on $\theta$, with a clear maximum at $45^\circ$ for ground-level launch and landing. Variations in $v_0$ and $g$ scale the range but preserve this optimum, highlighting the robustness of the result. Future analysis could explore non-zero launch heights, where symmetry breaks and the optimal angle shifts.

## References
- Goldstein, H., Poole, C., & Safko, J. (2002). *Classical Mechanics*. 3rd ed. Addison-Wesley.
- Taylor, J. R. (2005). *Classical Mechanics*. University Science Books.

## Codes and Plots

![alt text](image-1.png)

```python
import numpy as np
import matplotlib.pyplot as plt

# Constants
g = 9.81  # gravitational acceleration (m/s^2)
angles_deg = np.arange(0, 91, 5)  # angles from 0° to 90° in 5° increments
angles_rad = np.deg2rad(angles_deg)  # convert to radians
v0_values = [10, 20, 30]  # initial velocities (m/s)

# Calculate range for each v0
plt.figure(figsize=(10, 6))
for v0 in v0_values:
    R = (v0**2 * np.sin(2 * angles_rad)) / g
    plt.plot(angles_deg, R, label=f'$v_0 = {v0} \, \text{{m/s}}$')

# Plot settings
plt.xlabel('Angle of Projection ($^\circ$)')
plt.ylabel('Range (m)')
plt.title('Range vs. Angle for Different Initial Velocities ($g = 9.81 \, \text{m/s}^2$)')
plt.legend()
plt.grid(True)
plt.savefig('range_vs_angle_v0.png')  # Save for Markdown embedding
plt.show()
```

## Colab 

[Colab 1](https://colab.research.google.com/drive/1DPhWK40LB2ZhQ4Tf30tDa6CkUmWPynDH)
   