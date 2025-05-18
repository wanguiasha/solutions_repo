# Problem 1
# Experimental Physics Notes: Measuring Gravitational Acceleration with a Pendulum

**Date:** 02:07 PM CEST, Sunday, May 18, 2025  
**Prepared by:** Grok 3, xAI

## Section 1: Perform Calculations

This section details the mathematical framework for calculating the period ($T$) and gravitational acceleration ($g$) of a simple pendulum, using experimental data collected on May 18, 2025. The approach emphasizes precision, uncertainty propagation, and adherence to rigorous academic standards suitable for a Harvard-level experimental physics course.

### 1.1 Calculation of the Period ($T$)

The period of oscillation ($T$) is determined from the mean time for 10 oscillations ($\overline{T}_{10}$). Given the data for 10 sets of 10 oscillations—13.58 s, 12.44 s, 13.13 s, 13.34 s, 12.68 s, 12.44 s, 11.76 s, 11.53 s, 11.49 s, 10.88 s—we first compute the mean:

$$
\overline{T}_{10} = \frac{1}{n} \sum_{i=1}^{n} T_{10,i}
$$

Where:
- $T_{10,i}$ represents each measurement of time for 10 oscillations.
- $n = 10$ is the number of trials.

Summing the measurements:

$$
\sum_{i=1}^{10} T_{10,i} = 13.58 + 12.44 + 13.13 + 13.34 + 12.68 + 12.44 + 11.76 + 11.53 + 11.49 + 10.88 = 123.27 \, \text{s}
$$

Thus:

$$
\overline{T}_{10} = \frac{123.27}{10} = 12.327 \, \text{s}
$$

The period ($T$) is then:

$$
T = \frac{\overline{T}_{10}}{10} = \frac{12.327}{10} = 1.2327 \, \text{s}
$$

Next, we calculate the uncertainty in $\overline{T}_{10}$ ($\Delta T_{10}$). First, compute the standard deviation ($\sigma_T$):

$$
\sigma_T = \sqrt{\frac{1}{n-1} \sum_{i=1}^{n} (T_{10,i} - \overline{T}_{10})^2}
$$

The squared deviations are:

- $(13.58 - 12.327)^2 = 1.5625$
- $(12.44 - 12.327)^2 = 0.0128$
- $(13.13 - 12.327)^2 = 0.6456$
- $(13.34 - 12.327)^2 = 1.0276$
- $(12.68 - 12.327)^2 = 0.1250$
- $(12.44 - 12.327)^2 = 0.0128$
- $(11.76 - 12.327)^2 = 0.3215$
- $(11.53 - 12.327)^2 = 0.6340$
- $(11.49 - 12.327)^2 = 0.6845$
- $(10.88 - 12.327)^2 = 2.1132$

Sum of squared deviations:

$$
\sum_{i=1}^{10} (T_{10,i} - \overline{T}_{10})^2 = 1.5625 + 0.0128 + 0.6456 + 1.0276 + 0.1250 + 0.0128 + 0.3215 + 0.6340 + 0.6845 + 2.1132 = 7.1395
$$

Variance:

$$
\frac{\sum_{i=1}^{10} (T_{10,i} - \overline{T}_{10})^2}{n-1} = \frac{7.1395}{9} \approx 0.7933
$$

Standard deviation:

$$
\sigma_T = \sqrt{0.7933} \approx 0.8907 \, \text{s}
$$

The uncertainty in the mean ($\Delta T_{10}$) is:

$$
\Delta T_{10} = \frac{\sigma_T}{\sqrt{n}} = \frac{0.8907}{\sqrt{10}} \approx \frac{0.8907}{3.1623} \approx 0.2816 \, \text{s}
$$

Thus, the uncertainty in the period ($\Delta T$) is:

$$
\Delta T = \frac{\Delta T_{10}}{10} = \frac{0.2816}{10} = 0.02816 \, \text{s}
$$

### 1.2 Determination of Gravitational Acceleration ($g$)

