# Sega Saturn Development Tools - Compilers and Toolchains

## Official and Recommended

- **Hitachi SHC Compiler**: Original for SH-2. COFF format.
- **KPIT GNUSH**: Free GCC-based toolchain for SuperH (SH-2). Recommended for modern use. COFF version for Sega libs compatibility. Available from kpit.com (now part of Renesas?).
  - Prebuilt for Windows/Linux.
  - ELF also available but COFF preferred for Saturn.

## Other
- **Cygnus GCC** (old, in Antime collection): Cygnus v2.7 for Saturn.
- **SBL601.zip**: Includes sources for low-level libs.
- **SS-SDK Win95 Graphic Tools**: For graphics conversion.

## Building IP.BIN
- Tools in Antime: IPGNUSRC.zip for GNU env.
- Must include specific security code from SDK for real hardware boot.

## Assemblers/Debuggers
- SNASM (Cross Products / Psy-Q): ASM68K/ASMSH.
- Psy-Q tools.
- SCU DSP Assembler (ST-240-A).

See Antime "Compilers, libs and tools" for archives and links.