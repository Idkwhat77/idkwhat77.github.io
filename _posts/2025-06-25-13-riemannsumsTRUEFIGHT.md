---
layout: post
title: "Riemann Sums in a nutshell (Calculus Material 4)"
math: true
description: Man, I hate calculating these cursed triangles.
date: 2025-06-25
categories: [calculus, math]
tags: [calculus]
image:
 path: /assets/img/RIEMANNDEF.png
---
## Introduction
What is a "Riemann Sums"? Is it the sum of someone named Riemann? What is that supposed to mean? The concept IS actually made by someone named Riemann, but what does the sum part mean? Alright, enough babbling, Let's just move on to *What even is Riemann Sums*?

## What is Riemann Sums?

In short, a Riemann Sums is the concept of estimating the curve under an area with irregular shape (think about some messed up triangle or circle with weird curves). We do this by breaking down the area into a bunch of small rectangles and add them all up to calculate the total area, hence where the *Sums* part of Riemann Sums come from. The smaller the rectangles, the more accurate the total area is. Area length is usually determined by an interval, like from x = 1, to x = 5. The official formula is shown below : 

$$
\sum_{i=1}^{n} f(x_i) \Delta x
$$

- n: the number of rectangles
- $$\Delta x$$: found by subtracting the left endpoint from the right, then dividing by the number of rectangles
- $$\Delta x = \frac{b - a}{n}$$
- $$f(x_i)$$: the height of each rectangle, found by plugging $$x_i$$ into the function  

Depending on how you choose $$x_i$$, you get different types of Riemann Sums:
- Left Endpoint: use the left edge of each subinterval. Does not include the rightmost subinterval.
- Right Endpoint: use the right edge of each subinterval. Does not include the leftmost subinterval
- Midpoint: use the center of each subinterval

What's an endpoint? For Left Endpoints, you get the leftmost interval (let's say we use interval from [1,5], which is 1). Now we find the width ($$\Delta x$$). Then we keep adding that leftmost interval with the width, with each interval being one endpoint. Keep doing this until you reach the rightmost interval (but don't include it). Same case with Right Endpoints, but you instead subtract it with the width until you reach the leftmost interval. For Midpoints, just get the average of each interval's left and right bounds.

## Example Problem

Estimate the area under the curve of:

$$
f(x) = x^2 + 1
$$

on the interval \([1, 5]\), using **4 rectangles** and a **Left Riemann Sum**.

---

### Step 1: Find \(\Delta x\)

$$
\Delta x = \frac{5 - 1}{4} = 1
$$

---

### Step 2: Left Endpoints

Since we’re using a **Left Riemann Sum**, we use:

$$
x_1 = 1,\quad x_2 = 2,\quad x_3 = 3,\quad x_4 = 4
$$

---

### Step 3: Evaluate \(f(x_i)\)

$$
f(1) = 2,\quad f(2) = 5,\quad f(3) = 10,\quad f(4) = 17
$$

---

### Step 4: Apply the Riemann Sum Formula

$$
\sum_{i=1}^{4} f(x_i)\Delta x = (2 + 5 + 10 + 17)(1) = 34
$$

$$
\boxed{\text{Area} \approx 34}
$$

## Conclusion

Riemann Sums are for estimating the area under a curve with an irregular shape. It has 3 main types, Left, Right, and MidPoint.
The more rectangles you use, the more accurate the estimate becomes. Riemann Sums are the stepping stone toward understanding **definite integrals**. So yeah. Curse the rectangles all you want—but they *do* get the job done.