---
title: "Underwater Robot System (CPS Drone Reproduction)"
excerpt: "A 5-DoF waterproof underwater robot built from the open CPS Drone design — my first step toward the aerial–aquatic platforms Flamingo and Nami."
collection: portfolio
permalink: /portfolio/underwater-robot-system/
date: 2025-05-01
order: 4
header:
  teaser: /images/projects/underwater/robot-photo.jpg
  teaser_video: /videos/covers/underwater-cover.mp4
---

<img src="{{ '/images/projects/underwater/overview.png' | relative_url }}" alt="Underwater robot: CAD model of the hull, the acrylic-tube electronics enclosure, and the assembled physical robot" style="width:100%;max-width:850px;border-radius:6px;">

*From left to right: hull CAD model, the acrylic-resin-tube electronics enclosure, and the assembled physical robot.*

## Overview

Before developing the aerial–aquatic platforms [Flamingo]({{ '/portfolio/flamingo-aerial-aquatic-bicopter/' | relative_url }}) and [Nami]({{ '/portfolio/nami-articulated-aerial-aquatic-robot/' | relative_url }}), I built a fully working **underwater robot system** by reproducing the open-source [CPS Drone](https://www.cpsdrone.com/) design as the first stage of my master's research on cross-domain robots.

The goal was to master the fundamentals that every aquatic platform depends on — waterproof hardware design, underwater propulsion and thrust mapping, buoyancy trimming, and closed-loop underwater control — on a proven design before committing to my own aerial–aquatic prototypes.

## System

- **5-DoF underwater system** with vectored thrusters.
- **Acrylic resin tube** as the sealed electronics enclosure.
- Whole-body waterproof hardware integration (propulsion, ESCs, sensors, onboard electronics).
- **Up to 40 minutes** of continuous operation on one charge.
- Cascaded PID feedback control of attitude and depth using IMU and pressure sensing.

## Demo video

<video controls muted playsinline preload="metadata" poster="{{ '/images/projects/underwater/demo-frame.jpg' | relative_url }}" style="width:100%;max-width:850px;border-radius:6px;">
  <source src="{{ '/videos/underwater-robot-demo.mp4' | relative_url }}" type="video/mp4">
  Your browser does not support the video tag.
</video>

*Underwater demo run: teleoperated swimming and attitude/depth keeping in the test pool.*

## What it led to

This platform validated my waterproofing workflow, the acrylic-enclosure sealing approach, and the underwater thruster driving/control stack. All of these carried over directly into the propulsion and electronics design of **Flamingo** (aerial–aquatic bi-copter) and the articulated **Nami** robot.

## Tech stack

`ROS` · `C++` · `Python` · `SolidWorks` · `3D printing` · `BLDC/ESC` · `IMU` · `Pressure sensing` · `PID control` · `Waterproof design`
