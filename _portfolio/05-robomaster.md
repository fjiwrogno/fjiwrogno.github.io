---
title: "RoboMaster UAV Vision System"
excerpt: "A >200 Hz dual-camera real-time detection, tracking, and state-estimation pipeline for competing mobile robots in the DJI RoboMaster 2024 competition."
collection: portfolio
permalink: /portfolio/robomaster-uav-vision/
date: 2024-08-01
order: 5
header:
  teaser: /images/projects/robomaster/uav.jpg
  teaser_video: /videos/covers/robomaster-cover.mp4
---

<img src="{{ '/images/projects/robomaster/uav.jpg' | relative_url }}" alt="RoboMaster UAV" style="width:100%;max-width:720px;border-radius:6px;">

## Overview

I worked as a **UAV vision-system developer** for the DJI RoboMaster robotics competition. The goal was to build a high-frame-rate real-time perception and state-estimation system using industrial cameras under strict latency and reliability constraints.

## Demo video

<video controls muted playsinline preload="metadata" style="width:100%;max-width:850px;border-radius:6px;">
  <source src="{{ '/videos/robomaster-2024-demo.mp4' | relative_url }}" type="video/mp4">
  Your browser does not support the video tag.
</video>

*Real-time detection and tracking of competing mobile robots during RoboMaster 2024.*

## My contribution

- Developed a **>200 Hz dual-camera vision pipeline** for real-time detection, tracking, and state estimation of competing mobile robots, using industrial cameras with different focal lengths to provide 2D trajectories and attitude estimates.
- Implemented a real-time dual-camera state-estimation and data-processing pipeline with **asynchronous image acquisition, producer–consumer threading, and circular buffers** to reduce I/O blocking and maintain stable processing throughput.
- Implemented and tested the tracking and state-estimation components in the actual competition environment, and debugged performance under real-time operational constraints.

## Outcome

- **National 2nd prize** in DJI RoboMaster 2024.
- **3rd place** in the regional competition.

## Tech stack

`C++` · `Python` · `OpenCV` · `Industrial cameras` · `Multithreading` · `Linux` · `Real-time vision`
