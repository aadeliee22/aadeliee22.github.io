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
runnrg1to4 200 1.46 1.45 15.0 && \
runnrg1to4 200 1.47 1.46 15.0 && \
runnrg1to4 200 1.48 1.47 15.0 && \
runnrg1to4 200 1.49 1.48 15.0 && \
runnrg1to4 200 1.5  1.49 15.0 && \
runnrg1to4 200 1.51 1.5  15.0 && \
runnrg1to4 200 1.52 1.51 15.0 && \
runnrg1to4 200 1.53 1.52 15.0 && \
runnrg1to4 200 1.54 1.53 15.0 && \
runnrg1to4 200 1.55 1.54 15.0
# insulator-metal
runnrg4to1 200 1.99 2.0  18.0 && \
runnrg4to1 200 1.98 1.99 18.0 && \
runnrg4to1 200 1.97 1.98 18.0 && \
runnrg4to1 200 1.96 1.97 18.0 && \
runnrg4to1 200 1.95 1.96 18.0 && \
runnrg4to1 200 1.94 1.95 18.0 && \
runnrg4to1 200 1.93 1.94 18.0 && \
runnrg4to1 200 1.92 1.93 18.0 && \
runnrg4to1 200 1.91 1.92 18.0 && \
runnrg4to1 200 1.9  1.91 18.0
```

* insulator-metal  
at 2.99, keepE = 10 : 100 cycle/ 12: 5 cycle/ 15~20: 4 cycle  
from 4.0: 10.0  
from 2.99: 12  
from 2.62: 15  
from 2.49: 20  
> transition: 2.3

* metal-insulator  
from 1.0: 12.0  
from 1.16: 15.0  
> transition:
