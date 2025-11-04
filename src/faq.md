# Frequently Asked Questions

* [What is Homebrew?](#what-is-homebrew)
* [Will it ever be a real std version?](#will-it-ever-be-a-real-std-version)
* [How to learn Rust?](#how-to-learn-rust)
* [Why Rust on the Wii U](#why-rust-on-the-wii-u)

## What is Homebrew?

Homebrew software encompasses unofficial applications and tools created by the community, operating outside of the manufacturer's officially supported ecosystem. It empowers users to expand a console's capabilities, unlocking functionalities such as custom games, supplementary software, and system modifications.

## Will it ever be a real std version?

It is highly unlikely that `rust-wiiu` will ever become a fully integrated standard Rust environment. Several aspects of the underlying toolchain are fundamentally incompatible with standard Rust configurations. While a future integration might theoretically be possible given sufficient interest and a dedicated team of contributors, it is not feasible in the foreseeable future. Therefore, `rust-wiiu` will continue to exist as an external toolchain that strives to offer a developer experience (DX) as close as possible to a standard Rust environment.

Furthermore, the freedom from strict adherence to the standard library (`std`) API can offer significant convenience, particularly for rapid development. While this flexibility might occasionally result in APIs that are less optimal or non-standardized in terms of performance, security, or other aspects, the trade-off in terms of ease and speed of development is often considered worthwhile.

## How to learn Rust?

Start using it. If you have no prior programming experience, it's worth noting that Rust, with its explicit and strict nature (qualities that ultimately contribute to its strength and reliability), might present a steeper initial learning curve compared to some other languages. However, I would never want to discourage anyone from embarking on the journey of learning Rust. To support you in this endeavor, here's a curated list of resources that I personally recommend or that are highly regarded within the Rust community:

* [Comprehensive Rust 🦀](https://google.github.io/comprehensive-rust/): A complete course about Rust by Google.
* [The Rust Programming Language](https://doc.rust-lang.org/stable/book/): The "official" Rust book by and for the community 
* [Rust By Example](https://doc.rust-lang.org/rust-by-example/): Collection of Rust code examples

## Why Rust on the Wii U?

> I am a Rust developer. Of course, I’ve spent six months rewriting everything in Rust. So let me tell you about it...

I was tired of the chaos that is C & C++. The fragmented compiler ecosystem, the ever-evolving standards, and the compiler's tendency to let programmers wreak havoc can make C feel less like a language and more like an intricate maze. Add to that the sheer number of opportunities for bugs or undefined behavior, and you have a recipe for frustration. Rust, by comparison, feels like a breath of fresh air: modern, well-structured, and designed to make your code both safe and sane.

But it’s not just about my personal vendetta against C. I firmly believe that modern languages like Rust have a valuable role to play ~~even~~ especially on legacy hardware. Rust lowers the barrier to entry for new developers. Okay, I know Rust has a reputation for a steeper learning curve, but at least Rust comes with fantastic default tools for managing packages, formatting, error handling, ... and the compiler is flipping awesome once you develop Stockholm syndrome.

Ultimately, there's a bigger vision here. By introducing Rust to legacy environments, we can help sustain niche communities and ensure their codebases remain manageable, readable, and understandable. So much existing homebrew code reflects individual formatting and coding styles, making it challenging for others to contribute. Rust, with its inherent clean structure, great tooling, and increasing popularity, offers a promising path forward. So, whether you're drawn by the technical sophistication, the desire for a bit of nostalgia, or simply the curiosity to explore something new, welcome—let's build something great together.
