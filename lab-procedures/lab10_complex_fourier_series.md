---
layout: page
title: "lab10: complex_fourier_series"
parent: Lab Procedures
nav_order: 13
math: mathjax3
---

# Complex Fourier Series

## Background

In this lab we are going to explore the complex Fourier series representation of a periodic signal and how we can use this representation to model the behavior of a circuit.  We will be using a familiar RLC circuit from an earlier lab.

First, consider the following periodic signal.

Your first task is to derive the complex Fourier series for this signal.  Let's start by deriving the Fourier coefficients


$$
C_n = \frac{1}{T} \int_{t_0}^{t_0 + T} v(t) e^{-j n \omega_0 t} dt
$$


where $T$ is the period of the signal, $\omega_0 = \frac{2\pi}{T}$ is the fundamental angular frequency, and $t_0$ is an arbitrary starting point.  You can choose any value for $t_0$ since the signal is periodic.

Once we have the Fourier coefficients, we can write the complex Fourier series representation of the signal as


$$
v_i(t) = \sum_{n=-\infty}^{\infty} C_n e^{j n \omega_0 t}.
$$



Derive the Fourier coefficients and define them as a Python function `C_n(n)` that takes an integer `n` (both positive and negative) as input and returns the corresponding Fourier coefficient.  It might be helpful to adjust $v_i(t)$ such that the period starts at a more convenient point and adjust the vertical shift of the signal to make the integration easier.

Once you are confident in your $C_n$ coefficients, let's build the Fourier series approximation of the signal.  Define a function `v_i(t, N)` that takes a time vector `t` and an integer `N` as input and returns the Fourier series approximation of the signal using the first `N` Fourier coefficients (i.e., from $-N$ to $N$).  Because the original $v_i(t)$ is real-valued, the output of your function should also be real-valued.  You will notice that if you set up your function properly, the imaginary parts will be negligible and can be ignored (i.e., just return the real part).

Now let's visualize this to make sure it matches!  Make a plot from $-T$ to $T$ of the original signal and the Fourier series approximation using `N=1, 5, 10, 20, 1000` coefficients.  You should see that the Fourier series approximation closely matches the original signal.

Now consider the following circuit.  

<div style="text-align: center;"><img src="/assets/images/lab_images/complex_fourier_series/circuit.png" alt="RLC Circuit" width="383.274pt"></div>

Derive the transfer function $H(s)$ of this circuit.  Represent your answer as a function `H(s)`.

Finally, we can model the system output by using the Fourier series representation of the input signal and the transfer function of the system.  The output can be computed as


$$
v_o(t) = \sum_{n=-\infty}^{\infty} H(j n \omega_0) C_n e^{j n \omega_0 t}.
$$


Define a function `v_o(t, N)` that takes a time vector `t` and an integer `N` as input and returns the output of the system using the first `N` Fourier coefficients.  Again, because the output is real-valued, you can ignore any negligible imaginary parts.

Now, let's visualize the output of the system.  Make a plot from $-T$ to $T$ of the output signal using `N=1, 5, 10, 20, 1000` coefficients.  You should see that as you increase `N`, the output signal converges to a steady-state response that is a distorted version of the input signal due to the filtering effect of the RLC circuit.

We see in this plot that it takes fewer harmonics to converge to the output signal than it did to converge to the input signal.  Please explain why this is the case in the markdown cell below.

### BEGIN SOLUTION
The circuit acts as a bandpass filter, which filters out the higher frequency components of the input signal.  As a result, the output signal is smoother and has fewer high-frequency components than the input signal.  
### END SOLUTION

## SPICE simulation

Build this circuit in SPICE.  Generate the proper input using the `PULSE` source, but make sure that you adjust the timing parameters to match the period, duty cycle, and phase of the input signal we have been working with.  Simulate the circuit for around 500 μs.  When you look at the output plot of the simulation, you will notice that it takes a while for the output to reach steady-state.  We are interested in the steady-state response, so you can ignore the transient response at the beginning of the simulation.  

Plot the SPICE response.  You will need to adjust the time range to focus on the steady-state response.  My recommendation is to just adjust the time-array from the output data to shift the time so that the steady-state response (around 300 μs) is centered around $t=0$ and then restrict the plot from $-T$ to $T$.  You should see that the SPICE response closely matches the Fourier series approximation of the output signal.
```python
data_spice = np.loadtxt("rlc_cpx_spice_data.txt")
t_spice = data_spice[:, 0] - 300e-6  # Shift time to align with our plot
v_spice = data_spice[:, 1]
```
When comparing the SPICE response to the Fourier series approximation, make sure to include enough harmonic terms that approximates the $n\rightarrow \infty$ limit well.  From the earlier exercise you saw that it doesn't take a lot of terms to converge to a good approximation, so you can probably get away with around `N=100` or so.



## Hardware implementation

Let's see how this works in the physical world!  Build the circuit using the inductor that you wound earlier in the semester.  You might want to check that the windings are still okay and that the inductor still has the same inductance of around 1.14 mH.  Make sure that you set up in the input voltage source properly to capture the proper voltage and phase offsets.  

You will also need to trigger your oscilloscope properly so that the phase is aligned with the Fourier series approximation.  My recommendation is to generate a second square wave with a $0^\circ$ phase shift and use that as the trigger signal for the oscilloscope.  This way, you can ensure that the phase of the input signal is properly aligned with the Fourier series approximation.  Make sure that the two square waves are properly synchronized (i.e., make sure you hit `Sync Phase` on the function generator).  

Measured the output and make a plot of the calculated Fourier series approximation, SPICE simulation, and the measured output on the same plot.  You should see that all three responses closely match each other.  Restrict the plot to the range from $-T$ to $T$ and make sure to include enough harmonic terms in the Fourier series approximation to get a good approximation of the output signal.

