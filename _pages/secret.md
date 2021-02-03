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
runnrg1to4 200 1.56 1.55 16.0 && \
runnrg1to4 200 1.57 1.56 16.0 && \
runnrg1to4 200 1.58 1.57 16.0 && \
runnrg1to4 200 1.59 1.58 16.0 && \
runnrg1to4 200 1.5  1.59 16.0 && \
runnrg1to4 200 1.41 1.4  16.0 && \
runnrg1to4 200 1.42 1.41 16.0 && \
runnrg1to4 200 1.43 1.42 16.0 && \
runnrg1to4 200 1.44 1.43 16.0 && \
runnrg1to4 200 1.45 1.44 16.0
# insulator-metal
runnrg4to1 200 1.89 1.9  20.0 && \
runnrg4to1 200 1.88 1.89 20.0 && \
runnrg4to1 200 1.87 1.88 20.0 && \
runnrg4to1 200 1.86 1.87 20.0 && \
runnrg4to1 200 1.85 1.86 20.0 && \
runnrg4to1 200 1.84 1.85 20.0 && \
runnrg4to1 200 1.83 1.84 20.0 && \
runnrg4to1 200 1.82 1.83 20.0 && \
runnrg4to1 200 1.81 1.82 20.0 && \
runnrg4to1 200 1.8  1.81 20.0
```

* insulator-metal  
at 2.99, keepE = 10 : 100 cycle/ 12: 5 cycle/ 15~20: 4 cycle  
from 4.0: 10.0  
from 2.99: 12  
from 2.62: 15  
from 2.49: 20  
from 1.23: 12
> transition: 2.3

* metal-insulator  
from 1.0: 12  
from 1.16: 15  
from 1.56: 16   
from 2.3: 20
> transition:
