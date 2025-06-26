---
layout: post
title: "Numerical Integrals in a nutshell (Calculus Material 7)"
math: true
description: Estimating area without using anti-derivatives.
date: 2025-06-26
categories: [calculus, math]
tags: [calculus]
image:
  path: /assets/img/INTEGRALDEF.png
---

## Introduction

Welcome to the cousin of Numerical Derivatives! **Numerical Integrals**. The purpose of Numerical Integrals are exactly the same as Numerical Derivatives, to find the integral (mostly definite integral) by analyzing data values in a table (x points and its values). The 2 most common ways of finding a Numerical Integral are shown below:

---

## The Trapezoidal Rule

Instead of rectangles (like Riemann Sums), we use *trapezoids* to estimate area between points.

$$
\int_a^b f(x) \, dx \approx \frac{h}{2} \left[f(x_0) + 2f(x_1) + 2f(x_2) + \cdots + 2f(x_{n-1}) + f(x_n)\right]
$$

- $$ h $$ is the spacing between x-values: $$ h = \frac{b-a}{n} $$
- $$ x_0, x_1, ..., x_n $$ are the data points

It's like connecting the dots with straight lines and calculating the total area underneath. Not perfect, but pretty good if your function isn't throwing tantrums.

---

## Simpson’s Rule (if spacing is even and n is even)

$$
\int_a^b f(x) \, dx \approx \frac{h}{3} \left[f(x_0) + 4f(x_1) + 2f(x_2) + 4f(x_3) + \cdots + 2f(x_{n-2}) + 4f(x_{n-1}) + f(x_n)\right]
$$

You alternate 4s and 2s like it’s some weird integration chant. It’s *more accurate* than trapezoids, but it only works if:
- Your x-intervals are evenly spaced
- You have an **even** number of subintervals

So yeah. Fancy, but slightly picky.

---

## Example

Say you have:

| $$ x $$ | $$ f(x) $$ |
|--------|------------|
| 0      | 1          |
| 1      | 2          |
| 2      | 4          |

Using the **Trapezoidal Rule**:

$$
\int_0^2 f(x) dx \approx \frac{1}{2} [1 + 2(2) + 4] = \frac{1}{2} [1 + 4 + 4] = \frac{1}{2} \cdot 9 = 4.5
$$

---

## Conclusion

Numerical Integrals are your emergency backup when functions don’t behave or don’t even exist. Just plug in the values, pick the rule that fits, and go. Is it perfect? No. Is it **better than guessing**? 100%.
