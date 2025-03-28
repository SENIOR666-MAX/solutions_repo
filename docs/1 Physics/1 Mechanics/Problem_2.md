# Problem 2

## Investigating the Dynamics of a Forced Damped Pendulum

**Motivation**

The forced damped pendulum is a well-established model in nonlinear dynamics, known for exhibiting a wide array of complex motion patterns. These behaviors arise from the combined influence of three main factors: damping, restoring forces, and an external periodic input.

When both damping and periodic forcing are introduced, the pendulum's motion extends far beyond simple harmonic oscillations, giving rise to a diverse range of dynamic responses. These include synchronized periodic motion, quasiperiodicity, resonance effects, and chaotic trajectories. Because of this variety, the system is particularly useful in studying the emergence of chaos and nonlinearity in deterministic frameworks.

The addition of an external force brings two key parameters into play: the amplitude and frequency of the input. By adjusting these values, one can explore different types of transitions and bifurcations within the system, gaining insight into how nonlinear systems behave under continuous external influence. Depending on the parameter values, the system may settle into regular periodic motion, display quasiperiodic or chaotic behavior, or resonate at specific frequencies.

The study of forced damped pendulums has significant practical relevance across various engineering and physics disciplines. Its applications span energy harvesting, mechanical vibration control, electrical circuits (like RLC systems), and even biological systems such as human gait analysis. The pendulum serves as a simplified yet powerful analog for these more intricate real-world systems, acting as a bridge between theory and practical insight.

The objective of this project is to explore the behavior of the forced damped pendulum using a combination of analytical reasoning and computational simulations. By analyzing how initial conditions and physical parameters affect the system, we aim to gain a clearer understanding of nonlinear oscillations, chaotic dynamics, and the influence of damping and periodic forcing. Through tools such as Python and numerical methods (e.g., Runge-Kutta algorithms), various scenarios will be simulated and studied in depth.


# Mathematical Modeling of the Forced Damped Pendulum

## 1. Theoretical Background

### Governing Equation of Motion

The dynamics of a **forced damped pendulum** are described by a second-order, nonlinear, and non-homogeneous differential equation. This equation captures the combined influence of three main forces:

1. **Restoring Force**: caused by gravity  
   \[
   -mgL\sin(\theta)
   \]

2. **Damping Force**: related to angular velocity and opposing motion (e.g., due to friction or air resistance)  
   \[
   -b \frac{d\theta}{dt}
   \]

3. **External Driving Force**: a periodic torque of the form  
   \[
   A \cos(\omega t)
   \]

By applying Newton’s second law for rotational motion, the torque equation becomes:

\[
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
  <mi>I</mi>
  <mfrac>
    <mrow>
      <msup>
        <mi>d</mi>
        <mn>2</mn>
      </msup>
      <mi>t</mi>
      <mi>h</mi>
      <mi>e</mi>
      <mi>t</mi>
      <mi>a</mi>
    </mrow>
    <mrow>
      <mi>d</mi>
      <msup>
        <mi>t</mi>
        <mn>2</mn>
      </msup>
    </mrow>
  </mfrac>
  <mo>=</mo>
  <mo>&#x2212;</mo>
  <mi>m</mi>
  <mi>g</mi>
  <mi>L</mi>
  <mi>s</mi>
  <mi>i</mi>
  <mi>n</mi>
  <mo stretchy="false">(</mo>
  <mi>t</mi>
  <mi>h</mi>
  <mi>e</mi>
  <mi>t</mi>
  <mi>a</mi>
  <mo stretchy="false">)</mo>
  <mo>&#x2212;</mo>
  <mi>b</mi>
  <mfrac>
    <mrow>
      <mi>d</mi>
      <mi>t</mi>
      <mi>h</mi>
      <mi>e</mi>
      <mi>t</mi>
      <mi>a</mi>
    </mrow>
    <mrow>
      <mi>d</mi>
      <mi>t</mi>
    </mrow>
  </mfrac>
  <mo>+</mo>
  <mi>A</mi>
  <mi>c</mi>
  <mi>o</mi>
  <mi>s</mi>
  <mo stretchy="false">(</mo>
  <mi>o</mi>
  <mi>m</mi>
  <mi>e</mi>
  <mi>g</mi>
  <mi>a</mi>
  <mi>t</mi>
  <mo stretchy="false">)</mo>
</math>
\]

