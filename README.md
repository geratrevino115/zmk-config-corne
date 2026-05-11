# zmk-config-corne

ZMK firmware config for a Corne (CRKBD) split keyboard running on nice!nano v2 with nice!view displays.

## Hardware

| Part | Model |
| --- | --- |
| Keyboard | Corne (CRKBD) 6-column |
| Controller | nice!nano v2 (×2) |
| Display | nice!view (×2) |

## Layers

The keymap has two parallel stacks — Mac (default on boot) and Windows. Switch between them via the Function layer.

| Index | Name | How to reach |
| --- | --- | --- |
| 0 | Mac — Default | boot |
| 1 | Mac — Code | right thumb (hold) |
| 2 | Mac — Number | left thumb (hold) |
| 3 | Mac — Numpad | Number + Code simultaneously |
| 4 | Mac — Function | Numpad + hold |
| 5 | Windows — Default | Mac Function → `to 5` |
| 6 | Windows — Code | right thumb (hold) |
| 7 | Windows — Number | left thumb (hold) |
| 8 | Windows — Function | Windows Number + Code |

## Building & flashing

Firmware is built automatically on every push via GitHub Actions. To get your `.uf2` files:

1. Push changes to `main`
2. Go to **Actions** → latest run → **Artifacts** → download `firmware`
3. Put each half into bootloader mode (double-tap reset)
4. Drag the matching `.uf2` onto the USB drive that appears

If Bluetooth pairing is acting up, flash `settings_reset.uf2` to both halves first (with the keyboard unpaired from all devices), then re-flash the normal firmware.

## Customization

| File | What to edit |
| --- | --- |
| `config/corne.keymap` | Key bindings, layers, macros, behaviors |
| `config/corne.conf` | Kconfig options (sleep timeout, keyboard name, RGB, OLED) |
| `build.yaml` | Which firmware variants CI produces |
| `config/west.yml` | ZMK version / external modules |

## Display

Uses [nice-view-battery](https://github.com/infely/nice-view-battery) — shows battery level, active layer, Bluetooth status, and active profile.

To invert colors (white on black), add to `config/corne.conf`:
```
CONFIG_NICE_VIEW_WIDGET_INVERTED=y
```
