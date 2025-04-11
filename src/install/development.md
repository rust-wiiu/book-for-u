# Development

## Docker

To ensure a consistent and reproducible build environment for `rust-wiiu` projects, a Docker image is available on the [rust-wiiu/build](https://github.com/rust-wiiu/build) repository. Leveraging this Docker image eliminates the "It works on my machine" problem and mitigates potential issues arising from version discrepancies and differing local configurations.

By utilizing Docker, developers can build `rust-wiiu` code with only Docker installed on their system. For detailed instructions and further information on using this Docker image, please refer to the README file within the repository.

## Local Install

> [!TIP]
> For developers working on Windows, utilizing the [Windows Subsystem for Linux (WSL)](https://learn.microsoft.com/windows/wsl/about) is highly recommended. WSL significantly streamlines development workflows by providing a seamless integration of Windows and Linux environments. Popular IDEs such as VSCode offer excellent [support for WSL](https://code.visualstudio.com/docs/remote/wsl).

For developers intending to engage in Wii U homebrew development on an ongoing basis, establishing a local development environment is recommended. The following setup instructions primarily target Linux and Windows Subsystem for Linux (WSL) environments. Installation guides for the respective tools on other operating systems can be found on their official websites. Refer to the [rust-wiiu/build](https://github.com/rust-wiiu/build) repository for the currently supported versions of key build dependencies.

### DevkitPro

[DevkitPro](https://devkitpro.org/) serves as the foundational toolchain for Wii U homebrew development, with additional support for other Nintendo platforms such as the GBA, DS, GameCube, Wii, and Switch. It provides essential toolchains for compiling code targeting specific Nintendo consoles. For Wii U development, the **devkitPPC (PowerPC)** toolchain is required.

To install DevkitPro, please follow the comprehensive [Getting Started](https://devkitpro.org/wiki/Getting_Started) guide available on their website. Once `dkp-pacman` is configured, install the necessary `wiiu-dev` package using the following command in your terminal:

```bash
sudo dkp-pacman -S wiiu-dev
```

### Rust

An up-to-date installation of the Rust programming language is required. You can set up Rust by adhering to the [official installation guide](https://www.rust-lang.org/tools/install). After installation, verify the Rust version and confirm successful installation by executing the following command:

```bash
cargo --version
```

### cargo-make

[cargo-make](https://github.com/sagiegurari/cargo-make) is a versatile task runner that uses a simple TOML configuration to define and execute multi-platform build scripts by a single command. It is used to hide the more complex build- and linking commands.

```bash
cargo install cargo-make
```

### cargo-generate

Optional! [cargo-generate](https://github.com/cargo-generate/cargo-generate) is a utility that facilitates starting new projects from predefined templates instead of creating empty Cargo projects. While this functionality can be achieved through a few manual commands, cargo-generate can streamline the initial project setup.

```bash
cargo install cargo-generate
```