Where:  
- \( I = mL^2 \) is the moment of inertia for a mass at the end of a massless rod  
- \( L \): pendulum length  
- \( m \): mass of the bob  
- \( b \): damping coefficient  
- \( A \): amplitude of the driving torque

---

### Dimensionless Form of the Equation

Dividing both sides by the moment of inertia \( I \), we obtain the normalized version:

\[
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
  <mfrac>
    <mrow>
      <msup>
        <mi>d</mi>
        <mn>2</mn>
      </msup>
      <mi>t</mi>
      <mi>h</mi>
      <mi>e</mi>
      <mi>t</mi>
      <mi>a</mi>
    </mrow>
    <mrow>
      <mi>d</mi>
      <msup>
        <mi>t</mi>
        <mn>2</mn>
      </msup>
    </mrow>
  </mfrac>
  <mo>+</mo>
  <mfrac>
    <mi>b</mi>
    <mrow>
      <mi>m</mi>
      <msup>
        <mi>L</mi>
        <mn>2</mn>
      </msup>
    </mrow>
  </mfrac>
  <mfrac>
    <mrow>
      <mi>d</mi>
      <mi>t</mi>
      <mi>h</mi>
      <mi>e</mi>
      <mi>t</mi>
      <mi>a</mi>
    </mrow>
    <mrow>
      <mi>d</mi>
      <mi>t</mi>
    </mrow>
  </mfrac>
  <mo>+</mo>
  <mfrac>
    <mi>g</mi>
    <mi>L</mi>
  </mfrac>
  <mi>s</mi>
  <mi>i</mi>
  <mi>n</mi>
  <mo stretchy="false">(</mo>
  <mi>t</mi>
  <mi>h</mi>
  <mi>e</mi>
  <mi>t</mi>
  <mi>a</mi>
  <mo stretchy="false">)</mo>
  <mo>=</mo>
  <mfrac>
    <mi>A</mi>
    <mrow>
      <mi>m</mi>
      <msup>
        <mi>L</mi>
        <mn>2</mn>
      </msup>
    </mrow>
  </mfrac>
  <mi>c</mi>
  <mi>o</mi>
  <mi>s</mi>
  <mo stretchy="false">(</mo>
  <mi>o</mi>
  <mi>m</mi>
  <mi>e</mi>
  <mi>g</mi>
  <mi>a</mi>
  <mi>t</mi>
  <mo stretchy="false">)</mo>
</math>
\]

To simplify notation, we define:

- Damping ratio:  
  \[
  \gamma = \frac{b}{mL^2}
  \]

- Natural frequency squared:  
  \[
  \omega_0^2 = \frac{g}{L}
  \]

- Scaled forcing amplitude:  
  \[
  f = \frac{A}{mL^2}
  \]

Using these definitions, the equation becomes:

\[
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
  <mfrac>
    <mrow>
      <msup>
        <mi>d</mi>
        <mn>2</mn>
      </msup>
      <mi>t</mi>
      <mi>h</mi>
      <mi>e</mi>
      <mi>t</mi>
      <mi>a</mi>
    </mrow>
    <mrow>
      <mi>d</mi>
      <msup>
        <mi>t</mi>
        <mn>2</mn>
      </msup>
    </mrow>
  </mfrac>
  <mo>+</mo>
  <mi>g</mi>
  <mi>a</mi>
  <mi>m</mi>
  <mi>m</mi>
  <mi>a</mi>
  <mfrac>
    <mrow>
      <mi>d</mi>
      <mi>t</mi>
      <mi>h</mi>
      <mi>e</mi>
      <mi>t</mi>
      <mi>a</mi>
    </mrow>
    <mrow>
      <mi>d</mi>
      <mi>t</mi>
    </mrow>
  </mfrac>
  <mo>+</mo>
  <mi>o</mi>
  <mi>m</mi>
  <mi>e</mi>
  <mi>g</mi>
  <msubsup>
    <mi>a</mi>
    <mn>0</mn>
    <mn>2</mn>
  </msubsup>
  <mi>s</mi>
  <mi>i</mi>
  <mi>n</mi>
  <mo stretchy="false">(</mo>
  <mi>t</mi>
  <mi>h</mi>
  <mi>e</mi>
  <mi>t</mi>
  <mi>a</mi>
  <mo stretchy="false">)</mo>
  <mo>=</mo>
  <mi>f</mi>
  <mi>c</mi>
  <mi>o</mi>
  <mi>s</mi>
  <mo stretchy="false">(</mo>
  <mi>o</mi>
  <mi>m</mi>
  <mi>e</mi>
  <mi>g</mi>
  <mi>a</mi>
  <mi>t</mi>
  <mo stretchy="false">)</mo>
</math>
\]

