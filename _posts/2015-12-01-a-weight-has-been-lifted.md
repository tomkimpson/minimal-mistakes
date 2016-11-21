---
title: A Weight Has Been Lifted
modified:
categories: 
excerpt: The monster topical review has finally been published!
tags: []
date: 2015-12-01T19:22:41-08:00
---

The monster [topical review on testing general relativity]({% post_url 2015-01-28-testing-general-relativity-with-present-and-future-astrophysical-observations %}) is finally published
[in Classical and Quantum Gravity](http://iopscience.iop.org/article/10.1088/0264-9381/32/24/243001)!
This has taken a long time and a lot of effort from a large number of
people, all directed and coordinated by our fearless leader
[Emanuele Berti](http://www.phy.olemiss.edu/~berti/).  Here are some
statistics on this review:

* **179** pages (**188** in the [arXiv version](http://arxiv.org/abs/1501.07274))
* **46** figures
* **6** tables
* **53** coauthors (I had to write the
  [`make-iop-author-list`](https://github.com/duetosymmetry/make-iop-author-list)
  python script to keep the author list straight, since the IOP
  style files don't do this)
* **903** bibliographic references (I wrote at least **4** shell
  scripts and used my available emacs-fu to try to tame these)
* **1330** commits in the repo
* **countless** hours of telecons
* **countless** `grep`s, `sed`s, `awk`s, and other command-line-fu to
  get the whole thing under the same conventions
* **59** [citations](http://inspirehep.net/search?ln=en&p=refersto%3Arecid%3A1341964)
  *before* it's been officially published
* **4.8Mb** submission tarball with **112** files
* **10580** total lines of LaTeX (after stripping comments), doesn't
  count custom hacking of IOP style files


A timeline of the genesis of this baby:

* **January 6-10, 2014**: Emanuele's
  [workshop on testing GR](http://www.phy.olemiss.edu/TestGR2014/) in
  Oxford, MS.  I remember it well because I didn't bring a warm
  jacket, and the
  [high temperature on the 6th was 19°F](http://www.wunderground.com/history/airport/KUOX/2014/1/6/DailyHistory.html?req_city=Oxford&req_state=MS&req_statename=Mississippi&reqdb.zip=38655&reqdb.magic=1&reqdb.wmo=99999).
* **January 13, 2014**: first commit in the repo
* **December 23, 2014**: "first" draft circulated amongst co-authors
  (the "Christmas" draft)
* **January 28, 2015**: first arXiv version
* **February 9, 2015**: second arXiv version, including lots of
  additions from the gravity community following the first version.
  Version submitted to CQG
* **April 13, 2015**: received two referee reports. Yes, somebody has
  read this thing!
* **June 3, 2015**: responded to the referees' reports
* **August 3, 2015**: accepted by CQG
* **September 15, 2015**: received first round of proofs from CQG
* **September 21, 2015**: sent first round of corrections
* **September 22, 2015**: third arXiv version
* **November 20, 2015**: received secound round of proofs from CQG
* **November 22, 2015**: sent second round of corrections
* **December 1, 2015**: published in CQG!

In conclusion, I won't be coauthoring another review paper any time
soon ;) \\
Thanks again to everybody who contributed and especially to Emanuele!
