# Problem 1: Investigating the Range as a Function of the Angle of Projection

## 1. Motivation

Projectile motion is an essential concept in physics, describing the motion of an object launched into the air under the influence of gravity. This project investigates how the range of a projectile depends on its launch angle. Understanding this relationship is crucial for applications like sports and engineering.

## 2. Theory

The range \( R \) of a projectile launched with initial velocity \( v_0 \) at an angle \( \theta \) is given by the equation:

\[
R = \frac{v_0^2 \sin(2\theta)}{g}
\]

Where:
- \( v_0 \) = Initial velocity (m/s)
- \( \theta \) = Launch angle (degrees)
- \( g \) = Gravitational acceleration (9.81 m/s²)

This formula shows that the range of a projectile depends on the launch angle, and is maximized at 45°.

## 3. Python Code

The following Python code simulates projectile motion and calculates the range for different launch angles. The code also plots the range as a function of the angle.

```python
import numpy as np
import matplotlib.pyplot as plt

# Constants
v0 = 20  # Initial velocity in m/s
g = 9.81  # Gravitational acceleration in m/s²

# Angle values (0 to 90 degrees)
angles_deg = np.linspace(0, 90, 500)  # Generating angles between 0° and 90°
angles_rad = np.radians(angles_deg)  # Converting angles from degrees to radians

# Calculating the range for each angle
ranges = (v0**2) * np.sin(2 * angles_rad) / g

# Plotting the graph
plt.figure(figsize=(10, 6))
plt.plot(angles_deg, ranges, label=f'v₀ = {v0} m/s')  # Range vs angle plot
plt.axvline(45, color='red', linestyle='--', label='Max Range at 45°')  # Highlight 45°
plt.title("Projectile Range vs. Angle of Projection")
plt.xlabel("Angle (degrees)")
plt.ylabel("Range (meters)")
plt.grid(True)
plt.legend()

# Save the plot as an image
plt.savefig('Problem_1/projectile_range.png')

# Show the plot
plt.show()


---

### **Step 3: Run the Python Code**

Next, let's write and run the Python code that simulates the projectile motion and generates the plot.

1. **Run the Python code**: This will create a graph and save it as `projectile_range.png`.

2. The code will produce a plot and save it in the `Problem_1` folder.

---

### **Step 4: Upload the Image to GitHub**

Once you have the image (`projectile_range.png`), **upload it to your GitHub repository**:

1. Go to your GitHub repository and navigate to the `Problem_1` folder.
2. Upload the image file (`projectile_range.png`) into the `Problem_1` folder.
3. Alternatively, if you’re working locally, you can copy the image into the appropriate folder and then **commit** it to your repository:

```bash
git add Problem_1/projectile_range.png
git commit -m "Added projectile range plot"
git push origin main

![Projectile Range Plot](projectile_range.png)