This final form is the **nonlinear, non-homogeneous second-order differential equation** that governs the behavior of the forced damped pendulum.



## Small-Angle Linearization

When the angular displacement \( \theta \) remains small (i.e., \( \theta \ll 1 \)), the sine function can be approximated using the Taylor series expansion:

\[
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
  <mi>s</mi>
  <mi>i</mi>
  <mi>n</mi>
  <mo stretchy="false">(</mo>
  <mi>t</mi>
  <mi>h</mi>
  <mi>e</mi>
  <mi>t</mi>
  <mi>a</mi>
  <mo stretchy="false">)</mo>
  <mi>a</mi>
  <mi>p</mi>
  <mi>p</mi>
  <mi>r</mi>
  <mi>o</mi>
  <mi>x</mi>
  <mi>t</mi>
  <mi>h</mi>
  <mi>e</mi>
  <mi>t</mi>
  <mi>a</mi>
  <mo>&#x2212;</mo>
  <mfrac>
    <mrow>
      <mi>t</mi>
      <mi>h</mi>
      <mi>e</mi>
      <mi>t</mi>
      <msup>
        <mi>a</mi>
        <mn>3</mn>
      </msup>
    </mrow>
    <mn>6</mn>
  </mfrac>
  <mo>+</mo>
  <mfrac>
    <mrow>
      <mi>t</mi>
      <mi>h</mi>
      <mi>e</mi>
      <mi>t</mi>
      <msup>
        <mi>a</mi>
        <mn>5</mn>
      </msup>
    </mrow>
    <mn>120</mn>
  </mfrac>
  <mo>&#x2212;</mo>
  <mi>c</mi>
  <mi>d</mi>
  <mi>o</mi>
  <mi>t</mi>
  <mi>s</mi>
</math>
\]

By ignoring the higher-order (nonlinear) terms, this simplifies to:

\[
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
  <mi>s</mi>
  <mi>i</mi>
  <mi>n</mi>
  <mo stretchy="false">(</mo>
  <mi>t</mi>
  <mi>h</mi>
  <mi>e</mi>
  <mi>t</mi>
  <mi>a</mi>
  <mo stretchy="false">)</mo>
  <mi>a</mi>
  <mi>p</mi>
  <mi>p</mi>
  <mi>r</mi>
  <mi>o</mi>
  <mi>x</mi>
  <mi>t</mi>
  <mi>h</mi>
  <mi>e</mi>
  <mi>t</mi>
  <mi>a</mi>
</math>
\]

Applying this simplification to the nonlinear pendulum equation, we get:

\[
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
  <mfrac>
    <mrow>
      <msup>
        <mi>d</mi>
        <mn>2</mn>
      </msup>
      <mi>t</mi>
      <mi>h</mi>
      <mi>e</mi>
      <mi>t</mi>
      <mi>a</mi>
    </mrow>
    <mrow>
      <mi>d</mi>
      <msup>
        <mi>t</mi>
        <mn>2</mn>
      </msup>
    </mrow>
  </mfrac>
  <mo>+</mo>
  <mi>g</mi>
  <mi>a</mi>
  <mi>m</mi>
  <mi>m</mi>
  <mi>a</mi>
  <mfrac>
    <mrow>
      <mi>d</mi>
      <mi>n</mi>
      <mi>t</mi>
      <mi>h</mi>
      <mi>e</mi>
      <mi>t</mi>
      <mi>a</mi>
    </mrow>
    <mrow>
      <mi>d</mi>
      <mi>t</mi>
    </mrow>
  </mfrac>
  <mo>+</mo>
  <mi>o</mi>
  <mi>m</mi>
  <mi>e</mi>
  <mi>g</mi>
  <msubsup>
    <mi>a</mi>
    <mn>0</mn>
    <mn>2</mn>
  </msubsup>
  <mi>t</mi>
  <mi>h</mi>
  <mi>e</mi>
  <mi>t</mi>
  <mi>a</mi>
  <mo>=</mo>
  <mi>f</mi>
  <mi>c</mi>
  <mi>o</mi>
  <mi>s</mi>
  <mo stretchy="false">(</mo>
  <mi>o</mi>
  <mi>m</mi>
  <mi>e</mi>
  <mi>g</mi>
  <mi>a</mi>
  <mi>t</mi>
  <mo stretchy="false">)</mo>
</math>
\]

