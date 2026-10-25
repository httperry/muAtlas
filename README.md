<picture>
  <source media="(prefers-color-scheme: dark)" srcset="Resources/Icons/Icon Exports/Icon-macOS-Default-1024@1x.png">
  <source media="(prefers-color-scheme: light)" srcset="Resources/Icons/Icon Exports/Icon-macOS-Dark-1024@1x.png">
  <img alt="μAtlas Icon" src="Resources/Icons/Icon Exports/Icon-macOS-Default-1024@1x.png" width="100">
</picture>

# Project μAtlas

![Status](https://img.shields.io/badge/Status-In%20Development-orange?style=flat-square)
![Compute](https://img.shields.io/badge/SoC-Intel%20N100-lightgrey?style=flat-square)
![License](https://img.shields.io/badge/License-MIT-yellow?style=flat-square)

**A custom 100x100mm carrier board for the LattePanda Mu (Intel N100) — built as a compact, open-source NAS and home server.**

---

**Navigate:** [Schematics](./Schematics/README.md) · [PCB](./PCB/README.md) · [BOM](./BOM/README.md) · [Resources](./Resources/README.md) 

---

## Overview

Project μAtlas is a custom PCB carrier board for the LattePanda Mu compute module. It fits a full NAS build — dual SATA drives, NVMe cache, 2.5GbE, Wi-Fi, and USB 3.2 — onto a 100x100mm footprint. Designed in EasyEDA as a Hack Club project.

For detailed specs, see the [Schematics](./Schematics/README.md), [PCB](./PCB/README.md), and [BOM](./BOM/README.md).

---

## Board Preview

<p align="center">
  <img src="Resources/PCB_Images/Screenshot%202026-10-24%20120139.png" alt="μAtlas 3D Isometric View" width="850">
</p>

| Top Side (SoM & Power Rails) | Bottom Side (Dual M.2 & RTC Battery) |
|:---:|:---:|
| <img src="Resources/PCB_Images/Screenshot%202026-10-24%20120110.png" alt="Top View" width="420"> | <img src="Resources/PCB_Images/Screenshot%202026-10-24%20120121.png" alt="Bottom View" width="420"> |

<p align="center">
  <em>Rear I/O Profile (2.5GbE, HDMI, 4x USB-A):</em><br>
  <img src="Resources/PCB_Images/Screenshot%202026-10-24%20120157.png" alt="Rear I/O Profile View" width="850">
</p>

---

## Progress

| Module | Status | Schematic |
|---|---|---|
| PWR Management | ![Complete](https://img.shields.io/badge/Schematic-Complete-brightgreen?style=flat-square) | [View](./Schematics/PWR%20Management/README.md) |
| SATA Connections | ![Complete](https://img.shields.io/badge/Schematic-Complete-brightgreen?style=flat-square) | [View](./Schematics/SATA%20Connections/README.md) |
| SO-DIMM Connections | ![Complete](https://img.shields.io/badge/Schematic-Complete-brightgreen?style=flat-square) | [View](./Schematics/SO-DIMM%20Connections/README.md) |
| NVMe Connections | ![Complete](https://img.shields.io/badge/Schematic-Complete-brightgreen?style=flat-square) | [View](./Schematics/NVMe%20Connections/README.md) |
| IO Connections | ![Complete](https://img.shields.io/badge/Schematic-Complete-brightgreen?style=flat-square) | [View](./Schematics/IO%20Connections/README.md) |
| PCB Layout & Routing | ![Complete](https://img.shields.io/badge/Status-Complete-brightgreen?style=flat-square) | [View](./PCB/README.md) |
| Fabrication & Assembly | ![Ready](https://img.shields.io/badge/Files-Ready-brightgreen?style=flat-square) | [View](./PCB/Fabrication/README.md) |



## License

MIT — see [LICENSE](./LICENSE).

---

<img src="https://assets.hackclub.com/flag-standalone.svg" alt="Hack Club" width="48"> &nbsp; A [Hack Club](https://hackclub.com) project.
