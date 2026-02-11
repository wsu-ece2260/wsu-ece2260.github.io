---
layout: page
title: "lab04: rlc_parallel"
parent: Lab Procedures
nav_order: 7
math: mathjax3
---

# Parallel RLC

## Inductor Fabrication and Measurment

We will wind our own inductors for this lab. Follow the instructions in the lab manual to fabricate and measure your inductors.  Use the supplied inductor core.  It gives you 


$$
L = 2.36 \mu H \cdot N^2
$$


where \(N\) is the number of turns you wind on the core.  If you use 22 turns, what inductor value should you get?  That is the inductor value you should use in the analysis and simulation for this lab.  Represent your answer as a variable `L = XX` where `XX` is the inductor value in mH.  Round your answer to two decimal places in mH.

Wind your own inductor.  You should have 22 turns on the core.  Measure the inductance and to verify you are in the right ballpark of the theoretical value.  Use the theoretical value for the rest of the lab.

<div style="text-align: center;"><img src="/assets/images/lab_images/rlc_parallel/inductor.jpeg" alt="Inductor image"></div>

When you are done, trim the leads and scratch off the coating so you and make good electrical contact when you put the inductor in the circuit.


## Circuit 1

### Derivation

Consider the circuit below.

<div style="text-align: center;"><img src="/assets/images/lab_images/rlc_parallel/rlc_1.png" alt="Parallel RLC Circuit" width="451.98pt"></div>

Before time $t=0$ we assume that the circuit has been at rest.  At time $t=0$, a switch opens.  Please derive an expression for $v(t)$ for all values of $t$.  Express your answer a function `v_1(t)`.

Plot the voltage $v(t)$ for $t$ from -0.1 ms to 0.5 ms.  

What type of response is this circuit exhibiting (overdamped, underdamped, critically damped)?  Respond with a variable `damping_type_1 = "over"`, `damping_type_1 = "under"`, or `damping_type_1 = "critically"`.

### SPICE simulation

Simulate this circuit in SPICE to verify your results.  To model the switching behavior you can use

- pulse voltage source at 500 Hz frequency
- amplitude 5Vpp
- offset 2.5V

Plot this against your derived expression for $v(t)$ from time -0.1 ms to 0.5 ms to match your derived results.  Note, SPICE doesn't allow you to plot negative time, so you can just plot the SPICE simulation from 0 to 0.5 ms and compare that to your derived expression for $v(t)$ over the same time period.

### Experimental verification

Build the circuit using your inductor.  Set the function generator:
- square wave
- 500 Hz frequency
- load: High-Z
- amplitude 5Vpp
- offset 2.5V

Measure the voltage $v(t)$.  Make a plot from -0.1 ms to 0.5 ms.  Your plot needs to include:
- your derived expression for $v(t)$
- your SPICE simulation results
- your experimental results

Please label your plot axes and include a legend.  

## Circuit 2

### Derivation

Consider the circuit below.

<div style="text-align: center;"><img src="/assets/images/lab_images/rlc_parallel/rlc_2.png" alt="Parallel RLC Circuit" width="451.98pt"></div>

Before time $t=0$ we assume that the circuit has been at rest.  At time $t=0$, a switch opens.  Please derive an expression for $v(t)$ for all values of $t$.  Express your answer a function `v_2(t)`.


Plot the voltage $v(t)$ for $t$ from -0.05 ms to 0.2 ms.  

What type of response is this circuit exhibiting (overdamped, underdamped, critically damped)?  Respond with a variable `damping_type_2 = "over"`, `damping_type_2 = "under"`, or `damping_type_2 = "critically"`.

### SPICE simulation

Simulate this circuit in SPICE to verify your results.  To model the switching behavior you can use

- pulse voltage source at 500 Hz frequency
- amplitude 5Vpp
- offset 2.5V

Plot this against your derived expression for $v(t)$ from time -0.05 ms to 0.1 ms to match your derived results.  Note, SPICE doesn't allow you to plot negative time, so you can just plot the SPICE simulation from 0 to 0.1 ms and compare that to your derived expression for $v(t)$ over the same time period.

### Experimental verification

Build the circuit using your inductor.  Set the function generator:
- square wave
- 500 Hz frequency
- load: High-Z
- amplitude 5Vpp
- offset 2.5V

Measure the voltage $v(t)$.  Make a plot from -0.05 to 0.1 ms.  Your plot needs to include:
- your derived expression for $v(t)$
- your SPICE simulation results
- your experimental results

Please label your plot axes and include a legend.  

