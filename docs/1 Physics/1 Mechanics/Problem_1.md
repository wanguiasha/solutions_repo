## Projectile Motion Analysis

## 1. Theoretical Foundation

We start with Newton's second law, $\vec{F} = m\vec{a}$. Assuming only gravity acts on the projectile, we have:

* $\vec{F} = m\vec{g}$, where $\vec{g} = (0, -g)$ (assuming the y-axis is upward).
* Therefore, $\vec{a} = \vec{g}$.

Since acceleration is the second derivative of position, we have:

* $\frac{d^2\vec{r}}{dt^2} = \vec{g}$.

Integrating twice with respect to time, we get:

* $\frac{d\vec{r}}{dt} = \vec{v}_0 + \vec{g}t$ (velocity equation).
* $\vec{r} = \vec{r}_0 + \vec{v}_0t + \frac{1}{2}\vec{g}t^2$ (position equation).

Let's break this into components, assuming the initial position $\vec{r}_0 = (0, 0)$:

* $x(t) = v_{0x}t = v_0\cos(\theta)t$
* $y(t) = v_{0y}t - \frac{1}{2}gt^2 = v_0\sin(\theta)t - \frac{1}{2}gt^2$

Where:

* $v_0$ is the initial speed.
* $\theta$ is the launch angle.
* $g$ is the acceleration due to gravity.

## 2. Analysis of the Range

To find the range (R), we set $y(t) = 0$ and solve for $t$ (time of flight):

* $0 = v_0\sin(\theta)t - \frac{1}{2}gt^2$
* $t = \frac{2v_0\sin(\theta)}{g}$

Substituting this into the $x(t)$ equation:

* $R = x(t) = v_0\cos(\theta) \cdot \frac{2v_0\sin(\theta)}{g} = \frac{v_0^2\sin(2\theta)}{g}$

**Influence of Parameters:**

* **Initial Velocity ($v_0$)**: Range is proportional to $v_0^2$. Higher initial velocity leads to a significantly larger range.
* **Launch Angle ($\theta$)**: The range is maximum when $\sin(2\theta) = 1$, i.e., $2\theta = 90^\circ$ or $\theta = 45^\circ$.
* **Gravitational Acceleration ($g$)**: Range is inversely proportional to $g$. On a planet with lower gravity, the range will be greater.

## 3. Practical Applications

* **Uneven Terrain**: We can adjust the initial y position of the projectile, to simulate a launch from a hill.
* **Air Resistance**: We can add a drag force term to the equations of motion, which is proportional to velocity (or velocity squared). This makes the equations more complex and requires numerical solutions.
* **Wind**: We can add a horizontal velocity component due to wind, affecting the x equation.
* **Rocketry**: We can model rocket trajectories by considering variable mass, thrust, and changing gravity with altitude.
* **Sports**: The trajectory of balls in sports like baseball, golf, and soccer can be modeled using these principles, with adjustments for spin and air resistance.

## 4. Implementation

Here's a Python script to simulate projectile motion and plot the range vs. launch angle:

```python
import numpy as np
import matplotlib.pyplot as plt

def projectile_range(v0, theta_deg, g=9.81):
    """Calculates the range of a projectile."""
    theta_rad = np.radians(theta_deg)
    return (v0**2 * np.sin(2 * theta_rad)) / g

def plot_range_vs_angle(v0, g=9.81):
    """Plots the range vs. launch angle."""
    angles = np.linspace(0, 90, 100)
    ranges = [projectile_range(v0, angle, g) for angle in angles]
    plt.plot(angles, ranges)
    plt.xlabel('Launch Angle (degrees)')
    plt.ylabel('Range (meters)')
    plt.title(f'Range vs. Launch Angle (v0={v0} m/s, g={g} m/s^2)')
    plt.grid(True)
    plt.savefig('projectile_range_plot.png') # Save the plot as an image
    plt.show()

# Example usage
plot_range_vs_angle(20)
![projectile_range_plot](https://github.com/user-attachments/assets/31a1c74d-f54d-4013-8252-ff11da3ebd5e)
