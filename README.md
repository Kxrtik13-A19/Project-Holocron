# 🌌 Project Holocron

<div align="center">

[![KiCad Version](https://img.shields.io/badge/KiCad-v10.0%2B-blue.svg)](https://kicad.org/)
[![PCB Layers](https://img.shields.io/badge/PCB-2%20Layer%20Custom-orange.svg)]()
[![Routing Status](https://img.shields.io/badge/Unrouted%20Nets-0%20(100%25)-success.svg)]()

> *A custom-engineered, ultra-sleek handheld gaming console controller board designed for high-performance portable computing and embedded control.*

</div>

---

## ⚡ Overview

**Project Holocron (KAR & EVE)** is a custom 2-layer printed circuit board (PCB) designed as the primary user interface and control deck for a custom portable handheld system. Built from scratch using **KiCad**, this board integrates a comprehensive button matrix, dual analog thumbsticks, and precise SPI analog-to-digital conversion into a compact, pocket-friendly form factor.

---

## 🎮 Hardware Architecture & Features

*   **🕹️ Dual Analog Thumbsticks:** Utilizes low-profile, PSP-style analog sticks driven by dual 10k potentiometers for smooth multi-axis tracking.
*   **🔘 Full Tactile Button Matrix:** Features **10 high-tactility push-buttons** arranged for a dedicated directional D-pad, standard action buttons (ABXY), and shoulder triggers.
*   **🔌 High-Precision ADC Integration:** Powered by an onboard **MCP3008 8-channel 10-bit ADC (`U1`)**, translating analog joystick signals over a high-speed SPI bus.
*   **🧠 Modular Compute Interface:** Features a 40-pin dual-row expansion header (`J1`) for seamless connection to host single-board computers (such as Raspberry Pi models).
*   **📐 Optimized 2-Layer Routing:** Hand-routed across Front (`F.Cu`) and Back (`B.Cu`) copper layers using 0.25mm trace widths and strategic via-tunnelling to achieve **zero unrouted nets** and full DRC compliance.

---

## 📋 Bill of Materials (BOM)

| Designator | Component | Description / Function |
| :--- | :--- | :--- |
| **`J1`** | 40-Pin Dual-Row Header | Main Compute / System Interface Header |
| **`J2`, `J3`** | Pin Headers | SPI / I2C / Power Breakout Headers |
| **`U1`** | MCP3008 (DIP-16) | 8-Channel 10-bit Analog-to-Digital Converter |
| **`RV1` - `RV4`** | Potentiometer Footprints | Left & Right PSP-Style Analog Joysticks (X/Y Axes) |
| **`SW1` - `SW4`** | Tactile Push Buttons (6mm) | Directional D-Pad (Up, Down, Left, Right) |
| **`SW5` - `SW6`** | Tactile Push Buttons (6mm) | Shoulder Triggers |
| **`SW7` - `SW10`** | Tactile Push Buttons (6mm) | Action Buttons (ABXY) |

---

## 📌 Signal Routing & Pinout Map

*   **Analog Inputs:** Joysticks (`JOY_L_X`, `JOY_L_Y`, `JOY_R_X`, `JOY_R_Y`) route directly into channels CH0 through CH3 of the MCP3008 ADC.
*   **SPI Bus:** Connected via `SPI_CLK`, `SPI_MOSI`, `SPI_MISO`, and `SPI_CS` lines.
*   **Digital Controls:** Push buttons interface directly with general-purpose I/O lines via the main compute header.
*   **Power Distribution:** Dedicated `+3V3`, `+5V`, and multi-point `GND` layout channels to ensure signal integrity across all sensors.

---

## 🚀 Manufacturing & Design Workflow

1. **Schematic Capture:** Logical schematic mapping of all input modules, ADC channels, and expansion headers.
2. **Footprint Customization:** Tailored component footprints optimized for low-profile physical assembly.
3. **Board Outline (`Edge.Cuts`):** Precise rectangular perimeter defining the physical dimensions of the control deck.
4. **Copper Routing:** Dual-layer trace balancing (`F.Cu` red / `B.Cu` blue) with via stitching.
5. **DRC Validation:** Verified against manufacturing constraints to ensure absolute zero unrouted nets and zero keepout violations.
