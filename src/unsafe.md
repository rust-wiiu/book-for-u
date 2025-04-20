# Exploring Unsafe Territory

> [!IMPORTANT]
> While the raw bindings are primarily intended for contributors to `rust-wiiu`, there are scenarios where the currently available high-level features may not suffice, necessitating their use.

As you've likely gathered by now, `rust-wiiu` aims to be more than just a thin wrapper around C libraries; it provides a comprehensive, Rusty abstraction layer for Wii U development. However, for situations requiring direct interaction with the underlying system or when higher-level abstractions are insufficient, `rust-wiiu` exposes raw bindings to most C symbols through the `wut::bindings` module. These bindings are automatically generated using [bindgen](https://docs.rs/bindgen/latest/bindgen/), leveraging Rust's Foreign Function Interface (FFI).

It is crucial to understand that these FFI functions are inherently marked as `unsafe` in Rust. This is because the Rust compiler cannot provide any guarantees regarding memory safety, ownership, or the behavior of the external C code being called. When interacting with these raw bindings, it is the developer's responsibility to ensure the correctness and safety of the operations performed.

TODO: Refer to the wut docs and explain an example using the C ABI
