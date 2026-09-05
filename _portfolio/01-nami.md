---
title: "Articulated Aerial–Aquatic Robot (Nami)"
excerpt: "A transformable two-link robot with separate aerial/aquatic propulsion, configuration-dependent control allocation, in-flight transformation, and underwater attitude/depth control."
collection: portfolio
permalink: /portfolio/nami-articulated-aerial-aquatic-robot/
date: 2026-08-17
order: 1
header:
  teaser: /images/projects/nami/prototype.jpg
  teaser_video: /videos/covers/nami-cover.mp4
---

<img src="{{ '/images/projects/nami/prototype.jpg' | relative_url }}" alt="Nami prototype" style="width:100%;max-width:850px;border-radius:6px;">

## Overview

Nami is an **articulated aerial–aquatic two-link robot** developed as part of my master's work at The University of Tokyo. A head link and tail link are connected by a 1-DoF yaw joint, while separate rotor sets are used for aerial and underwater locomotion.

The platform was designed to investigate whether body articulation can be introduced without losing controllability in either medium, and to establish a system foundation for future interaction-oriented aerial–aquatic robots.

## My contribution

- Mechanical design and system integration of the physical robot.
- Integration of aerial and aquatic propulsion, electronics, sensors, onboard computing, and embedded control.
- Development of waterproof enclosures and waterproofing measures for the articulated hardware.
- Implementation of a bidirectional aquatic-thruster driver and thrust mapping.
- Development of configuration-dependent modeling and control allocation.
- Implementation and tuning of aerial and underwater feedback controllers.
- Gazebo simulation and real-world experimental validation.

## System

<img src="{{ '/images/projects/nami/joint-design.png' | relative_url }}" alt="Nami whole-robot design and 1-DoF yaw joint with pulley, timing belt, and servo motor" style="width:100%;max-width:850px;border-radius:6px;">

*Left: the full two-link robot. Right: the 1-DoF yaw joint — (a) CAD design and (b) physical implementation, actuated by a servo motor through a timing belt and pulley.*

- **Mass:** approximately 3.535 kg
- **Size:** 840 × 571 × 304.5 mm in the undeformed configuration
- **Articulation:** 1-DoF yaw joint with belt transmission
- **Aerial propulsion:** four aerial rotors, canted by 10°
- **Aquatic propulsion:** four bidirectional underwater rotors
- **State feedback:** motion capture + IMU in air; IMU + pressure sensor underwater
- **Computing:** onboard computer + real-time flight controller

## Representative results

### In-flight transformation

The physical prototype maintained flight while the internal yaw joint was driven through:

**0° → +25° → −25° → 0°**

The control allocation was updated continuously from the measured joint angle.

<img src="{{ '/images/projects/nami/inflight-transformation.jpg' | relative_url }}" alt="Nami in-flight transformation experiment" style="width:100%;max-width:850px;border-radius:6px;">

<video controls muted playsinline preload="metadata" style="width:100%;max-width:850px;border-radius:6px;margin-top:0.8rem;">
  <source src="{{ '/videos/nami-transform-10x.mp4' | relative_url }}" type="video/mp4">
  Your browser does not support the video tag.
</video>

*In-flight transformation experiment (10× speed): the yaw joint is driven through 0° → +25° → −25° → 0° while the robot maintains stable hover.*

### Underwater control

The physical prototype achieved closed-loop regulation of **roll, pitch, yaw, and depth** using onboard IMU and pressure feedback.

<video controls muted playsinline preload="metadata" style="width:100%;max-width:850px;border-radius:6px;margin-top:0.8rem;">
  <source src="{{ '/videos/nami-pool-test.mp4' | relative_url }}" type="video/mp4">
  Your browser does not support the video tag.
</video>

*Underwater 4-DoF test: basic closed-loop control responses in roll, pitch, yaw, and depth.*

## Simulation

Before the physical experiments, the full system was validated in a **ROS + Gazebo** simulation environment built on the UUV Simulator plugin, covering aerial flight, underwater operation, and cross-domain flight at the water surface, including aerial and underwater transformation at different joint angles.

<img src="{{ '/images/projects/nami/sim-overview.png' | relative_url }}" alt="Nami simulation overview: Gazebo environments for aerial, underwater, and water-surface operation, with aerial and underwater transformation at 0, 30, and 45 degrees" style="width:100%;max-width:720px;border-radius:6px;">

## Envisioned applications

The in-flight transformation ability opens up application scenarios that a fixed-shape vehicle cannot handle:

<img src="{{ '/images/projects/nami/application.png' | relative_url }}" alt="Envisioned applications of Nami: passing narrow paths, circular inspection of underwater pipes, and whole-body grasping" style="width:100%;max-width:850px;border-radius:6px;">

- **Passing narrow paths:** the body can bend to follow a path with a specific curvature.
- **Circular inspection:** bending around a structure (e.g., an underwater pipe) lets multiple onboard sensors observe it from complementary viewpoints simultaneously.
- **Whole-body grasping:** the articulated body itself can wrap around and secure an object.

## Tech stack

`ROS` · `C++` · `Python` · `Gazebo` · `Linux` · `SolidWorks` · `Dynamixel` · `BLDC/ESC` · `IMU` · `MS5837` · `PID control` · `Control allocation`

