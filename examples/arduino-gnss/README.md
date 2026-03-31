How to build PlatformIO based project
=====================================

1. [Install PlatformIO Core](https://docs.platformio.org/page/core.html)
2. Clone or download this `platform-sonyspresense-Acuity` repository
3. Extract ZIP archive
4. Run these commands:

```shell
# Change directory to example
$ cd platform-sonyspresense-Acuity/examples/arduino-gnss

# Build project
$ pio run

# Upload firmware
$ pio run --target upload

# Build specific environment
$ pio run -e spresense-Acuity

# Upload firmware for the specific environment
$ pio run -e spresense-Acuity --target upload

# Clean build files
$ pio run --target clean
```