The gravitational acceleration ($g$) is calculated using the simple pendulum formula:

$$
g = \frac{4 \pi^2 L}{T^2}
$$

Where:
- $\pi \approx 3.1415926535$.
- $L = 0.9 \, \text{m}$ (given).
- $T = 1.2327 \, \text{s}$ (from Section 1.1).

First, compute the denominator:

$$
T^2 = (1.2327)^2 \approx 1.5197 \, \text{s}^2
$$

Numerator:

$$
4 \pi^2 L = 4 \cdot (3.1415926535)^2 \cdot 0.9 \approx 4 \cdot 9.8696 \cdot 0.9 \approx 35.5306 \, \text{m}
$$

Thus:

$$
g = \frac{35.5306}{1.5197} \approx 23.38 \, \text{m/s}^2
$$

### 1.3 Uncertainty Propagation for $g$ (Additional Step for Completeness)

To provide a complete analysis, we propagate the uncertainty in $g$ ($\Delta g$) using:

$$
\frac{\Delta g}{g} = \sqrt{\left( \frac{\Delta L}{L} \right)^2 + \left( 2 \frac{\Delta T}{T} \right)^2}
$$

Given:
- $\Delta L = 0.005 \, \text{m}$.
- $\Delta T = 0.02816 \, \text{s}$.

Relative uncertainties:
- $\frac{\Delta L}{L} = \frac{0.005}{0.9} \approx 0.005556$
- $2 \frac{\Delta T}{T} = 2 \cdot \frac{0.02816}{1.2327} \approx 2 \cdot 0.02284 \approx 0.04568$

Combined relative uncertainty:

$$
\frac{\Delta g}{g} = \sqrt{(0.005556)^2 + (0.04568)^2} = \sqrt{0.00003086 + 0.0020868} \approx \sqrt{0.0021177} \approx 0.04602
$$

Absolute uncertainty:

$$
\Delta g = g \cdot \frac{\Delta g}{g} = 23.38 \cdot 0.04602 \approx 1.08 \, \text{m/s}^2
$$

### 1.4 Discussion of Results

The calculated $g \approx 23.38 \pm 1.08 \, \text{m/s}^2$ is significantly higher than the accepted value of $9.81 \, \text{m/s}^2$. This discrepancy suggests potential experimental errors, such as an incorrect pendulum length ($L$) measurement or systematic timing errors. The pendulum length $L = 0.9 \, \text{m}$ yields a theoretical period of $T \approx 1.9 \, \text{s}$ (using $T = 2\pi \sqrt{\frac{L}{g}}$), which is higher than the measured $1.2327 \, \text{s}$, indicating a need to verify the setup.

### 1.5 Key Considerations

- The small-angle approximation ($\theta < 15^\circ$) must hold for the formula $g = \frac{4 \pi^2 L}{T^2}$ to be valid.
- Systematic errors (e.g., air resistance, pivot friction) may affect $T$.
- Ensure $L$ is measured to the center of mass of the pendulum bob.

This analysis provides a rigorous framework for calculating $g$, suitable for advanced experimental physics studies.
# Experimental Physics Notes: Measuring Gravitational Acceleration with a Pendulum

**Date:** 02:09 PM CEST, Sunday, May 18, 2025  
**Prepared by:** Grok 3, xAI

## Section 2: Propagate Uncertainties

This section outlines the rigorous methodology for propagating uncertainties in the gravitational acceleration ($g$) derived from a simple pendulum experiment, conducted on May 18, 2025. The process adheres to advanced experimental physics standards, ensuring a comprehensive analysis suitable for a Harvard-level academic context.

### 2.1 Uncertainty Propagation for $g$ ($\Delta g$)

The uncertainty in the gravitational acceleration ($\Delta g$) is calculated using the propagation of errors for the functional relationship $g = \frac{4 \pi^2 L}{T^2}$. The formula for the relative uncertainty in $g$ is given by:

$$
\frac{\Delta g}{g} = \sqrt{\left( \frac{\Delta L}{L} \right)^2 + \left( 2 \frac{\Delta T}{T} \right)^2}
$$

