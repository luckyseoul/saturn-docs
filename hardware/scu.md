# Sega Saturn SCU (Saturn Control Unit)

## Official Docs
- ST-097-R5-072694: SCU User's Manual (3rd version)
- ST-210-110194: SCU Final Specifications - Precautions
- Technical Bulletins #10, #16, #39, etc. for updates.

## Overview
- Custom ASIC with:
  - DMA controller (3 channels? powerful with priority)
  - DSP for geometry (fixed-point, matrix ops)
  - Interrupt controller
  - Bus arbitration

## DSP
- 32-bit fixed point
- Instructions for multiply-accumulate, etc.
- Used in SGL for 3D transforms.
- Assembler and simulator tools in SDK (ST-240 series).
- Quirks: 48-bit registers, specific instruction behaviors.

## DMA
- High speed transfers between WRAM, VDP, etc.
- Interruptible in some modes (for CD LLE).
- Restrictions on byte counts, priorities with SH-2s.
- Common source of bugs in games.

## Memory & Access
- 32 KB SRAM on SCU?
- Connected to main bus.

## Emulation Notes from Ymir
- Optimize DSP ops involving 48-bit.
- DMA interrupt signals delayed based on length.
- Properly handle 8/16-bit writes to registers.
- Timer fixes.

## References
- ST-097, ST-210
- Antime, Exodus mirrors
- Ymir SCU code for accurate timing/DMA
- SegaXtreme SCU DSP notes

See also Dual CPU guide for coordination.