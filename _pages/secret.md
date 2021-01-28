---
title: "Page for my schedule"
permalink: /secret/
toc: true
toc_sticky: true
toc_ads : true
layout: single
author_profile: true
sidebar:
   nav: docs
---

## To do list

### NRG solver
* obtaining data of metal -- insulator and plot transition
* study DMFT, hybridization function, self energy
* plot `S_w_imag`
* another temperature for $\beta$ = 10000

### other things
* bring cookies

### routine
- study toefl for T(R/L) T(S/W) SS(V)
- exercise MWF

## For my research

```shell
# metal-insulator
runnrg1to4 200 1.16 1.15 15.0 && \
runnrg1to4 200 1.17 1.16 15.0 && \
runnrg1to4 200 1.18 1.17 15.0 && \
runnrg1to4 200 1.19 1.18 15.0 && \
runnrg1to4 200 1.2  1.19 15.0 && \
runnrg1to4 200 1.21 1.2  15.0 && \
runnrg1to4 200 1.22 1.21 15.0 && \
runnrg1to4 200 1.23 1.22 15.0 && \
runnrg1to4 200 1.24 1.23 15.0 && \
runnrg1to4 200 1.25 1.24 15.0
# insulator-metal
runnrg4to1 200 2.19 2.2  20.0 && \
runnrg4to1 200 2.18 2.19 20.0 && \
runnrg4to1 200 2.17 2.18 20.0 && \
runnrg4to1 200 2.16 2.17 20.0 && \
runnrg4to1 200 2.15 2.16 20.0 && \
runnrg4to1 200 2.14 2.15 20.0 && \
runnrg4to1 200 2.13 2.14 20.0 && \
runnrg4to1 200 2.12 2.13 20.0 && \
runnrg4to1 200 2.11 2.12 20.0 && \
runnrg4to1 200 2.1  2.11 20.0
```

* insulator-metal  
at 2.99, keepE = 10 : 100 cycle/ 12: 5 cycle/ 15~20: 4 cycle  
from 4.0: 10.0  
from 2.99: 12  
from 2.62: 15  
from 2.49: 20

* metal-insulator  
from 1.0: 12.0  
from 1.16: 15.0  
