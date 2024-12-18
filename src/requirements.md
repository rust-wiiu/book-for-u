# Requirements

This page will give you a short overview of recommended stuff you need to start developing for the Wii U. Required things are marked with an asterics*. More explanations can be found durign the [Installation](./install.md).

## Hardware (Optional)

- Wii U Console
- SD Card
- SD Card Reader

While you don't actually **need** a Wii U console at hand to develop software, it is highly recommended as not everything can be ran on emulators due to stuff not being implemented, having different implementations, etc. Software which runs on an emulator might not work on hardware or vice versa.

## Software

- [Cemu](...)[^1]
- [Rust](...)*
- [cargo-make](...)*
- [DevkitPro](...)*
- [Wiiload](...)

## Skills

- Rust*
- C / C++
- Low Level Software / Debugging

Rust should be quite obvious, since this is a Rust project. So why C / C++? Well, the underlying <abbr title="Software Development Kit">SDK</abbr> is a collection of C libraries. But fear not, you will likely not have to interact with C / C++! It is only needed if you want to go beyond the provided std-like features and venture into unsafe territory. All C functionalities are binded to `extern "C"` functions and can be called by the user. This is most needed by people contributing to this project. For more information take a look at the [motivation](./intro.md#why-rust-on-the-wii-u) and [this part of the hardware page](...).

[^1]: Other emulators like [decaf-emu](https://github.com/decaf-emu/decaf-emu), etc. exist but I highly recommend sticking to Cemu.
