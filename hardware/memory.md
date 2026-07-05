# Sega Saturn Memory Map

## Overview
- Work RAM High (WRAM-H): 1MB SDRAM, fast, shared bus.
- Work RAM Low (WRAM-L): 1MB DRAM, slower, CPU private?
- Sound RAM: 512KB
- VDP1 VRAM: 512KB
- VDP2 VRAM: 512KB (split banks)
- SCU SRAM? 32KB?
- Cartridge: up to 4MB?
- CD buffer, etc.

## Detailed Map (from emulators + manuals)
Typical addresses:
- 0x00000000 - 0x000FFFFF : Boot ROM / IPL (1MB mirrored?)
- 0x00200000 - 0x002FFFFF : Work RAM Low
- 0x06000000 - 0x060FFFFF : Work RAM High
- 0x05A00000 - SCU
- 0x05B00000 - SCSP
- 0x05C00000 - VDP1
- 0x05E00000 - VDP2
- 0x05F00000 - SMPC, etc.
- Cache areas: 0xC0000000 etc. for SH2 cache.

## Access
- Byte, word, long word.
- Specific restrictions per device.
- DMA from SCU for high speed.

## References
- Ymir memory.hpp and saturn.cpp
- ST-103 Overview, hardware manuals.
- Memory map diagrams in docs.

See also per-device docs.