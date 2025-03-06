# Getting Started

Now that everything is setup, we can start creating our dream software.

## 1. Create new project

### cargo-generate (Recommended)

```bash
cargo-generate rust-wiiu/application-template
```

Running this command will open a simple CLI to help you setup the project.

### git

`Use this template` button on github to copy the template to a new repository. Add the projects name as the new repos name and clone it to your machine (of course replacing <Username> & <Project> appropietly)

```bash
git clone https://github.com/<Username>/<Project>.git
```

You will need to modify `Cargo.toml` by changing `{{project-name}}` and `{{authors}}` to appropiet values.

## 2. It is alive!

You can now try to compile and run the program for the first time. When everything is setup correctly you should be able to call the following command to compile the program.

```bash
cargo-make --xx production rpx
```

If everything works and you get no compile error you can find your program at `/target/powerpc-none-eabi/release/<Project>.rpx`. You can open Cemu, click Load, select the .rpx file and (hopefully) see it running. For more information about the [different file formats](), take a look at the documentation.

Congratulations, you now are able to write Wii U software using Rust.

## Let's get into it

So now that we know everything is working, we can take a look at the underlying code and explore the parts of the system. When you open the `src/main.rs` file it will look something like this:

```rust
!#[no_std]
!#[no_main]

use wut;
use wut::prelude::*;
use wut::time::Duration;

#[no_mangle]
fn main() {
    wut::process::default();

    while wut::process::running() {
        println!("{:?}", wut::time::now());
        wut::thread::sleep(Duration::from_secs(1));
    }

    wut::process::exit();
}
```

Let's digest this code part by part:

#### 1. `!#[no_std]`

The Wii U / CafeOS does now have official Rust support; who could have guessed? Rust, by default, assumes that you are on a "typical" platform like x86-linux, ARM-windows, AppleSilicon, etc[^1]. There exist 3 stages of features programmers can use with Rust: core, alloc, std. This enabled Rust to be used at every level of the software stack; from bootloaders to websites.

std is the "default" and used when on a typical platform and provides the entire Rust std library with platform specific implemtations. So no matter if you are on a UNIX or Windows system, `std::path` will just work. alloc is one level lower and provides a interface to and allocator. This basically means that the system has a heap and can make use of dynamic allocations (malloc, strings, vectors, ...). However, as this still requires some platform dependent code, a even lower level exist: core. Here, only base Rust functions exist (no platform dependence or dynamic allocations); meaning only stack-based memory can be used.

So wait a minutes, does this mean at rust-wiiu doesn't even support `String`?! Calm down, rust-wiiu is way more close to a official supported platform (in form of programmer usage) than that might suggest. rust-wiiu defines a custom allocator and implements most of the relevant std-features, so you can use existing Rust knowledge. Still, the compiler/linker has to be informed about this "unusual environment".

#### 2. `!#[no_main]`

Also an embedded rust macro. This special macro tells the linker to not create a main function. This is needed because the `fn main()` isn't the first thing that get's ran during program execution. Lots of other functions run beforehand, to setup heaps, forward arguments, etc. devkitPro has it's own pre-main instructions, so we need to tell Rust to not do it's otherwise useful magic.

#### 3. `use ...`

These are your well known Rust import statements. Nothing unusual about them. The "wut" library contains the functionalities of rust-wiiu and `prelude::*` is to "import common stuff"[^2].

It should be mentioned that `wut::time::Duration` is the **same** thing as `std::time::Duration`. Both are just reexports of `core::time::Duration`, which contains the actual implementations. Wut, like std, exports the entire `core` module for convinience and a single point of access.

#### 4. `!#[no_mangle]`

This macro is commonly used when interacting with forein functions, e.g. functions compiled in C[^3]. It disables [Name Mangeling](https://wikipedia.org/wiki/Name_mangling), which is a technique to make function names truly unique by changing them at compile time. This is normally not a problem (and actual wanted), but the devkitPro toolchain searches for a symbol named "main" during compiling/linking, so mangeling this name will make the main function indetectable.

#### 5. `wut::process::default()`

This function sets up some functionalities for wut. It does some thing similar, but not exlusively, to the stuff that would run pre-main. There are some configuration you could do by running `wut::process:new()` instead, but you can read the documentation for that. For now, it is required and you can mostly just ignore it.

#### 6. `while wut::process::running() {…}`

This is what in game development is called the "game loop". Here, the main code of the program is ran in an "infinite" loop. It would also be valid to write

```rust
loop {
    // code
    if !wut::process::running() {
        break;
    }
}
```

The important thing is that during an infinite loop `wut::process::running()` is called somewhat frequently, as it is required for the HOME button to function (or more precisely, to move the app out of the foreground). This means, if you have the main thread blocking is some way, the app cannot be closed.

#### 7. `println!(…)`

What's so special about `println!()`? Nothing really, but since it deals with strings, it is normally defined by std. It is part of the "common stuff" imported via `wut::prelude::*`. Also, it's one of the things configurable via `wut::process::new()`.

#### 8. `wut::time::now() & wut::thread::sleep()`

These are examples of std features which are implemented in wut. They (should) behave like their std siblings.

#### 9. `wut::process::exit()`

This is like `wut::process:default()` but for exiting the app. It's required to clean up everything.

## Time to modify

You now know all the basics of writing Rust code on the Wii U. Now it's time to get your hands dirty and try to implement whatever you want to implement. You can take a look at the documentation to see what std-like features are available and which additional tools are available like `wut::screen` for drawing simple(!) graphics or `wut::gamepad` for controller inputs.

A great source of inspiration is to look at what other people have done, understand their code, and adopt the code for your needs.

[^1]: [List of supported platform](https://doc.rust-lang.org/nightly/rustc/platform-support.html), in case you are wondering.

[^2]: [Read up](https://doc.rust-lang.org/reference/names/preludes.html) on `prelude`.

[^3]: When decorating a function with `extern "C"` it will also disable name mangeling for the same reason: FFI expects the exact name, not some convoluted version.
