Multi Processing Message Example
================================

**Important:** This example's `platformio.ini` contains two configurations:
1. `spresense-Acuity_mainCore` for the main core
2. `spresense-Acuity_subCore1` for the sub core 1

**Both** firmwares must be built and uploaded for this sketch to work. Use the [project tasks](https://docs.platformio.org/en/latest/integration/ide/vscode.html#project-tasks) for each respective environment for this, and switch into the environment you want to work in with the project environment switcher detailed in the last link.

How to build PlatformIO based project
=====================================

1. [Install PlatformIO Core](https://docs.platformio.org/page/core.html)
2. Clone or download this `platform-sonyspresense-Acuity` repository
3. Extract ZIP archive
4. Run these commands:

```shell
# Change directory to example
$ cd platform-sonyspresense-Acuity/examples/arduino-multiprocessing-message

# Build project
$ pio run

# Upload firmware
$ pio run --target upload

# Build specific environment
$ pio run -e spresense-Acuity_mainCore
$ pio run -e spresense-Acuity_subCore1

# Upload firmware for the specific environment
$ pio run -e spresense-Acuity_mainCore --target upload
$ pio run -e spresense-Acuity_subCore1 --target upload

# Clean build files
$ pio run --target clean
```
