---
layout: page
title: Neuromodulated Mixture of Experts for Lifelong Learning
description: A prefrontal cortex-inspired neural network architecture that uses neuromodulatory gating to enable flexible, context-dependent computation without catastrophic forgetting.
img: assets/img/projects/nmoe.png
importance: 2
category: research
related_publications: true
---

How does the prefrontal cortex (PFC) support **continual learning** — the ability to master new
tasks while retaining previously learned ones? A key feature of PFC is its dense innervation by
**neuromodulatory systems** (dopamine, acetylcholine, serotonin, norepinephrine), which dynamically
regulate the gain and connectivity of cortical circuits. This project asks whether neuromodulation
is a *computational mechanism* for lifelong learning, and whether that mechanism can be instantiated
in a neural network architecture.

I designed the **Neuromodulated Mixture of Experts (NMoE)** architecture, in which a learned
neuromodulatory signal gates a set of expert sub-networks. Each expert specialises in a subset of
tasks or contexts; the gating mechanism, analogous to neuromodulatory tone, selectively activates
the relevant experts for the current context. This prevents the weight interference that underlies
catastrophic forgetting in standard networks.

The model was developed and benchmarked alongside a **novel Multi-Context "Seasonal" Foraging
Task**, designed to mirror the kind of non-stationary, context-dependent decision-making demands
placed on rodents and humans across changing environments. The task requires the agent to infer
the current context (season), retrieve the appropriate foraging strategy, and update that strategy
when the context shifts — a regime where neuromodulatory gating provides a principled advantage.

{% if page.img %}
<div class="row justify-content-center">
  <div class="col-sm-10 mt-3 mt-md-0">
    {% include figure.liquid path=page.img title="NMoE architecture" class="img-fluid rounded z-depth-1" %}
  </div>
</div>
<div class="caption">
  Schematic of the Neuromodulated Mixture of Experts architecture.
  To add your own figure, save it to <code>assets/img/projects/nmoe.png</code> —
  a good candidate is the architecture diagram from the Cosyne 2024 poster.
</div>
{% endif %}

**Collaborators:** Anousheh Bakhti-Suroosh, Clara N. Yi, Terrence Sejnowski, Kay Tye (Salk / UCSD)

**Presentations:** Cosyne 2024 (Lisbon) &middot; SfN 2023 (Washington DC)
