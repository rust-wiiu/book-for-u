## Let's get into it

So now that we know everything is working, we can take a look at the underlying code and explore the parts of the system. When you open the `src/main.rs` file it will look something like this:

```rust
!#[no_std]
!#[no_main]

use wut;
use wut::prelude::*;
use wut::time::Duration;

#[wut_main(Console)]
fn main() {
    while wut::process::running() {
        println!("{:?}", wut::time::now());
        wut::thread::sleep(Duration::from_secs(1));
    }
}
```

Let's digest this code part by part:

#### 1. `!#[no_std]`

The Wii U / CafeOS does now have official Rust support; who could have guessed? Rust, by default, assumes that you are on a "typical" platform like x86-linux, ARM-windows, AppleSilicon, etc[^1]. There exist 3 stages of feature sets programmers can use with Rust: core, alloc, std. This enables Rust to be used at every level of the software stack; from bootloader to websites.

[`std`](https://doc.rust-lang.org/std/index.html) is the "default" and used when on a typical platform and provides the entire Rust std library with platform specific implementations. So no matter if you are on a UNIX or Windows system, `std::path` will just work. [`alloc`](https://doc.rust-lang.org/alloc/index.html) is one level lower and provides a interface to and allocator. This basically means that the system has a heap and can make use of dynamic allocations (malloc, strings, vectors, ...). However, as this still requires some platform dependent code, a even lower level exist: [`core`](https://doc.rust-lang.org/core/index.html). Here, only base Rust functions exist (no platform dependence or dynamic allocations); meaning only stack-based memory can be used.

So wait a minutes, does this mean at rust-wiiu doesn't even support `String`?! Calm down, rust-wiiu is way more close to a official supported platform (in form of programmer usage) than that might suggest. rust-wiiu defines a custom allocator and implements most of the relevant std-features, so you can use existing Rust knowledge. Still, the compiler/linker has to be informed about this "unusual environment".

#### 2. `!#[no_main]`

Also an embedded rust macro. This special macro tells the linker to not create a main function. This is needed because the `fn main()` isn't the first thing that get's ran during program execution. Lots of other functions run beforehand, to setup heaps, forward arguments, etc. devkitPro has it's own pre-main instructions, so we need to tell Rust to not use it's otherwise useful magic.

#### 3. `use ...`

These are your well known Rust import statements. Nothing unusual about them. The "wut" library contains the functionalities of rust-wiiu and `prelude::*` is to "import common stuff"[^2].

It should be mentioned that `wut::time::Duration` is the **same** thing as `std::time::Duration`. Both are just reexports of `core::time::Duration`, which contains the actual implementations. Wut, like std, exports the entire `core` module for convenience and a single point of access.

<!-- #### 4. `!#[no_mangle]`

This macro is commonly used when interacting with foreign functions, e.g. functions compiled in C[^3]. It disables [Name Mangeling](https://wikipedia.org/wiki/Name_mangling), which is a technique to make function names truly unique by changing them at compile time. This is normally not a problem (and actual wanted), but the devkitPro toolchain searches for a symbol named "main" during compiling/linking, so mangling this name will make the main function indetectable.

#### 5. `wut::process::default()`

This function sets up some functionalities for wut. It does some thing similar, but not exlusively, to the stuff that would run pre-main. There are some configuration you could do by running `wut::process:new()` instead, but you can read the documentation for that. For now, it is required and you can mostly just ignore it. -->

#### 4. `!#[wut_main(Console)]`

Here the magic of rust-wiiu begins. This macro sets up some stuff not necessarily needed for the program to work but to make it behave more like a std environment. You can look up the documentation, but TL;DR it initializes a logger, cleaner exit, etc. This macro can be replaced with some other code and just a convenience.

The most important thing for now is the attribute given to the macro, `Console`. This will result in a on screen console (which will conflict with on screen rendering btw). This is especially useful for early testing. The attribute can be omitted, changed or combined with other logger. Check the documentation for more info. 

#### 6. `while wut::process::running() {…}`

This is a normal main loop. Here, the main code of the program is ran in an "infinite" loop. It would also be valid to write

```rust
loop {
    // code
    if !wut::process::running() {
        break;
    }
}
```

The important thing is that during an infinite loop `wut::process::running()` is called somewhat frequently, as it is required for the foreground release, i.e. the HOME button,  to function (or more precisely, to move the app out of the foreground). This means, if you have the main thread blocking is some way, the app cannot be closed.

#### 7. `println!(…)`

What's so special about `println!()`? Nothing really, but since it deals with strings, it is normally defined by std. It is part of the "common stuff" imported via `wut::prelude::*` (and gets setup with the `wut_main(Console)` macro).

#### 8. `wut::time::now() & wut::thread::sleep()`

These are examples of std features which are implemented in wut. They (should) behave like their std siblings.
