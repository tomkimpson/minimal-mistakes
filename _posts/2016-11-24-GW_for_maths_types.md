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


With the detection of the first test gravitational waves by LIGO just over one year ago, there have been a plethora of great articles explaining gravitational waves to the layman. These are all excellent resources, but someone with a more maths-based background might find them lacking: questions such as **"Why does a spinning star not emit gravitational waves?"**, **"Why is the amplitude of gravitational waves so small"** or **"do gravitational waves carry energy"** can only be properly explained with reference to the mathematics associated with the physics. Hopefully this post will help those with a stronger maths background gain a deeper understanding of one of the greatest empirical detections.

** Linearized theory**
At small scales we can consider space to be flat and described by the Minkowski metric $\nu_{ab}$. For our paedological purposes, it will be sufficient to consider the linearized theory of gravitational waves, and introduced a small perturbation $h_{ab}$ to the flat space, such that the total metric is,

$$ g_{ab}=\nu_{ab}+h_{ab}$$

This equation can be solved (arduously, see MTW) to show that

$$ \Box h_{ab} = 16 \pi T_{\mu \nu}$$

where $$ \Box$$ is the d'Alembertian operator and $$ T_{\mu \nu}$$ the stress energy tensor.

This equation is simply the wave equation with a source term $$16 \pi T_{\mu \nu}$$ The stress-energy tensor describes all the energy and momentum (in addition to the pressure and stress) in a space. So the equation can simple be read as "the perturbation changes like a wave, in a way determined by the amount of energy and mass."

Note that the linearized theory is only an approximation - in using it we consider a localized source of GW in steady oscillation, radiating periodic wave. In the exact theory the energy of the source decreases secularly (long-term, non periodic) due to the energy lost by gravitational radiation. There are also spacetime curvatures due to planets/stars/galaxies etc. and the propagation of GW through these curvatures can cause a backscatter that is not accounted for in the linearized theory.


### Quadrupole


### References
Misner, Thorne, Wheeler  - Gravitation
