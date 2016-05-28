---
layout: post
title: Kerr Spherical Photon Orbits
modified: 2016-03-05
categories: [tool]
excerpt: Interactive tool for visualizing spherical/circular photon orbits in Kerr
tags: [general relativity, black holes, interactive, dynamics]
image:
  feature:
date: 2016-03-02
jsxgraph: true
published: true
---

{% include _toc.html %}

<!------------------------------------------------------------>

## Intro

In flat spacetime, light moves on straight lines.  In *curved*
spacetime, light moves on **geodesics**, the straightest-possible
lines as prescribed by the geometry.  Around a black hole, spacetime
is so curved that light can go into orbit!  Below you can play around
with those orbits and see what they look like.

You have control over two numbers: the spin $$0\le a \le 1$$, and the
radius of the orbit (the limits depend on the spin).

You can also ask the code to try to match some frequency ratio (it
might be impossible).  Try some [small-integer ratios](#resonances),
and drag the spin until a solution is found (the *r* slider will be
disabled).

The [details](#details) behind the math and physics appear below.

Drag/zoom around the 3d visualization to get a feeling for these
orbits.

<!------------------------------------------------------------>

<div id="box" class="jxgbox" style="width:500px; height:100px; margin-bottom:1em;">
</div>
<div id="three" style="width:500px; height:500px;"></div>

<table style="display:inline-block; margin-bottom:0em;"><tbody><tr>
<td>
<input type="button" id="playpause" value="Pause" onClick="togglePlayState();" style="width:4em;margin:0.5em">
</td>
<td> $$\tfrac{\Omega_\phi}{\Omega_\theta}=\tfrac{\Delta\phi}{2\pi}\approx$$ </td>
<td>
<input type="number" id="DeltaPhiOver2pi" style="width:5em" value="1.33" readonly step="any">
</td>
<td>
<input type="checkbox" id="MatchFreqQ" style="margin:0.5em" onchange="processMatchFreqUI()">Try to match this ratio?
</td>
<td>
<input type="number" id="DeltaPhiOver2piDesired" style="width:5em;margin:0.5em" onchange="processMatchFreqUI()" value="1.333" readonly step="any">
</td>
</tr></tbody></table>

<!------------------------------------------------------------>

# Details

Everything is in geometric units, $$G=1=c$$, and furthermore the total
mass has been scaled out, $$M=1$$.  The $$a$$ which appears here is
$$\tfrac{a}{M}$$, and the $$r$$ is $$\tfrac{r}{M}$$.  Everything is in
[Boyer-Lindquist coordinates](https://en.wikipedia.org/wiki/Boyer%E2%80%93Lindquist_coordinates).

## Controls and visualization

In the visualization you will see a red curve animating around, a gray
ellipsoid, and a blue arrow.  The gray ellipsoid represents the event
horizon (a constant-r surface in B-L coords), and the blue arrow
represents the direction of the spin vector.  The red curve is a chunk
of the photon's trajectory.  Some history of the trajectory is saved.

* Play/pause: no explanation needed.
* $$a$$ slider: this controls the spin of the black hole, from
  $$0 \le a \le 1$$.
* $$r$$ slider: this controls the radius of the orbit.  The minimum
  and maximum radius depend on the spin.  Disabled when "Try to match"
  is checked.
* History length slider: how much history of the photon's trajectory
  is plotted.  This is in terms of an arbitrary affine parameter.
* $$\tfrac{\Delta\phi}{2\pi}$$: this shows the ratio of frequencies
  between the azimuthal motion and the polar motion.
* "Try to match" checkbox and field: See below in
  [resonances](#resonances).  With the box checked, the *r* value
  will be automatically determined from the *a* value; so move the
  *a* slider around, because the *r* slider will be disabled.

**Update 2016-03-05**: Boyer-Lindquist coordinates are converted into
Cartesian coordinates by treating them as oblate spheroidal
coordinates, with the appropriate oblateness determined by the spin
(thanks to [Steve Drasco](http://www.calpoly.edu/~sdrasco/) for this
suggestion).

## Physics

Disclaimer: since this is visualizing the trajectories of photons,
this is not something anybody could "see" with their own eyes--because
the only photons you see are those which make it to your eyeballs.
Moreover while the photon trajectories themselves are good geometric
objects, I'm plotting their Boyer-Lindquist coordinates turned into
standard Cartesian coordinates. It's
[very coordinate-dependent](https://twitter.com/RelativistsSay/status/606523341885743104),
and remember that in general relativity, coordinates don't mean anything!

Now on to the physics.  Circular photon orbits are usually ignored,
because they are *unstable*: any tiny perturbation and the photon will
end up shooting out to infinity, or plunging into the black hole.
Still, they're useful to understand (see
e.g. [reference 5](#references)), and they're just fun to visualize.

Finding photon orbits firstly requires finding null
[geodesic](https://en.wikipedia.org/wiki/Geodesic) curves,
i.e. geodesics where the tangent vector is lightlike.  We also need it
to be null, $$u^a u_a = 0$$ where the tangent vector is
$$u^a \equiv dx^a/d\lambda$$ for some coordinate trajectory
$$x^a(\lambda)$$ with $$\lambda$$ an affine parameter.

Finding the system of ordinary differential equations is pretty
straightforward (see any of the [references](#references)).  For
example, from Teo's paper:
\\[
\Delta \Sigma \dot{t} = ((r^2+a^2)^2-\Delta a^2\sin^2\theta)E - 2Mr a L_z
\\]
\\[
\Sigma^2 \dot{r}^2 = E^2 r^4 + (a^2E^2-L_z^2-\mathcal{Q})r^2 + 2M[(aE-L_z)^2+\mathcal{Q}]r - a^2 \mathcal{Q}
\\]
\\[
\Sigma^2\dot{\theta}^2 = \mathcal{Q} - \left( \frac{L_z^2}{\sin^2\theta}-E^2a^2 \right)\cos^2\theta
\\]
\\[
\Delta\Sigma\dot{\phi} = 2MraE + (\Sigma-2Mr)\frac{L_z}{\sin^2\theta}
\\]
where overdots are derivatives with respect to an affine parameter,
and with the usual Kerr quantities $$\Delta = r^2-2Mr+a^2$$,
$$\Sigma = r^2+a^2\cos^2\theta$$, and where $$ \mathcal{Q}$$ is the
so-called Carter constant.

### Parameters

After you study the radial equation, you learn that the only
bound photon trajectories---that is, orbits!---are those
for which $$r=\mathrm{const}$$ in Boyer-Lindquist coordinates.  This
is why these photon orbits are sometimes called "circular" or
"spherical."

Now to make life easier: all photons, regardless of energy, follow the
same trajectories.  This means we can just set $$E=1$$ in the above
equations. This is exactly the same as doing an affine tranformation
on the trajectory.  This allows us to parameterize orbits in terms of
two parameters instead of three:
instead of $$(E,L_z, \mathcal{Q})$$, we use just $$(\Phi,Q)$$ where
$$\Phi \equiv L_z/E$$ and $$Q \equiv \mathcal{Q}/E^2$$.

Not all choices of parameters give solutions.  I recommend following
along in Teo's paper to understand which parts of parameter space are
allowed.

In the end, you see that at each $$a$$, there is a one-parameter
family of trajectories given by the radius $$r$$, which must be
between the two limits $$r_1(a) \le r \le r_2(a)$$.  The innermost
photon orbit is a prograde circle lying in the equatorial plane, and
the outermost orbit is a retrograde circle lying in the equatorial
plane.  You saw those functions previously on my
[Kerr calculator]({{ site.url }}{% post_url 2015-10-08-kerr-calculator-v2 %}).
You can switch between $$(r,a)$$ and $$(\Phi,Q)$$ (in the appropriate
part of parameter space) via
\\[
\Phi = -\frac{r^3-3Mr^2+a^2 r+a^2 M}{a(r-M)}
\\]
\\[
Q = - \frac{r^3(r^3-6Mr^2+9M^2r-4a^2M)}{a^2(r-M)^2}
\\]

For any radius between the minimum and maximum, the photon will
oscillate in latitude between a minimum and maximum, which you can
read off of the angular potential.  This minimum/maximum is given by:
\\[
u_0^2 = \cos^2\theta_\mathrm{min\ or\ max}
=
\frac{1}{2a^2} \left\[
(a^2-Q+\Phi^2) + \sqrt{(a^2-Q+\Phi^2)^2+4a^2Q}
\right\]
\\]
This function is plotted below:
<div id="u0plot" class="jxgbox" style="width:500px; height:500px; margin-bottom:1em;"></div>
<!-- Javascript for this box is at the end -->
The photon will hit every latitude value between the two blue curves
at fixed $$(a,r)$$, making something like a truncated sphere
(justifying the name "spherical" photon orbits)---unless it's
[resonant](#resonances)!

### Reparameterizing latitudinal motion

By construction, the radius is constant.  Keeping track of the
Boyer-Lindquist coordinate time doesn't really add information.
Therefore the only thing I integrate here is the $$(\theta,\phi)$$
motion.

The differential equation for $$\phi$$ is straightforward.  But look
back at the $$\theta$$ equation: it is quadratic in $$\dot{\theta}$$,
so there are two roots: one positive, and one negative.  These
correspond to the photon ascending/descending in latitude, so if you
were to use this equation you'd have to switch which root you're using
at the turning points ($$\cos\theta = \pm u_0$$).

That's pretty annoying, plus you might worry about the
[Lipschitz condition](https://en.wikipedia.org/wiki/Lipschitz_continuity).
All of this can be avoided by reparameterizing the latitudinal motion
with a periodic function of a monotonically increasing/decreasing
phase angle.  I learned this trick from Scott Hughes (see
e.g. [reference 4](#references)), though I'm not sure where it
originally came from.

First, instead of using $$\theta$$, we switch variables to $$u =
\cos\theta$$.  The differential equation for $$u$$ is
\\[
\Sigma^2 \dot{u}^2 = a^2 (u_0^2-u^2)(u^2-u_1^2)
\\]
where $$u_1^2$$ is the other root of the potential on the right hand
side:
\\[
u_1^2 =
\frac{1}{2a^2} \left\[
(a^2-Q+\Phi^2) - \sqrt{(a^2-Q+\Phi^2)^2+4a^2Q}
\right\]
\\]
Note that my $$u_1$$ is not the same as Teo's $$u_1$$.  Also keep
track of the fact that $$u_1^2 \le 0$$, but I'll stick with the name.

Now we write $$u = u_0 \sin\chi(\lambda)$$ with a new monotonic phase
function $$\chi(\lambda)$$, and do a tiny bit of algebra to get
\\[
\dot{\chi} = \pm \frac{a}{\Sigma} \sqrt{u^2 - u_1^2}
= \pm \frac{a}{r^2 + a^2 u_0^2 \sin^2 \chi} \sqrt{u_0^2 \sin^2 \chi - u_1^2}
\\]
Because of the cancellation of the root at the turning point, there is
clearly no Lipschitz problem.  And, since the phase angle is
monotonic, we just pick the positive root once and for all.

### Resonances

For "most" choices of $$(a,r)$$, the frequency $$\Omega_\phi$$ of the
azimuthal motion and the frequency $$\Omega_\theta$$ of the
longitudinal motion are incommensurate.  That is, the ratio
$$\Omega_\phi/\Omega_\theta$$ is an irrational number
"[almost everywhere](https://en.wikipedia.org/wiki/Almost_everywhere)"
(in the measure-theoretic sense).  That means that most of these
photon orbits will completely fill their respectively allowed
truncated spheres.

However, when $$\Omega_\phi/\Omega_\theta$$ is the ratio of small
integers, the orbit will close/recur, and the photon on that orbit
will visit only a small part of the truncated sphere.

Let's calculate $$\Omega_\phi/\Omega_\theta$$, which is actually the
same as the extra azimuthal phase (over $$2\pi$$) for a complete
longitudinal cycle.  That is, we want to be able to compute
\\[
\Delta\phi = \oint_{\chi-\mathrm{cycle}} d\phi
= \int_0^{2\pi} \frac{d\phi}{d\chi} d\chi
= \int_0^{2\pi} \frac{d\phi/d\lambda}{d\chi/d\lambda} d\chi
\\]
After plugging in the above equations of motion and doing a bit of
algebra, this quantity can be written in terms of complete elliptic
integrals
([see what conventions I use for complete elliptic integrals]({{ site.url }}{% post_url 2016-02-24-elliptic-integrals-in-javascript %})):
\\[
\Delta\phi = \frac{4}{\sqrt{-u_1^2}} \left[
\frac{2r-a\Phi}{\Delta} K\left(\frac{u_0^2}{u_1^2}\right)
+
\frac{\Phi}{a} \Pi\left(u_0^2, \frac{u_0^2}{u_1^2}\right)
\right] .
\\]
This expression is somewhat simpler than Teo's.

Teo's paper goes into a bit more depth on this function, but for now
let's just examine a plot of $$\Delta\phi/2\pi$$:
<div id="Deltaphiplot" class="jxgbox" style="width:500px; height:500px; margin-bottom:1em;"></div>
<!-- Javascript for this box is at the end -->
Yes, that jump is real.  That's where the orbits switch from being
prograde (on the left, positive $$\Delta\phi$$) to being retrograde (on
the right).  It's the same point where $$\Phi=0$$, which is where
$$u_0^2=1$$, which is a polar orbit.  There is a jump of exactly 2
between the left and right branches of $$\Delta\phi/2\pi$$, and the
exactly polar orbit is half way in between the two branches.

A perhaps more informative way to plot this is as contours of
$$\Delta\phi/2\pi$$ in the $$r-a$$ plane, which I've only done
statically in Mathematica (maybe at some point in the future I'll do
it in javascript).  Here's what this function looks like:

<figure>
<a href="{{ site.url }}/images/deltaphi.png"><img src="{{ site.url }}/images/deltaphi.png" /></a>
</figure>

This should give you an idea of some of the easier-to-find resonances
in parameter space.

If you want to see what one of these resonances looks like, check the
"Try to match" checkbox and type in the desired ratio (in decimal) in
the field at right.  Then drag the slider for *a* into the appropriate
range, and the simulation should solve for the appropriate value of *r*.
The *r* slider will be disabled while the checkbox is checked.

If you move *a* outside the range where a certain resonance exists,
the simulation will probably rail to $$r_1$$ or $$r_2$$.

If you choose a target value for $$\Delta\phi/2\pi$$ that only exists
on the $$\Phi=0$$ line (the discontinuity), you're gonna have a bad
time---the simulation is pretty wonky along the $$\Phi=0$$ line, for
[technical reasons](#limitations).

<!--
Here are a few quick links to jump into some of the lower-order
resonances.  Click on the pair $$(\Delta\phi/2\pi, a)$$ to jump
immediately there.

|-----------|---
|Resonance  | $$(\Delta\phi/2\pi, a)$$
|----------:|--:
|  -4:5     | <a onclick="setMatchFreqAnda(-0.8, 0.6)">(-0.800, 0.6)</a>
|  -3:4     | <a onclick="setMatchFreqAnda(-0.75, 0.8)">(-0.750, 0.8)</a>
|  -2:3     | <a onclick="setMatchFreqAnda(-0.66667, 0.9)">(-0.667, 0.9)</a>
|  -3:5     | <a onclick="setMatchFreqAnda(-0.6, 0.95)">(-0.600, 0.95)</a>
|   6:5     | <a onclick="setMatchFreqAnda(1.2, 0.4)">(1.200, 0.4)</a>
|   5:4     | <a onclick="setMatchFreqAnda(1.25, 0.5)">(1.250, 0.5)</a>
|   4:3     | <a onclick="setMatchFreqAnda(1.3333, 0.6)">(1.333, 0.6)</a>
|   7:5     | <a onclick="setMatchFreqAnda(1.4, 0.7)">(1.400, 0.7)</a>
|   3:2     | <a onclick="setMatchFreqAnda(1.5, 0.8)">(1.500, 0.8)</a>
|   5:3     | <a onclick="setMatchFreqAnda(1.66666, 0.9)">(1.667, 0.9)</a>
|   2:1     | <a onclick="setMatchFreqAnda(2.0, 0.9)">(2.000, 0.9)</a>
|   3:1     | <a onclick="setMatchFreqAnda(3.0, 0.95)">(3.000, 0.95)</a>
|-----------|--
{: rules="groups" style="width:auto"}
-->

## Code

This page was made using the
[JSXGraph](http://jsxgraph.uni-bayreuth.de/wp/) toolkit,
[three.js](http://threejs.org/),
[threestrap](https://github.com/unconed/threestrap), and javascript
that I wrote by hand.  The latter includes code for
[complete elliptic integrals in javascript]({{ site.url }}{% post_url 2016-02-24-elliptic-integrals-in-javascript %})
(which is only used for the frequency ratio calculations).

The numerical integrator from JSXGraph that I use is a fixed step-size
[RK4](https://en.wikipedia.org/wiki/Runge%E2%80%93Kutta_methods)
integrator.  It is sadly not adaptive!  This is a problem for orbits
close to the spin axis.

## Limitations

* The major limitation is that this is in javascript, which is not
  ideal for numerical work.  There are very few numerical libraries.
* JSXGraph only has fixed-step-size integrators, no adaptive ones.  I
  picked what seemed like a reasonable step size in most of parameter space.
* Orbits that pass very close to the spin axis experience rapid
  variation in $$\phi$$ in a small amount of affine parameter.  These
  numerics will be especially bad.
* For *exactly* polar orbits, the situation is even worse.  In
  principle, $$\phi$$ goes through a jump discontinuity of $$\pi$$
  when going across the pole.  This isn't possible with the
  formulation I've got here.  Maybe there's a better way.
* The iterative scheme for elliptic integrals may be bad at
  converging for certain inputs.
* The code is a bit of spaghetti.  I have not made much effort to
  untangle it.  Maybe in the future.
* Memory leaks.  There are probably memory leaks, even though
  javascript is a garbage-collected language... it needs its hand held
  to be convinced that I really don't need this earlier data.

# References

1. Any of a number of standard textbooks on GR, e.g. [MTW](https://books.google.com/books/about/Gravitation.html?id=w4Gigq3tY1kC),
   [Wald](http://press.uchicago.edu/ucp/books/book/chicago/G/bo5952261.html),
   or [Carroll](http://preposterousuniverse.com/spacetimeandgeometry/)
2. [Chandra's book](https://global.oup.com/academic/product/the-mathematical-theory-of-black-holes-9780198503705)
3. E. Teo, Spherical photon orbits around a Kerr black hole,
   [General Relativity and Gravitation, 2003, Volume 35, Issue 11, pp 1909-1926](http://dx.doi.org/10.1023/A:1026286607562).
4. Some papers by Scott Hughes, where I learned the nicer
   parameterization for the latitudinal motion; for example,
   [this paper](http://arxiv.org/abs/gr-qc/9910091v3).
5. Some of these calculations also appeared in Yang et al.,
   Quasinormal-mode spectrum of Kerr black holes and its geometric
   interpretation,
   [Phys. Rev. D 86, 104006 (2012)](http://dx.doi.org/10.1103/PhysRevD.86.104006)
   \[[arXiv:1207.4253](http://arxiv.org/abs/1207.4253)\]

# Future

Timelike orbits? We shall see!

<!------------------------------------------------------------>
<!-- CODE -->

<script type="text/javascript" src="{{ site.url }}/assets/js/vendor/three.min.js"></script>
<script type="text/javascript" src="{{ site.url }}/assets/js/vendor/threestrap.min.js"></script>
<script type="text/javascript" src="{{ site.url }}/assets/js/vendor/OrbitControls.js"></script>

<script type="text/javascript" src="{{ site.url }}/assets/js/elliptic.js"></script>

<script type="text/javascript">

////////////////////////////////////////////////////////////
// Utility

// Because mods should always be in the range 0 <= x < m
function fmod(x, m)
{
  return ((x<0)? Math.abs(m) : 0) + (x % m);
};

////////////////////////////////////////////////////////////
// Some Kerr calculations specific to circular photon orbits
// All calculations are in units where M=1

// \Phi is the Lz component of angular momentum per unit energy
function Phi(a, r)
{
  return -((r*r*r - 3.*r*r + a*a*r + a*a)/(a*(r - 1.)));
};

// Q is the Carter constant per units energy
function Q(a, r)
{
  return -((r*r*r * (r*r*r - 6.*r*r + 9.*r - 4.*a*a))/(a*a*(r - 1.)*(r - 1.)));
};

// r1 is the innermost possible circular photon orbit
function r1(a)
{
  return 2.*(1. + Math.cos(2./3.*Math.acos(-a)));
};

// r2 is the outermost possible circular photon orbit
function r2(a)
{
  return 2.*(1. + Math.cos(2./3.*Math.acos(a)));
};

// r3 is the radius of the Phi=0 circular photon orbit
// I might not need this function for anything, but might as well type
// it up
function r3(a)
{
  var sqrtOneMinusThirdASq = Math.sqrt(1. - 1./3.*a*a);
  return 1. + 2.*sqrtOneMinusThirdASq *
         Math.cos(1./3. * Math.acos((1. - a*a)/Math.pow(sqrtOneMinusThirdASq,3.)));
};

// u is used in place of \cos\theta, u = \cos\theta
// +u0 and -u0 are the maximum and minimum "latitudes" of an orbit at
// this given a, r.
// The square of u0 appears more often than the number itself.
function u0sq(a, r)
{
  var phi = Phi(a,r), q = Q(a,r);
  var b = a*a - q - phi*phi;

  return 0.5*(b + Math.sqrt(b*b + 4.*a*a*q))/(a*a);
};

function u0(a, r)
{
  return Math.sqrt(u0sq(a,r));
};

// Just for completeness, the other root of u equation.
// This enters into calculations of frequencies and their ratios.
// This is u_1^2 in my language, which is NOT equal to Teo's Eq. (19).
// Reminder that u_1^2 < 0 in the part of parameter space where
// circular photon orbits exist
function u1sq(a, r)
{
  var phi = Phi(a,r), q = Q(a,r);
  var b = a*a - q - phi*phi;

  return 0.5*(b - Math.sqrt(b*b + 4.*a*a*q))/(a*a);
};

// The change in azimuthal angle over a complete polar oscillation
function Deltaphi(a, r)
{
  var Delta = r*r - 2.*r + a*a;
  var phi = Phi(a, r);
  var U0sq = u0sq(a, r), U1sq = u1sq(a, r);
  var absu1 = Math.sqrt( - U1sq );

  return 4./absu1 * ( (2.*r - a*phi)/Delta * Math.EllipticK( U0sq / U1sq )
                      + phi/a * Math.EllipticPi( U0sq, U0sq/U1sq ) );
};

// This is the function Deltaphi evaluated at r=r3(a), to avoid numerical errors
function Deltaphiatr3(a)
{
  var r = r3(a);
  var Delta = r*r - 2.*r + a*a;
  var U0sq = u0sq(a, r), U1sq = u1sq(a, r);
  var absu1 = Math.sqrt( - U1sq );

  return 8./absu1 * r/Delta * Math.EllipticK( U0sq / U1sq );
};

function findRGivenADeltaPhiOver2pi(a, DeltaPhiOver2piDesired)
{
  var minR = r1(a), maxR = r2(a);
  var f = function(r){ return 0.5*Deltaphi(a, r)/Math.PI - DeltaPhiOver2piDesired; };

  return JXG.Math.Numerics.fzero( f, [minR, maxR] );

}

function updateDeltaPhiField(a, r)
{
  var DeltaPhiOver2pi = 0.5*Deltaphi(a,r)/Math.PI;

  document.getElementById('DeltaPhiOver2pi').value = DeltaPhiOver2pi.toPrecision(4);
}

function processMatchFreqUI()
{
  var checked = document.getElementById('MatchFreqQ').checked;

  document.getElementById('DeltaPhiOver2piDesired').readOnly = !checked;
  r.isDraggable = !checked;

  if (checked) {
    tryMatchFreq();
    updateDeltaPhiField(a.Value(), r.Value());
    initialSolution( a.Value(), r.Value(), historyLength, historyPoints );
    updateTrajGeom( a.Value(), r.Value(), currentSolution );
  }
}

function tryMatchFreq()
{
  var DeltaPhiOver2piDesired = document.getElementById('DeltaPhiOver2piDesired').value;
  var rGoal = findRGivenADeltaPhiOver2pi(a.Value(), DeltaPhiOver2piDesired);

  r.setValue( rGoal );
}

function setMatchFreqAnda(DeltaPhiOver2piDesired, newa)
{
  a.setValue(newa);
  document.getElementById('DeltaPhiOver2piDesired').readOnly = false;
  document.getElementById('DeltaPhiOver2piDesired').value = DeltaPhiOver2piDesired.toPrecision(4);
  document.getElementById('MatchFreqQ').checked = true;

  processMatchFreqUI();
  document.getElementById('MatchFreqQ').scrollIntoView();
}

////////////////////////////////////////////////////////////
// ODE system

// This comes from my reparameterization of the latitude in terms of
// the monotonic phase function chi. It's basically Scott's
// approach. Make sure to write up the reparameterization.

// Here is a javascript function to emit a function that computes the
// RHS of the ODE, given a certain (a,r).
function makechidotphidotRHS(a, r)
{
  var ell = Phi(a,r), U0sq = u0sq(a,r), U1sq = u1sq(a,r), Delta = r*r - 2.*r + a*a;

  return function(zeta, chiphi)
  {
    var chi = chiphi[0], phi = chiphi[1];
    var sinchi = Math.sin(chi);
    var sinchisq = sinchi*sinchi;
    var Sigma = r*r + a*a*U0sq*sinchisq;

    var chidot = a/Sigma * Math.sqrt( U0sq*sinchisq - U1sq );
    var phidot = (2.*r*a + (Sigma - 2.*r)*ell/(1. - U0sq*sinchisq)) *
                 1. / (Delta*Sigma);

    return [chidot, phidot];
  };
};

var currentSolution = [];

function updateSolution(a, r, zetaIntervalLength, numZetaPoints)
{
  var data = JXG.Math.Numerics.rungeKutta(
    'rk4',                                       // Butcher table
    currentSolution[currentSolution.length - 1], // Initial conditions
    [0, zetaIntervalLength],                     // zeta interval
    numZetaPoints,                               // how many points
    makechidotphidotRHS(a,r)                     // the RHS of the system
  );

  // Take mods
  for(var i=0; i<data.length; i++) {
    data[i][0] = fmod( data[i][0] , 2. * Math.PI);
    data[i][1] = fmod( data[i][1] , 2. * Math.PI);
  };

  // make the replacement atomic
  var newSolution = currentSolution.concat(data);
  newSolution.splice(0, data.length);

  currentSolution = newSolution;
};

function initialSolution(a, r, historyLength, historyPoints)
{
  var data = JXG.Math.Numerics.rungeKutta(
    'rk4',                                       // Butcher table
    [0., 0.],                                    // Initial conditions
    [0, historyLength],                          // zeta interval
    historyPoints,                               // how many points
    makechidotphidotRHS(a,r)                     // the RHS of the system
  );

  // Take mods
  for(var i=0; i<data.length; i++) {
    data[i][0] = fmod( data[i][0] , 2. * Math.PI);
    data[i][1] = fmod( data[i][1] , 2. * Math.PI);
  };

  currentSolution = data;

};

////////////////////////////////////////////////////////////
// Some global state

var dzeta = 0.05;
var historyLength = 20.;
var historyPoints = Math.ceil(historyLength / dzeta);
var zetaIntervalLength = 0.5;
var numZetaPoints = Math.ceil(zetaIntervalLength / dzeta);

var tickTime = 35; // in milliseconds
var timeoutID;
var playingState = false;

////////////////////////////////////////////////////////////
// Make some plots

var brd = JXG.JSXGraph.initBoard('box',
                                 {boundingbox:[0.,1.,1.,0.],
                                  axis:false,
                                  pan: {enabled: false},
                                  showNavigation: false,
                                  showCopyright:  false});

brd.suspendUpdate();
var a = brd.create('slider',[[0.05,.75],[0.7,.75],[0.001,0.6,0.999]],
                   {name:'a', precision:3});
var r = brd.create('slider',[[0.05,.5],[0.7,.5],
                             [r1(a.Value()),
                              0.5*(r1(a.Value())+r2(a.Value())),
                              r2(a.Value())]],
                          {name:'r', precision:3 //,showInfobox: true
                           });
var histSlider = brd.create('slider',
                            [[0.05,.25],[0.7,.25],[15,historyLength,300]],
                            {name:'History length'});

// Make r be updated by changing a
// Update Deltaphi field
a.on('drag',
     function()
     {
       r.setMin(r1(a.Value()));
       r.setMax(r2(a.Value()));
       if (document.getElementById('MatchFreqQ').checked) tryMatchFreq();
       updateDeltaPhiField(a.Value(), r.Value());
       initialSolution( a.Value(), r.Value(), historyLength, historyPoints );
       updateEH( a.Value() );
       updateTrajGeom( a.Value(), r.Value(), currentSolution );
     });

r.on('drag',
     function()
     {
       updateDeltaPhiField(a.Value(), r.Value());
       initialSolution( a.Value(), r.Value(), historyLength, historyPoints );
       updateTrajGeom( a.Value(), r.Value(), currentSolution );
     });

histSlider.on('drag',
              function(){
                historyLength = Math.ceil(histSlider.Value());
                historyPoints = Math.ceil(historyLength / dzeta);
                initialSolution( a.Value(), r.Value(), historyLength,
                                 historyPoints );
                updateTrajGeom( a.Value(), r.Value(), currentSolution );
              });

// Create the hovertext for the r slider
// r.highlight = function(){
//   brd.highlightCustomInfobox("Disabled when trying to match frequency ratio");
//}

// var curve = brd.create('curve', [[0],[0]],
//   {strokeColor: "#cc0000"//,
// //   name:function(){ return "Δφ(" + a.Value().toFixed(2) + ", r)/2π"; },
// //   withLabel:true,
// //   label:{}
//   });
// curve.updateDataArray = function() {
//   var U0 = u0(a.Value(), r.Value());
//   this.dataX = [];
//   this.dataY = [];
//   for(var i=0; i<currentSolution.length; i++) {
//     this.dataX[i] = currentSolution[i][1];
//     this.dataY[i] = U0 * Math.sin(currentSolution[i][0]);
//   }
// };

updateDeltaPhiField(a.Value(), r.Value());
initialSolution( a.Value(), r.Value(), historyLength, historyPoints );

brd.unsuspendUpdate();

// Running the animation is started below

////////////////////////////////////////////////////////////
// Try some 3D stuff

// Bootstrap core + controls plugin into element
var three = THREE.Bootstrap({
  element: document.querySelector('#three'),
  plugins: ['core', 'controls', 'cursor'],
  controls: {
    klass: THREE.OrbitControls
  },
});

three.scene.add( new THREE.AmbientLight( 0xf0f0f0 ) );

var helper = new THREE.GridHelper( 60, 5 );
helper.position.y = - 6;
helper.material.opacity = 0.25;
helper.material.transparent = true;
three.scene.add( helper );

three.renderer.setClearColor( 0xf0f0f0 );

// Alter controls
three.controls.rotateSpeed = 0.5;

// Place camera
three.camera.position.set(6, 5, 4);

////////////////////////////////////////////////////////////
// Taking a solution and turning it into an array of Vector3
function solutionTo3D(a, r, solution)
{
  var xyR = Math.sqrt( r*r + a*a );
  var U0 = u0(a,r);
  var threeVectors = new Array(solution.length);

  for(var i=0; i<solution.length; i++)
  {
    var chi = solution[i][0], phi = solution[i][1];
    var u = U0 * Math.sin(chi);
    var cou = Math.sqrt(1. - u*u);

    // REMINDER: computer graphics people have a stupid convention for
    // their coordinate system. For them, z is out of the
    // screen. I want the default controls to work well, so I rotate
    // my threeVectors to work with their coordinate system.
    threeVectors[i] = new THREE.Vector3(
      xyR * cou * Math.sin(phi),
      r * u,
      xyR * cou * Math.cos(phi));
  };

  return threeVectors;
};

var traj;

function initTraj()
{
  traj = new Object;
  traj.material = new THREE.LineBasicMaterial( { color : 0xff0000,
                                                 linewidth : 2 } );

  var trajGeom = new THREE.Geometry();

  // Create the new Object3d to add to the scene
  traj.object = new THREE.Line( trajGeom, traj.material );

  three.scene.add( traj.object );
}

initTraj();

function updateTrajGeom( a, r, solution )
{
  var threeVectors = solutionTo3D( a, r, currentSolution );

  var newGeom = new THREE.Geometry();
  newGeom.vertices = threeVectors;

  traj.object.geometry.dispose();
  traj.object.geometry = newGeom;

};

var eh;

function initEH( a )
{
  eh = new Object;
  eh.material = new THREE.MeshBasicMaterial( {color: 0x000000} );
  eh.material.opacity = 0.5;
  eh.material.transparent = true;
  eh.haveScaled = false;

  var rplus = 1. + Math.sqrt(1. - a*a) ;
  var ehGeom = new THREE.SphereGeometry( rplus , 32, 32 );
  var newEhMesh = new THREE.Mesh( ehGeom, eh.material );

  // Remember the ridiculous coord system
  var dir = new THREE.Vector3( 0., 1., 0. );
  var origin = new THREE.Vector3( 0., rplus, 0. );
  var length = 0.75;
  var hexColor = 0x0000ff;
  var newArrowHelper = new THREE.ArrowHelper( dir, origin, length,
                                              hexColor );

  newArrowHelper.line.material.linewidth = 3;
  newArrowHelper.cone.geometry.scale( 5, 1, 5 ); // why this needs to happen only once? No idea...

  three.scene.add( newEhMesh );
  three.scene.add( newArrowHelper );

  eh.mesh = newEhMesh;
  eh.arrowhelper = newArrowHelper;

};

function updateEH( a )
{
  var rplus = 1. + Math.sqrt(1. - a*a) ;
  var xyR = Math.sqrt( rplus*rplus + a*a );
  var ehGeom = new THREE.SphereGeometry( 1 , 32, 32 );

  ehGeom.scale( xyR, rplus, xyR );

  eh.mesh.geometry.dispose();
  eh.mesh.geometry = ehGeom;

  // Remember the ridiculous coord system
  var dir = new THREE.Vector3( 0., 1., 0. );
  var origin = new THREE.Vector3( 0., rplus, 0. );
  var length = 0.75;
  var hexColor = 0x0000ff;
  var newArrowHelper = new THREE.ArrowHelper( dir, origin, length,
                                              hexColor );

  newArrowHelper.line.material.linewidth = 3;

  three.scene.remove( eh.arrowhelper );
  eh.arrowhelper.line.geometry.dispose();
  eh.arrowhelper.line.material.dispose();
  eh.arrowhelper.cone.geometry.dispose();
  eh.arrowhelper.cone.material.dispose();
  delete(eh.arrowhelper);

  three.scene.add( newArrowHelper );

  eh.arrowhelper = newArrowHelper;
};

initEH( a.Value() );

////////////////////////////////////////////////////////////
// Running the ODE integrator on a timer

function runTick()
{
  brd.suspendUpdate();
  updateSolution( a.Value(), r.Value(), zetaIntervalLength, numZetaPoints );
  updateTrajGeom( a.Value(), r.Value(), currentSolution );
  brd.unsuspendUpdate();

  if (playingState)
    timeoutID = window.setTimeout(runTick, tickTime);
};

function togglePlayState()
{
  if (playingState) {
    window.clearTimeout(timeoutID)
    playingState = false;
    document.getElementById('playpause').value = "Play";
  } else {
    timeoutID = setTimeout(runTick, tickTime);
    playingState = true;
    document.getElementById('playpause').value = "Pause";
  };
};

// Hit play!
togglePlayState();

</script>
<!-- Code for auxiliary plots -->
<script type="text/javascript">
var u0brd = JXG.JSXGraph.initBoard('u0plot',
                                   {boundingbox:[0.0,1.1,4.5,-1.1],
                                    axis:false,
                                    pan: {enabled: false},
                                    showNavigation: false,
                                    showCopyright:  false});


u0brd.create('axis', [[0.0, 0.0], [4.0, 0.0]], {name: 'r', withLabel:true, label:{position:'rt', offset:[-20, 10]}});
u0brd.create('axis', [[0.0, -1.0], [0.0, 1.0]], {name: 'u_0', withLabel:true, label:{position:'rt', offset:[10, 0]}});

u0brd.suspendUpdate();
var aSlideru0 = u0brd.create('slider',[[0.25,.8],[1.5,.8],[0.001,0.6,0.999]],
                             {name:'a', precision:3});

u0brd.create('curve',
[
function(q){var a = aSlideru0.Value(); return r1(a)+q*(r2(a)-r1(a));},
function(q){var a = aSlideru0.Value(); return u0(a, r1(a)+q*(r2(a)-r1(a)));},
0.,
1.
]);
u0brd.create('curve',
[
function(q){var a = aSlideru0.Value(); return r1(a)+q*(r2(a)-r1(a));},
function(q){var a = aSlideru0.Value(); return -u0(a, r1(a)+q*(r2(a)-r1(a)));},
0.,
1.
]);
u0brd.unsuspendUpdate();

var Deltaphibrd = JXG.JSXGraph.initBoard('Deltaphiplot',
                                         {boundingbox:[0.0,3,4.5,-1.1],
                                          axis:false,
                                          pan: {enabled: false},
                                          showNavigation: false,
                                          showCopyright:  false});


Deltaphibrd.create('axis', [[0.0, 0.0], [3.0, 0.0]], {name: 'r', withLabel:true, label:{position:'rt', offset:[-20, 10]}});
Deltaphibrd.create('axis', [[0.0, -1.1], [0.0, 4.0]], {name: 'ΔΦ/2π', withLabel:true, label:{position:'rt', offset:[10, 0]}});

Deltaphibrd.suspendUpdate();
var aSliderDeltaphi = Deltaphibrd.create('slider',[[0.25,.8],[1.5,.8],[0.001,0.6,0.999]],
                                         {name:'a', precision:3});

Deltaphibrd.create('curve',
[
function(q){var a = aSliderDeltaphi.Value(); return r1(a)+q*(r2(a)-r1(a));},
function(q){var a = aSliderDeltaphi.Value(); return 0.5*Deltaphi(a, r1(a)+q*(r2(a)-r1(a)))/Math.PI;},
0.,
1.
]);
Deltaphibrd.create('point',
[
function(q){var a = aSliderDeltaphi.Value(); return r3(a);},
function(q){var a = aSliderDeltaphi.Value(); return 0.5*Deltaphiatr3(a)/Math.PI;},
],
{name:'polar orbit', size:1});
Deltaphibrd.unsuspendUpdate();

</script>
