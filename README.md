# EFM32 Base Project

This base project is designed to provide a quick and platform independent method of building projects for Silicon Labs EFM32 microcontrollers.  
Designed and tested on OSX and Debian. Windows might work with cygwig/mingw/gnuwindows tools, but hasn't been attempted.

If you have any issues, suggestions or alterations, feel free to open an issue or a pull request.

[![Build Status](https://travis-ci.org/ryankurte/efm32-base.svg)](https://travis-ci.org/ryankurte/efm32-base)

## Motivation

 - Getting started with Microcontrollers is hard (and time consuming)
 - Vendor IDEs are ultimately useless when approaching testing and build-automation

This project addresses this by providing a common base for for projects using Silicon Labs EFM32 and EZR32 processors.   
If you're not into cmake, you might want to check out [ARM Mbed Yotta](http://yottadocs.mbed.com/) or [PlatformIO](http://platformio.org/), both of which offer higher level approaches to embedded setup/development.

## Dependencies

 - cmake - use brew on osx, or your favourite package manager for linux
 - make - should be available by default, otherwise as above
 - arm-none-eabi-gcc - Embedded ARM Compiler/Toolchain (https://launchpad.net/gcc-arm-embedded/+download)
 - JLink tools - download and install from https://www.segger.com/jlink-software.html

If you're into docker, check out [ryankurte/docker-arm-embedded](https://hub.docker.com/r/ryankurte/docker-arm-embedded/) for a containerised toolchain. You will still need JLink tools locally to flash and debug.

## Usage

This project can either be used directly or as a submodule in a larger project.
Note that submodule use will allow updates to this project for fixes or further device support.  
For an example project using this method, see [ryankurte/usb-thing](https://github.com/ryankurte/usb-thing).

### To use the project directly:

1. Download this repository
2. Change the project name and device in the CMakeLists.txt file
3. Move your source  and include files into the source and include directories
4. Add your source files to the CMakeLists.txt file
5. Make something awesome!

### To use this project as a submodule:

1. Add the submodule to your (already git controlled) project using:  
   `git submodule add https://github.com/ryankurte/efm32-base.git`  
   `git submodule update`  
2. Copy the CMakeLists.txt file from this project (efm32-base) to the top level of your project
3. Update the project name and BASE_LOCATION variables in the new CMakeLists.txt
4. Add your source files (and cmake libraries) to the CMakeLists.txt file
5. Make something even more awesome!

## Building

Once you have integrated this project with your project, you can build in the standard cmake manner.

1. `mkdir build` to create the build directory
2. `cd build` to switch to the build directory
3. `cmake ..` to configure the build
4. `make` to execute the build
5. `make flash` to flash to a device

## Licensing

Since this is a combination of a number of Silicon Labs (ex. Energy Micro) components, as well as custom additions, licensing is a little interesting. A summary of the licenses involved follows, but I take no responsibility for the accuracy or interpretation of such.  

The CMSIS Core falls under a fairly permissive ARM [license](cmsis/Include/arm_common_tables.h). This requires that the license requires the copyright and license note to be distributed in the documentation accompanying binary distribution, and that the name ARM LIMITED may not be used to promote any products derived from this without written permission.  

The device and emlib components fall under the above ARM license (startup files) as well as a permissive Silicon Labs [license](device/EFM32GG/efm32gg280f1024.h). This allows use, alteration and distribution for any purpose provided the origin of the source is not represented, altered versions are plainly marked, and the notice is not removed from the source distribution.  

Drivers are covered by the [Silabs License Agreement](drivers/Silabs_License_Agreement.txt). This is similar to the the license above, however prohibits sublicensing the included code and use of the code on non-silabs devices.  

The CMake components of this project are distributed under the MIT license.  


