# Frequently Asked Questions

* [What is Homebrew?](#what-is-homebrew)
* [Why Rust on the Wii U](#why-rust-on-the-wii-u)
* [Will it every be a real std version?](#will-it-every-be-a-real-std-version)

## What is Homebrew?

Homebrew software refers to unofficial applications and tools developed by the community, bypassing manufacturer restrictions. It allows users to extend a console's functionality, enabling features like custom games, additional software, and system modifications.

## Why Rust on the Wii U?

> I am a Rust developer. Of course, I’ve spent six months rewriting everything in Rust. So let me tell you about it...

I was tired of the chaos that is C & C++. Between multiple (often partially incompatible) compilers, countless standards, and enough different ways to write the same functionality to make your head spin, C can feel more like an elaborate trap than a programming language. Add to that the sheer number of opportunities for bugs, and you have a recipe for frustration. Rust, by comparison, feels like a breath of fresh air: modern, well-structured, and designed to make your code both safe and sane.

But it’s not just about my personal vendetta against C. C carries the 21ˢᵗ century on its back—and for that, it has my respect. However, I firmly believe that modern languages like Rust have a place ~~even~~ especially on legacy hardware. It lowers the barrier to entry for new developers. Yes, I know Rust isn’t exactly known for being beginner-friendly, but let’s be real: neither is C or C++. At least Rust comes with fantastic default tools for managing packages, formatting, error handling, ... and the compiler is flipping awesome once you develop Stockholm syndrome.

Finally, there’s a bigger picture here. By bringing Rust to legacy systems, we’re keeping niche communities alive and ensuring their codebases remain maintainable, readable, and understandable. A lot of the existing homebrew code is based on personal preferences in formatting and coding style, which makes it hard for third parties to follow. Rust offers a path forward with its clean structure by design, excellent tools, and rapidly growing popularity. So whether you’re here for the technical elegance, the nostalgia, or just to try something new, welcome aboard—let’s make something great.

# Will it every be a real std version?

Most likely not-unless tremendous effort is done and the external dependcies are at least reduced, to make a more standalone toolchain. *Maybe* oneday if the interest is high enough and there are enough contributers to make it feasable. But for the forseeable future, `rust-wiiu` remains an external tool which just trys to have a DX similar to the a std environment.
