# Argh

[![crates.io](https://img.shields.io/crates/v/argh.svg)](https://crates.io/crates/argh)
[![license](https://img.shields.io/badge/license-BSD3.0-blue.svg)](https://github.com/google/argh/LICENSE)
[![docs.rs](https://docs.rs/argh/badge.svg)](https://docs.rs/crate/argh/)
![Argh](https://github.com/google/argh/workflows/Argh/badge.svg)

Argh is an opinionated Derive-based argument parser optimized for code size. It provides a clean and uniform way
to add command line parsing to your binary with low object size overhead.

## Table of Contents
- [Getting Started](#getting-started)
  - [Setup](#setup)
  - [Basic Example](#basic-example)
- [Binary Size](#binary-size)
  - [Argument Parser Comparisons](#argument-parser-comparisons)
  - [Tracking over time](#TODO)
- [Features](#features)
- [Contributing](#contributing)

## Getting Started
### Setup

If you are using Cargo as your build system, add a line for the latest version of Argh:

```toml
[dependencies]
argh = "0.1.3"
```

### Basic Example

```rust,no_run
use argh::FromArgs;

#[derive(FromArgs)]
/// Reach new heights.
struct GoUp {
    /// whether or not to jump
    #[argh(switch, short = 'j')]
    jump: bool,

    /// how high to go
    #[argh(option)]
    height: usize,

    /// an optional nickname for the pilot
    #[argh(option)]
    pilot_nickname: Option<String>,
}

fn main() {
    let up: GoUp = argh::from_env();
}
```

```console
$ cargo run -- --help

Usage: cmdname [-j] --height <height> [--pilot-nickname <pilot-nickname>]

Reach new heights.

Options:
  -j, --jump        whether or not to jump
  --height          how high to go
  --pilot-nickname  an optional nickname for the pilot
  --help            display usage information
```


## Binary Size
One of the primary goals of Argh is to keep it's object footprint small. All features and usability improvements are
viewed through this lens.

### Argument Parser Comparisons

TODO: Comparison chart of binary size

### Tracking Over Time

TODO: Link to Binary Size Tracker

## Features

TODO: Comprehensive list of all supported Argh features

## Contributing

### Code reviews

All submissions, including submissions by project members, require review. We
use GitHub pull requests for this purpose. Consult
[GitHub Help](https://help.github.com/articles/about-pull-requests/) for more
information on using pull requests.

### Community Guidelines

This project follows [Google's Open Source Community
Guidelines](https://opensource.google/conduct/).
