---
layout: page
title: "lab01: phasors"
parent: Lab Procedures
nav_order: 4
math: mathjax3
---

# Phasors and Op-Amps

In this lab we are going to analyze a circuit that takes two AC waveforms


$$
\begin{align*}
&v_1(t) = 2\sin(\omega_1 t)\\
&v_2(t) = 2\sin(\omega_2 t)\\
\end{align*}
$$


as inputs.  The $v_1(t)$ waveform has a frequency of 5 kHz ($\omega_1 = 2\pi\cdot 5\,\text{kHz}$) and the $v_2(t)$  waveform has a frequency 10 kHz ($\omega_1 = 2\pi\cdot 10\,\text{kHz}$).  Both waveforms have an amplitude 2 V, or 4 Vpp.

<div style="text-align: center;"><img src="/assets/images/lab_images/phasors/circuit.png" alt="Circuit diagram" width="737.88pt"></div>


## Phasor analysis

Our task is to find the phasor representation of the output voltage $Y$ of the circuit shown above.  We will do this in several steps.

We notice that the circuit is made up of two op-amp stages.  The first stage is an inverting summing amplifier circuit.  The easiest approach is to analyze the circuit using superposition.  We will first analyze the circuit with only $v_1(t)$ present (i.e., we will replace $v_2(t)$ with a short to ground).  Then we will analyze the circuit with only $v_2(t)$ present (i.e., we will replace $v_1(t)$ with a short to ground).  Finally, we will add the two results together to get the final output voltage.

First, we analyze the circuit with only $v_1(t)$ present.  Solve for the magnitude and phase of the phasor output voltage $Y_1$ due to input voltage $v_1(t)$.  Save this result as two Python variables: `Y1_mag` and `Y1_phase`.

The next code cell is a provided check to make sure you got the correct answer for this part.  Run the cell to see if your results are correct.  Often the numerical answers will be obscured.

Next, we analyze the circuit with only $v_2(t)$ present.  Solve for the magnitude and phase of the phasor output voltage $Y_2$ due to input voltage $v_2(t)$.  Save this result as two Python variables: `Y2_mag` and `Y2_phase`.

Because we solved this circuit using superposition, we can convert phasors $Y_1$ and $Y_2$ back to time-domain signals $y_1(t)$ and $y_2(t)$, and then add them together to get the final output signal $y(t)$.  You don't have to do anything, but it is worthwhile to look at the code if you want to see how this is done.  

You are also provided with a plot so you can visualize the output signal $y(t)$.

## SPICE simulation

Next, we will simulate the circuit using SPICE.  Open the provided `phasor_opamps.cir` file in LTspice (or your favorite SPICE simulator).  Run a transient response from 1 ms to 2 ms (to capture steady state behavior).  Compare the results to your hand calculations and the Python simulation.

Finally, run a transient analysis with both input waveforms present.  Plot the output voltage and compare it to your hand calculations and the Python simulation.  For now, the code to do this is provided for you.  You can run the code with your file (call it `spice.txt`)

## Hardware implementation

Finally, build the circuit on your breadboard.  You can use whatever op-amp you like, but I like the LF353.  Make sure you power the op-amps with +/- 10 V supplies.

Connect the output of your function generator to the two input channels of your circuit as shown in the schematic above.  You will need to set up the function generator to produce two sine waves, one at 5 kHz and one at 10 kHz, both with 2 V amplitude (4 Vpp).

A few things about the function generator settings:
* Set both channels to `High-Z` output impedance.
* Set channel 1 to a sine wave
    - Frequency: 5 kHz
    - Amplitude: 2 V (4 Vpp)
* Set channel 2 to a sine wave
    - Frequency: 10 kHz
    - Amplitude: 2 V (4 Vpp)
    - You will need to sync both channels:
      - Hit `Phase` -> `Sync` -> `Sync Internal`

On the oscilloscope, you connect the probe to the output of your circuit, make sure the ground clip is connected to circuit ground.  To make sure the timing is right, set the oscilloscope to trigger on one of the sine wave inputs. `Trigger` -> `Trigger Type` -> make sure it is set to one of the sine waveforms.

Finally, capture the output waveform data from the oscilloscope.  `Save/Recall` -> Format: `CSV Data` -> press to save.  Name the file `hardware.csv`.

Code below will read in your hardware data and plot it against your hand calculations and SPICE simulation.

_Note:_ The oscilloscope may save the CSV file with the last row with the time and not the voltage.  If this happens, just open the file in a text editor and delete the last row.

