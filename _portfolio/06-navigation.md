---
title: "Autonomous Navigation & UAV Tracking"
excerpt: "ROS navigation, Cartographer mapping, local planning, PX4 offboard control, and camera-based target tracking."
collection: portfolio
permalink: /portfolio/autonomous-navigation-and-uav-tracking/
date: 2023-08-01
order: 6
---

## Indoor autonomous navigation

- Assembled an autonomous mobile-robot platform and configured a Jetson Nano onboard computer.
- Built a 2D indoor map using **Cartographer**.
- Integrated ROS **move_base** and the **Timed Elastic Band (TEB)** local planner for autonomous navigation.

## UAV tracking of a moving object

- Built a Gazebo simulation containing a ground robot and a depth-camera-equipped quadrotor.
- Implemented **PX4 offboard control** and image-processing logic for autonomous target tracking.

## Embedded multirotor attitude control

- Implemented PWM motor control on an **STM32** microcontroller.
- Implemented a Mahony complementary filter for attitude estimation.
- Developed a cascaded PID attitude controller and USART communication.

## Tech stack

`ROS` · `Gazebo` · `PX4` · `Jetson Nano` · `Cartographer` · `TEB` · `STM32` · `C/C++` · `OpenCV`
