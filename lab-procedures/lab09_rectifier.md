---
layout: page
title: "lab09: rectifier"
parent: Lab Procedures
nav_order: 12
math: mathjax3
---

# Rectifier

## Warmup!

Consider the waveform, which is plotted below. 

Write a function `f_fs_square(t, N)` that computes the Fourier series approximation of this waveform using $N$ Fourier coefficients (summing up to $N$). 

Plot the Fourier series approximation from $-5 \leq t \leq 5$ for $N = 1, 3, 5, 10, 50$.

Notice what happens as you increase the number of Fourier coefficients.  What do you observe?  How does the Fourier series approximation change as you increase $N$?  What happens at the points where the function is discontinuous?  This phenomenon is known as the Gibbs phenomenon.  You can read more about it [here](https://en.wikipedia.org/wiki/Gibbs_phenomenon).

## Fourier series derivation

Consider the following circuit.

<div style="text-align: center;"><img src="/assets/images/lab_images/rectifier/rectifier_circuit.png" alt="Rectifier Circuit" width="565.2045pt"></div>


This circuit acts as a full-wave rectifier, which takes an input voltage $v_\text{in}(t)$ and produces an output voltage $v_\text{out}(t)$ that is the absolute value of the input voltage.  In this instance, we will consider the input voltage to be a sinusoidal waveform given by 

$$v_\text{in}(t) = 2 \sin(2\pi f_\text{in}) t)\text{ V}$$

 where $f_\text{in} = 60\text{ Hz}$ is the frequency of the input signal.  

Derive the Fourier series representation of the output voltage $v_\text{out}(t)$, which is given by 

$$v_\text{out}(t) = |v_\text{in}(t)|.$$

  Represent your answer as a sum of the relevant sine and cosine terms.  Your function should take in the time variable $t$ and the number of Fourier coefficients $N$ to compute the approximation.  Your function call should look like `v_out(t, N)`, where `t` is a numpy array of time values and `N` is the number of Fourier coefficients to compute.

Let's see how well your approximation works!  Plot the Fourier series approximation of $v_\text{out}(t)$ from $-2T \leq t \leq 2T$ for $N = 1, 3, 5, 10, 50$.  Plot the original function $v_\text{out}(t)$ on the same graph to compare the approximation to the original function.

We see that just like in the first square wave example, as we increase the number of harmonics, we converge closer and closer to the original function!  

## SPICE SIMULATION

Simulate the circuit in SPICE using a sine-wave input waveform with an amplitude of 2 V and a frequency of 60 Hz.  Plot the output voltage $v_\text{out}(t)$ from the SPICE simulation and compare it to the Fourier series approximation you derived in the previous section (use $N=100$).  Make your plot from $0 \leq t \leq 4T$.

Plot the frequency spectrum of the output voltage.  Measure the FFT (the fast Fourier transform---something you will learn about in Signals and Systems) at the output node and plot the magnitude of the FFT as a function of frequency.  The SPICE command for this is:

```
fft V(vout)
```

When you do this, make sure your transient simulation runs long enough (about 10 seconds) to achieve good frequency resolution in the FFT.  You can use the following command to set the transient simulation time:

```
.tran 20u 10 0 5u
```

Plot the magnitude of this FFT as a function of frequency.  Restrict your plot from 0 to 2 kHz.  

Next, plot the magnitude of the coefficients of the Fourier series approximation you derived in the previous section as a function of frequency.  The frequency each coefficient corresponds to is given by $f_n = n f_0$, where $f_0$ is the fundamental frequency of the rectified signal.  Plot your coefficients as a scatter plot (`plt.scatter`).  Restrict your plot from 0 to 2 kHz.

What you are seeing in the FFT of the rectified signal is the harmonic content of the waveform, which consists of a DC component (the average value of the waveform) and harmonics at integer multiples of the input frequency (60 Hz, 120 Hz, 180 Hz, etc.).  The Fourier series approximation you derived should roughly match the FFT of the rectified signal, since they are both representations of the same function.  There will be some slight differences because the Fourier series approximation represents an infinitely long signal, while the FFT represents a finite-length signal. We will learn more about this in great detail in Digital Signal Processing.


## Physical circuit

Build the circuit.  Use the same input (4 Vpp, 60 Hz) and measure the output voltage $v_\text{out}(t)$ on an oscilloscope.  Plot the output voltage and compare it to the Fourier series approximation you derived in the previous section (use $N=100$).  Make your plot from $0 \leq t \leq 3T$.

Now let's measure the frequency spectrum of the output voltage.  The oscilloscopes also have a built-in FFT function, so you can use that to measure the FFT of the output voltage.  Select the FFT function on the oscilloscope.  Adjust the setting such that:
* The source is set to the channel you are measuring the output voltage on
* The time window is set to 100 ms per division (this will give you good frequency resolution)
* The frequency center is set to `1 kHz`
* The frequency span is set to `2 kHz`
* The Vertical Units are are set to `V RMS`
* The Window is set to `Flat Top`
Save this data to a CSV.  Plot the FFT data against the SPICE data and the Fourier series coefficients on the same graph.  Restrict your plot from 0 to 2 kHz.  

You will notice that there is _some_ differences between the measured and predicted.  
1.  The DC component is gone.  
2.  The amplitudes of the measured FFT do not match the predicted amplitudes based on the coefficients.  This is a DSP thing, stemming from the FFT.  

