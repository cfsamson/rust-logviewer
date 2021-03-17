# Log viewer

A minmimalist app to view and filter logs easily.

![Example GIF](https://github.com/cfsamson/rust-logviewer/blob/master/assets/logv4.gif)

## Usage

The app transverses all subdirectories from where it's called and looks for
*.log files. These files are all parsed and categorized by the keywords:

- DEBUG
- INFO
- WARN
- ERROR

Lines that doesn't match any of these are categorized as "other".

The app will launch a local webserver and open a UI in the default web browser.

This is a small program that should be pretty easy to audit and look through.
It only implements the bare minimum of functionality, and is especially geared
towards typical log output from Rust programs.

## Large files

There is no paging so rendering very large files will take a lot of resources.

## Installation

`cargo install logv`

Or download the source code, build with `cargo build --release` and drop
the resulting binary somewhere in "PATH" so you can call it in a project
directory from the command line.

Since the program depends on the Rocket web framework, it requires nightly so
set `rustup override set nightly` before building if you compiling from source.
