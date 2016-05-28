---
layout: post
title: Kerr Calculator V2
modified:
categories: [tool]
excerpt: Interactive tool to compute Kerr quantities
tags: [general relativity, black holes, interactive]
image:
  feature:
date: 2015-10-08T09:41:44-07:00
jsxgraph: true
---

After posting the
[Kerr ISCO calculator]({{ site.url }}{% post_url 2015-10-07-kerr-isco-calculator %}),
I got some suggestions for improvements.  I may add to this page later
if I feel like procrastinating. Grab a red dot and drag.  Or, change
the value in the $$a$$ input box below and hit enter.  Horizontal
axis is $$a$$, vertical axis is Boyer-Lindquist $$r$$.  I use units
where $$M=1$$.  Scroll down for [details](#details).

<div id="box" class="jxgbox" style="width:500px; height:500px;"></div>
<div id="out"></div>

Details
===========
This plot is more or less an interactive version of Fig. 1 of
[Bardeen, Press, and Teukolsky (1972)](http://adsabs.harvard.edu/doi/10.1086/151796).
All formulas and way more detail may be found in that reference.

The darker shaded region is inside the event horizon.  The lighter
shaded region denotes the extent of the ergosphere.

Aside from the outer horizon, a quantity with a + (respectively -)
sign refers to a prograde (resp. retrograde) orbit.  The dimensionless
spin parameter is $$\chi\equiv a/M$$, $$-1 \le \chi \le +1$$.  The
following quantites are plotted:

* $$r_+$$: This is the event horizon.  It is given by
\\[
  \frac{r_+}{M} = 1 + \sqrt{1 - \chi^2}.
\\]

* $$r_{ms\pm}$$: The marginally stable orbits for massive particles,
  also known as the ISCO (innermost stable circular orbit).  They are
  given by
  \\begin{align}
  \frac{r_{ms\pm}}{M} &= 3 + Z_2 \mp \sqrt{(3-Z_1)(3+Z_1+2Z_2)}, \\\
  Z_1 &= 1 + \left(1 - \chi^2\right)^{1/3} \left((1 + \chi)^{1/3} + (1 - \chi)^{1/3}\right),\\\
  Z_2 &= \sqrt{3 \chi^2 + Z_1^2}. 
  \\end{align}

* $$r_{ph\pm}$$: Photon orbits, given by
\\[
\frac{r_{ph\pm}}{M} = 2\left\[ 1 + \cos \left( \frac{2}{3} \cos^{-1}\mp \chi \right) \right]
\\]

* $$r_{mb\pm}$$: Marginally bound orbits, given by
\\[
\frac{r_{mb\pm}}{M} = 2 \mp \chi + 2 \sqrt{1 \mp \chi}
\\]

One word of caution.  Note that all of the prograde quantities
converge to Boyer-Lindquist $$r\to M$$ as $$a\to M$$.  You can read
about how this is a coordinate artifact in
[Bardeen, Press, and Teukolsky](http://adsabs.harvard.edu/doi/10.1086/151796),
or in many other places, e.g. Jacobson's
[Where is the extremal Kerr ISCO?](http://arxiv.org/abs/1107.5081).

<script type="text/javascript">

////////////////////////////////////////////////////////////
// curve functions

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

var rHrz = function(a) {
  return 1. + sqrt(1. - a*a);
};

var rPhoPro = function(a) {
  return 2.*(1. + Math.cos(2./3.*Math.acos(-a)));
};

var rPhoRet = function(a) {
  return 2.*(1. + Math.cos(2./3.*Math.acos(a)));
};

var rMBPro = function(a) {
  return 2. - a + 2.*sqrt(1. - a);
};

var rMBRet = function(a) {
  return 2. + a + 2.*sqrt(1. + a);
};

////////////////////////////////////////////////////////////
// Begin board

var plotLeft   = -0.01;
var plotRight  = 1.01;
var plotBottom = 0.7;
var plotTop    = 9.05;
var board = JXG.JSXGraph.initBoard('box',
{boundingbox: [plotLeft, plotTop, plotRight, plotBottom],
 axis: false,
 grid: true,
 pan: {enabled: false},
 showNavigation: false,
 showCopyright:  false});

////////////////////////////////////////////////////////////
// Axes

var lX = board.create('axis', [[0.0, 1.0], [1.0, 1.0]], {label: 'a/M'});
var lY = board.create('axis', [[0.0, 1.0], [0.0, 9.0]], {label: 'r/M'});

////////////////////////////////////////////////////////////
// Some shaded regions for ergoregion and inside horizon

var gErg = board.create('functiongraph', [function(t){return 2.;}], {strokeColor:'#444444',strokeWidth:1, dash:2});

var shdErg = board.create('polygon',
[[0., plotBottom],
 [0., 2.],
 [1., 2.],
 [1., plotBottom]],
 {fillColor:'#000000', hasInnerPoints:false,
  vertices:{ visible:false },
   withLines: false});

var gHrz = board.create('functiongraph', [rHrz],
  {strokeColor:'#000000',strokeWidth:2, visible:false});

var pShdHrz = [ [0., plotBottom] ];

for (var i = 0; i < gHrz.numberPoints; i++) {
  if ((gHrz.points[i].usrCoords[1] >= 0.) &&
      (gHrz.points[i].usrCoords[1] <= 1.)) 
      pShdHrz.push([gHrz.points[i].usrCoords[1],gHrz.points[i].usrCoords[2]]);
};

pShdHrz.push([1., plotBottom]);
pShdHrz.push([0., plotBottom]);

var shdHrz = board.create('polygon',
 pShdHrz,
  {fillColor:'#000000', fillOpacity:0.3,
   hasInnerPoints:false,
   vertices:{ visible:false },
   withLines: false});

////////////////////////////////////////////////////////////
// Curves we care about

var curveDefs = [
 ['$$r_+$$',     rHrz,    {strokeColor:'#000000',strokeWidth:2,dash:0}, {size:3,face:'[]',name:'r_+'}],
 ['$$r_{ms+}$$', rPro,    {strokeColor:'#0000ff',strokeWidth:2},        {size:3,face:'[]',name:'r_{ms+}'}],
 ['$$r_{ms-}$$', rRet,    {strokeColor:'#0000ff',strokeWidth:2},        {size:3,face:'[]',name:'r_{ms-}', label: {anchorX: 'right'}}],
 ['$$r_{ph+}$$', rPhoPro, {strokeColor:'#cc0000',strokeWidth:2,dash:0}, {size:3,face:'[]',name:'r_{ph+}'}],
 ['$$r_{ph-}$$', rPhoRet, {strokeColor:'#cc0000',strokeWidth:2,dash:0}, {size:3,face:'[]',name:'r_{ph-}', label: {anchorX: 'right'}}],
 ['$$r_{mb+}$$', rMBPro,  {strokeColor:'#333333',strokeWidth:2,dash:2}, {size:3,face:'[]',name:'r_{mb+}'}],
 ['$$r_{mb-}$$', rMBRet,  {strokeColor:'#333333',strokeWidth:2,dash:2}, {size:3,face:'[]',name:'r_{mb-}', label: {anchorX: 'right'}}]
 ];

var curves  = new Array(curveDefs.length);
var gliders = new Array(curveDefs.length);
var yPts    = new Array(curveDefs.length);

var updateMost = function(a, i){
  for (var j = 0; j<curveDefs.length; j++)
    if (j != i) gliders[j].moveTo([a, curveDefs[j][1](a) ]);
};

board.suspendUpdate();

var aStart = 0.2;

for (var i=0; i < curveDefs.length; i++)
  // Javascript's lambdas are utter shite, so we need to capture like this.
  (function(i) {

  curves[i]  = board.create('functiongraph', [curveDefs[i][1]], curveDefs[i][2]);
  gliders[i] = board.create('glider', [aStart, curveDefs[i][1](aStart), curves[i]], {withLabel:false});
  yPts[i]    = board.create('point', [function(){return gliders[i].X();},function(){return curveDefs[i][1](gliders[i].X());}],curveDefs[i][3]);

  gliders[i].on('drag', function(){
    updateMost(gliders[i].X(), i);
  });

  })(i);

////////////////////////////////////////////////////////////
// Add output table

var tableHTML = '<table><tbody><tr><td>$$a$$</td>';

for(var i = 0; i < curveDefs.length; i++)
  tableHTML += '<td>' + curveDefs[i][0] + '</td>';

tableHTML += '</tr><tr id="outRow"><td style="text-align:center"><input type="number" min="0.0" max="1.0" step=".05" id="out-a" style="width:5em" onchange="updateMost(parseFloat(this.value),-1)"></td>';

for(var i = 0; i < curveDefs.length; i++)
  tableHTML += '<td id="out-' + i +  '" style="text-align:center"></td>';

tableHTML += '</tr></tbody></table>';

document.getElementById('out').innerHTML = tableHTML;

board.on('update', function () {
document.getElementById('out-a').value = gliders[0].X().toPrecision(4);

for (var i = 0; i < curveDefs.length; i++)
document.getElementById('out-' + i).innerHTML = gliders[i].Y().toPrecision(4);

});

board.unsuspendUpdate();
</script>
