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


## some tips for Linux (Ubuntu 20.04)

~/.dropbox-dist/dropboxd

* COMPILE
   - g++ -I/home/hyejin/trng4-4.22  -L/opt/trng/lib -ltrng4 -std=gnu++11 -ltrng4 -std=gnu++11

* localhost
   - scp -r -oProxyJump=hyejin@172.27.54.** hyejin@172.27.54.**:~/ $(pwd)

* vim
   - u: undo
   - ctrl+r: redo

* shell
   - ctrl+a/e: front/back
   - ctrl+u/k: clear front/back
   -ctrl+w: clear front 1
   -ctrl+y: paste

* python3
   - module load blas && mpiexec -n 4 python3 ~.py
 
* tmux
   - tmux new -s [name]
   - tmux kill-session -t [name]
   - tmux at -t [name]
   - vim ~/.tmux.conf
   - set -g default-terminal "screen-256color"

* git
   - git init :: initiate git
   - git branch -r :: branch list
   - #from gitserver
   - git pull :: bring newest code from server and merge
   - git fetch :: bring newest code from server
   - git add && git commit -m 'blah'
   - git push
   - password/token: check Kakaotalk for this information

* cache
   - sudo sysctl -w vm.drop_caches=2 (3 for page)
   - sudo swapoff -a && sudo swapon -a

