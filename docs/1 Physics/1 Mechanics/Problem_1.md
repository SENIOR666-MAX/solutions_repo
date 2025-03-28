# Problem 1

## Exploring the Relationship Between Angle and Projectile Range

### 1. Introduction

Projectile motion may appear simple at first glance, but it forms a critical foundation for exploring essential physics concepts. In this problem, we aim to examine how the range of a projectile is influenced by the angle at which it is launched.

Though the scenario is straightforward, the mathematics behind it involves both linear and nonlinear dynamics, making it a rich field of study.

Some of the primary factors affecting the motion include:

- **Initial speed \( v_0 \)**
- **Gravitational force \( g \)**
- **Launch height \( h \)**

These variables lead to a broad variety of trajectories—from sports ball throws to missile launches—making this problem relevant in many real-world situations.

## 2. Theoretical Foundation

To explore projectile motion in more depth, we rely on Newton’s Second Law of Motion to derive the core equations that govern the system.

### 2.1 Kinematic Equations of Motion

Projectile motion follows Newton’s law:

\[
F = m \cdot a
\]

In our case, the forces involved are:
1. **Gravitational force** acting downward \( (mg) \)
2. **No horizontal forces**, assuming no air resistance

So the acceleration in each direction is:

\[
a_x = 0, \quad a_y = -g
\]

#### Velocity components:
By integrating acceleration, we find:

\[
v_x = v_0 \cos(\theta), \quad v_y = v_0 \sin(\theta) - gt
\]

#### Position components:
Integrating once more gives:

\[
x(t) = v_0 \cos(\theta) \cdot t
\]
\[
y(t) = v_0 \sin(\theta) \cdot t - \frac{1}{2}gt^2
\]

---

### Summary of Equations:

- **Horizontal motion (no acceleration)**:  
  \[
  x(t) = v_0 \cos(\theta)t
  \]

- **Vertical motion (with constant acceleration)**:  
  \[
  y(t) = v_0 \sin(\theta)t - \frac{1}{2}gt^2
  \]

---

Where:
- \( x(t) \), \( y(t) \): projectile’s position at time \( t \)
- \( v_0 \): initial velocity
- \( \theta \): launch angle
- \( g \): acceleration due to gravity (9.81 m/s²)

These kinematic equations are the basis for calculating projectile range, time of flight, and trajectory.

### 2.2 Time of Flight

The total duration that the projectile remains in the air can be calculated by setting the vertical displacement to zero:

\[
y(t) = 0 \quad \Rightarrow \quad t_f = \frac{2v_0 \sin(\theta)}{g}
\]

---

### 2.3 Range of the Projectile

The horizontal range \( R \) is the total distance the projectile travels before hitting the ground. Using the time of flight \( t_f \), we substitute into the horizontal position equation:

\[
R = v_0 \cos(\theta) \cdot \frac{2v_0 \sin(\theta)}{g}
\]

Using the identity \( 2 \sin(\theta) \cos(\theta) = \sin(2\theta) \), we get:

\[
R(\theta) = \frac{v_0^2}{g} \sin(2\theta)
\]

---

### 2.4 Maximum Range

The range is maximized when \( \sin(2\theta) = 1 \), which occurs at a launch angle of \( \theta = 45^\circ \). Therefore, the maximum horizontal distance is:

\[
R_{\text{max}} = \frac{v_0^2}{g}
\]

## 3. Analysis of the Range

### 3.1 Influence of Launch Angle

- The range displays a **symmetric pattern** around \( \theta = 45^\circ \).
- Launch angles \( \theta \) and \( 90^\circ - \theta \) produce **identical ranges**, due to the sine double angle identity.

### 3.2 Impact of Initial Velocity

- As the initial speed \( v_0 \) increases, the range also increases.
- Specifically, the range is **proportional to \( v_0^2 \)**.

### 3.3 Role of Gravitational Acceleration

- A larger gravitational pull (like on Jupiter) **decreases** the range.
- A smaller gravitational field (like on the Moon) **increases** the range.

---

import numpy as np
import matplotlib.pyplot as plt

# Define parameters
v0 = 20  # Initial velocity (m/s)
g = 9.81  # Gravity (m/s^2)
theta = np.linspace(0, 90, 100)  # Angle range from 0 to 90 degrees

# Compute range
R = (v0**2 * np.sin(np.deg2rad(2 * theta))) / g

# Plot the range vs. angle
plt.figure(figsize=(10, 6))
plt.plot(theta, R, label='Range (R)', color='blue')

# Mark the maximum range at 45°
plt.axvline(45, color='red', linestyle='--', label='Max Range at 45°')
plt.text(46, max(R)-2, "Maximum Range", color='red')

plt.xlabel('Projection Angle (θ) [Degrees]')
plt.ylabel('Range (R) [m]')
plt.title('Projectile Range as a Function of Launch Angle')
plt.grid(True)
plt.legend()
plt.show()

```python
import numpy as np
import matplotlib.pyplot as plt

# Define parameters
v0 = 20  # Initial velocity (m/s)
g = 9.81  # Gravity (m/s^2)
theta = np.linspace(0, 90, 100)  # Angle range from 0 to 90 degrees

# Compute range
R = (v0**2 * np.sin(np.deg2rad(2 * theta))) / g

# Plot the range vs. angle
plt.figure(figsize=(10, 6))
plt.plot(theta, R, label='Range (R)', color='blue')

# Mark the maximum range at 45°
plt.axvline(45, color='red', linestyle='--', label='Max Range at 45°')
plt.text(46, max(R)-2, "Maximum Range", color='red')

plt.xlabel('Projection Angle (θ) [Degrees]')
plt.ylabel('Range (R) [m]')
plt.title('Projectile Range as a Function of Launch Angle')
plt.grid(True)
plt.legend()
plt.show()
```

![Projectile Range vs Launch Angle](https://i.imgur.com/YWBGwXy.png)
