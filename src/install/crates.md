# Crates within `rust-wiiu`

The `rust-wiiu` project is structured as a collection of interconnected crates (Rust's package management units). These crates serve various purposes:

- **Fundamental Toolchain Crates:** These provide the core building blocks for Wii U development, such as [rust-wiiu/wut](https://github.com/rust-wiiu/wut) and [rust-wiiu/wups](https://github.com/rust-wiiu/wups).
- **C Library Wrappers:** These crates encapsulate and extend the functionality of existing C libraries, offering a safer and more idiomatic Rust interface. Examples include [rust-wiiu/notifications](https://github.com/rust-wiiu/notifications) and [rust-wiiu/kernel](https://github.com/rust-wiiu/kernel).
- **Pure Rust Crates:** These are newly developed crates written entirely in Rust and do not rely on pre-existing C code.

From a developer's perspective, all these crates are used in the same way. However, understanding their underlying nature can be helpful when troubleshooting errors, particularly during the compilation phase.

While it is technically possible to install these crates in arbitrary locations, it would necessitate manual configuration adjustments and is generally not recommended. Instead, the suggested approach is to create a dedicated parent directory to house all `rust-wiiu` code. This facilitates easier access to files across different crates using relative paths. (Note: The feasibility of utilizing Cargo's Git dependencies for this purpose is currently under investigation.)

Once you have created a parent folder in your preferred location, you can obtain any of the provided crates by cloning their respective repositories into this directory. For example, to get the `wut` crate, you would execute the following command:

```bash
git clone https://github.com/rust-wiiu/wut.git
```
