# Roadmap

Last updated: 2026-09-17

## Current Progress

- [x] Project concept defined
- [x] Basic schematic defined
- [x] Microcontroller, IMU, MOSFETs, etc. selected
- [x] Motors, MOSFETs, perfboards, etc. purchased

## Next Steps

- [ ] Buy battery and battery charger
- [ ] Develop detailed schematic
- [ ] Hardware validation
- [ ] Software flowchart development
- [ ] Software architecture development
- [ ] Test motors
- [ ] More (yet to be defined)

## Problems / Blockers

None yet.

## Future Ideas

Items marked **[?]** are undecided. None of these should be started before basic flight works.

### Hardware
- Custom PCB
- Barometer [?]
- Time-of-flight sensor for altitude sensing [?]
- Camera for optical flow / FPV [?]

### Software
- Improved motor control
- Battery current monitoring
- Telemetry
- OTA firmware update
- Web-based control

### Other
- ROS2 / Micro-ROS simulation
- Autonomous flight
- Rust-based firmware experiments
- Target-based reinforcement learning

## Open Investigations

- Kalman filtering: only if the BNO085's onboard fusion is not enough
- ESP-NOW as a control link
- ESP-IDF vs Arduino-ESP32 (framework choice)
- Motor flyback / transient protection (TBD in the hardware design)
