# Hardware Notes

Design decisions, open questions, and validation checklists. Update this as the detailed schematic develops. Record measured values here rather than trusting advertised specs.

## Motor Driver

**Chosen:** one IRLML2502 N-channel MOSFET per motor, low-side switched, PWM driven from the ESP32-S3.

Per channel:
- Gate resistor between the GPIO and the gate
- Gate pulldown so the motor stays off during boot and reset
- Flyback protection across the motor: **TBD** (a diode per motor is the usual approach; decide and verify)

Shared:
- Bulk capacitor near the battery input
- Decoupling capacitors near the MOSFETs and the microcontroller

**To verify**
- [ ] Gate drive from 3.3 V GPIO gives full turn-on at the motor's actual current (measure the Vds drop)
- [ ] MOSFET does not run hot at stall or peak current
- [ ] Motors are off during boot, reset and firmware upload

## Power

- 1S 400 mAh LiPo (nominal 3.7 V, roughly 3.0 to 4.2 V in use)
- 1S charger and battery connector still to be purchased

**Open questions**
- [ ] Measured current draw per motor and total at hover-like throttle
- [ ] Voltage sag under load, and whether it resets the ESP32 (brownout)
- [ ] Battery voltage monitoring: divider ratio and ADC pin (the battery voltage exceeds the ADC range, so it needs dividing)
- [ ] Low-battery threshold and what happens when it is reached
- [ ] Whether motor noise on the supply disturbs the IMU or the radio

## IMU

BNO085 on the XIAO ESP32-S3 (bus and pins TBD).

- [ ] Choose I2C or SPI
- [ ] Confirm mounting orientation relative to the frame axes
- [ ] Log gyro and accelerometer noise with motors off, then with motors running, to measure vibration coupling

## Frame and Mass

- Carbon-fiber frame, motor mounts, lightweight hardware, 28 AWG wiring
- [ ] Record the all-up weight (with battery)
- [ ] Record thrust per motor and prop (see `data/measurements/motor-thrust/`)
- [ ] Check thrust-to-weight ratio before attempting flight

## Prototype Approach

V1 is built on perfboard. Validate each subsystem on the bench (motors, IMU, battery ADC) before assembling everything onto the frame. A custom PCB is a future idea, not a V1 goal.

## Decision Log

| Date | Decision | Reason |
|------|----------|--------|
| 2026-09-17 | ESP32-S3 (XIAO) as the single controller for flight control and wireless | Simplicity: one chip, BLE and Wi-Fi built in |
| 2026-09-17 | BNO085 IMU | Onboard sensor fusion reduces initial software effort |
| 2026-09-17 | IRLML2502 MOSFETs for motor switching | Small, low-cost, suitable for direct GPIO drive (to be verified) |
| 2026-09-17 | Perfboard for V1 | Cheap and easy to modify |
