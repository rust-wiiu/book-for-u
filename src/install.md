# Installation

## Homebrew

While you **don’t need a Wii U console** to develop software, having one is highly recommended. Not everything can run perfectly on emulators due to incomplete implementations, differences in behavior, or other quirks. Software that works on an emulator may fail on actual hardware, and vice versa. At the time of writing, the preferred homebrew environment for the Wii U is **Aroma**. To install it, I recommend following [this guide](https://wiiu.hacks.guide), though there are plenty of other resources available on Google, YouTube, and elsewhere.

Once you’ve set up Aroma, I suggest installing the [Homebrew App Store](https://github.com/fortheusers/hb-appstore). This tool simplifies the process of installing and updating homebrew software. Any Wii U software I recommend *should* be available through this store. Some essential tools include:

- **[Wiiload Plugin](./requirements.md#software):** Avoid the hassle of repeatedly ejecting and reinserting the SD card. This tool allows you to upload `.rpx` or `.wuhb` files directly from the command line without requiring a reboot.
- **[FTPiiU Plugin](./requirements.md#software):** Transfer generic files between your PC[^1] and the Wii U via FTP. This tool also allows you to inspect the local file structure, which can be invaluable for debugging.

## Development

> [!TIP]
> If you’re a Windows user, I highly recommend trying [Windows Subsystem for Linux (WSL)](https://learn.microsoft.com/windows/wsl/about) for development (even beyond this project). WSL simplifies workflows significantly, blending Windows and Linux environments seamlessly. IDEs like VSCode offer excellent WSL integration. 

### Emulator

Using an emulator during development can save you a lot of time. It significantly reduces the time spent switching between compiling and testing. When crashes inevitably happen (especially while working with the more advanced features of WUT), restarting an emulator is far quicker than rebooting a physical console.

Luckily, there’s a free and open-source emulator for the Wii U called **[Cemu](requirements.md#software)**, which is actively maintained and widely regarded as the standard for Wii U emulation. It allows for faster testing and offers useful debugging features like memory viewers, call stack inspection, and more. These tools are invaluable for troubleshooting issues that aren’t immediately obvious. You can [download Cemu here](https://github.com/cemu-project/Cemu/releases) and extract it to a convenient location on your system.

### DevkitPro

[DevkitPro](https://devkitpro.org/) is the backbone of Wii U homebrew development (and supports platforms like the GBA, DS, GameCube, Wii, and Switch). It provides a set of toolchains that enable you to compile code for specific Nintendo platforms. For Wii U development, you’ll need the **devkitPPC (PowerPC)** toolchain.

To install it, follow the [Getting Started](https://devkitpro.org/wiki/Getting_Started) guide on their website. After setting up `dkp-pacman`, install the necessary `wiiu-dev` package with the following command:

```bash
sudo dkp-pacman -S wiiu-dev
```

### Rust

All you need is an up-to-date Rust installation; everything else is provided by the other tools. You can set up Rust by following the [official installation guide](https://www.rust-lang.org/tools/install).

[^1]: If you need to transfer files between your PC and the Wii U, you’ll need an FTP client. I personally use [FileZilla](https://filezilla-project.org/), but you can use any client that suits your needs.
