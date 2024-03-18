---
title: "Markdown Latex Demonstration"
last_modified_at: 2024-03-18
categories:
  - blog
tags:
  - crypto
  - hacking
---
Let's solve the following physics problem

![Problem](/assets/images/2024-03-15-latex-demo/problem.png)

We are given $$R = 1m\Omega \:$$, $$L = \text{OA} = 10 \text{cm} \:$$ and the frequency at which the rod rotates is $$\nu = 60 \text{Hz}$$, we need to find the electric current induced in this circuit denoted as $$I(t)$$

Let's start by writing the laws for induction, from Faraday's law we have

$$U = \frac{\Delta \Phi}{\Delta t}$$

So a change of magnetic flux generates an electromotive force which produces electric current

$$I = U/R$$

Now we need to find $$U$$, for that reason we need to figure out $$\Delta \Phi$$, which is the change of magnetic flux, but before that let's write down the definition of magnetic flux, in our case since the surface vector and the magnetic field vector are always parallel aka $$\theta = 0$$ we find that

$$ \Phi = \vec{B} \cdot \vec{S} = B \cdot S \cos(\theta) = B \cdot S$$

Now let's figure out $$\Phi$$ explicitly at times $$t$$ and $$t+\Delta t$$
$$\Delta \Phi = \Phi(t+\Delta t) - \Phi (t) = B \cdot (S(t + \Delta t) - S(t))$$

It follows

$$U = B  \frac{ (S(t + \Delta t) - S(t))}{\Delta t} = B \cdot \frac{d S(t)}{d t} $$

so we just need to find the derivative of $$S(t)$$

$$ 
S(t) = \frac{1}{2} L^2 \tan(2\pi\nu t) 
$$

$$
\frac{d S(t)}{d t} = \frac{1}{2} L^2 \nu \sec^2(2\pi\nu t)
$$

Finally 

$$
I(t) = \frac{B \cdot L^2 \nu \sec^2(2\pi\nu t)}{2R}
$$