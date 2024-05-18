# blr_procgen

<p align="left">
  <a href="https://github.com/AndrejOrsula/blr_procgen/actions/workflows/rust.yml">   <img alt="Rust"       src="https://github.com/AndrejOrsula/blr_procgen/actions/workflows/rust.yml/badge.svg"></a>
  <a href="https://github.com/AndrejOrsula/blr_procgen/actions/workflows/docker.yml"> <img alt="Docker"     src="https://github.com/AndrejOrsula/blr_procgen/actions/workflows/docker.yml/badge.svg"></a>
  <a href="https://deps.rs/repo/github/AndrejOrsula/blr_procgen">                     <img alt="deps.rs"    src="https://deps.rs/repo/github/AndrejOrsula/blr_procgen/status.svg"></a>
  <a href="https://codecov.io/gh/AndrejOrsula/blr_procgen">                           <img alt="codecov.io" src="https://codecov.io/gh/AndrejOrsula/blr_procgen/branch/main/graph/badge.svg"></a>
</p>

This repository contains pipelines for procedural generation of assets via Blender's Geometry Nodes. The generation pipelines are implemented in Rust via [blr](https://github.com/AndrejOrsula/blr) while leveraging [NodeToPython](https://github.com/BrendanParmer/NodeToPython) to automate the construction of nodes from Python.

## Overview

The workspace contains these packages:

- **[procgen_peg_in_hole](procgen_peg_in_hole):** Procedural pipelines for generating peg-in-hole modules for [drl_omni_peg](https://github.com/AndrejOrsula/drl_omni_peg)

## Instructions

### <a href="#-rust"><img src="https://rustacean.net/assets/rustacean-flat-noshadow.svg" width="16" height="16"></a> Rust

> \[!TIP\]
> You can install Rust and Cargo through your package manager or via <https://rustup.rs>.

#### Generation of Procedural Peg-in-Hole Modules

The train and test sets can be generated via [`generate_peg_in_hole_train.rs`](procgen_peg_in_hole/src/bin/generate_peg_in_hole_train.rs) and [`generate_peg_in_hole_test.rs`](procgen_peg_in_hole/src/bin/generate_peg_in_hole_test.rs), respectively.

```bash
# Generate train set
cargo run --release --bin generate_peg_in_hole_train
# Generate test set
cargo run --release --bin generate_peg_in_hole_test
```

#### Build Image

To build a new Docker image from [`Dockerfile`](Dockerfile), you can run [`.docker/build.bash`](.docker/build.bash) as shown below.

```bash
.docker/build.bash ${TAG:-latest} ${BUILD_ARGS}
```

#### Run Container

To run the Docker container, you can use [`.docker/run.bash`](.docker/run.bash) as shown below.

```bash
.docker/run.bash ${TAG:-latest} ${CMD}
```

#### Run Dev Container

To run the Docker container in a development mode (source code mounted as a volume), you can use [`.docker/dev.bash`](.docker/dev.bash) as shown below.

```bash
.docker/dev.bash ${TAG:-latest} ${CMD}
```

As an alternative, users familiar with [Dev Containers](https://code.visualstudio.com/docs/devcontainers/containers) can modify the included [`.devcontainer/devcontainer.json`](.devcontainer/devcontainer.json) to their needs. For convenience, [`.devcontainer/open.bash`](.devcontainer/open.bash) script is available to open this repository as a Dev Container in VS Code.

```bash
.devcontainer/open.bash
```

#### Join Container

To join a running Docker container from another terminal, you can use [`.docker/join.bash`](.docker/join.bash) as shown below.

```bash
.docker/join.bash ${CMD:-bash}
```

</details>

## License

This project is dual-licensed to be compatible with the Rust project, under either the [MIT](LICENSE-MIT) or [Apache 2.0](LICENSE-APACHE) licenses.
