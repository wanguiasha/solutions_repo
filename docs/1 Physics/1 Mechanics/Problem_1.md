# Problem 1# Investigating the Range as a Function of the Angle of Projection

## 1. Theoretical Foundation

Projectile motion involves both horizontal and vertical motion. The key equations governing projectile motion (without air resistance) are derived from basic kinematics.

### Horizontal Motion:
\[
x(t) = v_0 \cdot \cos(\theta) \cdot t
\]

### Vertical Motion:
\[
y(t) = v_0 \cdot \sin(\theta) \cdot t - \frac{1}{2} g t^2
\]

Where:
- \( v_0 \) is the initial velocity,
- \( \theta \) is the launch angle,
- \( g \) is the gravitational acceleration (9.8 m/s²).

### Range of the Projectile:
The **range** \( R \) is the horizontal distance traveled by the projectile when it reaches the ground. The time of flight \( t_f \) is given by:
\[
t_f = \frac{2 v_0 \sin(\theta)}{g}
\]

Substituting this into the horizontal motion equation:
\[
R(\theta) = \frac{v_0^2 \sin(2\theta)}{g}
\]

The range depends on the angle \( \theta \) and reaches its maximum at \( \theta = 45^\circ \).

---

## 2. Analysis of the Range

The range varies with the angle of projection. For any initial velocity \( v_0 \), the optimal launch angle for the maximum range is 45°. We can observe the relationship between the range and angle through a graph.

Changes in initial velocity \( v_0 \) and gravitational acceleration \( g \) also affect the range. Higher initial velocity or lower gravitational acceleration results in a longer range.

---

## 3. Practical Applications

This model is applicable in real-world scenarios such as:
- Sports (e.g., soccer, basketball),
- Engineering (e.g., launching projectiles),
- Space exploration (e.g., rocket trajectories).

However, it assumes no air resistance and level ground, which limits its realism in some cases.

---

## 4. Code Implementation

Below is the Python code used to simulate projectile motion and plot the range vs angle graph.

```python
import numpy as np
import matplotlib.pyplot as plt

# Constants
v_0 = 30  # Initial velocity in m/s
g = 9.8  # Gravitational acceleration in m/s²

# Range of angles
angles = np.linspace(0, 90, 100)

# Calculate the range as a function of angle
ranges = (v_0**2 * np.sin(np.radians(2*angles))) / g

# Plot the range vs angle
plt.figure(figsize=(10, 6))
plt.plot(angles, ranges)
plt.title("Range vs. Angle of Projection")
plt.xlabel("Angle of Projection (degrees)")
plt.ylabel("Range (meters)")
plt.grid(True)

# Save the plot as an image
plt.savefig("range_vs_angle.png")

# Show the plot (optional)
plt.show()


### **3. View the Plot in Markdown**

When you open the Markdown file (in a Markdown viewer or GitHub), you should see the graph embedded in the document.

---

### **4. Push to GitHub (If Needed)**

If you want to push the updated **Markdown file** and **image** to **GitHub**, follow these steps:

1. **Add the image and markdown file to Git**:
   - If the image (`range_vs_angle.png`) and your Markdown file are in the same folder, just add them to the repository.

2. **Commit the changes**:
   ```bash
   git add .
   git commit -m "Add graph to markdown notes"
