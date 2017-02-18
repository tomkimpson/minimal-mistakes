---
title: "The Detectability of Gravitons"
modified:
categories: [GR]
excerpt: "Short note re gravitons - too long for a tweet"
tags: [GR,GW]
image:
feature:
date: 2017-02-13
pinned: false
---

> tl;dr A detector the mass of Jupiter in a close orbit around a strong source of gravitons like a neutron star would result in only 1 detection every 100 years.


I recently came across a paper, [Rothman, T. and Boughn, S. 2006](https://arxiv.org/pdf/gr-qc/0601043v3.pdf), which is now over a decade old, discussing the feasibility of graviton detection. It was produced in response to a comment made by Freeman Dyson questioning whether it would ever be possible to actually detect a graviton.

In the expected quantum theory of gravity, the gravitational force will be quantized into particles called gravitons. In the same way that a photon mediates the electromagnetic force, so will a graviton mediate the gravitational force. A (now decade old!) paper,  discusses the detectability of these theoretical particles, in response to Freeman Dyson's question on whether it is conceivable that any experiment could directly detect a graviton. Below is summarized the trail of thought and conclusions from what is an interesting, and perhaps ultimately depressing paper.


Imagine some detector of mass $$M_d$$ a distance $$ R$$ from a source - mass $$ M_s$$-of gravitons which have energy $$ \epsilon_{\gamma}$$ The criterion for detecting a single graviton with a high probability is that the path length $$ \lambda$$ should be greater than the mean-free-path,

$$ \lambda > l$$

$$ n \sigma \lambda > 1$$

for density of particles in the detector $$n$$ and $$ \sigma$$ interaction cross section which quantifies the likelihood of a scattering event.

It can be shown (pg. 3) that this criterion approximately reduces to,

$$ f_{\gamma} \sigma M_d \frac{M_s}{R^2} \frac{1}{\epsilon_{\gamma}} >1$$

This seems to make intuitive sense - we want the flux/cross-section and masses of the detector and source to be as large as possible, and also want to minimize the distance between the source and detector.


### Cross section
As stated, the cross section $$ \sigma$$ is an effective area that sets how likely it is that a scattering event will take place when a beam is incident on an object composed of particles. It can also be thought of as the _rate_ of an event; high cross section, high rate of scattering. This is a scalar quantity. Typically in physics we talk of the differential cross section $$ d \sigma /d\Omega$$ which tells us the rate of scattering at a given angle ($$ \Omega$$ here is the [solid angle](https://en.wikipedia.org/wiki/Solid_angle) ). We can define this basically as,

$$ d \sigma = \frac{P}{I}$$

for power absorbed by detector $$P$$ and flux $$ I$$. Now, it can be seen that,

$$ P = \hbar \omega \Gamma$$

where $$ \Gamma$$ is the transition rate given by [Fermi's golden rule](https://en.wikipedia.org/wiki/Fermi's_golden_rule)

$$\Gamma = \frac{2\pi}{\hbar} |<a|H|b>|^2 \rho $$

From here it is possible to show (pg 7 - 10) that for gravitons,

$$ \sigma \sim \hbar G$$

i.e. **some very small quantity**.

With this cross section we are now in a position to determine how likely we are to detect a graviton in different physical situations. We take our detector mass $$ M_d$$ detector to be equal to that of Jupiter, $$ \sim 10^{27}$$ kg, and composed entirely of atomic hydrogen.



### Graviton luminosity

There are few feasible sources of gravitons. We consider each mechanism and the likelihood of graviton detection via this mechanism (see pg 11 onwards.)

**i) Spontaneous Emission**
There are two sub-mechanisms to consider here. One is direct spontaneous emission, where a graviton is emitted spontaneously in the decay of a hydrogen atom from the *3d* to the *1s* state (*Personal note: why should this be true?*). In this case the emitted graviton would have insufficient energy to ionize any of the hydrogen in our Jupiter-mass detector. The second is a gravitational analogue of the [Compton effect](https://en.wikipedia.org/wiki/Compton_scattering), where a graviton is scattered off an electron and we use our detector to detect the electrons recoil energy. In this case, even if we take the source mass to be equal to the mass of the galaxy ($$ \sim 10^{42}$$ kg) and assume that the source - detector separation $$ R \sim 30$$ kpc, the detection criterion is not satisfied. Consequently it is concluded that the detection of gravitons from spontaneous emission is impossible.



**ii) Gravitons from BH decay**
It is thought that black holes evaporate via [Hawking radiation](https://en.wikipedia.org/wiki/Hawking_radiation). Since the Hawking temperature is


$$ T \sim \frac{\hbar}{k_B G} \frac{1}{M}$$

and particle energy $$E = k_b T $$, there is an inverse relationship between graviton energy and BH mass. In order to produce gravitons with energies $> 10 eV$ requires BH with masses much less than a stellar mass and so such BHs must be [primordial](https://en.wikipedia.org/wiki/Primordial_black_hole). It can be shown that the number of gravitons detected over the lifetime of the BH source is of the order,

$$ N_{\gamma} \sim 10^{-5}$$

i.e. non-detectable

**iii) Gravitational Bremsstrahlung**

Electromagnetic Bremsstrahlung radiation occurs when charged particles are decelerated. In the electromagnetic case, the power radiated is,

$$ P \sim (m \ddot{x})^2 $$

However, [gravitational dipole radiation does not exist](http://tomkimpson.com/gr/GW_for_maths_types/). Instead, gravitational radiation is quadrupolar. In this case, if we assume that the detector is in a close orbit around a neutron star, the number of expected detections per year is,

$$ N_{\gamma} = 10^-2$$

i.e. 1 detection every 100 years


### Further complications
The above numbers were determined in ideal conditions with a Jupiter-mass detector of 100% efficiency. If we take a more 'realistic' (!) detector of mass $0.01 M_{Earth}$, the detection of gravtions is not possible in any of the above discussed cases.

Further issues arise relating to noise. A neutron star would also emit neutrinos. The cross section for the interaction of neutrinos with matter is $$ \sim 10^{-45} cm^2$$, which is 20 orders of magnitude greater than the gravito-electric cross section. Furthermore, it is estimated that $$ \sim 10^{13}$$ neutrinos would be emitted for every graviton. Consequently, we might expect $\sim 10^{33}$ neutrinos to be detected for every graviton. WE might therefore want to construct some shield to prevent neutrinos striking our detector. Such a shield should have a thickness greater than the mean free path for neutrinos. However, since the neutrino cross section is so small, for ordinary materials of standard density, this thickness is of the order of lightyears. A shield of such size would quickly collapse into a BH.


### Final Words
With the above analysis, the authors feel quite safe in predicting that no one will ever detect a graviton in our universe. However, it is possible that gravitons can be detected indirectly. For example, [Krauss, L. and Wilczek, F. (2013)](https://arxiv.org/abs/1309.5343) have suggested that gravitons may leave a detectable imprint on the polarization of the Cosmic Microwave Background.



Does this mean we can never detect gravitons?
