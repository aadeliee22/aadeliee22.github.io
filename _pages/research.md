---
title: "Research"
permalink: /research/
layout: single
author_profile: false
hide_title: true
excerpt: "Research on machine learning for quantum measurements, monitored dynamics, error correction, and neutral-atom compilation."
---

<div class="page-intro">
  <p class="eyebrow">Research</p>
  <p class="page-deck">How can a learning system identify the task-relevant structure hidden in complex quantum data, then use it reliably when measurements, noise, and hardware constraints prevent exact modeling?</p>
</div>

My research approaches this question at three levels. I learn physical structure from measurement records, protect logical information through scalable decoding, and translate circuits into executable hardware decisions. Machine learning is the method; the scientific questions come from quantum information and dynamics.

<section id="quantum-attention-network" class="project-detail">
  <div class="project-detail__text">
    <p class="project-status">Published · Science Advances (2025)</p>
    <h2>Quantum Attention Network</h2>
    <p>Experimental access to a quantum state often consists of finite sets of noisy bitstrings. QuAN treats those snapshots as an unordered set and uses attention between subsets of measurements to learn information carried by the distribution, including higher-order structure that a single-snapshot classifier misses.</p>
    <p>Across driven hard-core bosons, random quantum circuits, and noisy toric-code states, QuAN learns entanglement scaling, complexity growth, and a decodability phase diagram. Attention pooling also allows the model to emphasize measurements that carry cleaner information.</p>
    <p class="text-links"><a href="https://www.science.org/doi/10.1126/sciadv.adu0059">Science Advances</a></p>
  </div>
  <figure class="project-detail__figure">
    <img src="{{ '/assets/images/QuAN-fig1.png' | relative_url }}" alt="Quantum Attention Network architecture and applications">
    <figcaption>QuAN learns correlations across sets of quantum-measurement snapshots.</figcaption>
  </figure>
</section>

<section id="monitored-quantum-dynamics" class="project-detail project-detail--reverse">
  <div class="project-detail__text">
    <p class="project-status">Preprint · under review at PRX Intelligence</p>
    <h2>Learning measurement-induced phase transitions</h2>
    <p>Measurement-induced phase transitions are difficult to observe because conventional protocols require exponential post-selection or comparison with classical simulation. I developed a data-centric alternative that uses only measurement records.</p>
    <p>The architecture combines attention across trajectories with temporal attention within each record. It detects a learnability transition between initial states and, in a lower-sample phase-recognition task, provides a noise-tolerant upper bound on the transition. Inspection of the learned attention shows sensitivity to informative tails of the early-time Born-probability distribution.</p>
    <p>Ongoing work with Quantinuum investigates this approach in an experimental setting.</p>
    <p class="text-links"><a href="https://arxiv.org/abs/2508.15895">arXiv:2508.15895</a></p>
  </div>
  <figure class="project-detail__figure">
    <img src="{{ '/assets/images/MIPT-fig2.png' | relative_url }}" alt="Temporal and inter-trajectory attention for monitored quantum dynamics">
    <figcaption>Temporal and inter-trajectory attention extract structure from monitored-circuit records.</figcaption>
  </figure>
</section>

<section id="quantum-error-correction" class="project-detail project-detail--text-only">
  <div class="project-detail__text">
    <p class="project-status">Ongoing research</p>
    <h2>Scalable, adaptive quantum error-correction decoding</h2>
    <p>Logical circuits produce syndrome histories whose geometry changes across single-qubit gates, entangling operations, boundaries, and measurement. A useful decoder must capture those circuit-dependent correlations without allowing its computational cost to grow prohibitively with code distance.</p>
    <p>I am developing a sparse-attention extension of a modular circuit-level surface-code decoder. The architecture restricts most computation to physically and causally relevant neighborhoods, with the longer-term goal of transferring across code distances and adapting to device-specific correlated noise.</p>
    <div class="research-question">
      <strong>Research direction</strong>
      <p>Can a single decoder generalize across code distance, logical operations, and changing device noise while meeting real-time accuracy and latency constraints?</p>
    </div>
  </div>
</section>

<section id="neutral-atom-compilation" class="project-detail">
  <div class="project-detail__text">
    <p class="project-status">Manuscript in preparation (2026)</p>
    <h2>Neutral Atom Compiler Agent</h2>
    <p>Reconfigurable atom arrays provide flexible connectivity by physically transporting qubits, but compilation must jointly coordinate placement, parallel movement, gate scheduling, and hardware constraints. NACA formulates these coupled choices as structured sequential decision-making.</p>
    <p>An autoregressive policy constructs simultaneous transport batches while state-dependent masks exclude invalid actions. Heuristic imitation supplies feasible initial behavior, and reinforcement learning refines the policy against an end-to-end hardware error model.</p>
    <p>Under the modeled error assumptions in our study, NACA reduces atom transfers and execution time, improves fidelity over the heuristic baseline, and transfers without retraining across circuit sizes and families.</p>
  </div>
  <figure class="project-detail__figure">
    <img src="{{ '/assets/images/research/naca-overview.png' | relative_url }}" alt="Hardware-aware compilation of reconfigurable neutral-atom arrays with NACA">
    <figcaption>NACA constructs physically valid parallel transport batches autoregressively.</figcaption>
  </figure>
</section>

<figure class="full-width-figure">
  <img src="{{ '/assets/images/research/naca-results.png' | relative_url }}" alt="Comparison of modeled circuit fidelity for NACA and a heuristic compiler on error-correction state preparation and ripple-carry adders">
  <figcaption>Modeled fidelity comparison on error-correction state-preparation circuits and ripple-carry adders.</figcaption>
</figure>

## Robust learning under severe corruption

In complementary work on attribute noise, we found that multilayer perceptrons retain above-chance performance even when inputs are more than 90% corrupted. An infinite-width analysis identifies a universal leading decision rule in the heavy-corruption regime: classification approaches a nearest-class-centroid comparison. This provides an interpretable example of complex learned behavior reducing to a simple statistic in an extreme limit. [Read the preprint](https://arxiv.org/abs/2606.11319).

## Earlier research

My undergraduate research used interpretable machine learning to study the metal-insulator transition in dynamical mean-field theory and explored learning-accelerated Monte Carlo methods for lattice models. This work established my continuing interest in models that expose physically meaningful structure rather than serving only as black-box predictors.

## Future program

I plan to connect these projects through an adaptive quantum-information loop: measurement records inform learned diagnostics and decoders; calibrated device behavior informs compilation and control; new experiments then refine the models. Near-term questions include active selection of quantum measurements, decoder adaptation with limited hardware data, and compiler objectives based on logical rather than component-level fidelity.
