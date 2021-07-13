---
title: "Page for additional material"
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

### DMFT
* study IPT and make code: <https://github.com/sprudel/DMFT>, <https://github.com/Titan-C/pydmft>

### Python

```python
import matplotlib as mpl
mpl.rcParams.update({
    'font.family' : 'STIXGeneral',
    'mathtext.fontset' : 'stix',
    'xtick.direction' : 'in' ,
    'xtick.labelsize' : 13 ,
    'xtick.top' : True ,
    'ytick.direction' : 'in' ,
    'ytick.labelsize' : 13 ,
    'ytick.right' : True ,
    'axes.labelsize' : 16,
    'legend.frameon' : False,
    'legend.fontsize' : 13,
    'legend.handlelength' : 1.5,
    'savefig.dpi' : 600, 
    'savefig.bbox' : 'tight'
})
```

### Visualization of Weight matrix
```python
def dat2f(datw, rw):
    for i, w in enumerate(datw):
        if rw < w: break
    a = (w-rw) / (w-datw[i-1])
    return i, a
for i,wq in enumerate(weq):
    weqind[i], weqalp[i] = dat2f(w.real, wq)
    
def G2Geq(datG, rw):
    Giweq = np.zeros_like(weq)
    for i,wqind in enumerate(weqind):
        Giweq[i] = datG[wqind]*(1-weqalp[i]) + datG[wqind-1]*weqalp[i]
    return Giweq
```
