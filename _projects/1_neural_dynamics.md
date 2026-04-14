---
layout: page
title: Neural Ensembles in Social Cognition
description: Discovering how medial prefrontal cortex population dynamics encode social rank and orchestrate competitive behavior through downstream hypothalamic circuits.
img: assets/img/projects/social_dominance.png
importance: 1
category: research
related_publications: true
---

Social hierarchies are a fundamental feature of group-living animals, yet the neural computations
underlying social rank — how the brain represents who you are relative to others, and how that
representation updates — remain poorly understood. This project asks how **populations of
prefrontal neurons** solve this problem.

Working with large-scale calcium imaging recordings from the **medial prefrontal cortex (mPFC)**
during a novel social competition task, I identified rank-dependent neural manifolds: low-dimensional
subspaces of population activity that tile the dominance hierarchy. Dominant and subordinate mice
occupy geometrically distinct regions of mPFC population state space, and the trajectory of
population activity during competition predicts behavioral outcome.

To extract these latent states in an unsupervised way, I developed a computational framework
coupling **Hidden Markov Models (HMMs) with Generalized Linear Models (GLMs)**. The HMM infers
discrete internal states from high-dimensional spike-count data; each state is described by a GLM
that captures how neural activity relates to behavioral covariates. Applied to mPFC recordings
during competition, this model identified states that track social rank and predict nine distinct
behavioral motifs with a mean ROC-AUC of **0.92**.

Causal perturbation experiments revealed that mPFC ensemble activity drives competitive behavior
through **projections to the lateral hypothalamus** — establishing a cortical-subcortical circuit
for the top-down control of social dominance.

{% if page.img %}

<div class="row justify-content-center">
  <div class="col-sm-10 mt-3 mt-md-0">
    {% include figure.liquid path=page.img title="mPFC manifolds encode social rank" class="img-fluid rounded z-depth-1" %}
  </div>
</div>
<div class="caption">
  Rank-dependent neural manifolds in mPFC (left: dominant, right: subordinate trajectories).
  To add your own figure, save it to <code>assets/img/projects/social_dominance.png</code>.
  A good choice is Extended Data Fig. 3 or Fig. 4 from the Nature 2022 paper.
</div>
{% endif %}

**Collaborators:** Nancy Padilla-Coreano, Ila Fiete, Kay Tye (Salk / UCSD)

**Publication:** Padilla-Coreano\*, **Batra**\* et al., _Nature_ (2022) — [link](https://www.nature.com/articles/s41586-022-04507-5)
