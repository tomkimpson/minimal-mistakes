---
title: "Gravitational Waves for Maths People"
modified:
categories: [GR]
excerpt: "GW - Warning maths ahead!"
tags: [GR,GW]
image:
feature:
date: 2016-11-24
pinned: true
---

1. [Intro](#intro)

2. [Primer](#primer)

3. [Linearized Theory](#lin)

4. [Multipoles](#multipole)

5. [Amplitude](#amp)

## Introduction <a name="intro"></a>
With the [detection of the first gravitational waves by LIGO](https://www.nasa.gov/feature/goddard/2016/nsf-s-ligo-has-detected-gravitational-waves) just over one year ago, there have been a plethora of great articles (e.g. [this one](http://www.popsci.com/whats-so-important-about-gravitational-waves)) explaining gravitational waves to the general public. This is all excellent and important outreach, but someone with a more maths/science based background might find these articles lacking.

**"Why does a spinning star not emit gravitational waves?"**, **"Why is the amplitude of gravitational waves so small?"**, **"Do gravitational waves carry energy?"** These are all interesting questions that can only be properly explained with reference to the underlying mathematics and the physics. Hopefully this post will help those with a stronger maths background gain a deeper understanding of one of the greatest empirical detections of this millennium.

## Quick Primer <a name="primer"></a>
We are going to be dealing with metrics and tensors. A metric describes how a space is curved. For a flat space, we have the Minkowski metric, which is given by the tensor $$\eta_{ab}$$. For this post, just think of a tensor as a matrix. With this notation, we can write a distance between two points in a space as,

$$ ds^2 = \eta_{ab} dx^a dx^b$$  

If we consider just two dimensions $$ x,y $$ then the flat metric can be written,

$$ \eta_{ab} = \begin{pmatrix}1 & 0\\0 & 1\end{pmatrix}$$

The only non-zero terms are $$\eta_{11}$$ and $$\eta_{22}$$. Therefore we can write a distance interval in Cartsesian coordinates, in flat space 2D space as,

$$ ds^2 = \eta_{11} dx^1 dx^1 + \eta_{22} dx^2 dx^2 $$
$$ = x^2 +y^2$$

which is simply Pythagoras' theorem! Were we on a curved surface, e.g. the surface of a sphere, then Pythagoeas' theorem does not apply and we would use a different metric to describe the curvature. But the general expression $$ ds^2 = \eta_{ab} dx^a dx^b$$ works for all curvatures.

So bottom line: **tensor=matrix** and **metric=curvature**. Also, in GR we don't work just in two spatial dimensions, but in 4 dimensions - 3 spatial and 1 temporal - to form a general spacetime.

## Linearized Theory <a name="lin"></a>
At small scales we can consider space to be flat and described by the Minkowski metric $$\eta_{ab}$$. For our paedological purposes, it will be sufficient to consider the linearized theory of gravitational waves, and introduced a small perturbation $$h_{ab}$$ to the flat space, such that the total metric is,

$$ g_{ab}=\eta_{ab}+h_{ab}$$

This equation can be solved (arduously, see MTW) to show that

$$ \Box h_{ab} = - \kappa T_{\mu \nu}$$

where $$ \Box$$ is the d'Alembertian operator, $$ \kappa $$ is some constant and $$ T_{\mu \nu}$$ the stress energy tensor.

This equation is simply the wave equation with a source term $$- \kappa T_{\mu \nu}$$ The stress-energy tensor describes all the energy and momentum (in addition to the pressure and stress) in a space. So the equation can simple be read as "the perturbation changes like a wave, in a way determined by the amount of energy and mass."

Note that the linearized theory is only an approximation - in using it we consider a localized source of GW in steady oscillation, radiating periodic wave. In the exact theory the energy of the source decreases secularly (long-term, non periodic) due to the energy lost by gravitational radiation. There are also spacetime curvatures due to planets/stars/galaxies etc. and the propagation of GW through these curvatures can cause a backscatter that is not accounted for in the linearized theory.

We can rearrange this equation to obtain,

$$ h^{\mu \nu} = -\frac{\kappa}{4 \pi} \int d^3 x \frac{T^{\mu\nu}(t-|\vec{x}-\vec{x}'|, \vec{x}')}{\vec{x}-\vec{x}'|}$$

But then all this says is that $$ h^{\mu \nu}$$ is proportional to the second time derivative of the reduced quadrupole moment, or,

$$ h^{\mu \nu} \propto \ddot{Q}^{\mu \nu}$$

where,

$$ \ddot{Q}^{\mu\nu} = \int d^3x \rho(x^{\mu} x^{\nu} - \frac{1}{3}\delta^{\mu\nu}r^2)$$
is the \textit{reduced quadrupole moment}. Let's take a moment to think about what this is, and why it makes sense that GW are related to this moment.


## Multipoles <a name="multipole"></a>
We can expand a radiation field in terms of multipole moments. Let the mass-energy density be $$ \rho(\mathbf{r})$$. We can then expand in terms of multipole moments as:

* **Monopole** $$ \int \rho(\mathbf{r}) d^3r$$.

* **Dipole** $$ \int \rho(\mathbf{r}) \mathbf{r} d^3r$$

* **Quadrupole** $$ I_{ij} =\int \rho(\mathbf{r}) r_i r_jd^3r $$

Now the multipole moment is just the total mass-energy. This is constant and so cannot be the source of gravitational radiation. The dipole is just the centre of mass-energy of the system and so is also constant. The quadrupole is the lowest moment that is not conserved. Physically, it can be thought of as describing how the mass is distributed throughout a system

Now we can see why only certain types of variations produce gravitational waves. A spinning star leaves the quadrupole moment unchanged and so no GW are emitted. Similarly, a spherically symmetric variation is only monopolar and so a collapsing star does not have any variations in the quadrupole either.

To simplify the formulas, in the literature the reduced quadrupole moment is often used, which is defined as the trace free part of the second moment of the mass distribution, i.e. :

$$ Q = I_{jk} - \frac{1}{3} \delta_{jk} trace(I_{ab}) = \int \rho (x_j x_k - \frac{1}{3} \delta_{jk} r^2) d^3 x$$

Alternatively we can think of it in terms of explicit spherical harmonics...

## Amplitude <a name="amp"></a>


### References
Misner, Thorne, Wheeler  - Gravitation
