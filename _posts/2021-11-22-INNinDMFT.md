---
title: "Interpretation of a minimal neural network to learn the metal-insulator transition in the dynamical mean-field theory"
toc: true
toc_sticky: true
date: 2021-08-03 20:07:00
categories: 
  - Physics (research)
tags: 
  - 2021-1 (spring)
  - 2021-1.5 (summer)
use_math: true
published : true
---
This work is a collaborative work.

In this research, we address the derivation of a new measure through interpretation of machine learning by employing DMFT with single-band Hubbard model which experiences a metal-insulator transition.
Our goal is to present a machine learning scheme that detects the metal-insulator transition and to interpret the pattern of the neural network with respect to the phase of matter.

- Conducting DMFT-NRG and obtain data from it.
- Train neural network model with DMFT-NRG hybridization function, calculate accuracy.
- Interpretation of weight pattern of neural network connectivity.
- Derive a simple expression inspired by this interpretation.
- Investigate the performance of this phase indicator
- Discussion on the relationship between phase indicator and the quasiparticle weight.


## Learning a metal-insulator transition from DMFT
### DMFT procedure
Dynamic mean-field theory is the method to describe the properties of the strongly correlated materials.
The Hamiltonian of the single orbital Hubbard model is
$$
H=-t\sum_{i,j,\sigma}{\bigg(c^{\dagger}_{i\sigma}c_{j\sigma}+c^{\dagger}_{j\sigma}c_{i\sigma}\bigg)+U\sum_{i}{n_{i\uparrow}n_{i\downarrow}}}+\mu\sum_{i\sigma}n_{i\sigma}
$$
where $\mu$ is the chemical potential, $t$ is the hopping element, and $U$ is the on-site interaction.
The system experiences Mott transition by tuning $U$ in half-filling ($\mu=U/2$).

DMFT maps many-body lattice problem into the local problem, such as Anderson Impurity model (AIM).

$$
H_\text{AIM} = \sum_k \epsilon_k a_k^\dagger a_k + \sum_{k\sigma}V_k^\sigma\bigg(c_\sigma^\dagger a_{k\sigma}+a_{k\sigma}^\dagger c_\sigma\bigg) + Un_\uparrow n_\downarrow - \mu(n_\uparrow+n_\downarrow)
$$

where $\epsilon_k$ is the electronic level of the bath and $V_k$ is the hopping term between the impurity and the bath.
Using the Anderson impurity model, it is now solvable with the self-consistency equation. 
(Various solvers are such as NRG(numerical renormalization group), ED(exact diagonalization), or QMC(quantum Monte-Carlo).)
One DMFT loop consists of the following steps.
1. DMFT mapping onto AIM.
2. Solve AIM with specific solver.
3. Extract self-energy of the impurity mode, make DMFT approximation on lattice self-energy.
4. Repeat.

DMFT-NRG is the method that can calculate the exact spectral function on the real frequency without analytic continuation.
This method is capable of calculating on the arbitrary low temperature scale using the renormalization group techniques by employing logarithmic intervals.
(Vast majority of the data is centered near zero frequency.)

<center><img src="/assets/images/DMFTNN/w_dist.png" width="60%" height="60%"></center>

In Bethe lattice, self consistency: $\Gamma = D^2 G/4$. 
Implementing broyden method with hybridization function have increased the speed of calculation. 
$$
\Gamma_{out} = dmftstep(\Gamma_{in}))\\
0 = F(\Gamma_{new}) = dmftstep(\Gamma_{in})-\Gamma_{in}
$$

Finally, calculated phase transition points $U_{c1}\sim2.3$ and $U_{c2}\sim2.9$. (See [Previous work](https://aadeliee22.github.io/physics%20(research)/ML-DMFT/))

During DMFT procedure, hybridization function is used for reproducing lattice dynamics, 
as it is closely related to the dynamics of the electrons and the bath of the impurity by bath parameters.
We calculated the hybridization function under logarithmic discretization mesh~(frequency) ratio of $\lambda=1.01$ spanning from $|\omega|_{\min}=10^{-5}$ to $|\omega|_{\max}=5.0$. 
For the NRG calculation parameters, we set logarithmic discretization parameter $\Lambda=2.0$, the number of interleaved discretization grids $N_z=4$, 
the lowest temperature scale of Wilson chain $T_{\min}=10^{-6}$, and the truncated rescale energy cutoff $12.0$ for the good convergence. 


### Artificial neural network to learn the spectral features

<center><img src="/assets/images/DMFTNN2/fig1.png" width="100%" height="100%"></center>

The scheme of supervised machine learning model that classifes phase based on the hybridization is illustrated above.
The neural network receives the hybridization function $\Gamma(\omega_n)$ as an input, and gives the probability of being in each phase as an output. 
The sigmoid function $\sigma(x) = 1/(1+\exp(-x))$ is employed as an activation function between each layer.

$$
\mathbf{y}=\mathbf{W}^{(1)}\Gamma(\omega_n)^{\mathbf{T}} + \mathbf{b}^{(1)}, \\
\mathbf{z}=\mathbf{W}^{(2)}\sigma(\mathbf{y})+ \mathbf{b}^{(2)}, \\
\mathbf{P}=\sigma(\mathbf{z}),
$$
where each $\mathbf{W}^{(i)}$ and $\mathbf{b}^{(i)}$ are the weight matrix and the bias vector, 
and $\mathbf{P}$ is the output vector of our model which is $\mathbc{P}=(P_\text{metal},P_\text{insulator})^\mathbf{T}$.

The neural network is trained with the hybridization function on the real frequency axis obtained by DMFT-NRG.
The training set consists of the data in the Bethe lattice under half-filling for a given range of on-site interactions 
of metallic phase $U_M^{(tr)}=\{u \mid 0.5\leq u\leq 2.0\}$ and of insulating phase $U_I^{(tr)}=\{u \mid 3.0\leq u\leq 5.0\}$. 
By excluding region around phase coexistence $U=\{u \mid U_{c1} \leq u \leq U_{c2}\}$ from the training set, 
we can examine whether our machine representation can be extended to the phase coexistence region.

The testing set consists of the data in the same condition as the training set but for the range of on-site interactions including phase coexistence region $U=\{u \mid U_{c1} \leq u \leq U_{c2}\}$. 
This corresponding test output in Fig (d) demonstrates that our neural network models have a high accuracy of predicting transition points $U_{c1}$ and $U_{c2}$ 
by reconstructing the discontinuous hysteresis behavior of the first-order phase transition. 
Even without the hidden layer, the logistic regression model output shows the high accuracy of classification of each phase within the phase coexistence region. 
The high accuracy regardless of the model complexity also implies that our models have converged to the same solution.


## Extracting a simple phase indicator
Figure below displays the heat map of the weight matrix $\mathbf{W}^{(1)}$ of different models in order of decreasing complexity. 
This pattern shows a similar weight response toward the real and the imaginary part of the hybridization function regardless of the model kind, 
roughly divided into low and high-frequency regions.

<center><img src="/assets/images/DMFTNN2/fig2.png" width="100%" height="100%"></center>
