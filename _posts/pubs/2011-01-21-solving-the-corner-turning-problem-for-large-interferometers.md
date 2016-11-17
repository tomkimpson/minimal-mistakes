---
layout: pub-link
title: "Solving the Corner-turning Problem for Large Interferometers"
modified:
categories: pubs
excerpt: "Turning an O(n^2) problem into an O(n log n) problem in radio interferometry, similar in spirit to how the fast Fourier transform operates."
tags: []
pub:
  authors: "Lutomirski, Tegmark, Sanchez, Stein, Urry, and Zaldarriaga"
  doi: 10.1111/j.1365-2966.2010.17587.x
  arXiv: "0910.1351"
  jref: "MNRAS 410: 2075–2080 (2011)"
date: 2011-01-21T00:00:00-05:00
---

> The so-called corner-turning problem is a major bottleneck for radio
> telescopes with large numbers of antennas. The problem is
> essentially that of rapidly transposing a matrix that is too large
> to store on one single device; in radio interferometry, it occurs
> because data from each antenna need to be routed to an array of
> processors each of which will handle a limited portion of the data
> (say, a frequency range) but requires input from each antenna. We
> present a low-cost solution allowing the correlator to transpose its
> data in real time, without contending for bandwidth, via a butterfly
> network requiring neither additional RAM memory nor expensive
> general-purpose switching hardware. We discuss possible
> implementations of this using FPGA, CMOS, analog logic and optical
> technology, and conclude that the corner-turner cost can be small
> even for upcoming massive radio arrays.
