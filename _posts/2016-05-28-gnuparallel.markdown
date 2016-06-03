---
layout: post
title: "Running in parallel"
modified:
categories: 
excerpt: "Usage of GNU parallel for running processes in parallel"
tags: []
image:
feature:
date: 2016-01-02T18:29:39-07:00

---

[GNU parallel](http://www.gnu.org/software/parallel/) is a handy tool for easily executing jobs in parallel across any number of cores.

Suppose we have 32 jobs we want to run across 4 cores. A simple way to parallelize this is to run 8 jobs on each core. GNU parallel instead starts a new process when one finishes, keeping all cores actve and reducign the dead time.

![alt text](https://quantmetryblog.files.wordpress.com/2015/01/2015-02-09_ds_at_the_cli_gnuparallel.png)


Installation:

        (wget -O - pi.dk/3 || curl pi.dk/3/ || fetch -o - http://pi.dk/3) | bash

Suppose you then have $X$ jobs named `script_n.sh` for identifier $n$. The easy way to run this across Y cores is simply

        parallel -j Y bash -c ::: ./script_*.sh

To prevent parallel quitting if you exit - i.e. if your remote session expires - run this with nohup:

nohup parallel -j Y bash -c ::: ./script_*.sh

An excellent full how-to guide is found [here](https://www.usenix.org/system/files/login/articles/105438-Tange.pdf)




