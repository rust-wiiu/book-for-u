# Emulator

Utilizing an emulator during the development process offers significant time savings by minimizing the overhead associated with compilation and testing cycles. In particular, when encountering crashes (which are not uncommon, especially when working with advanced features of WUT), restarting an emulator is considerably faster than rebooting a physical console.

Fortunately, a free and open-source Wii U emulator, [**Cemu**](requirements.md#software), is available. This emulator is actively maintained and widely recognized as the standard for Wii U emulation. Cemu facilitates rapid testing and provides valuable debugging capabilities, including memory viewers and call stack inspection, among others. These tools are invaluable for diagnosing and resolving issues that are not immediately apparent. You can [download Cemu here](https://github.com/cemu-project/Cemu/releases) and extract the archive to a convenient directory on your system.

Other emulators like [decaf-emu](https://github.com/decaf-emu/decaf-emu) exist, but we recommend you sticking with Cemu.
