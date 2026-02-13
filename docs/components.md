# Components and Tools 
RVBuilder includes a set of components and tools that support the complete software development workflow for Andes RISC-V–based targets. These components provide predefined configurations and utilities required throughout development, including target configuration files (Chip Profiles), toolchains, connection configurations, the Andes In-Circuit Emulator driver (ICEman), the Andes QEMU emulator, the Linker Script Generator (LdSaG), and flash programming utilities. 

The integration of these components within VS Code enables you to manage build, run and debug workflows through a unified interface, eliminating the need for manual installation and configuration of individual components for the desired Andes RISC-V target.

The following provide brief introduction to the key components and tools in the RVBuilder package.

## Chip Profiles 
Chip profiles describe the specifications and software configuration of specific target platforms.
RVBuilder provides a set of predefined chip profiles for Andes targets. Each chip profile contains the required software settings for the corresponding target, such as 
- the preferred toolchain
- compiler, linker, and assembler options specific to the target core
- target connection configuration and related arguments
When creating or configuring an RVBuilder project, select an appropriate chip profile to match the intended target and take note of the chip profile naming convention when making a selection.

Andes chip profiles follow the naming format:
> **`ADP-<PLATFORM>-<CORE>-<SUFFIX>`**

- `ADP` stands for Andes Development Platform. It is used as the prefix for Andes target configurations.
- **`<PLATFORM>`** refers to an AndeShape™ platform. Supported platform IPs or development platforms include: AE250, AE350, and Corvette-F1. For more information, see [AndeShape™ Platforms](https://www.andestech.com/en/products-solutions/andeshape-platforms/).
- **`<CORE>`** refers to a 32-bit or 64-bit AndesCore™ processor core. The RVBuilder package supports a variety of AndesCore processor series designed for different applications
For more information, see [AndesCore™ Processors](https://www.andestech.com/en/products-solutions/andescore-processors/).
- **`<SUFFIX>`** denotes additional features or configurations of the target. Supported suffixes include: 

    - `RVB` — Bit-manipulation extension enabled
    - `SE` — Security processor configuration
    - `1C` — Single-core configuration of a multi-core target
    - `SMP` — Symmetric multiprocessing configuration for multi-core targets

Examples of chip profiles within the RVBuilder Package: ADP-AE250-N25F, ADP-AE350-NX45-RVB, ADP-AE350-AX46MPV-SMP and more. 

## Toolchains
The RVBuilder package provides two toolchains, `nds32le-elf-newlib-v5` and `nds64le-elf-newlib-v5`, for software development on Andes RISC-V targets.

The toolchain naming convention denotes the following:

- `nds32`/`nds64` indicates the supported processor architecture. `nds32` for 32-bit Andes RISC-V processors and `nds64` for 64-bit Andes RISC-V processors.
- `le` indicates that the supported target endianness is little-endian.
- `newlib` indicates that the toolchain provides the Newlib support.
- `v5` indicates that the toolchain targets the AndeStar™ Instruction Set Architecture (ISA) V5 implementation.

The appropriate toolchain for a specific Andes target is predefined in the associated chip profile and does not require manual selection.  However, for RVBuilder projects that use a custom Makefile, you must update the target-related settings and toolchain paths in `tasks.json` after switching to a target (chip profile) with a different architecture (e.g. changing from 32-bit to 64-bit). The toolchain executable path is located at `${RVBUILDER_PACKAGE_ROOT}/toolchains/{TOOLCHAIN}/bin/`. 


## Connection Configurations 

AICE, Andes QEMU, maverick, GDB server 

###  ICEman

###   

## Linker Script Generator (LdSaG)



## Flash Burners 



