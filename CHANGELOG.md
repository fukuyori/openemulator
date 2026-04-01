# Changelog

All notable changes to this fork of OpenEmulator are documented in this file.

## 1.0.7 - 2026-04-02

### Added

- Added a Japanese usage guide in [USAGE_ja.md](USAGE_ja.md).
- Added fork-specific license wording to the README.
- Added ignore rules for generated disk images and local derived-data artifacts.

### Changed

- Updated the application version from `1.0.6` to `1.0.7`.
- Updated the Xcode project to use Apple Silicon Homebrew paths under `/opt/homebrew`.
- Prepared the macOS app for local release packaging as a forked build.

### Fixed

- Fixed modern AppleClang/C++11 narrowing errors in `libemulation` so the project builds on the current macOS toolchain.
- Fixed missing dependency lookup for Homebrew-installed libraries during Xcode builds.
- Fixed the macOS build flow so `OpenEmulator.app` can be produced successfully in this environment.
- Fixed Apple IIe composite color rendering so new Apple IIe emulations now show expected blue/orange artifact colors in titles such as Lode Runner.
- Fixed the composite decoder implementation so `Composite Y'IQ` uses a real YIQ decode matrix instead of falling back to the YUV path.
- Fixed Apple IIe default monitor presets to use an AppleColor-style composite configuration with `Composite Y'IQ` and a neutral hue baseline.

### Packaging

- Built a macOS release application bundle: `OpenEmulator.app`
- Built a macOS distribution disk image: `OpenEmulator-1.0.7.dmg`
