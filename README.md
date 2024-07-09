# Godot Cpp Starter Kit

This project is meant as a starting point for creating new C++/CMake-based Godot 4 extensions. The goal is to lower the barrier to entry to building a GDExtension using [CMake](https://cmake.org).

It is currently set up to work with the **[Godot 4.2.2](https://github.com/godotengine/godot/releases/tag/4.2.2-stable)** release.

Read full readme for **[GDExtensionTemplate](https://github.com/asmaloney/GDExtensionTemplate/blob/master/README.md)**.

## Prerequisites

To use this locally on your machine, you will need the following:

- **[CMake](https://cmake.org/)** v3.22+
- C++ Compiler with at least **C++17** support (any recent compiler)
- (optional) **[ccache](https://ccache.dev/)** for faster rebuilds
- (optional) **[clang-format](https://clang.llvm.org/docs/ClangFormat.html)** for linting and automatic code formatting (CI uses clang-format version 15)

The GitHub actions (CI) are set up to include all of these tools. To see how to download them on your platform, take a look at the [workflow](.github/workflows/main.yml) file.

## How To Use

### Setup

Steps I had to do in order to make it work in MSVC:

- Pull the submodule code
```sh
$ git submodule update --init --recursive
```
- Dump latest extension API data using the engine version you want
```sh
godot --dump-extension-api --dump-gdextension-interface
```
- Compile godot-cpp and generate the latest Godot bindings headers using the dump
```sh
python -m SCons custom_api_file=gdextension/extension_api.json
```

MSVC should pick up CMake lists at this points and allow you to compile the project.

### References

- Forked from **[GDExtensionTemplate](https://github.com/asmaloney/GDExtensionTemplate/blob/master/README.md)**
- Follow **[godot-cpp](https://github.com/godotengine/godot-cpp)** repo for latest updates
- Made for **[Godot](https://github.com/godotengine/godot)**
