---
layout: page
title: Machine Learning for Medical Imaging
description: Voxel-level cancer segmentation and diffusion MRI distortion correction for prostate cancer and bone metastasis diagnosis.
importance: 5
category: research
related_publications: true
---

Before my transition to neuroscience, I spent two years in the **Multimodal Imaging Lab** at
UC San Diego (advised by Tyler Seibert and Anders Dale) applying machine learning to clinical
medical imaging problems in oncology.

**Prostate cancer segmentation.** Standard diffusion MRI metrics (ADC maps) provide limited
specificity for prostate cancer detection. I contributed to developing a **four-compartment
Restriction Spectrum Imaging (RSI)** model that decomposes the diffusion signal into
biophysically interpretable compartments. Paired with a voxel-level classifier, this approach
substantially improved the accuracy of automatic prostate cancer segmentation compared to
single-compartment methods.

**B0 distortion correction in bone metastasis imaging.** Whole-body diffusion MRI is increasingly
used to assess skeletal metastatic burden, but **B0 field inhomogeneities** introduce geometric
distortions that can mislocalize lesions and corrupt quantitative metrics. I developed and
validated correction algorithms — based on field map acquisition and reverse phase-encode
approaches — that reduce these distortions, enabling more reliable quantitative imaging of bone
metastases.

Both projects involved close collaboration with radiologists at UC San Diego Health, combining
clinical annotation workflows with machine learning model development.

{% if page.img %}

<div class="row justify-content-center">
  <div class="col-sm-10 mt-3 mt-md-0">
    {% include figure.liquid path=page.img title="RSI-based prostate cancer segmentation" class="img-fluid rounded z-depth-1" %}
  </div>
</div>
<div class="caption">
  Voxel-level prostate cancer classification using four-compartment RSI (right) vs. standard ADC (left).
  To add a figure, save it to <code>assets/img/projects/medical_imaging.png</code>.
  A good candidate is Fig. 1 or Fig. 3 from the JMRI 2021 paper.
</div>
{% endif %}

**Advisors:** Tyler Seibert &amp; Anders Dale (UC San Diego)

**Publications:**

- Feng et al. (incl. **Batra**), _Journal of Magnetic Resonance Imaging_ (2021) — [link](https://onlinelibrary.wiley.com/doi/10.1002/jmri.27498)
- Digma et al. (incl. **Batra**), _Scientific Reports_ (2022) — [link](https://www.nature.com/articles/s41598-022-08847-0)
