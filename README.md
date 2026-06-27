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

**Navigate:** [Schematics](./Schematics/README.md) · [BOM](./BOM.md) · [Resources](./Resources/README.md) · [Contributing](./.github/CONTRIBUTING.md) · [Code of Conduct](./CODE_OF_CONDUCT.md)

---

## Overview

Project μAtlas is a custom PCB carrier board and 3D-printed enclosure for the LattePanda Mu compute module. It fits a full NAS build — dual SATA drives, NVMe cache, 2.5GbE, Wi-Fi, and USB 3.2 — onto a 100x100mm footprint. Designed in EasyEDA as a Hack Club project.

For detailed specs, see the [Schematics](./Schematics/README.md) and [BOM](./BOM.md).

---

## Progress

| Module | Status | Schematic |
|---|---|---|
| PWR Management | ![Complete](https://img.shields.io/badge/Schematic-Complete-brightgreen?style=flat-square) | [View](./Schematics/PWR%20Management/README.md) |
| SATA Connections | ![Complete](https://img.shields.io/badge/Schematic-Complete-brightgreen?style=flat-square) | [View](./Schematics/SATA%20Connections/README.md) |
| SO-DIMM Connections | ![In Progress](https://img.shields.io/badge/Status-In%20Progress-orange?style=flat-square) | [View](./Schematics/SO-DIMM%20Connections/README.md) |
| NVMe Connections | ![Complete](https://img.shields.io/badge/Schematic-Complete-brightgreen?style=flat-square) | [View](./Schematics/NVMe%20Connections/README.md) |
| IO Connections | ![Complete](https://img.shields.io/badge/Schematic-Complete-brightgreen?style=flat-square) | [View](./Schematics/IO%20Connections/README.md) |
| PCB Layout & Routing | ![Planned](https://img.shields.io/badge/Status-Planned-lightgrey?style=flat-square) | — |
| Enclosure | ![Planned](https://img.shields.io/badge/Status-Planned-lightgrey?style=flat-square) | — |



## License

MIT — see [LICENSE](./LICENSE).

---

<img src="https://assets.hackclub.com/flag-standalone.svg" alt="Hack Club" width="48"> &nbsp; A [Hack Club](https://hackclub.com) project.
