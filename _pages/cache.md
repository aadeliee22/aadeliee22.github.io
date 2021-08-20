---
title: "Page only for ME"
permalink: /cache_hjk/
toc: true
toc_sticky: true
toc_ads : true
layout: single
author_profile: true
sidebar:
   nav: docs
---

This page is a cache.

## Paper

1. Write Results
2. Write Methods
3. Write Discussion
4. Write Abstract & Introduction

### Results
#### Metal-insulator transition with bath parameters
* Why hybridization function

#### Neural network analysis

* trained with the hybridization function on the Matsubara frequency -> failed (Fig. 2)
-> reason for using DMFT-NRG. (Fig. 1)

* trained with the hybridization function on the real frequency and tested in the Matsubara frequency -> success!
* Why?: Analyze the weight matrix with kernel density estimation. (Fig. 3)
* Analyzed results: how important the zero frequency point of the hybridization function is. Transformation... Why nontrivial transformation of weight matrix works well. Why does it work well even with different domain.

#### Effective order parameter

### Method
1. DMFT methods: DMFT-ED, DMFT-NRG
2. Lattice Green's function calculation on different lattice
3. Training method

### Figure
1. double occ, training scheme, failed training
2. Metal-insulator transition on DMFT-NRG
3. Good training
4. Analyzing: original, KDE, Matsubara in inset axis
5. different lattice geometries and S_2
6. self-energy calculation

## Matplotlib format

```python
import matplotlib as mpl
import matplotlib.pyplot as plt
import matplotlib.patches as mpatches
from matplotlib import rc
mpl.rcParams.update({
    'font.family' : 'STIXGeneral',
    'mathtext.fontset' : 'stix',
    'xtick.direction' : 'in' ,
    'xtick.labelsize' : 17.5 ,
    'xtick.top' : True ,
    'xtick.major.width' : 1.5,
    'xtick.major.size' : 6,
    'ytick.direction' : 'in' ,
    'ytick.labelsize' : 17.5 ,
    'ytick.right' : True ,
    'ytick.major.width' : 1.5,
    'ytick.major.size' : 6,
    'axes.labelsize' : 18,
    'legend.frameon' : False,
    'legend.fontsize' : 13,
    'legend.handlelength' : 2,
    'savefig.dpi' : 600, 
    'savefig.bbox' : 'tight',
    'axes.linewidth' : 1.5,
})
import matplotlib.ticker as ticker
from mpl_toolkits.axes_grid1.inset_locator import inset_axes
```

* IPT code : <https://github.com/sprudel/DMFT>, <https://github.com/Titan-C/pydmft>

