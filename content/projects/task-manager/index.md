---
title: "Autonomous Wheelchair Navigation System"
date: 2025-06-01
summary: "ROS2-powered autonomous indoor navigation system with SLAM, Nav2, LiDAR obstacle avoidance, and micro-ROS ESP32 firmware for real-time odometry."
tags:
  - Full-Stack
  - Robotics
  - Embedded
  - ROS2
tech_stack:
  - ROS2
  - Nav2
  - SLAM Toolbox
  - micro-ROS
  - ESP32
  - C++
  - Python
links:
  - type: github
    url: https://github.com/joshies-cpu
    label: Code
featured: true
status: "Completed"
role: "Solo Developer"
duration: "6 months"
highlights:
  - "50Hz real-time odometry publishing"
  - "Full SLAM + Nav2 autonomous navigation"
  - "micro-ROS serial at 115.2 kbps"
  - "Safety firmware with command timeouts & velocity smoothing"
---

A full-stack autonomous navigation system for a wheelchair platform, integrating ROS2, SLAM Toolbox, Nav2, and micro-ROS firmware on an ESP32 microcontroller for real-time indoor mapping and path planning.

## Overview

Built an end-to-end autonomous navigation system capable of mapping unknown indoor environments and navigating to goal poses without human input. The system combines a ROS2 software stack with custom embedded firmware on an ESP32.

## Key Features

### Embedded Firmware (ESP32 + micro-ROS)
- **Differential Drive Kinematics** — PID-controlled 4-wheel motion with smooth velocity profiles
- **Real-Time Odometry** — Wheel encoder-based odometry published to ROS2 at **50Hz**
- **micro-ROS Serial** — Bidirectional ROS2 communication over serial at **115,200 bps**
- **Safety Systems** — Command timeouts, acceleration limits, and velocity smoothing to prevent unsafe manoeuvres

### ROS2 Navigation Stack
- **SLAM Toolbox** — Real-time simultaneous localization and mapping (SLAM) for unknown indoor environments
- **Nav2** — Full autonomous path planning, obstacle avoidance, and goal execution
- **LiDAR Integration** — RPLiDAR A1 sensor for environment perception and obstacle detection
- **EKF Localization** — Encoder-fused odometry via `robot_localization` package

### Software Architecture
- Modular ROS2 node design for firmware-to-stack interoperability
- Custom launch files for SLAM, navigation, and sensor bringup
- Docker-based micro-ROS agent for reliable host-side connectivity

## Architecture

```
┌──────────────────────────────────────────────────────────┐
│               ROS2 Host (Laptop / SBC)                   │
│                                                          │
│  ┌──────────────┐  ┌───────────────┐  ┌──────────────┐  │
│  │ SLAM Toolbox │  │     Nav2      │  │    RViz2     │  │
│  │  (Mapping)   │  │  (Planning)   │  │ (Visualizer) │  │
│  └──────┬───────┘  └──────┬────────┘  └──────────────┘  │
│         │                 │                              │
│  ┌──────▼─────────────────▼──────────────────────────┐  │
│  │             ROS2 Topic Bus                         │  │
│  │  /odom  /scan  /cmd_vel  /map  /tf                 │  │
│  └──────────────────────┬──────────────────────────── ┘  │
│                         │                                │
│         ┌───────────────▼───────────────┐               │
│         │      micro-ROS Agent          │               │
│         │    (Serial Bridge, Docker)    │               │
│         └───────────────┬───────────────┘               │
└─────────────────────────│────────────────────────────────┘
                          │ UART 115200 bps
┌─────────────────────────▼────────────────────────────────┐
│                  ESP32 Firmware                           │
│                                                          │
│  ┌────────────────────┐   ┌──────────────────────────┐  │
│  │  Differential Drive│   │   Odometry Publisher     │  │
│  │  PID Controller    │   │   (50Hz, wheel encoders) │  │
│  └────────────────────┘   └──────────────────────────┘  │
│           ↕ Motor PWM              ↕ Encoder Interrupts  │
│      ┌────────┐               ┌────────────────────┐    │
│      │ Motors │               │   Wheel Encoders   │    │
│      └────────┘               └────────────────────┘    │
└──────────────────────────────────────────────────────────┘
```

## Performance

| Metric | Value |
|---|---|
| Odometry update rate | 50 Hz |
| Serial communication | 115,200 bps |
| Navigation | Fully autonomous (SLAM + Nav2) |
| Safety | Command timeout + velocity smoothing |

## Challenges & Solutions

### Challenge: Micro-ROS Time Synchronization
**Problem**: Message timestamps drifted between ESP32 and ROS2 host, causing TF tree issues.

**Solution**: Implemented micro-ROS time synchronization protocol to align clocks between the microcontroller and the ROS2 agent.

### Challenge: Reliable Serial Communication
**Problem**: Serial drops caused the navigation stack to send unchecked velocity commands.

**Solution**: Added command watchdog timer in firmware — if no `/cmd_vel` message is received within a threshold, the motors halt automatically.

### Challenge: SLAM Accuracy in Featureless Corridors
**Problem**: LiDAR-based SLAM struggled in long, uniform corridors.

**Solution**: Tuned SLAM Toolbox parameters (scan matching scores, search window sizes) and added IMU data for improved localization robustness.

## Tech Stack

| Layer | Technology |
|---|---|
| Firmware | C++ on ESP32 |
| RTOS Bridge | micro-ROS |
| Robot OS | ROS2 Humble |
| SLAM | SLAM Toolbox |
| Navigation | Nav2 |
| Localization | robot_localization (EKF) |
| Sensor | RPLiDAR A1 |
| Simulation | Gazebo |
| Visualization | RViz2 |

---

**Status**: ✅ Completed — First Place at Shristi Project Exhibition, Saintgits College of Engineering  
**GitHub**: [View on GitHub](https://github.com/joshies-cpu)