Where:
- $\Delta g$ is the absolute uncertainty in $g$.
- $g = 23.38 \, \text{m/s}^2$ is the calculated gravitational acceleration.
- $\Delta L = 0.005 \, \text{m}$ is the uncertainty in the pendulum length.
- $L = 0.9 \, \text{m}$ is the measured pendulum length.
- $\Delta T = 0.02816 \, \text{s}$ is the uncertainty in the period.
- $T = 1.2327 \, \text{s}$ is the calculated period.
- The factor of 2
# Experimental Physics Notes: Measuring Gravitational Acceleration with a Pendulum

**Date:** 02:11 PM CEST, Sunday, May 18, 2025  
**Prepared by:** Grok 3, xAI

## Section 3: Analyze Results

This section provides a detailed comparison of the experimentally determined gravitational acceleration ($g$) with the accepted standard value, conducted on May 18, 2025. The analysis adheres to rigorous academic standards suitable for a Harvard-level experimental physics course, emphasizing statistical and physical interpretation.

### 3.1 Comparison of Measured and Standard $g$

The gravitational acceleration ($g$) measured from the pendulum experiment is $g = 23.38 \pm 1.08 \, \text{m/s}^2$, derived from the data collected. This value is compared against the internationally accepted standard gravitational acceleration at the Earth's surface, which is:

$$
g_{\text{standard}} = 9.81 \, \text{m/s}^2
$$

The relative difference between the measured $g$ and the standard $g_{\text{standard}}$ is calculated as:

$$
\text{Relative Difference} = \frac{|g - g_{\text{standard}}|}{g_{\text{standard}}} \cdot 100\%
$$

Substituting the values:

$$
\text{Relative Difference} = \frac{|23.38 - 9.81|}{9.81} \cdot 100\% = \frac{13.57}{9.81} \cdot 100\% \approx 138.33\%
$$

This indicates a significant deviation of approximately 138% from the standard value.

### 3.2 Statistical Significance

To assess the statistical significance of the discrepancy, consider the uncertainty in the measured $g$ ($\Delta g = 1.08 \, \text{m/s}^2$). The measured value is considered consistent with the standard value if $g_{\text{standard}}$ lies within the uncertainty range:

$$
g \pm \Delta g = 23.38 \pm 1.08 \, \text{m/s}^2
$$

The range is:

$$
22.30 \, \text{m/s}^2 \text{ to } 24.46 \, \text{m/s}^2
$$

Since $9.81 \, \text{m/s}^2$ falls outside this range, the measured $g$ is statistically inconsistent with the standard value at the $1\sigma$ confidence level (68% confidence).

### 3.3 Potential Sources of Discrepancy

The large deviation suggests systematic errors or experimental misconfigurations. Key factors to investigate include:
- **Pendulum Length ($L$)**: The assumed $L = 0.9 \, \text{m}$ yields a theoretical period $T = 2\pi \sqrt{\frac{L}{g_{\text{standard}}}} \approx 1.9 \, \text{s}$ (using $g_{\text{standard}} = 9.81 \, \text{m/s}^2$), whereas the measured $T = 1.2327 \, \text{s}$ is lower. This discrepancy implies $L$ may be underestimated or mismeasured.
- **Small-Angle Approximation**: The formula $g = \frac{4 \pi^2 L}{T^2}$ assumes oscillations with an amplitude less than $15^\circ$. If exceeded, the period increases, affecting $g$.
- **Timing Accuracy**: Human reaction time or stopwatch resolution may introduce errors in the measured times (e.g., 13.58 s, 12.44 s, etc.), skewing $\overline{T}_{10}$.

### 3.4 Adjusted Theoretical Check

Using the measured $T = 1.2327 \, \text{s}$ and solving for $g$ with $L = 0.9 \, \text{m}$:

$$
g = \frac{4 \pi^2 L}{T^2} = \frac{4 \cdot (3.1416)^2 \cdot 0.9}{(1.2327)^2} \approx 23.38 \, \text{m/s}^2
$$

