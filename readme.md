# yaw-kb Firmware

ZMK firmware for the yaw-kb custom keyboard featuring:
- NRF52840 MCU (HOLYIOT-18010 module)
- 10x7 key matrix (62 keys + encoder button)
- Alps EC11 rotary encoder
- Cirque trackpad (I2C)
- USB and BLE connectivity
- ZMK Studio support

## Building

This project uses GitHub Actions for builds. Push to trigger a build, or build locally with:

```
west build -s zmk/app -b yaw-kb -- -DZMK_CONFIG="$(pwd)/config" -DCONFIG_ZMK_STUDIO=y -Dsnippet=studio-rpc-usb-uart
```

## Layers

| Layer | Activation | Purpose |
|-------|-----------|---------|
| 0 - Default | Always active | Alpha keys, numbers, modifiers |
| 1 - Lower | Hold Enter | F-keys, symbols, shifted numbers |
| 2 - Raise | Hold Space | Navigation, media, BT, bootloader, studio unlock |
| 3 - Adjust | Lower + Raise | BT management, system controls |

## Changelog

- Removed RGB underglow bindings (no RGB hardware configured)
- Added `&bootloader` and `&studio_unlock` to config keymap (previously only in board keymap, overridden)
- Fixed duplicate `CONFIG_ZMK_SLEEP` in defconfig
- Fixed missing `default y` for `ZMK_BATTERY_VOLTAGE_DIVIDER` in Kconfig
- Removed invalid `zmk,encoder` and `zmk,pointing_device` chosen properties from DTS
- Added encoder feature to zmk.yml metadata
