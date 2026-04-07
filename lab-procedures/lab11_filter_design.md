---
layout: page
title: "lab11: filter_design"
parent: Lab Procedures
nav_order: 14
math: mathjax3
---

# Filter Design

## Bandpass filter design

This lab will be a little different from the previous ones. Instead of working with a pre-designed circuit, we are going to design our own bandpass filter from a set of specifications.  The following specifications are given:

- The resonant frequency of the filter is 10 kHz (within 10%).
- The bandwidth of the filter is 10 kHz (within 15%).
- The gain of the filter at the resonant frequency is 1.

Recall that the bandwidth of the filter is related to the quality factor and the resonant frequency by the following relationship:


$$\beta = \frac{\omega_0}{Q}
$$



You need to design a bandpass filter that meets these specifications. You can use any filter topology you like, but it must be realizable with the components available in the lab. You will need to calculate the component values for your filter and then build it on a breadboard. Once you have built the filter, you will need to test it to make sure it meets the specifications.

I would strongly suggest starting with a simple RLC bandpass filter since we know the transfer function, solve for the component values (again, this is going to be highly dependent on the components you have available in the lab and you might need to make some parallel and series combinations), and then plotting the frequency response in Python from $f\in[1\text{ kHz}, 100\text{ kHz}]$.  You can plot the frequency response below.  A few notes about plotting frequency responses:

- The $x$-axis should be in logarithmic scale (use `plt.semilogx()` instead of `plt.plot()`).  Plot the frequency response in Hz, not in radians per second ($\omega$), but you will need to convert to $f\rightarrow \omega$ for the computation of $H(j\omega)$.
- For the magnitude response, the $x$-axis should be in decibels (use `20 * np.log10(np.abs(H))` to convert the magnitude of the transfer function to decibels).
- For the phase response, the $y$-axis should be in degrees (use `np.angle(H, deg=True)` to convert the phase of the transfer function to degrees).
- Annotate the plot with the resonant frequency and the quality factor of the filter. 


## SPICE simulation

We can also plot the frequency response of the filter using SPICE.  If you are using LTSpice, set your input voltage as an AC source with a voltage with magnitude 1 V.  You can use the `.ac` analysis to plot the frequency response of the filter.  You can plot the magnitude and phase response on separate subplots.  Make sure to label the axes and annotate the plot with the resonant frequency and the quality factor of the filter.

## Hardware implementation

Build the circuit in hardware using the components you have available in the lab.  First, you will need to measure the frequency response ``the hard way.''  Using the function generator, apply a sinusoidal input signal to the filter
- 1 Vpp
- 100 Hz
- High-Z

You will need to measure the input and output waveforms on the oscilloscope.  Measure the ratio of the output amplitude to the input amplitude and convert to dB.  Measure the phase difference between the input and output waveforms.  You will need to repeat this process over a range of frequencies from 100 Hz to 100 kHz (you can choose the frequencies, but I suggest a logarithmic spacing).  Make a plot of this measured frequency response and compare it to the theoretical frequency response you calculated in Python and what you observed in SPICE.  You should see that the measured frequency response matches the theoretical frequency response reasonably well, especially around the resonant frequency.

You might notice that your data looks kind of odd due to loading effects.  This spec will likely require a low-impedance resistor, which will draw a lot of current and cause the function generator to lose constant-voltage control.  This will reduce the input signal's amplitude, thereby lowering the measured gain.  To mitigate this issue, you can use a buffer amplifier (e.g., an op-amp in a voltage follower configuration) to isolate the function generator from the filter.  This will allow you to maintain a constant input voltage and obtain a more accurate frequency response measurement.

A standard voltage follower might not be enough.  Since we are primarily working with dual-sided LF353 opamps, we can use both sides of the chip.  The figure below shows this circuit.  

<div style="text-align: center;"><img src="/assets/images/lab_images/filter_design/dual_follower.png" alt="Dual Follower Circuit" width="423.816pt"></div>

If you use this, it will not affect the filter's frequency response, but it will allow you to maintain a constant input voltage and obtain a more accurate measurement of the frequency response.  

Now you have done this ``the hard way,'' the oscilloscopes can automate this process for you!

1. Hit the `Analyze` button on the oscilloscope.
2. Select `FRA` from the `Features` menu.
3. Select `Setup` from the `FRA` menu.
  * Set the `Start` frequency to 1 kHz and the `Stop` frequency to 100 kHz.
  * Set the `Amplitude` to something reasonable (e.g. `1 Vpp`).
  * Set the `Impedance` to `High-Z`.
  * Set the `Points` to something reasonable (e.g. `140`).
4. Hit the `Run Analysis` button to start the frequency response analysis.  The oscilloscope will automatically sweep through the frequencies and measure the amplitude and phase response of the filter.  

To save this result, go to the save menu like we usually do, but instead of saving the data as a `CSV`, select it as `FRA` instead.  This will save the data to a CSV file.  When you look at the CSV file, the oscilloscope will insert a degree symbol ($^\circ$) at the top of the phase column. You will need to just delete this symbol so `np.loadtxt()` can read the data properly.  

Once you have loaded the data, you can plot it on top of the theoretical and SPICE frequency responses to see how well they match.  Please plot the magnitude and phase response plots on separate subplots.  

You must save this data as arrays using specific variable names:
* The frequency array should be saved as `f_fra`.
* The magnitude response array should be saved as `mag_fra`.
* The phase response array should be saved as `phase_fra`.


Subsequent cells are tests to verify that the specifications are met and to plot the frequency response of the filter.  

