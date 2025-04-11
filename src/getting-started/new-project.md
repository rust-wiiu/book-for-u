# Create new project

There are templates for common types of Wii U applications available. These include templates for:
* [Rust crates](https://github.com/rust-wiiu/library-template) (for wrapping C libraries)
* [RPX apps](https://github.com/rust-wiiu/application-template)
* [WUPS plugins](https://github.com/rust-wiiu/plugin-template)
* [RPL libraries]() (TODO)
* [WUMS modules]() (TODO)

## cargo-generate (Recommended)

```bash
cargo generate rust-wiiu/application-template
```

Running this command will open a simple CLI to help you setup the project.

## git

`Use this template` button on github to copy the template to a new repository. Add the projects name as the new repos name and clone it to your machine (of course replacing <Username> & <Project> appropietly)

```bash
git clone https://github.com/<Username>/<Project>.git
```

You will need to modify `Cargo.toml` by changing `{{project-name}}` and `{{authors}}` to appropiet values.

## 2. It is alive!

You can now try to compile and run the program for the first time. When everything is setup correctly you should be able to call the following command to compile the program.

```bash
cargo make --profile release build
```

If everything works and you get no compile error you can find your program at `/target/powerpc-none-eabi/release/<Project>.rpx`. You can open Cemu, click Load, select the .rpx file and (hopefully) see it running. For more information about the [different file formats](), take a look at the documentation.

Congratulations, you now are able to write Wii U software using Rust.