This results in a **linear second-order differential equation**, which can be solved using classical techniques like undetermined coefficients or variation of parameters.  

The full solution generally consists of two components:

- **Homogeneous solution**: Describes the natural (transient) response, typically diminishing over time due to damping.  
- **Particular solution**: Represents the steady-state behavior induced by the periodic driving force.


## Homogeneous Response

The corresponding homogeneous differential equation, where the external forcing is removed, is written as:

\[
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
  <mfrac>
    <mrow>
      <msup>
        <mi>d</mi>
        <mn>2</mn>
      </msup>
      <mi>t</mi>
      <mi>h</mi>
      <mi>e</mi>
      <mi>t</mi>
      <mi>a</mi>
    </mrow>
    <mrow>
      <mi>d</mi>
      <msup>
        <mi>t</mi>
        <mn>2</mn>
      </msup>
    </mrow>
  </mfrac>
  <mo>+</mo>
  <mi>g</mi>
  <mi>a</mi>
  <mi>m</mi>
  <mi>m</mi>
  <mi>a</mi>
  <mfrac>
    <mrow>
      <mi>d</mi>
      <mi>t</mi>
      <mi>h</mi>
      <mi>e</mi>
      <mi>t</mi>
      <mi>a</mi>
    </mrow>
    <mrow>
      <mi>d</mi>
      <mi>t</mi>
    </mrow>
  </mfrac>
  <mo>+</mo>
  <mi>o</mi>
  <mi>m</mi>
  <mi>e</mi>
  <mi>g</mi>
  <msubsup>
    <mi>a</mi>
    <mn>0</mn>
    <mn>2</mn>
  </msubsup>
  <mi>t</mi>
  <mi>h</mi>
  <mi>e</mi>
  <mi>t</mi>
  <mi>a</mi>
  <mo>=</mo>
  <mn>0</mn>
</math>
\]

To solve this, we analyze the associated characteristic (auxiliary) equation:

\[
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
  <msup>
    <mi>r</mi>
    <mn>2</mn>
  </msup>
  <mo>+</mo>
  <mi>g</mi>
  <mi>a</mi>
  <mi>m</mi>
  <mi>m</mi>
  <mi>a</mi>
  <mi>r</mi>
  <mo>+</mo>
  <mi>o</mi>
  <mi>m</mi>
  <mi>e</mi>
  <mi>g</mi>
  <msubsup>
    <mi>a</mi>
    <mn>0</mn>
    <mn>2</mn>
  </msubsup>
  <mo>=</mo>
  <mn>0</mn>
</math>\]

The nature of the solution is determined by the **discriminant**:

\[
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
  <mo stretchy="false">(</mo>
  <mi>D</mi>
  <mi>e</mi>
  <mi>l</mi>
  <mi>t</mi>
  <mi>a</mi>
  <mo>=</mo>
  <mi>g</mi>
  <mi>a</mi>
  <mi>m</mi>
  <mi>m</mi>
  <msup>
    <mi>a</mi>
    <mn>2</mn>
  </msup>
  <mo>&#x2212;</mo>
  <mn>4</mn>
  <mi>o</mi>
  <mi>m</mi>
  <mi>e</mi>
  <mi>g</mi>
  <msubsup>
    <mi>a</mi>
    <mn>0</mn>
    <mn>2</mn>
  </msubsup>
  <mo stretchy="false">)</mo>
  <mo>:</mo>
</math>\]

Based on the value of \( \Delta \), we classify the behavior of the system into three cases:

---

### 1. Underdamped Motion

