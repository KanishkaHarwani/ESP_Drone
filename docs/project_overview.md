# Project Overview

| | |
|---|---|
| **Status** | Planning |
| **Priority** | Medium |
| **Type** | Embedded + Robotics + Learning |
| **Started** | 2026-09-17 |
| **Last updated** | 2026-09-17 |

## Goals

- Build a small, lightweight drone as an embedded-systems and robotics learning platform.
- Develop a basic flight-capable platform that I can program and experiment with.
- Learn the fundamentals of quadcopter flight control, stabilization, motor control, and wireless communication.
- Keep the design simple enough to understand, modify, and troubleshoot myself.

## Description

A small ESP32-S3-based quadcopter built around four coreless motors and a BNO085 IMU.

The drone is intended to be a simple experimental platform rather than a highly optimized or production-ready flight controller. The initial version focuses on getting a stable basic flight system working while keeping the hardware inexpensive, lightweight, and easy to modify.

The ESP32-S3 handles flight control as well as wireless communication. Bluetooth/BLE is intended for joystick-based control, and Wi-Fi for PC-based control and experimentation.

## Key Features

- Small and lightweight
- Low-cost components
- Simple hardware architecture
- Programmable flight controller
- Wireless control
- Modular software
- Easy to experiment with
- Useful as a learning platform
- Designed to be gradually improved rather than completed all at once

## Hardware

**Main controller**
- ESP32-S3 with CAM module (Seeed Studio XIAO series)
- BNO085 IMU

**Propulsion**
- 720 coreless brushed motors x4
- Matching propellers x4 (2 CW, 2 CCW)

**Motor controller**
- IRLML2502 N-channel MOSFET x4
- Gate resistors x4
- Gate pulldown resistors x4
- Motor transient / flyback protection (TBD)
- Bulk capacitor
- Decoupling capacitors

**Power**
- 1S 400 mAh LiPo
- 1S LiPo charger
- Battery connector
- Battery voltage monitoring

**Mechanical**
- Small carbon-fiber frame
- Motor mounts
- Lightweight hardware
- Perfboard (V1 prototype)
- 28 AWG wires

## Software

Modular code for flight control.

### Tech stack

**Languages**
- C++ for the ESP32 flight controller
- Python for PC tools and control
- Rust for future investigation

**Algorithms**
- PID control
- Motor mixing
- PWM control
- Sensor fusion
- Attitude estimation
- Kalman filtering (investigate if needed)

**Libraries and frameworks**
- ESP-IDF / Arduino-ESP32
- Adafruit BNO08x
- FreeRTOS
- ESP32 BLE
- ESP32 Wi-Fi
- ESP-NOW (investigate)
- Micro-ROS (future investigation)

## Working Principles

- Keep V1 simple.
- Prioritize understanding over optimization.
- Test individual subsystems before combining them.
- Avoid adding features before basic flight is working.
- Record measurements instead of relying on advertised specifications.
- Keep the software modular so individual components can be replaced easily.
- Treat the first version as a learning platform for future drone projects.

## See Also

- [Roadmap](roadmap.md): progress, next steps, future ideas
- [Architecture](architecture.md): software structure
- [Hardware notes](hardware-notes.md): design decisions and open questions
- [References](references.md): datasheets and links
