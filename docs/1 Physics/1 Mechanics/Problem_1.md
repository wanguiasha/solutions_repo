# Problem 1

# Projectile Motion: Analyzing Range vs. Angle of Projection

## Problem Overview
Projectile motion, while seemingly simple, offers a rich playground for exploring fundamental principles of physics. The task is to analyze how the range of a projectile depends on its angle of projection. This involves understanding how variations in parameters such as initial velocity, gravitational acceleration, and launch height impact the motion and range of the projectile.

## 1. Theoretical Foundation

### Governing Equations
The motion of a projectile can be described using the following fundamental equations of motion:

1. Horizontal motion (constant velocity):
   \[
   x(t) = v_0 \cdot \cos(\theta) \cdot t
   \]

2. Vertical motion (acceleration due to gravity):
   \[
   y(t) = v_0 \cdot \sin(\theta) \cdot t - \frac{1}{2} \cdot g \cdot t^2
   \]

Where:
- \( v_0 \) = initial velocity
- \( \theta \) = launch angle
- \( g \) = gravitational acceleration
- \( t \) = time

These equations are derived from the basic laws of motion under constant acceleration.

### Family of Solutions
The solution to projectile motion depends on the initial velocity, the launch angle, and gravitational acceleration. Changing any of these parameters results in different trajectories and ranges, leading to a wide variety of possible outcomes.

## 2. Analysis of the Range

### Horizontal Range as a Function of the Launch Angle
The horizontal range \( R \) of a projectile is given by the following equation:
\[
R = \frac{v_0^2 \sin(2\theta)}{g}
\]

- The range is maximized when \( \theta = 45^\circ \).
- If \( \theta \) is too small or too large, the range decreases.

### Effect of Initial Velocity and Gravitational Acceleration
- **Initial Velocity (\( v_0 \))**: A higher initial velocity increases the range.
- **Gravitational Acceleration (\( g \))**: A larger gravitational acceleration reduces the range. On the Moon, for example, with lower gravity, the range is greater for the same initial velocity and launch angle.

## 3. Practical Applications

### Real-World Adaptations
This model can be adapted to real-world scenarios by considering:
- **Uneven terrain**: If the projectile is launched from or lands on a hill, the equations need to account for the change in height.
- **Air resistance**: In real-world scenarios, drag forces affect the range, and these can be modeled with more complex differential equations that include air drag coefficients.

## 4. Implementation

### Python Script for Projectile Motion Simulation
```python
import numpy as np
import matplotlib.pyplot as plt

# Constants
g = 9.81  # Gravitational acceleration (m/s^2)

# Function to calculate the range
def calculate_range(v0, angle):
    # Convert angle to radians
    angle_rad = np.radians(angle)
    
    # Calculate range
    range_ = (v0**2 * np.sin(2 * angle_rad)) / g
    return range_

# Function to plot the range vs. angle
def plot_range_vs_angle(v0):
    angles = np.linspace(0, 90, 100)  # Angles from 0 to 90 degrees
    ranges = [calculate_range(v0, angle) for angle in angles]
    
    plt.figure(figsize=(10, 6))
    plt.plot(angles, ranges, label=f'Initial Velocity = {v0} m/s')
    plt.title('Range vs. Launch Angle')
    plt.xlabel('Launch Angle (degrees)')
    plt.ylabel('Range (meters)')
    plt.grid(True)
    plt.legend()
    plt.show()

# Example usage
v0 = 50  # Initial velocity in m/s
plot_range_vs_angle(v0)
