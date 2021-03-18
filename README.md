# Log viewer

A very simple program to view and filter logs easily. It's a crude, but
efficient tool to view log files. Focuses on ease of installation and ease
of use. Only one binary to drop somwhere in PATH and it will work anywhere
there is a browser available. Easy for non-techical users to use.

![Example GIF](https://github.com/cfsamson/rust-logviewer/blob/master/assets/logv4.gif)

## Usage

After installation, write: `logv` in a root folder where you want to search and
find log files in the subfolders.

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

Close the console program when you're done by closing the console window or
`Ctrl + C`.

## Goals and pros/cons

This is a crude tool with only some advantages:

- Easy to install. Just build and drop in PATH (or `cargo install`) and that's it
- Small program size
- Short codebase, easy to audit and review (for those that doesn't like to run arbitrary
programs in certain environments, this program probably takes 20 minutes to audit)
- Easy to adapt and extend to you own needs
- Easy to contribute to the codebase

This is not the most efficient, the most featurefull or the most advanced
log viewer available. It was built with the advantages above in mind and for my
own use.

## Large files

There is no paging so rendering very large files will take a lot of resources.

## Installation

*`+nightly` required since we use the [Rocket web server](https://rocket.rs/)

`cargo +nightly install logv`

Or download the source code, build with `cargo build --release` and drop
the resulting binary somewhere in "PATH" so you can call it in a project
directory from the command line.

Since the program depends on the Rocket web framework, it requires nightly so
set `rustup override set nightly` before building if you compiling from source.

## Technical details

The Rust program is only 260 lines of code and the UI is 320 lines of
HTML/JavaScript.

The search logic is written using only the Rust strandard libray, and the UI is
written using only vanilla JavaScript. Besides that the dependencies are as
follows.

- [Rocket](https://rocket.rs/) is used as the web server.
- [Serde](https://serde.rs/) is used for serialization
- [Bootstrap](https://getbootstrap.com/) is used as the frontend toolkit

## Compatability

Only tested in Windows, but should work on any fully supported Rust target
where a web browser is available.