\[
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
  <mo stretchy="false">(</mo>
  <mo stretchy="false">(</mo>
  <mi>g</mi>
  <mi>a</mi>
  <mi>m</mi>
  <mi>m</mi>
  <msup>
    <mi>a</mi>
    <mn>2</mn>
  </msup>
  <mo>&lt;</mo>
  <mn>4</mn>
  <mi>o</mi>
  <mi>m</mi>
  <mi>e</mi>
  <mi>g</mi>
  <msubsup>
    <mi>a</mi>
    <mn>0</mn>
    <mn>2</mn>
  </msubsup>
  <mo stretchy="false">)</mo>
  <mo stretchy="false">)</mo>
  <mo>:</mo>
  <mi>O</mi>
  <mi>s</mi>
  <mi>c</mi>
  <mi>i</mi>
  <mi>l</mi>
  <mi>l</mi>
  <mi>a</mi>
  <mi>t</mi>
  <mi>o</mi>
  <mi>r</mi>
  <mi>y</mi>
  <mi>d</mi>
  <mi>e</mi>
  <mi>c</mi>
  <mi>a</mi>
  <mi>y</mi>
</math>\]

- The solution involves oscillations that gradually decrease in amplitude over time.  
- This is the most common case in physical pendulum systems.

---

### 2. Critically Damped Motion

\[
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
  <mo stretchy="false">(</mo>
  <mo stretchy="false">(</mo>
  <mi>g</mi>
  <mi>a</mi>
  <mi>m</mi>
  <mi>m</mi>
  <msup>
    <mi>a</mi>
    <mn>2</mn>
  </msup>
  <mo>=</mo>
  <mn>4</mn>
  <mi>o</mi>
  <mi>m</mi>
  <mi>e</mi>
  <mi>g</mi>
  <msubsup>
    <mi>a</mi>
    <mn>0</mn>
    <mn>2</mn>
  </msubsup>
  <mo stretchy="false">)</mo>
  <mo stretchy="false">)</mo>
  <mo>:</mo>
  <mi>F</mi>
  <mi>a</mi>
  <mi>s</mi>
  <mi>t</mi>
  <mi>e</mi>
  <mi>s</mi>
  <mi>t</mi>
  <mi>n</mi>
  <mi>o</mi>
  <mi>n</mi>
  <mo>&#x2212;</mo>
  <mi>o</mi>
  <mi>s</mi>
  <mi>c</mi>
  <mi>i</mi>
  <mi>l</mi>
  <mi>l</mi>
  <mi>a</mi>
  <mi>t</mi>
  <mi>o</mi>
  <mi>r</mi>
  <mi>y</mi>
  <mi>d</mi>
  <mi>e</mi>
  <mi>c</mi>
  <mi>a</mi>
  <mi>y</mi>
</math>\]

- The system returns to equilibrium **as quickly as possible** without oscillating.  
- This represents the fastest non-oscillatory decay.

---

### 3. Overdamped Motion

\[
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
  <mo stretchy="false">(</mo>
  <mo stretchy="false">(</mo>
  <mi>g</mi>
  <mi>a</mi>
  <mi>m</mi>
  <mi>m</mi>
  <msup>
    <mi>a</mi>
    <mn>2</mn>
  </msup>
  <mo>&gt;</mo>
  <mn>4</mn>
  <mi>o</mi>
  <mi>m</mi>
  <mi>e</mi>
  <mi>g</mi>
  <msubsup>
    <mi>a</mi>
    <mn>0</mn>
    <mn>2</mn>
  </msubsup>
  <mo stretchy="false">)</mo>
  <mo stretchy="false">)</mo>
  <mo>:</mo>
  <mi>S</mi>
  <mi>l</mi>
  <mi>o</mi>
  <mi>w</mi>
  <mo>,</mo>
  <mi>n</mi>
  <mi>o</mi>
  <mi>n</mi>
  <mo>&#x2212;</mo>
  <mi>o</mi>
  <mi>s</mi>
  <mi>c</mi>
  <mi>i</mi>
  <mi>l</mi>
  <mi>l</mi>
  <mi>a</mi>
  <mi>t</mi>
  <mi>o</mi>
  <mi>r</mi>
  <mi>y</mi>
  <mi>d</mi>
  <mi>e</mi>
  <mi>c</mi>
  <mi>a</mi>
  <mi>y</mi>
</math>\]

- The system slowly returns to rest without oscillations.  
- The decay is slower than in the critically damped case.

---

Each damping regime gives insight into how energy is dissipated in the system and how quickly the pendulum settles back to equilibrium.


## Particular Solution: Response to External Forcing

In the case of the linearized differential equation, the **particular solution** represents the system’s steady-state behavior under continuous periodic driving. The general form is expressed as:

