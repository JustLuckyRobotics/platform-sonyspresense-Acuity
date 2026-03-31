# Bundled Sony v3.4.5 Content

This fork vendors the Sony Spresense `v3.4.5` release content directly so the
PlatformIO platform can be consumed from a git URL without depending on the old
external helper package repos.

Bundle sources:

* `framework-arduinosonyspresense-Acuity`
  * Copied from `Arduino15/packages/SPRESENSE/hardware/spresense/1.0.0`
  * Source repo: `sonydevworld/spresense-arduino-compatible`
  * Source tag: `v3.4.5`
* `tool-spresense-Acuity`
  * Copied from `Arduino15/packages/SPRESENSE/tools/spresense-tools/1.0.0`
  * Source repo: `sonydevworld/spresense-arduino-compatible`
  * Source tag: `v3.4.5`
* `tool-arduinosonyspresensesdk-Acuity`
  * Extracted from the official release asset `spresense-sdk-v3.4.5.tar.gz`
  * Source repo: `sonydevworld/spresense-arduino-compatible`
  * Source tag: `v3.4.5`
  * The top-level `spresense/` directory was stripped during extraction so the
    local builder paths match the PlatformIO layout expected by this fork
