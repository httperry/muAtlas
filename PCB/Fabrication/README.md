[← Back to PCB](../README.md) · [← Back to Root](../../README.md)

# Fabrication & Assembly Files

![Status](https://img.shields.io/badge/Status-Fabrication%20Ready-brightgreen?style=flat-square)
![Stackup](https://img.shields.io/badge/Stackup-6%20Layers-blue?style=flat-square)
![Dimensions](https://img.shields.io/badge/Dimensions-100x100mm-brightgreen?style=flat-square)

Production files for manufacturing the Project μAtlas carrier board at JLCPCB or any standard PCB fabrication house.

---

## Files

| File | Type | Description |
|---|---|---|
| [Gerber_μAtlas_PCB_2026-10-24.zip](./Gerber_%CE%BCAtlas_PCB_2026-10-24.zip) | Gerbers & Drills | Complete Gerber (RS-274X) and Excellon drill files for 6-layer manufacturing |
| [PickAndPlace_μAtlas_PCB_2026_10_24.csv](./PickAndPlace_%CE%BCAtlas_PCB_2026_10_24.csv) | Centroid / CPL | Component positions, layers, and rotations for automated SMT pick-and-place assembly |

---

## JLCPCB Order Settings

* **PCB Dimensions:** 100 x 100 mm
* **Layers:** 6 Layers
* **PCB Thickness:** 1.6 mm (or 1.2 mm depending on impedance profile)
* **Surface Finish:** ENIG (recommended for high-density 0.4mm pitch ICs and M.2/SODIMM edge pads)
* **Copper Weight:** 1 oz outer / 0.5 oz or 1 oz inner
* **Impedance Control:** Yes (match differential pairs: 90Ω USB, 100Ω PCIe / Ethernet / HDMI)
* **SMT Assembly:** Upload `Gerber_μAtlas_PCB_2026-10-24.zip`, `PickAndPlace_μAtlas_PCB_2026_10_24.csv`, and `../../BOM/BOM.csv`.
