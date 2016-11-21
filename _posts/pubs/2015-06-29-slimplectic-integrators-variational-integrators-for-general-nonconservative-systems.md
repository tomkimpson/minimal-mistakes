---
layout: pub-link
title: "“Slimplectic” Integrators: Variational Integrators for General Nonconservative Systems"
modified: 2015-08-06
categories: pubs
excerpt: "A generalization of symplectic integrators to non-conservative dynamics."
tags: [dynamics]
pub:
  authors: "David Tsang, Chad R. Galley, Leo C. Stein, Alec Turner"
  doi: "10.1088/2041-8205/809/1/L9"
  arXiv: "1506.08443"
  jref: "2015 ApJ <b>809</b> L9"
date: 2015-06-29T21:40:10-05:00
---

A python implementation which generates slimplectic integrators is
available on github as
[slimplectic](https://github.com/davtsang/slimplectic).

![]({{ site.url }}/images/DampSimpleCombined.png)
{: .align-right style="width: 250px"}
> Symplectic integrators are widely used for long-term integration of
> conservative astrophysical problems due to their ability to preserve
> the constants of motion; however, they cannot in general be applied
> in the presence of nonconservative interactions. In this Letter, we
> develop the “slimplectic” integrator, a new type of numerical
> integrator that shares many of the benefits of traditional
> symplectic integrators yet is applicable to general nonconservative
> systems. We utilize a fixed-time-step variational integrator
> formalism applied to the principle of stationary nonconservative
> action developed in Galley et al. As a result, the generalized
> momenta and energy (Noether current) evolutions are well-tracked. We
> discuss several example systems, including damped harmonic
> oscillators, Poynting–Robertson drag, and gravitational radiation
> reaction, by utilizing our new publicly available code to
> demonstrate the slimplectic integrator algorithm. Slimplectic
> integrators are well-suited for integrations of systems where
> nonconservative effects play an important role in the long-term
> dynamical evolution. As such they are particularly appropriate for
> cosmological or celestial N-body dynamics problems where
> nonconservative interactions, e.g., gas interactions or dissipative
> tides, can play an important role.
