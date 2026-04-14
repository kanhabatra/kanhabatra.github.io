---
layout: page
title: Hippocampal Remapping as a Framework for Continual Learning
description: "Active postdoc research: using the brain's own solution to non-stationarity — hippocampal remapping — to build AI systems that learn continually without forgetting."
img: assets/img/projects/remapping.png
importance: 3
category: research
related_publications: false
---

My current postdoctoral research, jointly with the **Giocomo Lab** and **Linderman Lab** at
Stanford, asks a fundamental question at the interface of neuroscience and machine learning:
*how does the brain avoid catastrophic forgetting?*

The hippocampus provides a compelling answer. When an animal moves into a new environment —
or encounters a familiar environment after a context change — hippocampal place cells
**remap**: they reorganise their firing fields to create a new, orthogonal representation of
the new context, while the old representation is preserved. This is, in effect, a biological
implementation of **non-stationary representation learning**: the system allocates distinct
representational resources to different contexts, preventing interference between them.

This project develops computational models of hippocampal remapping and asks whether the
computational principles it implements — context-dependent orthogonalization, resource
allocation, and rapid context inference — can be translated into AI architectures that learn
continually in non-stationary environments.

On the neural data side, I apply **state-space models** and related probabilistic methods to
large-scale recordings from hippocampus and entorhinal cortex to characterize the dynamics
of remapping: how quickly it occurs, what drives it, and how it interacts with learning.

{% if page.img %}
<div class="row justify-content-center">
  <div class="col-sm-10 mt-3 mt-md-0">
    {% include figure.liquid path=page.img title="Hippocampal remapping" class="img-fluid rounded z-depth-1" %}
  </div>
</div>
<div class="caption">
  Schematic of hippocampal remapping across environments.
  To add a figure, save it to <code>assets/img/projects/remapping.png</code>.
  A good candidate is a rate map comparison figure from a Giocomo or Frank lab paper.
</div>
{% endif %}

**Advisors:** Lisa Giocomo &amp; Scott Linderman (Stanford University)

**Status:** Active postdoctoral project (2024–present)
