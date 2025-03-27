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

