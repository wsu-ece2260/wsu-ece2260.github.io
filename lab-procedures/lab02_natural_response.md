---
layout: page
title: "lab02: natural_response"
parent: Lab Procedures
nav_order: 5
math: mathjax3
---

# Natural Response


## Prelab exercises

### RC circuit

An RC circuit is shown below. Assume $R = 10 \text{ k}\Omega$ and $C = 100 \text{ nF}$. The switch has been open for a long time before and is closed at $t = 0$.

<div style="text-align: center;"><img src="/assets/images/lab_images/natural_response/rc_circuit.png" alt="RC circuit" width="342.666pt"></div>


Calculate the time constant ($\tau$) of the circuit.  Represent your answer as `tau_RC = XX` in seconds.

Determine the expression for the voltage across the capacitor, $v_C(t)$ assuming the source voltage is 5V.  Represent your answer as a Python function `v_C(t)` that takes time `t` in seconds as input and returns the voltage across the capacitor in volts.  The

We can plot this to verify it matches our intuition.

Determine the expression for the current through the resistor, $i_R(t)$.  Represent your answer as a Python function `i_R(t)` that takes time `t` in seconds as input and returns the current through the resistor in amps.

If, after 10ms the voltage source is shorted out, find $v_C(t)$.  Represent your answer as a Python function `v_C_shorted(t)` that takes time `t` in seconds as input and returns the voltage across the capacitor in volts.  In other words, your circuit is at rest, the switched is closed, then at 10ms the voltage source is shorted out and you need to find the voltage across the capacitor for $t \geq 10\text{ ms}$.  Your function needs to handle $t<0\text{ ms}$, $t < 10\text{ ms}$ and $t \geq 10\text{ ms}$ correctly.  Note:  your function needs to be able to handle the case where $t$ is in seconds, not milliseconds.

### 2. RL Circuit

An RL circuit is shown below. Assume $R = 100 \Omega$ and $L = 100 \text{ mH}$. The switch is closed at $t = 0$.  Calculate the time constant ($\tau$) of the circuit.  Represent your answer as `tau_RL = XX` in seconds.

<div style="text-align: center;"><img src="/assets/images/lab_images/natural_response/rl_circuit.png" alt="RL circuit" width="339.2805pt"></div>

Determine the expression for the current through the inductor, $i_L(t)$, for $t \ge 0$, assuming the source voltage is 5V.  Represent your answer as a Python function `i_L(t)` that takes time `t` in seconds as input and returns the current through the inductor in amps.

Determine the expression for the voltage across the inductor, $v_L(t)$.  Represent your answer as a Python function `v_L(t)` that takes time `t` in seconds as input and returns the voltage across the inductor in volts.

If, after 10ms the voltage source is shorted out, find $I_L(t)$ and $v_L(t)$.  Represent your answers as Python functions `i_L_shorted(t)` and `v_L_shorted(t)` that take time `t` in seconds as input and return the current through the inductor in amps and voltage across the inductor in volts, respectively.  In other words, your circuit is at rest, the switched is closed, then at 10ms the voltage source is shorted out and you need to find the current through the inductor and voltage across the inductor for $t \geq 10\text{ ms}$.  Your functions need to handle $t<0\text{ ms}$, $t < 10\text{ ms}$ and $t \geq 10\text{ ms}$ correctly.  Note:  your functions need to be able to handle the case where $t$ is in seconds, not milliseconds.

## Experiment

## RC Circuit

Measure the actual capacitance of your capacitor using the multimeter.  Record this value as `C_meas = XX`, in farads.

Assemble the RC circuit. Use a square wave (5Vpk-pk, 50Hz, Offset +2.5V, High-Z). Save the data.  Plot the voltage across the capacitor during the charging phase and compare it to your theoretical prediction.  Label your axes and include a legend.

Plot this data from $t= -5\text{ ms}$ to $t= 20\text{ ms}$.  You may need to adjust the time offset on the measured data (just add some small amount to the time array) to align the data correctly.  Record the time offset you used as `time_offset = XX`, in seconds.

Let's measure the time constant on the circuit itself.  We know that the natural resopnse will decay to 36.8% of its initial value after one time constant, $\tau = RC$.  From your plot, determine the time it takes for the voltage across the capacitor to decay to 36.8% of its initial value after the source is shorted out.  Record this value as `tau_RC_meas = XX`, in micro seconds.  Print both this value and the theoretical value of the time constant calculated from your measured R and C values.

### Part 2: RL Circuit

Measure the actual inductance of your 100 mH inductor using an LCR meter.  Record this value as `L_meas = XX`, in henrys.  Record the resistance of the inductor as `R_meas = XX`, in ohms.  Compute the time constant of the circuit and record it as `tau_RL = XX`, in micro seconds.  Print these values.

Note:  these inductors are pretty terrible as they are primarily used as RF chokes and have a ton of parasitic resistance and capacitance.  You may find that the measured inductance is significantly different from the nominal value.  But it will mostly work with this lab.

Assemble the RL circuit. Capture the inductor voltage waveform using the same square wave settings as before. Save the data.  For the time scaling, please use $20\,\mu\text{s/div}$. Plot the voltage across the inductor during the energizing phase and compare it to your theoretical prediction.  Label your axes and include a legend.

Note:  you will see that this plot is less accurate than what you get with the RC circuit.  This is due to the non-idealities of the inductor.

Measure the time it takes for the inductor voltage (inductor current) to reach 36.8% of its peak value. Record this as the measured time constant.  Record your answer as `tau_RL_meas = XX` in seconds.