This confirms the calculation, but the inconsistency with $9.81 \, \text{m/s}^2$ suggests $L$ should be re-evaluated. If $g = 9.81 \, \text{m/s}^2$, the expected $L$ would be:

$$
L = \frac{g T^2}{4 \pi^2} = \frac{9.81 \cdot (1.2327)^2}{4 \cdot (3.1416)^2} \approx 0.376 \, \text{m}
$$

This indicates the measured $L = 0.9 \, \text{m}$ may be incorrect, possibly due to measurement error or misalignment.

### 3.5 Conclusion and Recommendations

The measured $g = 23.38 \pm 1.08 \, \text{m/s}^2$ is not consistent with $g_{\text{standard}} = 9.81 \, \text{m/s}^2$, with a relative error exceeding the uncertainty bounds. Recommendations include:
- Recheck $L$ measurement to the center of mass.
- Ensure oscillation amplitude remains below $15^\circ$.
- Use a more precise timing method to reduce $\Delta T$.

This analysis underscores the importance of systematic error identification in experimental physics.
# Experimental Physics Notes: Measuring Gravitational Acceleration with a Pendulum

## Section 4: Discuss Findings

This section provides a critical evaluation of the experimental findings from the pendulum-based measurement of gravitational acceleration ($g$), conducted on May 18, 2025. The discussion addresses the impact of measurement resolution on length uncertainty ($\Delta L$), the variability in timing and its effect on period uncertainty ($\Delta T$), and the underlying assumptions and limitations. The analysis meets the rigorous standards expected in a Harvard-level experimental physics course.

### 4.1 Effect of Measurement Resolution on $\Delta L$

The uncertainty in the pendulum length ($\Delta L$) is determined by the resolution of the measuring tool, typically defined as half the smallest division. Given $\Delta L = 0.005 \, \text{m}$ and $L = 0.9 \, \text{m}$, the resolution is:

$$
\text{Resolution} = 2 \cdot \Delta L = 2 \cdot 0.005 = 0.01 \, \text{m}
$$

This suggests a ruler or measuring tape with a minimum division of 1 cm was used. The relative uncertainty in length is:

$$
\frac{\Delta L}{L} = \frac{0.005}{0.9} \approx 0.005556
$$

This small relative uncertainty (approximately 0.56%) indicates that the resolution has a minimal direct impact on the overall $g$ calculation. However, any systematic offset in $L$ (e.g., misjudging the center of mass) could amplify errors, as $g \propto L$. For instance, a 1 cm error in $L = 0.9 \, \text{m}$ (a 1.11% change) would alter $g$ by approximately 2.22%, highlighting the need for precise alignment despite the low $\Delta L$.

### 4.2 Variability in Timing and Its Impact on $\Delta T$

The variability in timing is assessed through the standard deviation ($\sigma_T$) of the 10 oscillation time measurements: 13.58 s, 12.44 s, 13.13 s, 13.34 s, 12.68 s, 12.44 s, 11.76 s, 11.53 s, 11.49 s, 10.88 s. The mean ($\overline{T}_{10}$) is $12.327 \, \text{s}$, and the standard deviation is calculated as:

$$
\sigma_T = \sqrt{\frac{1}{n-1} \sum_{i=1}^{n} (T_{10,i} - \overline{T}_{10})^2}
$$

With the sum of squared deviations approximately $7.1395$ (as computed earlier), the variance is:

$$
\frac{7.1395}{9} \approx 0.7933
$$

Thus:

$$
\sigma_T = \sqrt{0.7933} \approx 0.8907 \, \text{s}
$$

The uncertainty in the mean time ($\Delta T_{10}$) is:

$$
\Delta T_{10} = \frac{\sigma_T}{\sqrt{n}} = \frac{0.8907}{\sqrt{10}} \approx 0.2816 \, \text{s}
$$

And the uncertainty in the period ($\Delta T$) is:

