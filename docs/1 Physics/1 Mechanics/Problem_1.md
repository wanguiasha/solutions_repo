# Investigating the Range as a Function of the Angle of Projection

## Motivation

Projectile motion is a fundamental concept in physics, offering a rich exploration of basic principles. While the problem—analyzing the range of a projectile based on its launch angle—appears simple, it involves complex relationships and versatile applications. The equations governing this motion involve linear and quadratic relationships, providing valuable insights.

The presence of free parameters like initial velocity, gravitational acceleration, and launch height leads to a diverse set of solutions, accurately describing various real-world phenomena, from the trajectory of a soccer ball to the path of a rocket.

## Task

1.  **Theoretical Foundation:** Derive the governing equations of motion from fundamental principles, solving a basic differential equation to establish the general form of the motion. Highlight how variations in initial conditions lead to a family of solutions.
2.  **Analysis of the Range:** Investigate the horizontal range's dependence on the angle of projection. Discuss how changes in other parameters, such as initial velocity and gravitational acceleration, influence this relationship.
3.  **Practical Applications:** Reflect on how this model can be adapted to describe various real-world situations, such as projectiles launched on uneven terrain or in the presence of air resistance.
4.  **Implementation:** Develop a computational tool or algorithm to simulate projectile motion and visualize the range as a function of the angle of projection for different sets of initial conditions.

## Deliverables

* A Markdown document with Python script or notebook implementing the simulations.
* A detailed description of the family of solutions derived from the governing equations.
* Graphical representations of the range versus angle of projection, highlighting how different parameters influence the curve.
* A discussion on the limitations of the idealized model and suggestions for incorporating more realistic factors, such as drag or wind.

## 1. Theoretical Foundation

### Derivation of Governing Equations

We begin with Newton's second law, breaking the motion into horizontal ($x$) and vertical ($y$) components.

* **Assumptions:**
    * Neglect air resistance.
    * Constant gravitational acceleration ($g$) acting downwards.
    * Initial velocity ($v_0$) at an angle ($\theta$) with respect to the horizontal.
* **Initial Conditions:**
    * Initial position: $(x_0, y_0) = (0, 0)$
    * Initial velocity: $(v_{0x}, v_{0y}) = (v_0 \cos(\theta), v_0 \sin(\theta))$
* **Equations of Motion:**
    * Horizontal acceleration: $a_x = 0$
    * Vertical acceleration: $a_y = -g$
* **Integration:**
    * Horizontal velocity: $v_x = \int a_x dt = v_{0x} = v_0 \cos(\theta)$
    * Vertical velocity: $v_y = \int a_y dt = -gt + v_{0y} = -gt + v_0 \sin(\theta)$
    * Horizontal position: $x = \int v_x dt = v_0 \cos(\theta) t$
    * Vertical position: $y = \int v_y dt = -\frac{1}{2}gt^2 + v_0 \sin(\theta) t$

### Family of Solutions

The equations $x(t) = v_0 \cos(\theta) t$ and $y(t) = -\frac{1}{2}gt^2 + v_0 \sin(\theta) t$ represent a family of solutions parameterized by $v_0$ and $\theta$. Varying these parameters leads to different trajectories.

## 2. Analysis of the Range

### Range Equation

To find the range ($R$), we need to find the horizontal distance traveled when the projectile returns to the ground ($y = 0$).

1.  Set $y = 0$: $-\frac{1}{2}gt^2 + v_0 \sin(\theta) t = 0$
2.  Solve for $t$: $t(v_0 \sin(\theta) - \frac{1}{2}gt) = 0$
3.  The solutions are $t = 0$ (initial time) and $t = \frac{2v_0 \sin(\theta)}{g}$ (time of flight).
4.  Substitute the time of flight into the horizontal position equation: $R = x = v_0 \cos(\theta) \left( \frac{2v_0 \sin(\theta)}{g} \right)$
5.  Simplify: $R = \frac{v_0^2 \sin(2\theta)}{g}$

### Influence of Parameters

* **Angle of Projection ($\theta$):** The range is maximized when $\sin(2\theta) = 1$, which occurs when $2\theta = 90^\circ$, or $\theta = 45^\circ$.
* **Initial Velocity ($v_0$):** The range is proportional to the square of the initial velocity. Higher initial velocities result in significantly greater ranges.
* **Gravitational Acceleration ($g$):** The range is inversely proportional to gravitational acceleration. On planets with lower gravity, projectiles travel farther.

## 3. Practical Applications

* **Sports:** Optimizing the launch angle in sports like golf, baseball, and football to maximize distance.
* **Military:** Calculating the trajectory of artillery shells and rockets.
* **Engineering:** Designing systems for launching objects, such as fireworks or water jets.
* **Uneven Terrain:** For uneven terrain, the y=0 condition would change to y=h, where h is the elevation of the landing point.
* **Air Resistance:** Air resistance introduces a drag force, which can significantly alter the trajectory. This requires more complex models involving differential equations with drag terms.
* **Wind:** Wind adds a velocity component that affects both horizontal and vertical motion.

## 4. Implementation

```python
import numpy as np
import matplotlib.pyplot as plt

def projectile_range(v0, theta_deg, g=9.81):
    """Calculates the range of a projectile."""
    theta_rad = np.radians(theta_deg)
    return (v0**2 * np.sin(2 * theta_rad)) / g

def plot_range_vs_angle(v0, g=9.81):
    """Plots the range as a function of the angle of projection."""
    theta_deg = np.linspace(0, 90, 100)
    ranges = projectile_range(v0, theta_deg, g)

    plt.figure(figsize=(10, 6))
    plt.plot(theta_deg, ranges)
    plt.title(f"Range vs. Angle of Projection (v0={v0} m/s, g={g} m/s^2)")
    plt.xlabel("Angle of Projection (degrees)")
    plt.ylabel("Range (meters)")
    plt.grid(True)
    plt.show()

# Example usage
v0_values = [10, 20, 30]
for v0 in v0_values:
    plot_range_vs_angle(v0)

#Example with different gravity
plot_range_vs_angle(20, g = 3.71) #Mars gravity

![alt text](Figure_1-1.png)
