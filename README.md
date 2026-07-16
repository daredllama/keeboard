# Keeboard

<img width="1150" height="618" alt="image" src="https://github.com/user-attachments/assets/c717068c-f5ed-40c0-a476-841f8fbb7b65" />

A custom 75%-layout mechanical keyboard, with per-key backlighting, a rotary encoder, a OLED status display, and RMK (Rust) firmware on an RP2040 (Raspberry Pi Pico).

---

## Features

- **79-keys** (78 keys + integrated rotary encoder pushbutton)
- **Per-key backlighting** — SK6812 Mini LEDs, one per switch
- **Rotary encoder** (EC11) — rotation bound to volume, click bound to OLED toggle
- **128×64 I2C OLED** - status display 
- **RMK firmware** (Rust) running on RP2040
- **Sandwich mount** case, plate-mount stabilizers, Cherry MX-compatible switches

---

## Hardware

| Component | Spec |
|---|---|
| MCU | Raspberry Pi Pico (RP2040) |
| Switches | Cherry MX-compatible |
| LEDs | SK6812 Mini, ~79x, per-key |
| Diodes | 1N4148WS (SOD-323) |
| Decoupling caps | 100nF ceramic, 0402 |
| Encoder | EC11 |
| Display | 128×64 I2C OLED (0.96") |
| Stabilizers | Cherry-style plate-mount — 2u (Backspace, Enter, LShift), 6.25u (Spacebar) |

## Plate / Case

- Case screws: M3

<img width="1330" height="626" alt="image" src="https://github.com/user-attachments/assets/91f2b051-d033-44b2-9669-ef64e3c65856" />

## Pin Mapping (RP2040 / Pico)

| Function | GPIO |
|---|---|
| Columns (col0–col14) | GPIO0, 9, 7, 12, 13, 3, 14, 20, 17, 6, 16, 5, 4, 2, 21 |
| Rows (row0–row5) | GPIO15, 11, 10, 8, 1, 22 |
| Encoder A / B | GPIO18 / GPIO19 |
| LED data | GPIO26 |
| OLED SDA / SCL | GPIO27 / GPIO28 |

<img width="834" height="1100" alt="image" src="https://github.com/user-attachments/assets/b5bd4e81-3009-425d-b305-2563d494aac3" />

<img width="1402" height="1064" alt="image" src="https://github.com/user-attachments/assets/e5f1f331-342b-4f87-b700-87533cb58bef" />

<img width="1906" height="1114" alt="image" src="https://github.com/user-attachments/assets/8283270f-32fb-458b-9d6a-62d781b2ef1f" />

<img width="2248" height="1030" alt="image" src="https://github.com/user-attachments/assets/b027b0d2-9741-496e-88dd-1f40855b5fd0" />

<img width="1886" height="934" alt="image" src="https://github.com/user-attachments/assets/f8c15014-eec1-4980-8a6f-8939a4f4b1ac" />


## Firmware

**Flashing:**
1. Hold the Pico's BOOTSEL button while plugging it in via USB
2. `cargo run --release`
   (uses `elf2uf2-rs` by default — install once with `cargo install elf2uf2-rs`)

**Keymap:** defined in `keyboard.toml` under `[layout].keymap`. 3 layers:
- **Layer 0** — base QWERTY layout matching the F75 layout
- **Layer 1** — Fn layer, RGB controls (mode/brightness on arrow keys)
- **Layer 2** — reserved

## PCB / Assembly Notes

- LEDs are intended to be **reverse-mounted** (bottom side, shining through a PCB cutout) — assembled and soldered by hand, **not** included in the JLCPCB assembly BOM/CPL

## Reflection

For this build, I really challenged myself with tedious ahh work. Even though that making this board was quite tedious, it was a good learning experience,
espcially since this is my first-ever keyboard. I wanted to add a OLED screen so that I could have cool animations or somthing moving on the keyboard while 
I typed. I learned many things form this project, such as how tedious it is to put per-key LEDS for every key. That might have been a mistake. But, I also
learned how to edit/make footprints. 
