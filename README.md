# nabu-touchscreen

**English** | 中文

Novatek NT36523 SPI touchscreen support for the Xiaomi Pad 5 (`nabu`, CSOT
panel), with pen input support.

This is a direct source overlay, like the other `nabu-*` repositories: kernel
files keep their original relative paths and are copied over a chosen kernel
baseline by `nabu-main`.

## Contents

```text
kernel-overlay/
├── drivers/input/touchscreen/Kconfig                  # source nt36523/Kconfig
├── drivers/input/touchscreen/Makefile                 # obj-... += nt36523/
└── drivers/input/touchscreen/nt36523/
    ├── Kconfig, Makefile
    ├── nt36xxx.c, nt36xxx.h
    ├── nt36xxx_fw_update.c
    └── nt36xxx_mem_map.h
```

Builds `drivers/input/touchscreen/nt36523/nt36523_ts.ko`
(`CONFIG_TOUCHSCREEN_NT36523_SPI=m`).

## Notes

- The driver is a full new subdirectory rather than a patch to an existing
  driver, so the overlay only adds files plus two one-line Kconfig/Makefile
  hooks.
- The panel sends a DRM notify on power on/off; that notifier lives in
  `nabu-display`, and the touchscreen node is in `nabu-platform`.
