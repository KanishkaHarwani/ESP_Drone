# ESP Drone

A small, lightweight ESP32-S3 quadcopter built as an embedded-systems and robotics learning platform.

> **Status:** Planning (started 2026-09-17) · **Priority:** Medium · **Type:** Embedded + Robotics + Learning

This is **not** a production flight controller. It is a simple, inexpensive, easy-to-modify platform for learning quadcopter flight control, stabilization, motor control, and wireless communication, built to be understood, debugged, and improved gradually rather than finished all at once.

## Goals

- Build a small, flight-capable platform that I can program and experiment with.
- Learn the fundamentals of flight control, stabilization, motor control, and wireless communication.
- Keep the design simple enough to understand, modify, and troubleshoot myself.

## Overview

An ESP32-S3 quadcopter with four coreless brushed motors and a BNO085 IMU. The ESP32-S3 runs the flight controller and handles wireless communication:

- **BLE** for joystick-based control
- **Wi-Fi** for PC-based control and experimentation
- **ESP-NOW** to be investigated

## Hardware

| Subsystem | Parts |
|-----------|-------|
| Controller | Seeed Studio XIAO ESP32-S3 (Sense/CAM variant), BNO085 IMU |
| Propulsion | 4× 720 coreless brushed motors, 4× matching props (2 CW, 2 CCW) |
| Motor drive | 4× IRLML2502 N-channel MOSFET, gate resistors, gate pulldowns, bulk + decoupling capacitors, flyback protection (TBD) |
| Power | 1S 400 mAh LiPo, 1S charger, connector, battery voltage monitoring |
| Mechanical | Small carbon-fiber frame, motor mounts, perfboard (V1 prototype), 28 AWG wire |

See [`hardware/bom.csv`](hardware/bom.csv) for the full parts list once it is added.

## Software

Modular C++ firmware for the ESP32-S3 (PlatformIO + Arduino-ESP32, FreeRTOS underneath), plus Python tools for the PC side.

- **Control:** PID, motor mixing, PWM
- **Estimation:** sensor fusion, attitude estimation (Kalman filtering if needed)
- **Libraries:** Adafruit BNO08x, ESP32 BLE, ESP32 Wi-Fi
- **Later:** Rust experiments, Micro-ROS

## Repository Structure

```
esp-drone/
├── docs/            # overview, roadmap, architecture, hardware notes, references
├── hardware/        # schematic, perfboard layout, BOM, datasheets, mechanical
├── firmware/
│   ├── src/         # main.cpp: wires modules together only
│   ├── lib/         # replaceable modules (imu, estimation, control, motors, comms, battery, config)
│   ├── bringup/     # standalone per-subsystem test programs
│   └── test/        # PC-side unit tests (PID, mixer)
├── tools/           # Python control, telemetry, and analysis scripts
└── data/            # logged measurements with setup notes
```

Folders are created as they are needed, so some of these may not exist yet.

## Getting Started

> Firmware does not exist yet. This section will be filled in as the project progresses.

Planned workflow:

1. Validate each subsystem on its own with the programs in `firmware/bringup/`, in order: motors, IMU, battery ADC, BLE link, control loop on the bench.
2. Integrate the validated modules through `firmware/src/main.cpp`.
3. Tether-test before any free flight.

**Prerequisites (planned):** [PlatformIO](https://platformio.org/), Python 3.10+ for `tools/`.

## Roadmap

- [x] Project concept defined
- [x] Basic schematic defined
- [x] Microcontroller, IMU, MOSFETs selected
- [x] Motors, MOSFETs, perfboards purchased
- [ ] Buy battery and charger
- [ ] Detailed schematic
- [ ] Hardware validation
- [ ] Software flowchart and architecture
- [ ] Motor tests

Longer-term ideas (custom PCB, barometer/ToF altitude, optical flow, telemetry, OTA updates, web control, Micro-ROS/ROS2, autonomous flight, RL) are tracked in [`docs/roadmap.md`](docs/roadmap.md).

## Design Principles

- Keep V1 simple.
- Prioritize understanding over optimization.
- Test individual subsystems before combining them.
- Don't add features before basic flight works.
- Record measurements instead of trusting advertised specs.
- Keep software modular so components can be swapped easily.
- Treat V1 as a learning platform for future drone projects.

## Safety

Spinning propellers can cause injury. Remove props during bench testing of anything other than thrust, and take care with LiPo batteries: use a proper 1S charger, never charge unattended, and don't use a damaged cell.

## License

To be decided. See [LICENSE](LICENSE).
