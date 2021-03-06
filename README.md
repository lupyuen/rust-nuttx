# Rust Stub Library for Apache NuttX OS

Read the articles...

-   ["Rust talks I2C on Apache NuttX RTOS"](https://lupyuen.github.io/articles/rusti2c)

-   ["Rust on Apache NuttX OS"](https://lupyuen.github.io/articles/rust2)

This is a Stub Library, the actual Rust code is at...

-   [lupyuen/rust-i2c-nuttx](https://github.com/lupyuen/rust-i2c-nuttx)

-   [lupyuen/rust_test](https://github.com/lupyuen/rust_test)

# Install Library

To add this repo to your NuttX project...

```bash
pushd nuttx/nuttx/libs
git submodule add https://github.com/lupyuen/rust-nuttx librust
popd
```

Next update the Makefiles and Kconfig...

-   [Kconfig](https://github.com/lupyuen/incubator-nuttx/blob/rust/Kconfig#L2014)

-   [tools/Directories.mk](https://github.com/lupyuen/incubator-nuttx/blob/rust/tools/Directories.mk#L170-L174)

-   [tools/FlatLibs.mk](https://github.com/lupyuen/incubator-nuttx/blob/rust/tools/FlatLibs.mk#L159-L163)

-   [tools/KernelLibs.mk](https://github.com/lupyuen/incubator-nuttx/blob/rust/tools/KernelLibs.mk#L145-L149)

-   [tools/LibTargets.mk](https://github.com/lupyuen/incubator-nuttx/blob/rust/tools/LibTargets.mk#L229-L233)

-   [tools/ProtectedLibs.mk](https://github.com/lupyuen/incubator-nuttx/blob/rust/tools/ProtectedLibs.mk#L159-L163)

Then update the NuttX Build Config...

```bash
## TODO: Change this to the path of our "incubator-nuttx" folder
cd nuttx/nuttx

## Preserve the Build Config
cp .config ../config

## Erase the Build Config
make distclean

## For BL602: Configure the build for BL602
./tools/configure.sh bl602evb:nsh

## For ESP32: Configure the build for ESP32.
## TODO: Change "esp32-devkitc" to our ESP32 board.
./tools/configure.sh esp32-devkitc:nsh

## Restore the Build Config
cp ../config .config

## Edit the Build Config
make menuconfig 
```

In menuconfig, enable the Rust Library under "Library Routines".
