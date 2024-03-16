# Libgtextutils

Gordon's text utils library.

This library is only ever used in fastx_toolkit project, see [this](https://github.com/merv1n34k/fastx_toolkit/tree/homebrew) GitHub repository.

## Software Requirements

1. Cmake >= 3.15

2. GCC (passing on 13.2.0), but probably >= 6 will be sufficient

## Installation

To install the tools one can do the following:

```bash
   $ git clone https://github.com/merv1n34k/libgtextutils
   $ cd libgtextutils
   $ git checkout cmake_version
   $ mkdir build && cd build
   $ cmake ..
   $ make install
```

If you are on macOS *(and probably Linux)* you can use [Homebrew](https://brew.sh/). However, if you are planning to install `fastx_toolkit` the `libgtextutils` will be installed automatically as a dependency. If for some reason you need only this library, one can do:

```bash
   $ brew tap merv1n34k/tap
   $ brew install merv1n34k/tap/libgtextutils
```

## LICENSE

Distributed under AGPLv3, see LICENSE for more.

## Notes from Author

A. Gordon designed and implemented Gordon-Text_utils-Library.

The `libgtextutils` has originally been written by A. Gordon.
Many people have further contributed to FOO by reporting problems,
suggesting various improvements, or submitting actual code. Here is
a list of these people. Help me keep it complete and exempt of errors.

## Notes from me

Feel free to open issues in this repository, PRs are appreciated :3

