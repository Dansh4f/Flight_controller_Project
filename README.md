# STM32F405 Flight Controller — Custom PCB Design

A compact, manufacturing-ready flight controller PCB designed around the STM32F405RGT6 (ARM Cortex-M4). This repository contains the Altium source files for a two-layer board focused on clean power distribution, modular sensor integration, and reliable communication for embedded flight applications.

## Highlights

- Core MCU: STM32F405RGT6 (Cortex-M4 @ 168 MHz)
- Sensors: BNO055 (IMU), MS5611 (barometer), depth sensor
- Wireless/comms: UWB (SPI interface), GPS (UART), SBUS receiver input
- Interfaces: multiple SPI buses, shared I2C, UARTs, USB
- Motor PWM outputs with dedicated connector
- On-board 3.3V regulation and input protection (BAT54C + MIC5504 LDO)

## System Overview

The design integrates MCU, sensors, and power subsystems to provide a reliable flight controller platform. Main subsystems:

- MCU core and support circuits (oscillator, VCAP, decoupling, reset/boot)
- Power input protection and 3.3V regulation
- Sensor interfaces (I2C and SPI) and connectors for expandability
- SBUS receiver input conditioning and motor PWM outputs
- USB for programming and diagnostics

## Microcontroller & Board Considerations

Design decisions made for the `STM32F405RGT6`:

- Individual decoupling capacitors for each VDD/VDDA pin
- Required VCAP caps and analog filtering for stable operation
- Ferrite bead isolation for analog supply (3.3VA)
- External crystal oscillator with proper load capacitors
- Boot configuration and reset network implemented for robust programming

## Power Architecture

Input sources:

- USB 5V (programming/power)
- External 5V header (battery or regulated input)

Protection & regulation:

- BAT54C Schottky diode for input protection/OR-ing
- MIC5504 LDO to provide regulated 3.3V to MCU and sensors
- Short, wide power traces and a bottom-layer ground pour for low impedance
- Proper input/output decoupling and via stitching for returns

Power routing was prioritized in layout to minimize noise injection into analog circuits.

## Sensors & Peripherals

- BNO055 IMU — I2C, with reset/interrupt lines routed
- MS5611 barometer — SPI with dedicated CS and local decoupling
- UWB module — SPI2 bus with IRQ and reset
- Depth sensor — I2C on the shared sensor bus
- GPS — UART interface on dedicated header

Components are placed and routed to keep analog sensors away from high-current traces.

## Communications & Signal Conditioning

- Multiple SPI buses isolate high-speed peripherals for signal integrity
- Shared I2C bus enables sensor expansion
- UARTs for GPS and debug
- SBUS receiver input uses an NPN transistor-based level shifter and pull-ups for reliable logic levels

## Motor PWM

Motor outputs are brought to a dedicated connector with shield/ground considerations and short route lengths from the MCU PWM pins.

## PCB Layout Strategy

- 2-layer PCB with bottom ground plane
- Ground via stitching in key areas
- Routing priority: power → decoupling → high-speed SPI → connectors
- Controlled trace widths for power, short SPI routes, and clear mechanical anchor points

## Files in this repository

- `Flight_controller_Project.PrjPcb` — Altium project file
- `PCB1.PcbDoc` — PCB layout document
- `Sheet1.SchDoc`, `Sheet2.SchDoc`, `Sheet3.SchDoc` — schematic pages
- `*.SchLib`, `*.PcbLib` — component libraries
- `Project Outputs for Flight_controller_Project/` — generated outputs (DRC, HTML reports)
- `.gitignore` — rules to exclude generated and temp files

## How to open (Altium Designer)

1. Open Altium Designer.
2. `File → Open Project` and choose `Flight_controller_Project.PrjPcb`.
3. Open schematic and PCB documents as needed.

## Notes & Next Steps

- Generated outputs and previews are excluded by `.gitignore`. If you want a smaller repo (source-only + BOM), I can prepare a cleaned export.
- Suggested additions: `LICENSE` (MIT recommended), `CONTRIBUTING.md`, `CONTEXT.md` with wiring notes.
- I can also prepare Gerber exports, a verified BOM, or a GitHub Actions job to run export/DRC steps if desired.

## License

Add your preferred license here (suggested: MIT).

## Contact

**Author:** Swastik Kumar

---
_This README was expanded and pushed to the repository by an assistant._
