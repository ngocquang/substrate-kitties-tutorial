# Substrate Node Template

[![Try on playground](https://img.shields.io/badge/Playground-Node_Template-brightgreen?logo=Parity%20Substrate)](https://docs.substrate.io/playground/) [![Matrix](https://img.shields.io/matrix/substrate-technical:matrix.org)](https://matrix.to/#/#substrate-technical:matrix.org)

A fresh FRAME-based [Substrate](https://www.substrate.io/) node, ready for hacking :rocket:

## Getting Started

Follow the steps below to get started with the Node Template, or get it up and running right from
your browser in just a few clicks using
the [Substrate Playground](https://docs.substrate.io/playground/) :hammer_and_wrench:

### Using Nix

Install [nix](https://nixos.org/) and optionally [direnv](https://github.com/direnv/direnv) and
[lorri](https://github.com/target/lorri) for a fully plug and play experience for setting up the
development environment. To get all the correct dependencies activate direnv `direnv allow` and
lorri `lorri shell`.

### Rust Setup

First, complete the [basic Rust setup instructions](./docs/rust-setup.md).

### Run

Use Rust's native `cargo` command to build and launch the template node:

```sh
cargo run --release -- --dev
```

### Build

The `cargo run` command will perform an initial build. Use the following command to build the node
without launching it:

```sh
cargo build --release
```

### Embedded Docs

Once the project has been built, the following command can be used to explore all parameters and
subcommands:

```sh
./target/release/node-kitties -h
```

## Run

The provided `cargo run` command will launch a temporary node and its state will be discarded after
you terminate the process. After the project has been built, there are other ways to launch the
node.

### Single-Node Development Chain

This command will start the single-node development chain with non-persistent state:

```bash
./target/release/node-kitties --dev
```

Purge the development chain's state:

```bash
./target/release/node-kitties purge-chain --dev
```

Start the development chain with detailed logging:

```bash
RUST_BACKTRACE=1 ./target/release/node-kitties -ldebug --dev
```

Test

```bash
cargo test
cargo test -p <pallet name>
cargo test -p <pallet name> tests::<unit test name> -- --exact
```

Debug

```bash
RUST_LOG=runtime=debug ./target/release/node-kitties --dev
```

Cac buoc Benchmark

1. Su dung macro benchmark! de test warst case
2. Enable features runtime-banchmark trong cargo.toml cua runtime
3. add_benchmark!
4. cargo build --release --features runtime-benchmarks

```bash
./target/release/node-kitties benchmark \
    --chain dev \
    --execution wasm \
    --wasm-execution compiled \
    --pallet pallet_kitties \
    --extrinsic '*' \
    --steps 20 \
    --repeat 10 \
    --json-file=raw.json \
    --output ./pallets/kitties/src/weights.rs
```
