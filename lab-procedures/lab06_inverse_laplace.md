---
layout: page
title: "lab06: inverse_laplace"
parent: Lab Procedures
nav_order: 9
math: mathjax3
---

# Computational Transforms

## Purpose

The Laplace Transform converts the integral-differential equations of electromechanical systems into algebraic equations. However, evaluating the inverse Laplace transform can be cumbersome. This lab will introduce Python tools that can be used to find the inverse Laplace transform.

## Background

In lecture, we learned how to analytically take the inverse Laplace transform. We noticed that the crux of this problem lies with finding the partial fraction expansion. We examined four cases of partial fraction expansion:

*   Real and distinct roots
*   Complex and distinct roots
*   Real and repeating roots
*   Complex and repeating roots

This lab will focus on tools in the `scipy` library that will aid in finding the coefficients for the partial fraction expansion. Please read the online documentation for the `scipy.signal.residue()` function.

## Procedure

Write a function `inverse_laplace` that computes the inverse Laplace transform for a proper rational function for values of time $t$. You do not have to worry about improper rational function cases.

The inputs are defined as:
*   `N_s`: This is a numpy array or list of the coefficients for the polynomial $N(s)$.
*   `D_s`: This is a numpy array or list of the coefficients for the polynomial $D(s)$.
*   `t`: This is a numpy array of the time values to compute the inverse transform.

The outputs are defined as:
*   `f`: This is a numpy array of the values of the inverse Laplace transform that corresponds to the time array `t`.

**Hint:** Use `scipy.signal.residue` to compute the partial fraction expansion coefficients (residues), poles, and direct terms.

**Hint:** The point of this lab is to realize that _many_ inverse Laplace transform pairs can be boiled down to a single entry on the Laplace transform table:


$$ \frac{n!}{(s-a)^{n+1}} \leftrightarrow t^n e^{at} u(t) $$


To write your function, you can just stick with this single entry and use the coefficients from the partial fraction expansion to compute the inverse Laplace transform.  You might be wondering about the complex roots case.  Let's look at a symbolic example.  Consider the following Laplace transform of a simple two complex pole system


$$ F(s) = \frac{a+jb}{s-(c+jd)} + \frac{a-jb}{s-(c-jd)}. $$


This is a _very_ common form in this class because we are working with real-valued time domain functions, so the poles will be complex conjugates and the residues will be complex conjugates.  The inverse Laplace transform of this function is


$$ f(t) = (a+jb) e^{(c+jd)t}u(t) + (a-jb) e^{(c-jd)t}u(t) = 2e^{ct}\left[a\cos(dt) - b\sin(dt)\right]u(t). $$


However, our solver isn't looking for an analytical solution, it is just looking for a numerical solution in the time-domain, so we _do not_ need to worry about casting the solution into a clean analytical form of sines and cosines (though on an exam you would need to do this!).  Instead, it turns out that if you were just plot 


$$ f(t) = (a+jb) e^{(c+jd)t}u(t) + (a-jb) e^{(c-jd)t}u(t) $$


you would get some complex values, but the real part would be non-zero while the imaginary parts would cancel out to zero for every time value!  In short, you can just compute the inverse Laplace transform using the residues and poles like we normally do with the real and distinct case and then just take the real part!  The real and distinct case is just a special case of the complex and distinct case where the poles and residues happen to be real numbers.  

If you just write your code for the complex and distinct case, it will work for all cases!  This is a very common theme in engineering: the more general solution will always work for the special cases, but the special cases will not work for the general case.  So, it is often best to just write code for the most general case and then let that code handle all the special cases as well!

And since I am already on my soapbox, in engineering you routinely need to valid your work with numerical tools.  We do this all the time in our circuits-oriented labs.  We first derive an expression for $v(t)$ or $i(t)$ using the tools we have learned in class, and then we simulate it using SPICE, which is a numerical tool.  We then compare our analytical results to the numerical results to make sure they match.  If they don't match, then we know we made a mistake in our analytical work, and we can go back and fix it. This workflow is very common in engineering:  derive, simulate, and compare.

**A final note:** In this exercise you are not provided a solution to test your function against.  This is intentional.  In engineering, you will often not _know_ the solution to a problem and will not necessarily be provided a solution.  Here, we are going to develop our numerical method and simultaneously derive the inverse Laplace transforms for various test cases.  We will compare our numerical results to our analytical results to validate that our code is working correctly.  If they both align, they both most likely are correct.

### Test Case 1: Real and Distinct Roots
Consider the following Laplace transform


$$ F(s) = \frac{96(s+5)(s+12)}{s(s+8)(s+6)}. $$


First, derive the inverse Laplace transform analytically. Write a Python function represents this function called `f_1(t)`.  

Now, plot your function `f_1(t)` for $t$ values from -1 to 5 seconds.  Along with your simulation.  They should align nearly exactly!

### Test Case 2: Complex and Distinct Roots
Consider the following Laplace transform


$$ F(s) = \frac{100(s+3)}{(s+6)(s^2+6s+25)} $$


First, derive the inverse Laplace transform analytically. Write a Python function represents this function called `f_2(t)`.

Now, plot your function `f_2(t)` for $t$ values from -1 to 5 seconds.  Along with your simulation.  They should align nearly exactly!

### Test Case 3: Real and Repeating Roots
Consider the following Laplace transform


$$ F(s) = \frac{100(s+25)}{s(s+5)^3} $$


First, derive the inverse Laplace transform analytically. Write a Python function represents this function called `f_3(t)`.

Now, plot your function `f_3(t)` for $t$ values from -1 to 5 seconds.  Along with your simulation.  They should align nearly exactly!

### Test Case 4: Complex and Repeating Roots
Consider the following Laplace transform


$$ F(s) = \frac{768}{(s^2+6s+25)^2} $$


First, derive the inverse Laplace transform analytically. Write a Python function represents this function called `f_4(t)`.

Now, plot your function `f_4(t)` for $t$ values from -1 to 5 seconds.  Along with your simulation.  They should align nearly exactly!