\[
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
  <mi>t</mi>
  <mi>h</mi>
  <mi>e</mi>
  <mi>t</mi>
  <msub>
    <mi>a</mi>
    <mi>p</mi>
  </msub>
  <mo stretchy="false">(</mo>
  <mi>t</mi>
  <mo stretchy="false">)</mo>
  <mo>=</mo>
  <mi>C</mi>
  <mi>c</mi>
  <mi>o</mi>
  <mi>s</mi>
  <mo stretchy="false">(</mo>
  <mi>o</mi>
  <mi>m</mi>
  <mi>e</mi>
  <mi>g</mi>
  <mi>a</mi>
  <mi>t</mi>
  <mo>&#x2212;</mo>
  <mi>d</mi>
  <mi>e</mi>
  <mi>l</mi>
  <mi>t</mi>
  <mi>a</mi>
  <mo stretchy="false">)</mo>
</math>\]

Where:

- \( C \) is the **amplitude** of the resulting oscillation, determined by the relation:

\[
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
  <mi>C</mi>
  <mo>=</mo>
  <mfrac>
    <mi>f</mi>
    <msqrt>
      <mo stretchy="false">(</mo>
      <mi>o</mi>
      <mi>m</mi>
      <mi>e</mi>
      <mi>g</mi>
      <msubsup>
        <mi>a</mi>
        <mn>0</mn>
        <mn>2</mn>
      </msubsup>
      <mo>&#x2212;</mo>
      <mi>o</mi>
      <mi>m</mi>
      <mi>e</mi>
      <mi>g</mi>
      <msup>
        <mi>a</mi>
        <mn>2</mn>
      </msup>
      <msup>
        <mo stretchy="false">)</mo>
        <mn>2</mn>
      </msup>
      <mo>+</mo>
      <mo stretchy="false">(</mo>
      <mi>g</mi>
      <mi>a</mi>
      <mi>m</mi>
      <mi>m</mi>
      <mi>a</mi>
      <mi>o</mi>
      <mi>m</mi>
      <mi>e</mi>
      <mi>g</mi>
      <mi>a</mi>
      <msup>
        <mo stretchy="false">)</mo>
        <mn>2</mn>
      </msup>
    </msqrt>
  </mfrac>
</math>\]

- \( \delta \) is the **phase lag**, describing how much the system’s response is delayed relative to the external force:

\[
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
  <mi>d</mi>
  <mi>e</mi>
  <mi>l</mi>
  <mi>t</mi>
  <mi>a</mi>
  <mo>=</mo>
  <mi>t</mi>
  <mi>a</mi>
  <msup>
    <mi>n</mi>
    <mrow data-mjx-texclass="ORD">
      <mo>&#x2212;</mo>
      <mn>1</mn>
    </mrow>
  </msup>
  <mi>l</mi>
  <mi>e</mi>
  <mi>f</mi>
  <mi>t</mi>
  <mo stretchy="false">(</mo>
  <mfrac>
    <mrow>
      <mi>g</mi>
      <mi>a</mi>
      <mi>m</mi>
      <mi>m</mi>
      <mi>a</mi>
      <mi>o</mi>
      <mi>m</mi>
      <mi>e</mi>
      <mi>g</mi>
      <mi>a</mi>
    </mrow>
    <mrow>
      <mi>o</mi>
      <mi>m</mi>
      <mi>e</mi>
      <mi>g</mi>
      <msubsup>
        <mi>a</mi>
        <mn>0</mn>
        <mn>2</mn>
      </msubsup>
      <mo>&#x2212;</mo>
      <mi>o</mi>
      <mi>m</mi>
      <mi>e</mi>
      <mi>g</mi>
      <msup>
        <mi>a</mi>
        <mn>2</mn>
      </msup>
    </mrow>
  </mfrac>
  <mi>r</mi>
  <mi>i</mi>
  <mi>g</mi>
  <mi>h</mi>
  <mi>t</mi>
  <mo stretchy="false">)</mo>
</math>\]

This particular solution captures the long-term response of the system, where transient effects have diminished and the motion is fully synchronized with the external driving input — though possibly with reduced amplitude and a time delay depending on damping and frequency mismatch.


## Resonance Condition

Resonance takes place when the amplitude \( C \) of the particular solution reaches its peak value. This occurs when the denominator in the amplitude expression becomes as small as possible:

