---
layout: page
title: "lab05: rlc_series"
parent: Lab Procedures
nav_order: 8
math: mathjax3
---

# Series RLC

## Circuit 1

### Derivation

Consider the circuit below.

<div style="text-align: center;"><img src="/assets/images/lab_images/rlc_series/rlc_1.png" alt="Parallel RLC Circuit" width="390.3825pt"></div>

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
- load: 50 ohm
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

<div style="text-align: center;"><img src="/assets/images/lab_images/rlc_series/rlc_2.png" alt="Parallel RLC Circuit" width="390.3825pt"></div>

Before time $t=0$ we assume that the circuit has been at rest.  At time $t=0$, a switch opens.  Please derive an expression for $v(t)$ for all values of $t$.  Express your answer a function `v_2(t)`.


Plot the voltage $v(t)$ for $t$ from -0.1 ms to 0.5 ms.  

What type of response is this circuit exhibiting (overdamped, underdamped, critically damped)?  Respond with a variable `damping_type_2 = "over"`, `damping_type_2 = "under"`, or `damping_type_2 = "critically"`.

### SPICE simulation

Simulate this circuit in SPICE to verify your results.  To model the switching behavior you can use

- pulse voltage source at 500 Hz frequency
- amplitude 5Vpp
- offset 2.5V

Plot this against your derived expression for $v(t)$ from time -0.1 ms to 0.5 ms to match your derived results.  Note, SPICE doesn't allow you to plot negative time, so you can just plot the SPICE simulation from 0 to 0.1 ms and compare that to your derived expression for $v(t)$ over the same time period.

### Experimental verification

Build the circuit using your inductor.  Set the function generator:
- square wave
- 500 Hz frequency
- load: 50 Ohm
- amplitude 5Vpp
- offset 2.5V

Measure the voltage $v(t)$.  Make a plot from -0.1 to 0.5 ms.  Your plot needs to include:
- your derived expression for $v(t)$
- your SPICE simulation results
- your experimental results

Please label your plot axes and include a legend.  

