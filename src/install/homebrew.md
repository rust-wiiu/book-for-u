# Homebrew

> [!WARNING]
> Modifying your system carries inherent risks. However, the Wii U homebrew community generally considers the process reasonably safe. If you encounter any issues, do not hesitate to seek assistance from the community.

Currently, [**Aroma**](https://github.com/wiiu-env/Aroma) is the recommended homebrew environment for the Wii U. For installation, we suggest following the comprehensive guide available at [https://wiiu.hacks.guide](https://wiiu.hacks.guide). Numerous other resources, including tutorials on Google and YouTube, are also available.

After successfully installing Aroma, we highly recommend setting up the [Homebrew App Store](https://github.com/fortheusers/hb-appstore). This application streamlines the installation and updating of homebrew software. Any Wii U software recommended within this documentation *should* be accessible through this store. Some essential tools include:

- [**Wiiload Plugin**](./requirements.md#software): This plugin eliminates the need for repeated SD card removal and insertion. It enables direct uploading of executables from your command line interface, avoiding system reboots.
- [**FTPiiU Plugin**](./requirements.md#software): Facilitate the transfer of general files between your PC[^1] and the Wii U using the FTP protocol. This tool also provides the capability to inspect the Wii U's local file system, which can be valuable for debugging purposes.


[^1]: To transfer files between your PC and the Wii U, an FTP client is required. We use [FileZilla](https://filezilla-project.org/) for a GUI and [curl](https://curl.se/) for a CLI, but you are free to use any FTP client that meets your requirements.
