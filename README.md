# Temper ZMK Config

My personal [ZMK](https://zmk.dev/) firmware config for the [Temper](https://github.com/raeedcho/temper) — a 36-key wireless split keyboard (3×5 + 3 thumb keys per half).

## Hardware

- 2× [nice!nano v2](https://nicekeyboards.com/nice-nano/) controllers (wireless BLE split)
- SSD1306 128×32 OLED on each half
- Left half is the split **central**

## Firmware

- ZMK pinned to **v0.3.0** (see [`config/west.yml`](config/west.yml) and [`.github/workflows/build.yml`](.github/workflows/build.yml))
- Swedish locale via [joelspadin/zmk-locales](https://github.com/joelspadin/zmk-locales) (`SV_*` keycodes)
- Built automatically by GitHub Actions on every push

## Layout

Swedish QWERTY base, tuned for programming and text editing.

### Layers

| # | Layer | Access |
|---|-------|--------|
| 0 | Default (QWERTY) | — |
| 1 | Num | hold right thumb |
| 2 | Nav | hold right thumb |
| 3 | Sym | hold left thumb |
| 4 | Fun | Nav + Sym held together (conditional) |

### Combos (default layer)

| Keys | Output |
|------|--------|
| U + I | å |
| J + K | ä |
| M + , | ö |
| D + F | Backspace |
| C + V | Enter |

### Highlights

- **Mod-morphs** on the base layer: `,`/`;`, `.`/`:`, `?`/`!`, `-`/`_`, and a smart shift that turns into Caps Word.
- **Nav layer** built for editing: sticky mods (Shift / Ctrl / Alt / Gui) on the left home row combine with the arrows, Home/End and Page Up/Down on the right, plus a one-tap clipboard cluster (undo / cut / copy / paste / redo) on the `Z X C V B` positions.
- **Num layer**: one-handed right-hand numpad with decimal point, comma and minus in the inner column.
- **Sym layer**: brackets, braces and parentheses stacked vertically on the left hand.

![Temper Keymap](keymap_img/temper.svg)

## Battery

Both halves report their battery level over BLE — the central (left) half proxies the peripheral's level via `CONFIG_ZMK_SPLIT_BLE_CENTRAL_BATTERY_LEVEL_PROXY` and `CONFIG_ZMK_SPLIT_BLE_CENTRAL_BATTERY_LEVEL_FETCHING`. Windows only shows a single level in its own UI, so use a tray app such as [zmk-battery-center](https://github.com/kot149/zmk-battery-center) to see both halves.

## Building & flashing

Push to `main` → GitHub Actions builds the firmware → download the artifacts from the run and flash each half.
