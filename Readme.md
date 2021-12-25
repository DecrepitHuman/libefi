# libefi

`libefi` is a safe, idiomatic Rust implementation of the Unified Extensible Firmware Interface,
making it possible to write low-level EFI applications using purely Rust code. It also provides
target specifications that can be used to build EFI images directly with Xargo.

# Overview

UEFI is the modern replacement for PC BIOS systems. It specifies a standard interface that platform
firmware must honor, so that any software written against the specification is portable to any UEFI
platform.

This crate uses Rust's rich FFI support to implement types and functions for interacting with UEFI
firmware. Most of the structures, functions, and types described in the UEFI specification are
implemented purely in Rust, and on top of these are a set of functions for interacting using
idiomatic Rust code. This layered approach is used throughout the library, resulting in an API that
is ergonomic wherever possible but still incredibly flexible when necessary.

See https://github.com/rust-osdev/uefi-rs for a more general wrapper.

# Rust

A *nightly* compiler is required, as is the Rust source.

1. Install Rust via [*rustup*](https://www.rustup.rs/)
2. Add the Rust source component: `rustup component add rust-src`
3. Switch to the nightly compiler: `cd path/to/libefi && rustup override set nightly`

# Building

See `x86_64-unknown-efi` target for creating a EFI image.

# Running

To run an .efi executable on a real computer:
- Find a USB drive which is FAT12 / FAT16 / FAT32 formatted
- Copy the file to the USB drive, to /EFI/Boot/Bootx64.efi
- In the UEFI BIOS, choose "Boot from USB" or similar

# Examples

See the *src/bin/test.rs* file for an example of an EFI application that uses this crate. See also
the *Makefile*, which demonstrates how to test using qemu and OVMF. When running on Ubuntu, the
*Makefile* has the following package dependencies:

* `build-essential`
* `mtools`
* `ovmf`
* `qemu-system-x86`
* `xorriso`
