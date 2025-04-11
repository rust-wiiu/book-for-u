
## Time to modify

You now know all the basics of writing Rust code on the Wii U. Now it's time to get your hands dirty and try to implement whatever you want to implement. You can take a look at the documentation to see what std-like features are available and which additional tools are available like `wut::screen` for drawing simple(!) graphics or `wut::gamepad` for controller inputs.

A great source of inspiration is to look at what other people have done, understand their code, and adopt the code for your needs.

[^1]: [List of supported platform](https://doc.rust-lang.org/nightly/rustc/platform-support.html), in case you are wondering.

[^2]: [Read up](https://doc.rust-lang.org/reference/names/preludes.html) on `prelude`.

[^3]: When decorating a function with `extern "C"` it will also disable name mangeling for the same reason: FFI expects the exact name, not some convoluted version.
