# First Homebrew Application

With the development environment now set up, let's examine the fundamental code structure of a basic `rust-wiiu` application. Upon opening the `src/main.rs` file, you will typically find code resembling the following:

```rust
#![no_std]
#![no_main]

use wut;
use wut::prelude::*;
use wut::time::Duration;

#[wut::main(Console)]
fn main() {
    while wut::process::running() {
        println!("{}", wut::time::DateTime::now());
        wut::thread::sleep(Duration::from_secs(1));
    }
}
```

Let's dissect this code snippet part by part to understand its function and significance within the Wii U environment.

### 1. `!#[no_std]` Attribute

The `!#[no_std]` attribute signifies that this Rust code will not link against the standard Rust library (`std`). Unlike typical desktop or server environments, embedded systems like the Wii U require a more minimal runtime environment. The Rust ecosystem provides a tiered approach to library support:

* **`core`:** This is the foundational tier, providing essential language features without any platform-specific dependencies or dynamic memory allocation. Only stack-based memory management is available here.
* **`alloc`:** This tier builds upon `core` and introduces an interface to a memory allocator, enabling dynamic memory allocation capabilities such as `String` and `Vec`. However, it still requires platform-specific implementations for the allocator itself.
* **`std`:** This is the default tier for typical platforms[^1], offering the complete Rust standard library with platform-specific implementations for functionalities like file I/O, networking, and concurrency.

While the Wii U / CafeOS does not have official Rust support in the traditional sense, `rust-wiiu` bridges this gap by providing a custom allocator and implementing many relevant `std` features. This allows developers to leverage their existing Rust knowledge while targeting the Wii U. The `!#[no_std]` attribute informs the compiler and linker about this embedded environment.

### 2. `!#[no_main]` Attribute

The `!#[no_main]` attribute is another embedded Rust macro. It instructs the linker not to generate the conventional `main` function that serves as the program's entry point in standard Rust environments. In embedded systems, the program execution flow often involves platform-specific initialization routines that occur before the user's `main` function would typically be called. In the context of Wii U homebrew development using devkitPro, the toolchain provides its own pre-`main` setup procedures. Therefore, we use `!#[no_main]` to prevent Rust from generating its default `main` entry point.

### 3. `use` Statements

These lines are standard Rust import statements, bringing specific modules and types into the current scope for easier use.

* `use wut;`: Imports the top-level `wut` crate, which contains the Wii U-specific functionalities provided by `rust-wiiu`.
* `use wut::prelude::*;`: Imports commonly used items from the `wut` prelude. This is a convention to bring frequently used types and traits into scope for convenience.
* `use wut::time::Duration;`: Imports the `Duration` type specifically from the `wut::time` module, representing a span of time.

It's worth noting that `wut::time::Duration` is semantically equivalent to `std::time::Duration`. Both are ultimately re-exports of `core::time::Duration`, which houses the fundamental implementation. The `wut` crate, like `std`, re-exports parts of the `core` module for a more unified and accessible API.

### 4. `!#[wut::main(Console)]` Attribute

This macro performs platform-specific initialization tasks that enhance the development experience by mimicking a more standard environment. While not strictly necessary for the program to execute, it provides conveniences such as initializing a logging mechanism and ensuring a cleaner program exit. You can consult the `rust-wiiu` documentation for a comprehensive understanding of its functionality. This macro can be replaced with custom initialization code if needed.

The `Console` attribute passed to the `wut::main` macro is particularly important for early development and debugging. It configures the system to output log messages and `println!` statements to an on-screen console. Be aware that this on-screen console output may conflict with any graphical rendering you implement later in your application. The `Console` attribute can be omitted, changed to a different logger type, or combined with other logging configurations as detailed in the `rust-wiiu` documentation.

### 6. `while wut::process::running() {…}` Loop

This is the primary execution loop of the application. The code within this loop will continue to execute indefinitely until the application is terminated. An alternative, but functionally similar, way to write this loop is:

```rust
loop {
    if !wut::process::running() {
        break;
    }
}
```

A crucial aspect of this loop is the frequent call to `wut::process::running()`. This function checks if the application is still running in the foreground. It is essential for the proper functioning of the foreground release mechanism, specifically the HOME button. When the HOME button is pressed, the system relies on this check to move the application out of the foreground. Therefore, if the main thread within this loop becomes blocked for an extended period without calling `wut::process::running()`, the application may become unresponsive to the HOME button.

### 7. `println!(…)` Macro

The `println!()` macro is used for printing formatted text to the console. While typically defined in the standard library (`std`), in this `no_std` environment, its functionality is provided by the `wut` crate and is set up by the `wut::main(Console)` macro. It is part of the commonly used items imported via `wut::prelude::*`.

### 8. `wut::time::DateTime::now() & wut::thread::sleep()` Functions

These are examples of standard library-like features that have been implemented within the `wut` crate to provide familiar functionalities in the embedded Wii U environment. They are designed to behave similarly to their counterparts in the standard Rust library, offering time-related operations and thread pausing capabilities.

[^1]: For a comprehensive list of officially supported Rust platforms, please refer to the [Rust Platform Support documentation](https://doc.rust-lang.org/nightly/rustc/platform-support.html).