\[
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
  <msub>
    <mi>&#x3C9;</mi>
    <mrow data-mjx-texclass="ORD">
      <mtext>res</mtext>
    </mrow>
  </msub>
  <mo>=</mo>
  <msqrt>
    <mi>o</mi>
    <mi>m</mi>
    <mi>e</mi>
    <mi>g</mi>
    <msubsup>
      <mi>a</mi>
      <mn>0</mn>
      <mn>2</mn>
    </msubsup>
    <mo>&#x2212;</mo>
    <mfrac>
      <mrow>
        <mi>g</mi>
        <mi>a</mi>
        <mi>m</mi>
        <mi>m</mi>
        <msup>
          <mi>a</mi>
          <mn>2</mn>
        </msup>
      </mrow>
      <mn>2</mn>
    </mfrac>
  </msqrt>
</math>\]

In cases of light damping (\( \gamma \ll \omega_0 \)), this expression simplifies to:

\[
\omega \approx \omega_0
\]

At resonance:

- The system draws in energy from the external periodic force with high efficiency.
- The amplitude of oscillation may become extremely large, unless restrained by damping or system nonlinearities.


## Nonlinear Dynamics and Complex Motion

When the assumption of small-angle motion breaks down — for instance, when the pendulum swings with large initial displacement or is subjected to a strong periodic force — the linear approximation is no longer valid. In such cases, the system must be described by the full nonlinear equation:

\[
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
  <mfrac>
    <mrow>
      <msup>
        <mi>d</mi>
        <mn>2</mn>
      </msup>
      <mi>t</mi>
      <mi>h</mi>
      <mi>e</mi>
      <mi>t</mi>
      <mi>a</mi>
    </mrow>
    <mrow>
      <mi>d</mi>
      <msup>
        <mi>t</mi>
        <mn>2</mn>
      </msup>
    </mrow>
  </mfrac>
  <mo>+</mo>
  <mi>g</mi>
  <mi>a</mi>
  <mi>m</mi>
  <mi>m</mi>
  <mi>a</mi>
  <mfrac>
    <mrow>
      <mi>d</mi>
      <mi>t</mi>
      <mi>h</mi>
      <mi>e</mi>
      <mi>t</mi>
      <mi>a</mi>
    </mrow>
    <mrow>
      <mi>d</mi>
      <mi>t</mi>
    </mrow>
  </mfrac>
  <mo>+</mo>
  <mi>o</mi>
  <mi>m</mi>
  <mi>e</mi>
  <mi>g</mi>
  <msubsup>
    <mi>a</mi>
    <mn>0</mn>
    <mn>2</mn>
  </msubsup>
  <mi>s</mi>
  <mi>i</mi>
  <mi>n</mi>
  <mo stretchy="false">(</mo>
  <mi>t</mi>
  <mi>h</mi>
  <mi>e</mi>
  <mi>t</mi>
  <mi>a</mi>
  <mo stretchy="false">)</mo>
  <mo>=</mo>
  <mi>f</mi>
  <mi>c</mi>
  <mi>o</mi>
  <mi>s</mi>
  <mo stretchy="false">(</mo>
  <mi>o</mi>
  <mi>m</mi>
  <mi>e</mi>
  <mi>g</mi>
  <mi>a</mi>
  <mi>t</mi>
  <mo stretchy="false">)</mo>
</math>
\]

This nonlinear differential equation typically **cannot be solved exactly**, and requires the use of **numerical techniques** to analyze its behavior. Common approaches include:

- Runge-Kutta methods (e.g., RK4 integration)
- Phase space visualization
- Poincaré maps
- Bifurcation analysis

Nonlinear systems like this can exhibit a wide range of complex dynamics, such as:

- **Period doubling**
- **Quasiperiodic motion**
- **Chaotic behavior**

These behaviors are highly sensitive to both **initial conditions** and **parameter values**, making them a core area of study in nonlinear systems and dynamical analysis.

**Summary**
The behavior of a forced damped pendulum is governed by a nonlinear, second-order differential equation with external forcing.
By applying linear approximations, one can explore fundamental aspects such as resonance phenomena and the role of damping.
However, to fully capture the system’s complexity, especially in strongly nonlinear regimes, numerical techniques are indispensable.
This model acts as a foundational framework for investigating intricate dynamics, including the onset of chaos in nonlinear systems.