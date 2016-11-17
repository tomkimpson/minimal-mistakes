---
title: Kerr ISCO calculator
modified:
categories: [tool]
excerpt: Interactive tool to compute ISCOs in Kerr
tags: [general relativity, black holes, interactive]
date: 2015-10-07T21:02:47-07:00
jsxgraph: true
---

With no delay, here is the interactive ISCO calculator. Grab either of
the red circles on one of the two curves and drag.  Horizontal axis is
$$a/M$$, vertical axis is $$r_{ISCO}/M$$.  Scroll down for an
[explanation](#explanation).

**Update 2015-10-08**: After some suggestions I have created the
[Kerr Calculator v2]({{ site.url }}{% post_url 2015-10-08-kerr-calculator-v2 %}).

<div id="box" class="jxgbox" style="width:500px; height:500px;"></div>
<div id="out"></div>
<script type="text/javascript">
var board = JXG.JSXGraph.initBoard('box',
{boundingbox: [-0.01, 9.05, 1.01, .7],
 axis: false,
 grid: true,
 pan: {enabled: false},
 showNavigation: false,
 showCopyright:  false});

var sqrt = Math.sqrt;
var pow  = Math.pow;

var Z1 = function(a) {
  return 1. + pow(1. - a*a,1./3.)*(pow(1. + a,1./3.) + pow(1. - a,1./3.));
};

var Z2 = function(a) {
  return sqrt(3.*a*a + Z1(a)*Z1(a));
};

var rPro = function(a) {
  return 3. + Z2(a) - sqrt((3. - Z1(a))*(3. + Z1(a) + 2.*Z2(a)));
};

var rRet = function(a) {
  return 3. + Z2(a) + sqrt((3. - Z1(a))*(3. + Z1(a) + 2.*Z2(a)));
};

var lX = board.create('axis', [[0.0, 1.0], [1.0, 1.0]], {label: 'a/M'});
var lY = board.create('axis', [[0.0, 1.0], [0.0, 9.0]], {label: 'r/M'});

var gPro = board.create('functiongraph', [rPro], {strokeColor:'#ff0000',strokeWidth:2});
var gRet = board.create('functiongraph', [rRet], {strokeColor:'#0000ff',strokeWidth:2});

board.suspendUpdate();

var qPro = board.create('glider', [0.3, rPro(0.3), gPro], {withLabel:false});
var qRet = board.create('glider', [0.3, rRet(0.3), gRet], {withLabel:false});

var yPro = board.create('point', [function(){return qPro.X();},function(){return rPro(qPro.X());}],{size:2,face:'[]',name:'rPro/M'}); 
var yRet = board.create('point', [function(){return qRet.X();},function(){return rRet(qRet.X());}],
  {size:2,face:'[]',name:'rRet/M', label: {anchorX: 'right'}});

var lowPro = board.create('point', [function(){return qPro.X();},function(){return 1.0;}],{size:2,face:'[]',name:''});
var lowRet = board.create('point', [function(){return qRet.X();},function(){return 1.0;}],{size:2,face:'[]',name:''});

var vPro = board.create('segment', [lowPro,yPro],{strokeColor:'gray',dash:2,strokeWidth:1});
var vRet = board.create('segment', [lowRet,yRet],{strokeColor:'gray',dash:2,strokeWidth:1});

var hPro = board.create('curve', [function(t){return t},function(t){return yPro.Y();}], {strokeColor:'gray',dash:2,strokeWidth:1});
var hRet = board.create('curve', [function(t){return t},function(t){return yRet.Y();}], {strokeColor:'gray',dash:2,strokeWidth:1});

qPro.on('drag', function(){
  qRet.moveTo([qPro.X(),rRet(qPro.X()) ]);
});

qRet.on('drag', function(){
  qPro.moveTo([qRet.X(),rPro(qRet.X()) ]);
});

board.on('update', function () {
document.getElementById('out').innerHTML = 'a/M = ' + qPro.X() + '<br>\n' +
'rPro/M = ' + qPro.Y() + '<br>\n' +
'rRet/M = ' + qRet.Y();
});

board.unsuspendUpdate();
</script>

---

Explanation
===========

The ISCO is the Innermost Stable Circular Orbit.  Here I am referring
to massive test particles in the equatorial plane of the
[Kerr black hole](http://arxiv.org/abs/1410.2130).  In the
spherically-symmetric Schwarzschild spacetime, there is only one ISCO,
at $$r=6M$$.  However, in Kerr, rotation splits prograde and retrograde
orbits, and the ISCO may range all the way from $$1M$$ out to $$9M$$ for
respectively prograde and retrograde orbits in extremal ($$a=M$$) Kerr,
and anywhere in between, depending on the value of the spin parameter.

More than once I've been discussing with a colleague and asked
either "What spin has an ISCO of $$r$$?" or "If the ISCO is at $$r$$,
what is $$a$$?"  I can never answer immediately because the formula
for the ISCO is not so simple.  This page should solve this problem.

The two curves above come from two roots of a quartic polynomial (see
the derivation in
e.g. [Chris Hirata's notes](http://www.tapir.caltech.edu/~chirata/ph236/2011-12/lec27.pdf)).
Recall that quartics can be solved by radicals!  Turn the crank, find
the two appropriate roots.  The Kerr ISCO formula is:
\\[
\frac{r_{ISCO}}{M} = 3 + Z_2 \mp \sqrt{(3-Z_1)(3+Z_1+2Z_2)}.
\\]
The smaller root is for prograde orbits, and the larger root is for
retrograde orbits. Here
  \\begin{align}
  Z_1 &= 1 + \left(1 - \chi^2\right)^{1/3} \left((1 + \chi)^{1/3} + (1 - \chi)^{1/3}\right),\\\
  Z_2 &= \sqrt{3 \chi^2 + Z_1^2},
  \\end{align}
and $$\chi\equiv a/M$$ is the dimensionless spin parameter,
$$-1\le \chi \le 1$$.

Thanks to [Niels Warburton](http://nielswarburton.net/) for suggesting
the [JSXGraph](http://jsxgraph.uni-bayreuth.de/wp/) toolkit.
