# CMake example msp430fr5994

Examples for MSP430FR5994 LaunchPad based on CMake.

# Build process

- Install cmake (https://cmake.org/)
- Download msp430-gcc (https://www.ti.com/tool/MSP430-GCC-OPENSOURCE) and extract in any folder
- Adjust path to msp430-gcc in msp430-toolchain.cmake accordingly (i.e., replace path of MSP430 support file variables PATH_MSP430_SUPPORT, PATH_MSP430_LIB, PATH_MSP430_BIN, PATH_MSP430_INCLUDE)
- Create folder *build*
- Move into folder (`cd build`) and run `cmake -G Ninja -S .. -DCMAKE_TOOLCHAIN_FILE="..\msp430-toolchain.cmake"` to create build environment
- To build the binaries, run `ninja`
- The binary files are located directly in the build directory (e.g.*build/PROJECT.elf*) and can be flashed to the MSP430 LaunchPad using Uniflash (https://www.ti.com/tool/UNIFLASH?keyMatch=UNIFLASH%20DOWNLOAD) or mspdebug (see below)

## My build process

If you need to update the driverlib or if you need to add the driverlib for another device: [www.ti.com/tool/MSPDRIVERLIB](https://www.ti.com/tool/MSPDRIVERLIB)

# Projects

1) *blinky*: Simple Blinky program

- (TBD)*Tools*: includes devices drivers, e.g., UART, temperature sensor
- *MSP430FR5xx_6xx*: device drivers from TI to access board's peripherals (e.g., including driverlib)

# MSP430-GDBProxy++

MSP430-GDBProxy++ allows to flash and debug boards using command line and gdb.
- To install MSP430-GDBProxy++, follow instructions on: [https://gnutoolchains.com/msp430/gdbproxy](https://gnutoolchains.com/msp430/gdbproxy)
- To run in command line:
    1. Start the server: `msp430-gdbproxy.exe`
    2. In a separate terminal connect with gdb: `msp430-elf-gdb.exe build\blinky.elf -ex "target remote: 2000"`
- To run with VSCode, I am still figuring it out. The current configuration in .vscode/launch.json seems to start the server
    but it does not finde the sources and it does not recognize the sources and breakpoints in the VSCode UI.
