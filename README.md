# Common hardware components for MediaTek devices

## Changes in this fork

This fork is based on
[LineageOS/android_hardware_mediatek](https://github.com/LineageOS/android_hardware_mediatek)
`lineage-24.0` and is used for the LineageOS 24.0 build of the Redmi Pad
(`yunluo`). It adds these commits on top:

- `mediatek: Add lib_driver_cmd_mt66xx WiFi driver library`: cherry-picked
  from [xiaomi-mt6789-devs/android_hardware_mediatek](https://github.com/xiaomi-mt6789-devs/android_hardware_mediatek)
  `lineage-23.0`. The yunluo device tree needs this wpa_supplicant
  driver library, which upstream does not ship.
- `wpa_supplicant_8_lib: Avoid BITS() macro clash with upstream
  wpa_supplicant`: upstream `common.h` now defines `BITS()` with three
  arguments, so the MediaTek two-argument macro was skipped and the build
  failed.
- `PowerOffAlarm: Drop generated_kernel_headers`: the generated kernel
  headers define `struct sched_param` a second time next to Bionic.
  `RtcDriver.cpp` only needs `linux/ioctl.h` and `linux/rtc.h` from
  Bionic.
