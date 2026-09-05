---
title: "Flamingo — Aerial–Aquatic Bi-copter"
excerpt: "A minimal hybrid bi-copter using two shared tilting propulsion modules with dedicated aerial and aquatic rotors, experimentally validated in both media."
collection: portfolio
permalink: /portfolio/flamingo-aerial-aquatic-bicopter/
date: 2026-07-01
order: 2
header:
  teaser: /images/projects/flamingo/air-water.jpg
  teaser_video: /videos/covers/flamingo-cover.mp4
---

<img src="{{ '/images/projects/flamingo/design-prototype.jpg' | relative_url }}" alt="Flamingo design and prototype: CAD model with the tilt angle of the vectoring propulsion unit, and the physical prototype in the flight arena" style="width:100%;max-width:850px;border-radius:6px;">

## Overview

Flamingo is a **3.7 kg aerial–aquatic bi-copter** designed to explore the minimum vectored propulsion configuration that can operate in both air and water.

Each of its two tilting propulsion units carries one aerial rotor and one aquatic rotor. Only the medium-specific rotor is activated, while both rotors share the same tilting mechanism.

## Mechanical design

<img src="{{ '/images/projects/flamingo/solidworks-design.png' | relative_url }}" alt="SolidWorks rendering of the Flamingo bi-copter, showing the two tilting propulsion units and the waterproof cylindrical fuselage" style="width:100%;max-width:850px;border-radius:6px;">

*SolidWorks design of Flamingo. The two tilting propulsion modules each carry a dedicated aerial rotor (top) and aquatic rotor (bottom), mounted on a shared tilting axis. The cylindrical waterproof fuselage houses all electronics, and the curved landing legs support both ground takeoff and water entry.*

## Hardware architecture

<img src="{{ '/images/projects/flamingo/hardware-layout.png' | relative_url }}" alt="Overall arrangement of electronic components: aerial and aquatic motors with their ESCs, 6s battery, Spinal controller board, onboard computer, voltage and depth sensors, DC-DC converters, and two tilting servos" style="width:100%;max-width:850px;border-radius:6px;">

*Overall arrangement of the electronic components. A 6s battery powers two domain-specific propulsion branches (aerial motors + 160 A ESC, aquatic motors + 4-in-1 ESC), a real-time controller board, and an onboard computer; DC-DC converters supply the two tilting servos, while voltage and depth sensors provide monitoring and underwater state feedback.*

## My contribution

- Mechanical and system design of the hybrid aerial–aquatic platform.
- Propulsion selection based on bench thrust measurements.
- Waterproof electronics integration.
- ROS-based upper-level software and embedded control integration.
- Aerial position/attitude control and underwater attitude-control implementation.
- Physical experiments in an indoor flight arena and outdoor test pool.

## Representative results

<div style="display:grid;grid-template-columns:repeat(auto-fit,minmax(280px,1fr));gap:0.8rem;margin:1rem 0;">
  <figure style="margin:0;">
    <video controls muted playsinline preload="metadata" poster="{{ '/images/projects/flamingo/aerial-flight.png' | relative_url }}" style="width:100%;border-radius:6px;">
      <source src="{{ '/videos/flamingo-aerial-flight.mp4' | relative_url }}" type="video/mp4">
      Your browser does not support the video tag.
    </video>
    <figcaption style="font-size:0.85rem;color:#555;text-align:center;">Takeoff, hovering, and landing in the indoor flight arena</figcaption>
  </figure>
  <figure style="margin:0;">
    <video controls muted playsinline preload="metadata" poster="{{ '/images/projects/flamingo/underwater-swimming.png' | relative_url }}" style="width:100%;border-radius:6px;">
      <source src="{{ '/videos/flamingo-underwater-demo.mp4' | relative_url }}" type="video/mp4">
      Your browser does not support the video tag.
    </video>
    <figcaption style="font-size:0.85rem;color:#555;text-align:center;">Underwater swimming and attitude regulation in the test pool</figcaption>
  </figure>
</div>

- Demonstrated physical **takeoff and aerial flight** using the two aerial rotors.
- Demonstrated underwater **roll, pitch, and yaw regulation** using only two vectorized aquatic rotors.
- Identified controllability and actuator-bandwidth limitations that motivated the subsequent articulated platform.

## Envisioned applications

<img src="{{ '/images/projects/flamingo/application.png' | relative_url }}" alt="Envisioned application: 3D reconstruction of offshore infrastructure above and below the waterline using the Flamingo bi-copter" style="width:100%;max-width:640px;border-radius:6px;">

Because the bi-rotor configuration uses only two propulsion units, Flamingo is more energy-efficient and offers a **longer endurance** than typical multi-rotor hybrid vehicles. This makes it promising for missions that need sustained operation across both media — for example, **3D reconstruction and inspection of offshore infrastructure**, where the same vehicle scans a structure above the waterline in flight and continues the scan underwater.

## Tech stack

`ROS` · `C++` · `Linux` · `Gazebo` · `SolidWorks` · `BLDC/ESC` · `Servo actuation` · `IMU` · `Pressure sensing` · `PID control`

## Publication

C. Chen, J. Sugihara, Y. Wang, J. Li, Z. Ma, and M. Zhao,  
**“Flamingo: Design and Implementation of a Hybrid Bi-rotor Based Aerial-Aquatic System,”** ROBOMECH 2026, 2P2-B07, Fukuoka, 2026.
