# Vera — Starter Motor System

Custom VESC 6-based motor controller developed for the **Vera** Shell Eco-marathon ICE vehicle. It drives a sensored TP Power TP4050 brushless motor through a 6.67:1 belt reduction to reliably crank a rebuilt Honda GX35 4-stroke engine (900–1,200 RPM) at ultra-low energy consumption (<30 Joules per start).

<p align="center">
  <img src="pcb_render.png" alt="Vera VESC Starter PCB 3D Render" width="800">
</p>

## Overview

* **HW/**: KiCad design files for the custom 4-layer STM32F405 + TI DRV8323RS motor controller (`HW/vera_vesc_starter.kicad_pro`).
* **SW/**: [VEDDERB BLDC Firmware](https://github.com/vedderb/bldc) tracked as a Git submodule.

## Quick Start

### Cloning
```bash
git clone --recurse-submodules <REPO_URL>
```

### Pointing Firmware to Your Fork
Once you create your own fork of `vedderb/bldc`:
```bash
git submodule set-url SW https://github.com/<YOUR_USERNAME>/bldc.git
git submodule sync
git commit -am "Point SW submodule to personal fork"
```
