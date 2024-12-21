# Unsafe Territory

> [!IMPORTANT]
> The raw bindings are mostly needed by people contributing to rust-wiiu but there are also usecases where the (current) features are not enough.

As you should know by now, rust-wiiu is more than a wrapper for C libaries - it is a whole rusty abstraction. However, using `wut::bindings`, most C symbols are binded using Rusts FFI, automatically generated via [bindgen](https://docs.rs/bindgen/latest/bindgen/). These FFI functions are `unsafe` by design as the compiler cannot get any garanties on ownership.

Amet pariatur elit amet reprehenderit elit duis.
