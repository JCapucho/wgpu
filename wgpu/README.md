<img align="right" width="25%" src="logo.png">

wgpu-rs is an idiomatic Rust wrapper over [wgpu-core](https://github.com/gfx-rs/wgpu). It's designed to be suitable for general purpose graphics and computation needs of Rust community.

wgpu-rs can target both the natively supported backends and WASM directly.

See our [gallery](https://wgpu.rs/#showcase) and the [wiki page](https://github.com/gfx-rs/wgpu-rs/wiki/Applications-and-Libraries) for the list of libraries and applications using `wgpu-rs`.

## Usage

### How to Run Examples

All examples are located under the [examples](examples) directory.

These examples use the default syntax for running examples, as found in the [Cargo](https://doc.rust-lang.org/cargo/reference/manifest.html#examples) documentation. For example, to run the `cube` example:

```bash
cargo run --example cube
```

The `hello*` examples show bare-bones setup without any helper code. For `hello-compute`, pass 4 numbers separated by spaces as arguments:

```bash
cargo run --example hello-compute 1 2 3 4
```

The following environment variables can be used to configure how the framework examples run:

- `WGPU_BACKEND`

  Options: `vulkan`, `metal`, `dx11`, `dx12`, `gl`, `webgpu`

  If unset a default backend is chosen based on what is supported
  by your system.

- `WGPU_POWER_PREF`

  Options: `low`, `high`

  If unset a low power adapter is preferred.

#### Run Examples on the Web (`wasm32-unknown-unknown`)

See [wiki article](https://github.com/gfx-rs/wgpu-rs/wiki/Running-on-the-Web-with-WebGPU-and-WebGL).

## Development

If you need to test local fixes to gfx or other dependencies, the simplest way is to add a Cargo patch. For example, when working on DX12 backend on Windows, you can check out the latest release branch in the [gfx-hal repository](https://github.com/gfx-rs/gfx) (e.g. currently `hal-0.8`) and add this patch to the end of `Cargo.toml`:

```toml
[patch."https://github.com/gfx-rs/gfx"]
gfx-backend-dx12 = { path = "../gfx/src/backend/dx12" }
gfx-hal = { path = "../gfx/src/hal" }
```

If a version needs to be changed, you need to do `cargo update -p gfx-backend-dx12`.
