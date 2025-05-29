# Requirements

This page provides a brief overview and checklist of recommended items to begin Wii U development. Required items are marked with an asterisk (*). For more comprehensive explanations, please refer to the [Installation](./install.md) section.

## Software

- [Cemu](https://cemu.info)
- [Rust](https://www.rust-lang.org/)*
- [cargo-make](https://github.com/sagiegurari/cargo-make)*
- [cargo-generate](https://github.com/cargo-generate/cargo-generate)
- [DevkitPro](https://devkitpro.org/)*
- [Aroma](https://wiidatabase.de/wii-u-downloads/hacks/aroma/)
- [Wiiload Plugin](https://github.com/wiiu-env/wiiload_plugin)
- [FTPiiU Plugin](https://github.com/wiiu-env/ftpiiu_plugin)

## Skills

- Rust*
- C / C++
- Debugging [^1]

This guide assumes a foundational understanding of the Rust programming language. It will not cover Rust basics, as numerous excellent [free resources](./faq.md#how-to-learn-rust) are readily available. However, concepts related to `no_std` environments will be briefly introduced and explained as they arise.

While the underlying SDK is built upon C libraries, direct interaction with them will generally not be necessary unless you intend to extend beyond the provided standard library-like features and venture into [unsafe FFI Rust](./unsafe.md). Most C functions are bound using `extern "C"` and can be called directly which requires some understanding of the C calling convention / ABI. This should be mainly relevant for contributors to this project.

## Hardware

- Wii U Console
- SD Card
- SD Card Reader

While a physical Wii U console is **not strictly required** for development, it is strongly recommended. Emulators, while valuable, may not accurately replicate the behavior of all application types or features due to incomplete implementations, inherent differences, or other platform-specific quirks. Consequently, software that functions correctly on an emulator may encounter issues on actual Wii U hardware, and vice versa.

[^1]: While debugging tools like the Cemu PPC Debugger can be useful in certain situations, the Rust compiler is generally effective at catching many potential issues during the development process. <!-- GDB stub?  -->
