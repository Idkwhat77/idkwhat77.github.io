---
layout: post
title: "Integrals in a nutshell (Calculus Material 5)"
math: true
description: Area under curves and mysterious "+ C" magic.
date: 2025-06-25
categories: [calculus, math]
tags: [calculus]
image:
 path: /assets/img/INTEGRALDEF.png
---

## Introduction
Instead of doing rectangle stuff with Riemann Sums, why not use something much simpler? Introducing Integrals! They're basically the opposite of derivatives, we want to find what the function is BEFORE the derivative happens. There are 2 main types, Indefinite and Definite.

## Indefinite Integrals

Indefinite integrals are the integral themselves without any intervals. No calculating the area for now. The general formula looks like this:

$$
\int f(x) \, dx
$$

And the result is a **function** plus a constant:

$$
\int x^2 \, dx = \frac{x^3}{3} + C
$$

- The $$ \int $$ symbol means you're integrating.
- $$ f(x) $$ is the function you want to reverse.
- $$ dx $$ tells you the variable you're integrating with respect to.
- The $$ +C $$ is the **constant of integration**, because any constant disappears when you differentiate—so we have to add it back when going backwards.

---

### Example:

Let’s say you have:

$$
\int (3x^2 + 4x + 7) \, dx
$$

You just reverse each term:

- $$ \int 3x^2 \, dx = x^3 $$
- $$ \int 4x \, dx = 2x^2 $$
- $$ \int 7 \, dx = 7x $$

So the full answer is:

$$
x^3 + 2x^2 + 7x + C
$$

## Definite Integrals

Unlike indefinite integrals, **definite integrals** actually give you a number. Instead of reversing the derivative just to get a function, you use that function to calculate the **area under the curve** between two points.

The general form is:

$$
\int_{a}^{b} f(x) \, dx
$$

- $$ a $$ is the **lower bound**
- $$ b $$ is the **upper bound**
- The result is the **exact area** under the curve from $$ x = a $$ to $$ x = b $$

---

### Steps to Solve:

1. **Find the antiderivative** (just like indefinite integrals)
2. **Plug in the bounds** using this notation:
   $$
   \left[F(x)\right]_a^b = F(b) - F(a)
   $$

---

### Example:

Estimate the area under the curve:

$$
f(x) = x^2
$$

from $$ x = 1 $$ to $$ x = 5 $$:

---

**Step 1: Find the antiderivative**

$$
\int x^2 \, dx = \frac{x^3}{3}
$$

---

**Step 2: Plug in bounds**

$$
\left[\frac{x^3}{3}\right]_1^5 = \frac{5^3}{3} - \frac{1^3}{3} = \frac{125 - 1}{3} = \frac{124}{3}
$$

---

**Final Answer:**

$$
\boxed{\text{Area} = \frac{124}{3}}
$$

---

So yeah—no rectangles, no estimating. Just one clean number that tells you exactly how much space is under the curve.

## Weird Functions
What if the function we want to find the integral of is a function inside another function (chains rule flashback hehe)? Similar to chains rule, we have to deal with Integral substitution.

This method is often called **u-substitution**, and it helps us deal with complicated functions that look like:

$$
\int f(g(x)) \cdot g'(x) \, dx
$$

Sounds scary? Don’t worry—I’ll make it less cursed.

---

### The Strategy:

We turn the complicated inner part of the function into a single variable, usually \( u \). Then the integral becomes a lot easier to deal with.

---

### Example:

Let’s say we want to integrate this:

$$
\int 2x(x^2 + 1)^3 \, dx
$$

Looks like a mess, right? But if you look closer, you’ll notice something familiar...

- The inside of the parentheses is \( x^2 + 1 \)
- Its derivative is \( 2x \), which is *sitting outside!*

That’s our cue to use substitution.

---

### Step 1: Let \( u = x^2 + 1 \)

Then the derivative of \( u \) is:

$$
\frac{du}{dx} = 2x \Rightarrow du = 2x \, dx
$$

---

### Step 2: Replace everything in terms of \( u \)

The integral becomes:

$$
\int (x^2 + 1)^3 \cdot 2x \, dx = \int u^3 \, du
$$

---

### Step 3: Integrate \( u^3 \)

$$
\int u^3 \, du = \frac{u^4}{4} + C
$$

---

### Step 4: Substitute \( u \) back

$$
\frac{(x^2 + 1)^4}{4} + C
$$

---

### Final Answer:

$$
\boxed{\frac{(x^2 + 1)^4}{4} + C}
$$

---

So yeah—when a function *inside* a function shows up in your integral, **don’t panic**. Just give it a new name (like \( u \)), simplify, integrate, then put it back. 

## Conclusion 
Integrals are the opposite of derivatives. We want to find the original function BEFORE the derivative happens. It is a much easier way than doing those Riemann Sums rectangle witchcraft.