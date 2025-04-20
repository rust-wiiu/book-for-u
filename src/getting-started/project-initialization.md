
# Project Initialization

This section outlines the steps to create a new Wii U development project using provided templates. Several project templates are available, catering to different application types:

* **Rust Crates:** For creating Rust wrappers around existing C libraries. ([`rust-wiiu/library-template`](https://github.com/rust-wiiu/library-template))
* **RPX Applications:** For developing standalone Wii U executable applications. ([`rust-wiiu/application-template`](https://github.com/rust-wiiu/application-template))
* **WUPS Plugins:** For creating plugins that extend the functionality of existing Wii U software. ([`rust-wiiu/plugin-template`](https://github.com/rust-wiiu/plugin-template))
* **RPL Libraries:** (TODO)
* **WUMS Modules:** (TODO)

Refer to the [different file formats](https://www.google.com/search?q=) documentation for detailed information on Wii U file formats.

## Recommended Method: `cargo-generate`

The recommended method for creating a new project is using the `cargo-generate` tool. This provides an interactive CLI to streamline the setup process.

```bash
cargo generate rust-wiiu/application-template
````

Executing this command will prompt you for the project name. This name will be used for the project directory and the final binary name.

## Alternative Method: Git Template

Alternatively, you can utilize the "Use this template" button on the respective GitHub repository to create a new repository based on the chosen template.

1.  **Create a new repository:** On GitHub, use the "Use this template" button and name your new repository according to your project (e.g., `<Project>`).

2.  **Clone the repository:** Clone the newly created repository to your local machine, replacing `<Username>` and `<Project>` with your GitHub username and project name respectively.

```bash
git clone https://github.com/<Username>/<Project>.git
```

3.  **Configure `Cargo.toml`:** Navigate to the cloned project directory and open the `Cargo.toml` file. Modify the `{{project-name}}` and `{{authors}}` placeholders with the appropriate values for your project.

# Building and Running

This section describes the initial build and execution process for your new project.

## 1. Build the project

Execute the following command to compile your project in release mode.

```bash
cargo make --profile release build
```

Upon successful compilation, the resulting RPX executable will be located at `/target/powerpc-none-eabi/release/<Project>.rpx`.

## 2. Run the application (via Cemu)

To execute the compiled application, you can use the Cemu Wii U emulator.

* Open Cemu.
* Navigate to `File` \> `Load`.
* Select the generated RPX file (`/target/powerpc-none-eabi/release/<Project>.rpx`).

If the setup is correct, your application should now run within the emulator.

### Automated Execution (Optional)

You can configure the `run` task within the `Makefile.toml` file[^1] to automatically launch Cemu with your compiled application. Modify the path to your Cemu installation within the `run` task definition. Once configured, you can execute the application using:

```bash
cargo make --profile release run
```

## 3. Run on hardware

You can remove the comments and add your Wii U's IP to the `upload` task to upload the build file via FTP. Then you can upload and start the application from the Wii U Home-Menu so see the same result as Cemu.

```bash
cargo make --profile release upload
```

<br>

Congratulations\! You have successfully set up your development environment and are now ready to develop Wii U software using Rust.

[^1]: The documentation of cargo-make can be found at: [github.com/sagiegurari/cargo-make](https://github.com/sagiegurari/cargo-make).
