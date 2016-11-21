---
title: Elliptic Integrals in Javascript
modified:
categories: [code]
excerpt:
link: https://github.com/duetosymmetry/elliptic-integrals-js
tags: [javascript, special functions]
date: 2016-02-24T21:18:03-08:00
jsxgraph: true
---

I just created a repo on github for computing complete elliptic
integrals in javascript. The `README.md` is below, and a [demo](#demo)
after that. You might ask yourself, "why would anybody want to compute
elliptic integrals in javascript?" Stay tuned for an answer next week!

# [elliptic-integrals-js](https://github.com/duetosymmetry/elliptic-integrals-js)
Complete elliptic integrals in javascript

Here I've implemented complete elliptic integrals of the first, second, and third kind in javascript.
The implementation follows an iteration scheme based on the convergence of the arithmetic-geometric mean, which converges at least quadratically with number of iterations---therefore effectively doubling the number of digits each iteration.
These iteration schemes come from [Garrett, Milan Wayne, Journal of Applied Physics 34.9 (1963): 2567-2573](http://dx.doi.org/10.1063/1.1729771), Eqs. (18)-(21).

The functions extend the `Math` object with:

* `Math.agm(a,g)`: arithmetic-geometric mean of two non-negative numbers
* `Math.EllipticK(m)`: Complete elliptic integral of the first kind
* `Math.EllipticE(m)`: Complete elliptic integral of the second kind
* `Math.EllipticPi(n,m)`: Complete elliptic integral of the third kind

The arguments are the *parameter* $$m$$, which is related to the *modulus* $$k$$ via $$m=k^2$$; and the *characteristic* $$n$$.
The algorithms are valid for $$m<1, n<1$$.

To be completely clear, the functions are computing the following
integrals:

* $$ K(m) = \int_0^{\pi/2} \frac{d\theta}{\sqrt{1 - m (\sin\theta)^2}} $$
* $$ E(m) = \int_0^{\pi/2} \sqrt{1 - m (\sin\theta)^2} d\theta $$
* $$ \Pi(n,m) = \int_0^{\pi/2} \frac{d\theta}{(1-n(\sin\theta)^2)\sqrt{1 - m (\sin\theta)^2}} $$

This agrees with the conventions of `Mathematica`.

# Demo

Below, I used
[the code](https://github.com/duetosymmetry/elliptic-integrals-js/blob/master/elliptic.js)
and [JSXGraph](http://jsxgraph.uni-bayreuth.de/wp/index.html) to plot
$$K(m), E(m)$$, and $$ \Pi(n,m) $$. Drag the slider to change the
value of $$ n $$ (release for JSXGraph to replot; it's sampled sparsely
while you drag).

<div id="box" class="jxgbox" style="width:500px; height:500px; margin-bottom:1em;"></div>
<div id="out"></div>

<script type="text/javascript" src="{{ site.url }}/assets/js/elliptic.js">
</script>

<script type="text/javascript">

////////////////////////////////////////////////////////////
// Make some plots

var brd = JXG.JSXGraph.initBoard('box', {boundingbox:[-7,3,1.4,-0.5], axis:true});
 
brd.suspendUpdate();
n = brd.create('slider',[[-6,-0.25],[-2,-0.25],[-5,1,0.9]], {name:'n'}),
brd.create('functiongraph', [function(m){ return Math.EllipticK(m); },-10, 1],
  {strokeColor: "#cc0000",
   name:"K(m)",
   withLabel:true,
   label:{}
  });
brd.create('functiongraph', [function(m){ return Math.EllipticE(m); },-10, 1],
  {strokeColor:"#00cc00",
   name:"E(m)",
   withLabel:true,
   label:{offset:[200,-100]}
  });
brd.create('functiongraph', [function(m){ return Math.EllipticPi(n.Value(),m); },-10, 1],
  {strokeColor: "#0000cc",
   name:function(){return "Π("+ n.Value().toFixed(2) +",m)";},
   withLabel:true,
   label:{offset:[70,25]}
  });
brd.unsuspendUpdate();

</script>
