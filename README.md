# Vera — Starter Motor System Controller

Ultra-efficient motor controller hardware and firmware for the **Vera** starter motor system (Shell Eco-marathon ICE Prototype with rebuilt Honda GX35 engine).

---

## Repository Structure

```
Vera/
├── HW/                     # Hardware KiCad design files
│   ├── vera_vesc_starter.kicad_pro    # KiCad project file
│   ├── vera_vesc_starter.kicad_sch    # Top-level hierarchical root schematic
│   ├── vera_vesc_starter.kicad_pcb    # 4-layer PCB layout
│   ├── vera_vesc_starter.kicad_dru    # Custom design rules
│   ├── block1_power_input.kicad_sch   # Sheet 1: Power Input & Bulk DC-Link
│   ├── block2_inverter.kicad_sch      # Sheet 2: 3-Phase Inverter Power Stage
│   ├── block3_drv8323.kicad_sch       # Sheet 3: TI DRV8323RS Gate Driver & 5V Buck
│   ├── block4_standby_ldo.kicad_sch   # Sheet 4: 3.3V Standby LDO
│   ├── block5_stm32f405.kicad_sch     # Sheet 5: STM32F405 Controller Core
│   ├── block6_comm_adc.kicad_sch      # Sheet 6: Comm Port & Protected ADC1
│   ├── block7_hall_temp.kicad_sch     # Sheet 7: Hall Sensors & Temperature
│   └── block8_usb_esd.kicad_sch       # Sheet 8: USB-C Interface & ESD Protection
└── SW/                     # Software: VESC 6 firmware submodule (vedderb/bldc)
```

---

## Hardware (HW)

* **Architecture**: Custom VESC 6-compatible 4-layer motor controller.
* **MCU**: STMicroelectronics STM32F405RGT6.
* **Gate Driver**: Texas Instruments DRV8323RS (SPI control, 3x current shunt amplifiers, integrated buck regulator).
* **Power Stage**: 30V low-$R_{\text{DS(on)}}$ MOSFET 3-phase bridge.
* **CAD Software**: Designed in **KiCad 8 / 9 / 10**.
  * To open the project, launch KiCad and open `HW/vera_vesc_starter.kicad_pro`.

---

## Software (SW)

The `SW` directory tracks the official [VEDDERB BLDC Firmware](https://github.com/vedderb/bldc) as a Git submodule.

### Switching Submodule to Your Personal Fork

Once you fork `vedderb/bldc` to your own GitHub account:

```bash
# Update the submodule URL to your fork
git submodule set-url SW https://github.com/<YOUR_USERNAME>/bldc.git
git submodule sync
git commit -am "Update SW submodule URL to personal fork"
```

### Cloning This Repository

When cloning this repository on a new machine, remember to initialize submodules:

```bash
git clone --recurse-submodules <YOUR_REPO_URL>
```

Or if cloned without `--recurse-submodules`:

```bash
git submodule update --init --recursive
```
