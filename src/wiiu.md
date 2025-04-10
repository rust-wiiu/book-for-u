# Wii U Architecture

This document provides essential insights and relevant information about the Wii U platform, specifically tailored for developers. Its purpose is to familiarize you with the system's capabilities and constraints. For those seeking a more comprehensive understanding, a list of detailed resources discussing the platform extensively is provided below.

## Summary

- **CPU: "Espresso" [PowerPC](https://de.wikipedia.org/wiki/PowerPC)**
    - 32-bit architecture
    - Big-endian byte order
- **GPU: "Latte" AMD**
- **Memory: 2 GB DDR3 RAM**
    - 1 GB reserved for the operating system
    - 1 GB available for user applications
- **Operating System: CafeOS**
    - POSIX-like?
    - Supports foreground and background applications
    - Implements threads and scheduling mechanisms
    - Features a separation between user space and kernel space
    - Utilizes virtual memory addressing
    - Includes an OpenGL-like graphics library

## Further Information

- [**Wii U - Wikipedia**](https://de.wikipedia.org/wiki/Wii_U): A general overview of the platform and trivia.
- [**Hardware - WiiUBrew**](https://wiiubrew.org/wiki/Hardware): A concise summary of the Wii U's hardware components.
- [**Wii U Architecture - copetti.org**](https://www.copetti.org/writings/consoles/wiiu/): An in-depth exploration of the Wii U's hardware and software architecture.
- [**Cafe OS - WiiUBrew**](https://wiiubrew.org/wiki/Cafe_OS): Detailed information about the Wii U's operating system, CafeOS.
