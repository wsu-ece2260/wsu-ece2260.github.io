---
layout: page
title: "lab07: s_domain"
parent: Lab Procedures
nav_order: 10
math: mathjax3
---

# $s$ Domain Circuit Analysis

## Analytical derivation

In this lab, we will look at the passive ladder circuit shown below.

<div style="text-align: center;"><img src="/assets/images/lab_images/s_domain/passive_ladder.png" alt="Passive Ladder Circuit" width="648.189pt"></div>

This type of circuit has a wide variety of applications, including as a low-pass filter seen in power supplies and radio transmitters.  

Analyzing this circuit gets pretty complicated because there are three reactive components (two capacitors and one inductor), which will make this a third order differential equation.  Worse, the two stages are coupled together, so we can't just analyze each stage separately (we will spend much more time on what this means later in the semester).  If we tried to derive the output voltage $V_{out}(t)$ using KCL and KVL, we would end up with a very complicated third order differential equation that would be difficult to solve.  Instead, we will use the Laplace transform to analyze this circuit in the $s$-domain, which will allow us to derive the transfer function of the circuit, which is a much simpler algebraic expression that relates the input and output voltages.

*Note:* This circuit has an opamp in it.  This is a voltage follower configuration, which means that the output voltage will be the same as the voltage at the non-inverting input.  This opamp acts as a buffer, which prevents the function generator from being loaded down by the rest of the circuit.  This is important because the function generator has a finite output impedance, which can affect the behavior of the circuit if it is not buffered.  In terms of how this impacts the circuit analysis, we can more or less ignore it!  The output voltage of this opamp is the same as the voltage at the non-inverting input, so just analyze the circuit from the output of the opamp with an output voltage of $V_{in}(t) = 2u(t)$ V.

### Using symbolic math to solve the circuit

One issue with using the Laplace transform to analyze circuits is that it can be a hassle to derive the targeted voltage or current by hand, especially for more complicated circuits because all the equations are in terms of the variable $s$, which we can't just dump into our calculator.  We often end up with a symbolic system of equations that we will need to solve using Cramer's rule or some other method, which can be very annoying and error-prone.  This is especially true for circuits with more than two reactive components, which will lead to higher order differential equations and more complicated algebraic expressions in the $s$-domain.

To make our lives a bit easier, we can use the symbolic math library in Python called `sympy` to help us derive the transfer function.  This library allows us to define symbolic variables and perform algebraic manipulations on them, which is what we need to the Laplace transform voltage $V_{o}(s)$.

But first, we should look at how to use `sympy` to solve a somewhat complicated algebraic equation using symbolic constants rather than scalar values.  Suppose we had a complicated system of equations that we wanted to solve.  For example, suppose we had the following system of equations


$$
\begin{align*}
    2 R x + C y - s z   & = 3  \\
    R x - 2 C y + s z   & = -2 \\
    3 R x + C y + 2 s z & = 10
\end{align*}
$$


where $R$, $C$, and $s$ are symbolic constants.  We could use Cramer's rule to solve this system of equations, but it would be very tedious---even horrible. Instead, we can use the `sympy` package to solve this system of equations.  The following code will do just that.  Give it a try and see how it works!


Your turn!  Derive a system of equations to solve for $V_o(s)$.  Use `sympy` to solve for $V_o(s)$.  Represent your answer as a Python funciton `V_o(s)`.

Let's look at the locations of the poles and zeros for the expression for $V_o(s)$ that you derived.  Plot them as a scatter where the zeros are represented as a circle and the poles are represented as an 'x'.  Thought question:  what do you notice about the locations of the poles and zeros?  We will spend a lot more time about the impacts of the locations of the poles and zeros later this semester (and in ECE 3210, ECE 4100, ECE 5210, etc.), but see if you can make any observations about the locations of the poles and zeros for this circuit.

With your plot, the $x$-axis is the real part of the poles and zeros, and the $y$-axis is the imaginary part of the poles and zeros.  Make sure that the axes are labeled and the plot has a title.  Make sure that the aspect ratio of the plot is equal such that the axes are scaled equally.  This will make it easier to see the locations of the poles and zeros. You can do this by `plt.axis('equal')`.

Now we know $V_o(s)$, we can find $v_o(t)$ by taking the inverse Laplace transform of $V_o(s)$.  Use the `signal.residue` function from `scipy` to find the residues, poles, and direct term of $V_o(s)$, and then use these values to compute $v_o(t)$ for a given time vector `t`.  

Plot $v_o(t)$ for $t$ from -0.1 ms to 0.3 ms.  Make sure to label your axes and give your plot a title.  

## SPICE simulation

As always, we need to verify our analytical results with a SPICE simulation.  Use whatever flavor of SPICE you are most comfortable with to simulate the circuit and verify that your analytical results match the simulation results.  Your plot should span the same time range as your analytical plot, and should be labeled and titled appropriately.  Make sure to include a legend to differentiate between the analytical and simulation results. 

## Hardware

Build the circuit in hardware.  Use the LF353 opamp and power it with $\pm 15$ V supplies.  Use the same component values as in the analytical and simulation parts of the lab.  Set the function generator to output:
- A square wave
- 500 Hz
- 2 V amplitude (2 Vpp)
- 1 V offset (so that the input is a 2 Vpp square wave that oscillates between 0 V and 2 V)

Verify that your input is what you think it is by measuring the input voltage with an oscilloscope.

Use the oscilloscope to measure the output voltage $v_o(t)$.  Save the data and plot it against the analytical solution and the simulation results from -0.1 to 0.3 ms. Make sure to label your axes and give your plot a title.  Make sure to include a legend to differentiate between the analytical, simulation, and hardware results.

