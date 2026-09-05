---
title: "Enhancing 3D Diffusion Policy via Self-Supervised Visual Representation"
excerpt: "Reimplemented the 3D Diffusion Policy (DP3) visuomotor imitation-learning framework and extended it with two self-supervised auxiliary tasks, evaluated on four dexterous-manipulation benchmarks."
collection: portfolio
permalink: /portfolio/3d-diffusion-policy/
date: 2026-01-10
order: 3
header:
  teaser: /images/projects/dp3/dp3-tasks.png
---

<img src="{{ '/images/projects/dp3/dp3-tasks.png' | relative_url }}" alt="Montage of dexterous-manipulation simulation tasks used by 3D Diffusion Policy" style="width:100%;max-width:850px;border-radius:6px;">

## Overview

Imitation learning offers a direct way to teach robots a wide range of skills from expert demonstrations. **3D Diffusion Policy (DP3)** [RSS 2024] incorporates compact 3D point-cloud representations into diffusion-based action generation, achieving strong performance on diverse contact-rich tasks with few expert demonstrations.

In this project (Knowledge Acquisition Systems, The University of Tokyo, Jan 2026) I **reimplemented DP3 with a PointNet backbone** and investigated whether its 3D visual representation can be further improved with **self-supervised auxiliary objectives** — trying to discover a better 3D representation for control.

## Method

<img src="{{ '/images/projects/dp3/method-overview.png' | relative_url }}" alt="Model structure: DP3 perception and diffusion-policy decision modules, extended with a hard-denoising point-cloud reconstruction branch and a visual-proprioceptive alignment branch" style="width:100%;max-width:850px;border-radius:6px;">

On top of the DP3 baseline, I added **two self-supervised auxiliary tasks** that are trained jointly with the policy:

1. **Hard denoising reconstruction** — the encoder receives a noisy point cloud and a decoder must reconstruct the clean one, supervised by a **Chamfer-distance loss with hard-example mining**. This encourages better manifold learning and 3D scene/object understanding.
2. **Visual–proprioceptive alignment** — an MLP head predicts the robot's proprioceptive state from the visual features, injecting explicit robot-configuration information into the latent space. This lets the model infer the robot's state even when it is occluded, which frequently happens during manipulation.

## Demo

<video controls muted loop playsinline preload="metadata" style="width:336px;max-width:100%;border-radius:6px;">
  <source src="{{ '/videos/dp3-door-demo.mp4' | relative_url }}" type="video/mp4">
  Your browser does not support the video tag.
</video>

*Policy rollout on the Adroit door task: the learned policy controls a dexterous hand to unlatch and open the door.*

## Experiments

I evaluated on the **four hardest tasks** for the original DP3 (the ones with the lowest reported scores), covering fine manipulation, articulated objects, and high-dimensional dexterous control:

<div style="display:grid;grid-template-columns:repeat(auto-fit,minmax(200px,1fr));gap:0.8rem;margin:1rem 0;">
  <figure style="margin:0;">
    <img src="{{ '/images/projects/dp3/task-adroit-door.png' | relative_url }}" alt="Adroit door task" style="width:100%;border-radius:6px;">
    <figcaption style="font-size:0.85rem;color:#555;text-align:center;">Adroit door</figcaption>
  </figure>
  <figure style="margin:0;">
    <img src="{{ '/images/projects/dp3/task-adroit-pen.png' | relative_url }}" alt="Adroit pen task" style="width:100%;border-radius:6px;">
    <figcaption style="font-size:0.85rem;color:#555;text-align:center;">Adroit pen</figcaption>
  </figure>
  <figure style="margin:0;">
    <img src="{{ '/images/projects/dp3/task-dexart-laptop.png' | relative_url }}" alt="DexArt laptop task" style="width:100%;border-radius:6px;">
    <figcaption style="font-size:0.85rem;color:#555;text-align:center;">DexArt laptop</figcaption>
  </figure>
  <figure style="margin:0;">
    <img src="{{ '/images/projects/dp3/task-dexart-bucket.png' | relative_url }}" alt="DexArt bucket task" style="width:100%;border-radius:6px;">
    <figcaption style="font-size:0.85rem;color:#555;text-align:center;">DexArt bucket</figcaption>
  </figure>
</div>

### Results (success rate)

| Model / Task | door | pen | laptop | bucket |
|---|---|---|---|---|
| DP3 baseline | 0.575 | **0.450** | 0.700 | **0.440** |
| Mine (+ auxiliary tasks) | **0.650** | 0.300 | 0.700 | 0.350 |

<img src="{{ '/images/projects/dp3/training-curves.png' | relative_url }}" alt="Training curves comparing the baseline and the extended model on the door task" style="width:100%;max-width:720px;border-radius:6px;">

### Analysis

- The auxiliary tasks make the **latent space more discriminative** and yield a **higher peak performance** on the door task, and act as an exploration-encouraging regularizer.
- However, they also introduce **gradient conflict**: on pen and bucket the success rate drops, likely caused by the reconstruction loss competing with the behavior-cloning objective.
- Ablations that simply attach a reconstruction decoder (with or without input noising and state alignment) did not work — the combination and weighting of the auxiliary objectives matters.

### Future directions

- **Learnable loss weights** to resolve the gradient conflict between the policy loss and the auxiliary losses.
- **Curriculum learning:** rough manipulation in the early stage, precise manipulation later.
- **Feature decoupling:** splitting the encoder so that policy learning and representation learning use dedicated feature subspaces.

## Tech stack

`PyTorch` · `Diffusion models` · `PointNet` · `Point clouds` · `Imitation learning` · `Adroit` · `DexArt` · `Python`
