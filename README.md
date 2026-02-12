# Flight Controller Project

This repository contains the Altium Designer project for a Flight Controller board based on the STM32F405 microcontroller.

## Overview

- MCU: STM32F405RGT6
- Sensors / peripherals: BNO055 (IMU), barometer, UWB module, GPS, depth sensor
- Interfaces: I2C, SPI, SBUS, USB, UART, motor PWM headers
- Power: Schottky diode + LDO for 3.3V supply

Screenshots of the schematic pages were provided to illustrate the design (for reference only).

## Repository contents

- `Flight_controller_Project.PrjPcb` - Altium PCB project file
- `PCB1.PcbDoc` - PCB document
- `Sheet1.SchDoc`, `Sheet2.SchDoc`, `Sheet3.SchDoc` - Schematic sheets
- `*.SchLib`, `*.PcbLib` - Component libraries used by the project
- `Project Outputs for Flight_controller_Project/` - generated outputs (HTML, DRC, etc.)
- `.gitignore` - ignore rules for generated and temporary files

Note: The schematic and PCB source files are included in the repository and should be opened with Altium Designer.

## How to open the project

1. Open Altium Designer.
2. Use `File -> Open Project` and select `Flight_controller_Project.PrjPcb`.
3. Open schematic sheets (`Sheet1.SchDoc`, etc.) and `PCB1.PcbDoc` as needed.

## Important notes

- Do not modify or push large generated outputs (e.g., preview or History folders) — they are listed in `.gitignore`.
- If you want a cleaned repository with only source files, I can prepare a lighter export (removing large generated files).

## License & Contact

Add your preferred license here (MIT, GPL, etc.) and contact information.

---
_README created and pushed by helper script._
