# Requirements

This page provides a brief overview and checklist of recommended items for starting Wii U development. Required items are marked with an asterisk (*). Detailed explanations can be found in the [Installation](./install.md) section.

## Software

- [Cemu](https://cemu.info)[^1]
- [Rust](https://www.rust-lang.org/)*
- [cargo-make](https://github.com/sagiegurari/cargo-make)*
- [DevkitPro](https://devkitpro.org/)*
- [Aroma](https://wiidatabase.de/wii-u-downloads/hacks/aroma/)
- [Wiiload Plugin](https://github.com/wiiu-env/wiiload_plugin)
- [FTPiiU Plugin](https://github.com/wiiu-env/ftpiiu_plugin)

## Skills

- Rust*
- C / C++[^2]
- Debugging

## Hardware

- Wii U Console
- SD Card
- SD Card Reader

[^1]: Other emulators like [decaf-emu](https://github.com/decaf-emu/decaf-emu), etc. exist but I highly recommend sticking to Cemu.
[^2]: Why C/C++? The underlying SDK is built on C libraries, but you likely won't need to interact with them directly unless you go beyond the provided std-like features into unsafe territory. Most C functions are bound to `extern "C"` and can be called directly, requiring some knowledge of the C calling convention—especially for contributors to this project.
