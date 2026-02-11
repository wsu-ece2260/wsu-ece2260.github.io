---
layout: page
title: "lab03: sequential_switching"
parent: Lab Procedures
nav_order: 6
math: mathjax3
---

# Sequential Switching

## Consider the circuit below.

<div style="text-align: center;"><img src="/assets/images/lab_images/sequential_switching/rc_circuit.png" alt="Circuit Diagram" width="654.702pt"></div>

Assume that prior to $t_1$ the voltage source has been disconnected (the path shorted by connecting b and d positions) long enough for the capacitor to fully discharge.  At $t_1$ the left switch if flipped to position a, connecting the 10 V source.  At 25 ms later ($t_2$), the right switch is flipped to position c, connecting the 2 V source.  At 25 ms after that ($t_3$), the left switch is flipped back to position b, disconnecting the 10 V source.  Finally, at 25 ms after that ($t_4$), the right switch is flipped back to position d, disconnecting the 2 V source.

This switching sequence results in the following timeline:

| Time Interval | Left Switch Position | Right Switch Position | Description |
| :---: | :---: | :---: | :--- |
| $t < t_1$ | b | d | Capacitor discharging |
| $t_1 \leq t < t_2$ | a | d | 10 V source connected |
| $t_2 \leq t < t_3$ | a | c | 2 V source connected |
| $t_3 \leq t < t_4$ | b | c | 10 V source disconnected |
| $t \geq t_4$ | b | d | 2 V source disconnected |

Determine the voltage $v_C(t)$ across the capacitor for all time $t \geq 0$.  We will define this voltage as a Python function $v_C(t)$ that can be evaluated at any time $t \geq 0$.  The final function should be continuous and account for the switching events at $t_1$, $t_2$, $t_3$, and $t_4$.

Now we have derived and implemented the expression for $v_C(t)$ across the capacitor for all time $t \geq 0$, plot the voltage $v_C(t)$ over the time interval from $t = 0$ to $t = 100$ ms.  Make sure to label your axes and include a title for your plot.

## Simulating the circuit in SPICE

Next we can verify our results by simulating the circuit in SPICE.  We can simplify the circuit by replacing the switches with voltage sources that turn on and off at the appropriate times.  Because SPICE has ideal voltage sources, we are including the $50, \Omega$ resistors in series with each voltage source to limit the current when the sources are switched on.

<div style="text-align: center;"><img src="/assets/images/lab_images/sequential_switching/spice_circuit.png" alt="SPICE Circuit Diagram" width="345.8505pt"></div>

Run a transient analysis simulation of this circuit in SPICE, and plot the voltage across the capacitor.  The transient analysis should run from 0 to 100 ms.  For the voltage source you can use can use pulse sources with appropriate frequencies and phase shifts to achieve the desired switching behavior.

Finally, plot the results of your SPICE simulation along with your analytical solution on the same graph for comparison.  Make sure to label your axes and include a legend.

## Building the circuit

1. Set both sources in the function generator to be square waves with a frequency of 10 Hz. Use the settings below to set each source to its amplitude, offset, and phase shift as described. Hook up your oscilloscope directly to the sources to ensure you have the settings correct and obtain the inputs shown.

<div style="text-align: center;"><img src="/assets/images/lab_images/sequential_switching/timing.png" alt="timing" width="1023.3015pt"></div>



*Note:* we will need the 50Ω impedance setting on, which will result in double the voltage output that you type into the generator. Halve each of the values to obtain the correct amplitudes and offsets. You will also need to adjust the phase shift in the second signal until you obtain a 90‐degree shift as shown

*Note:* the value you enter may not be 90 degrees as your starting shift will depend on how you turned on your generator signals. Ensure that you have the correct sequence of states, for example: prior to $t_1$, both signals are off – then at $t_1$, V1 (10V) turns on...etc.

2.  Assemble the circuit below as shown using your dual‐function generator as described in step 1 for the two sources.  While this circuit will not explicitly have switches, the function generator outputs will act as the switches by turning on and off the voltage sources at the appropriate times.

<div style="text-align: center;"><img src="/assets/images/lab_images/sequential_switching/exp_circuit.png" alt="Experimental Circuit" width="339.882pt"></div>

3. View V1 on CH1 and V2 on CH2 of the oscilloscope. Use CH3 of the oscilloscope to observe the voltage across the capacitor.

4.  Save the data as a text file (CSV) to your USB drive. Plot this data including your simulation in your `v_C(t)` function and from the SPICE simulation.