$$
\Delta T = \frac{\Delta T_{10}}{10} = \frac{0.2816}{10} = 0.02816 \, \text{s}
$$

The relative uncertainty in $T$ is:

$$
\frac{\Delta T}{T} = \frac{0.02816}{1.2327} \approx 0.02284
$$

This variability, amplified by the factor of 2 in the $g$ uncertainty propagation ($\frac{\Delta g}{g} \propto 2 \frac{\Delta T}{T}$), contributes significantly to $\Delta g$. The standard deviation ($\sigma_T = 0.8907 \, \text{s}$) suggests human reaction time or stopwatch precision (likely on the order of 0.1–0.5 s) as primary sources, impacting the reliability of $g = 23.38 \pm 1.08 \, \text{m/s}^2$.

### 4.3 Assumptions and Experimental Limitations

Several assumptions and limitations underpin this experiment:
- **Small-Angle Approximation**: The formula $g = \frac{4 \pi^2 L}{T^2}$ assumes oscillations with amplitude $\theta < 15^\circ$. If exceeded, the period increases nonlinearly (e.g., $T \approx 2\pi \sqrt{\frac{L}{g}} (1 + \frac{\theta^2}{16})$ for small $\theta$ in radians), skewing $g$.
- **Ideal Pendulum Model**: The derivation assumes a massless string and point mass bob, neglecting air resistance and pivot friction, which dampen oscillations and slightly reduce $T$.
- **Measurement Precision**: The ruler resolution (0.01 m) and timing variability (0.8907 s) limit accuracy. Systematic errors (e.g., misaligning $L$ to the center of mass) may further distort results.
- **Environmental Factors**: Temperature-induced length changes or air currents could affect $L$ and $T$, though likely minimal in a controlled setting.

### 4.4 Synthesis and Implications

The effect of measurement resolution on $\Delta L$ is minor (0.56% relative uncertainty), but timing variability drives a larger $\Delta T$ (2.28% relative uncertainty), dominating $\Delta g$. The calculated $g = 23.38 \, \text{m/s}^2$ exceeds the standard $9.81 \, \text{m/s}^2$ by 138%, likely due to an overestimated $L$ or unaccounted systematic errors. Re-evaluating $L$ (e.g., $L \approx 0.376 \, \text{m}$ for $g = 9.81 \, \text{m/s}^2$ with $T = 1.2327 \, \text{s}$) and improving timing precision are recommended to align with theoretical expectations.

### 4.5 Recommendations

- Use a higher-resolution tool (e.g., 1 mm scale) to refine $\Delta L$.
- Employ automated timing (e.g., photogates) to reduce $\sigma_T$.
- Verify $\theta < 15^\circ$ and adjust $L$ measurement to the bob’s center of mass.

This discussion highlights the critical role of uncertainty analysis in interpreting experimental data in advanced physics.

# Experimental Physics Notes: Measuring Gravitational Acceleration with a Pendulum

**Date:** 02:20 PM CEST, Sunday, May 18, 2025  
**Prepared by:** Grok 3, xAI
# Experimental Physics Notes: Measuring Gravitational Acceleration with a Pendulum

**Date:** 02:22 PM CEST, Sunday, May 18, 2025  
**Prepared by:** Grok 3, xAI

## Section 6: Tabulated Data for 10 Trials and $T_{10}$

This section presents the raw timing data for the 10 trials of 10 oscillations each ($T_{10}$), along with the calculated mean time ($\overline{T}_{10}$), from the pendulum experiment conducted on May 18, 2025. The table is structured to provide a clear overview of the measurements, adhering to the rigorous academic standards expected in a Harvard-level experimental physics course.

### 6.1 Table of $T_{10}$ Measurements Across 10 Trials

