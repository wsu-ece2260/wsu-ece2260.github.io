---
layout: page
title: "lab08: convolution"
parent: Lab Procedures
nav_order: 11
math: mathjax3
---

# Convolution

## Circuit 1

Consider the circuit shown below, where the input voltage is a ramp function that increases linearly from 0 to 5 V over 200 μs and then drops to 0 V. The output voltage is measured across the capacitor.

<div style="text-align: center;"><img src="/assets/images/lab_images/convolution/rc_circuit.png" alt="Circuit Diagram" width="290.15250000000003pt"></div>

### Analytical solution

First, find the transfer function of the circuit $H_1(s)$.  Represent your answer as a function `H_1(s)`.

Now plot the poles and zeros on the complex plane.  Mark the poles with an `x` and the zeros with an `o`.  Label the axes in units of radians per second.  Make sure that the axes are scaled equally so that the angles of the poles and zeros are visually accurate.

From the transfer function, find the impulse response of the circuit $h_1(t)$.  Represent your answer as a function `h_1(t)`.

Given some input signal $x(t)$ that is a ramp function that increases linearly from 0 to 5 V over 200 μs and then drops to 0 V, find the output signal $y_1(t)$ by convolving the input signal with the impulse response of the circuit.  Represent your answer as a function `y_1(t)`.

### SPICE simulation

Run a SPICE simulation of the circuit to find the output voltage across the capacitor.  Record the output voltage as a function of time.  We will plot this against the analytical solution in a later cell.  To generate the input signal, you can use a piecewise linear (PWL) source in SPICE.  For example, you can define the input voltage as follows:

```
V1 in 0 PWL(0 0 200u 5 200.001u 0 1m 0)
```
### Experimental results

Build the circuit.  This ramp input signal is not in the function generator library, but we can generate it easily enough.  Use the `ramp_wave.arb` file in the repo.  Transfer it to the function generator using a USB drive.  On the function generator, select `Waveform`, then `Arb`, then `Arbs`, then `Select Arb`, then scroll to `External` on the screen, and then finally select `ramp_wave.arb`.  In the waveform parameters menu, make sure the sample rate is set to at 500 kSa, the amplitude is set to 5 Vpp, and the offset is set to 0.0 V.  Measure and save at least one period of the output.  Plot this using the same plot as the theoretical ramp response you derived earlier.  Make sure that the timing for both waveforms aligns and that both responses start at 0.0 s.   

### Plotting

Once you have the analytical solution, the SPICE simulation results, and the experimental results, plot them all on the same graph.  Make sure to label the axes and include a legend that identifies each curve.

## Circuit 2

Consider the circuit shown below, where the input voltage is a ramp function that increases linearly from 0 to 5 V over 200 μs and then drops to 0 V. The output voltage is measured across the resistor.

<div style="text-align: center;"><img src="/assets/images/lab_images/convolution/cr_circuit.png" alt="Circuit Diagram" width="290.15250000000003pt"></div>

### Analytical solution

First, find the transfer function of the circuit $H_2(s)$.  Represent your answer as a function `H_2(s)`.

Now plot the poles and zeros on the complex plane.  Mark the poles with an `x` and the zeros with an `o`.  Label the axes in units of radians per second.  Make sure that the axes are scaled equally so that the angles of the poles and zeros are visually accurate.

From the transfer function, find the impulse response of the circuit $h_2(t)$.  Represent your answer as a function `h_2(t)`.

_Note:_ If your solution has a delta function in it, you should use the `delta` function provided at the top of the notebook.

Given some input signal $x(t)$ that is a ramp function that increases linearly from 0 to 5 V over 200 μs and then drops to 0 V, find the output signal $y_2(t)$ by convolving the input signal with the impulse response of the circuit.  Represent your answer as a function `y_2(t)`.

This convolution is a bit harder than the first one due to the impulse response of the circuit.  It is worth remembering two facts:
1. What happens when you convolve a function with a delta function?
2. The convolution operation is linear, so you can break the input signal into pieces, convolve each piece separately, and then add the results together.


### SPICE simulation

Run a SPICE simulation of the circuit to find the output voltage across the resistor.  Record the output voltage as a function of time.  We will plot this against the analytical solution in a later cell.  To generate the input signal, you can use a piecewise linear (PWL) source in SPICE.  For example, you can define the input voltage as follows:

```
V1 in 0 PWL(0 0 200u 5 200.001u 0 1m 0)
```
### Experimental results

Build the circuit.  This ramp input signal is not in the function generator library, but we can generate it easily enough.  Use the `ramp_wave.arb` file in the repo.  Transfer it to the function generator using a USB drive.  On the function generator, select `Waveform`, then `Arb`, then `Arbs`, then `Select Arb`, then scroll to `External` on the screen, and then finally select `ramp_wave.arb`.  In the waveform parameters menu, make sure the sample rate is set to at 500 kSa, the amplitude is set to 5 Vpp, and the offset is set to 0.0 V.  Measure and save at least one period of the output.  Plot this using the same plot as the theoretical ramp response you derived earlier.  Make sure that the timing for both waveforms aligns and that both responses start at 0.0 s.   

### Plotting

Once you have the analytical solution, the SPICE simulation results, and the experimental results, plot them all on the same graph.  Make sure to label the axes and include a legend that identifies each curve.df

