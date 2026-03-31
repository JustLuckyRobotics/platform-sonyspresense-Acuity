# Sony SPRESENSE-Acuity PlatformIO Platform

PlatformIO integration for Sony Spresense with Acuity branding, a bundled Sony Arduino/SDK `v3.4.5` baseline, and direct support for using this fork from a git platform URL.

## What is bundled

* Sony Spresense Arduino core content from `v3.4.5`
* Sony Spresense SDK prebuilt binaries from `v3.4.5`
* Sony Spresense upload/build tools from `v3.4.5`
* `spresense-Acuity` board id, with legacy `spresense` kept as a compatibility alias

Sony added Arduino-side IMU Add-on driver support in `v3.4.0` on February 28, 2025. This fork ships `v3.4.5`, so it is above that minimum IMU-capable baseline.

## Recommended project setup

Use this fork directly from a firmware project's `platformio.ini`:

```ini
[env:spresense-Acuity]
platform = https://github.com/<your-github-user>/platform-sonyspresense-Acuity.git
board = spresense-Acuity
framework = arduino
monitor_speed = 115200
```

If you prefer a global install:

```sh
pio pkg install -g -p https://github.com/<your-github-user>/platform-sonyspresense-Acuity.git
```

## Included examples

The example projects inside this repo use `platform = file://${PROJECT_DIR}/../..` so they build directly against the checked-out platform without requiring a separate global install.

Examples currently included:

* `examples/arduino-blink`
* `examples/arduino-gnss`
* `examples/arduino-multiprocessing-message`
* `examples/arduino-mp3-decoder-installer`
* `examples/arduino-mp3-player`

## Special targets

This platform provides the Arduino-style `erase` and `bootloader` targets:

```sh
pio run -t erase
pio run -t bootloader
```

`erase` clears the application images. `bootloader` flashes the bundled Sony firmware set such as `loader.espk`, `gnssfw.espk`, `dnnrt-mp.espk`, `AESM.espk`, and `sysutil.spk`.

## Bootloader note for `v3.4.1+`

Sony marked the `v3.4.1` release on March 14, 2025 and the `v3.4.3` release on June 3, 2025 as requiring a new bootloader before use. If your board is still on an older bootloader, run the `bootloader` target once before expecting `v3.4.5` firmware uploads to behave correctly.

## Linux upload dependency

This platform still uses Sony's `flash_writer.py` for serial upload, erase, and bootloader tasks. On Linux, install the GUI dependency first:

```sh
sudo apt-get install -y libgtk-3-dev python3-wxgtk4.0
```

That allows the later `pip install wxPython` step to succeed when PlatformIO first needs the uploader's Python dependencies.

## Build settings

The same Arduino build knobs supported by the Spresense Arduino IDE can be expressed in `platformio.ini`.

### Debug

```ini
; Release is the default
build_flags = -DPIO_FRAMEWORK_ARDUINO_ENABLE_DEBUG
```

### Core selection

```ini
; Main core is the default
build_flags = -DPIO_FRAMEWORK_ARDUINO_CORE_SUB_CORE_1
```

Other subcores are available through:

* `-DPIO_FRAMEWORK_ARDUINO_CORE_SUB_CORE_2`
* `-DPIO_FRAMEWORK_ARDUINO_CORE_SUB_CORE_3`
* `-DPIO_FRAMEWORK_ARDUINO_CORE_SUB_CORE_4`
* `-DPIO_FRAMEWORK_ARDUINO_CORE_SUB_CORE_5`

### Memory size

```ini
; 1.5 MB application region
board_upload.maximum_size = 1572864
board_upload.maximum_ram_size = 1572864
```

### Upload settings

```ini
upload_speed = 921600
upload_port = COM7
```

### Example configuration

```ini
[env:spresense-Acuity]
platform = https://github.com/<your-github-user>/platform-sonyspresense-Acuity.git
board = spresense-Acuity
framework = arduino
build_flags =
  -DPIO_FRAMEWORK_ARDUINO_ENABLE_DEBUG
  -DPIO_FRAMEWORK_ARDUINO_CORE_SUB_CORE_1
board_upload.maximum_size = 1572864
board_upload.maximum_ram_size = 1572864
upload_speed = 921600
upload_port = COM7
monitor_speed = 115200
```