| **Trial Number** | **$T_{10}$ (s)** | **Description**                       |
|------------------|------------------|---------------------------------------|
| 1                | 13.58            | Time for 10 oscillations in trial 1.  |
| 2                | 12.44            | Time for 10 oscillations in trial 2.  |
| 3                | 13.13            | Time for 10 oscillations in trial 3.  |
| 4                | 13.34            | Time for 10 oscillations in trial 4.  |
| 5                | 12.68            | Time for 10 oscillations in trial 5.  |
| 6                | 12.44            | Time for 10 oscillations in trial 6.  |
| 7                | 11.76            | Time for 10 oscillations in trial 7.  |
| 8                | 11.53            | Time for 10 oscillations in trial 8.  |
| 9                | 11.49            | Time for 10 oscillations in trial 9.  |
| 10               | 10.88            | Time for 10 oscillations in trial 10. |
| **Mean**         | **$\overline{T}_{10}$ = 12.327** | Mean time for 10 oscillations, calculated as $\overline{T}_{10} = \frac{\sum T_{10,i}}{10}$. |

### 6.2 Notes on the Data

- The $T_{10}$ values range from 10.88 s to 13.58 s, indicating variability in timing measurements, likely due to human reaction time or inconsistencies in pendulum release.
- The mean $\overline{T}_{10} = 12.327 \, \text{s}$ serves as the basis for calculating the period $T = \frac{\overline{T}_{10}}{10} = 1.2327 \, \text{s}$, which is used in determining $g$.
- Variability in $T_{10}$ suggests the need for more precise timing methods (e.g., photogates) to reduce uncertainty in subsequent calculations.

This table provides a concise summary of the raw timing data, facilitating further analysis of the experiment's reliability and precision.

## Codes And Plots
![alt text](image.png)
```python
import matplotlib.pyplot as plt

trials = ["Trial 1", "Trial 2", "Trial 3", "Trial 4", "Trial 5", "Trial 6", "Trial 7", "Trial 8", "Trial 9", "Trial 10"]
t10_values = [13.58, 12.44, 13.13, 13.34, 12.68, 12.44, 11.76, 11.53, 11.49, 10.88]
mean_t10 = 12.327
deviations = [t - mean_t10 for t in t10_values]

plt.figure(figsize=(10, 6))
plt.bar(trials, deviations, color='coral', edgecolor='black')
plt.xlabel('Trial Number')
plt.ylabel('Deviation from Mean T10 (s)')
plt.title('Deviations of T10 from Mean (12.327 s)')
plt.grid(True, linestyle='--', alpha=0.7)
plt.show()
```
![alt text](image-1.png)
```python
import matplotlib.pyplot as plt

trials = ["Trial 1", "Trial 2", "Trial 3", "Trial 4", "Trial 5", "Trial 6", "Trial 7", "Trial 8", "Trial 9", "Trial 10"]
t10_values = [13.58, 12.44, 13.13, 13.34, 12.68, 12.44, 11.76, 11.53, 11.49, 10.88]

plt.figure(figsize=(10, 6))
plt.plot(trials, t10_values, color='forestgreen', marker='o', linestyle='-', linewidth=2)
plt.xlabel('Trial Number')
plt.ylabel('Time for 10 Oscillations (s)')
plt.title('T10 Measurements Over 10 Trials')
plt.ylim(0, 15)
plt.grid(True, linestyle='--', alpha=0.7)
plt.show()
```
![alt text](image-2.png)
```python
import matplotlib.pyplot as plt

labels = ['Length Uncertainty', 'Period Uncertainty']
contributions = [0.005556, 0.04568]  # $\frac{\Delta L}{L} = 0.005/0.9$, $2 \cdot \frac{\Delta T}{T} = 2 \cdot 0.02816/1.2327$

plt.figure(figsize=(8, 6))
plt.bar(labels, contributions, color=['gold', 'cyan'], edgecolor='black')
plt.xlabel('Uncertainty Source')
plt.ylabel('Relative Uncertainty')
plt.title('Contributions to Uncertainty in g')
plt.ylim(0, 0.05)
plt.grid(True, linestyle='--', alpha=0.7)
plt.show()
```
## Colab
[colab 11](https://colab.research.google.com/drive/16krdw9EPAc5-32J3YKll1ri1p04sAd6t)

