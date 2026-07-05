# Sega Saturn Hardware Quirks & Undocumented Behaviors (Compiled from RE + High-Accuracy Emulation)

This document collects behaviors that are either poorly documented in official manuals or discovered through reverse engineering and emulator development. Sources include Ymir, Kronos, other emulators, SegaXtreme, Copetti, and game-specific hacking.

## VDP1 / VDP2
- VRAM access during display period is strictly windowed. Writing/reading at the wrong cycle often causes one-pixel shifts, garbage, or full-line corruption.
- Illegal VDP1 command tables (zero CMDSIZE, certain jump patterns) can cause infinite loops or early termination — emulators implement detection.
- VDP1 distorted sprites and Gouraud shading have specific edge cases with transparent pixels and clipping.
- VDP2 per-dot coefficient access and line color screen have bank-specific restrictions not fully enumerated in the basic manual.
- High-resolution + interlace modes require coordinated VDP1/VDP2 + SMPC clock changes; many games have per-title hacks.

## SCU DMA
- SCU DMA has complex priority and interrupt interaction with the two SH-2s.
- Certain DMA transfers can be interrupted or have byte-count quirks (see Technical Bulletins).
- DSP + DMA interaction has documented but subtle timing.

## SH-2 Cache & Dual CPU
- Cache emulation is often required for correct behavior (palette glitches, timing-sensitive code). Some titles need forced enable via game DB.
- Master/Slave synchronization and bus contention are major sources of bugs; Dual CPU User's Guide (ST-202) is essential but not sufficient.
- Cache flush/invalidate timing relative to DMA and VDP access is a frequent source of "works on real hardware, breaks in emulator" issues.

## SMPC / Peripherals
- EXLE (external latch enable) and PDR registers are critical for lightguns and some mice. Incorrect handling causes missed shots or wrong coordinates.
- Multitap detection and port status bytes follow specific sequences; games poll in particular ways.
- Keyboard and mouse data formats have exact bit layouts in PTBs that some emulators initially got wrong.

## CD Block
- Command timing, error reporting, and seek behavior have many edge cases.
- Some images with non-standard track layouts or missing pauses fail on real hardware but work in early emulators.
- CD-DA playback routing through SCSP has specific volume and mixing rules.

## Boot / Security
- IP.BIN security code must match SDK exactly (see dedicated ipbin.md).
- Physical disc rings + data in early sectors are part of the protection.
- IPL (BIOS) behavior on bad discs or missing files is specific.

## Other
- SCSP DSP is the area with the least official documentation. Practical behavior comes almost entirely from emulator implementations and game reverse engineering.
- Some VDP2 color calculation and priority edge cases only appear in specific title combinations.
- PAL vs NTSC timing differences affect both video and audio (sample rate, VBlank).

## How to Use This
Cross-reference with:
- Official ST- documents (especially VDP1/VDP2, SMPC, SCU, CD, Dual CPU).
- Technical Bulletins (many are bug reports / clarifications from Sega).
- High-accuracy emulator source (Ymir is particularly well-commented for these cases).
- Game-specific RE when a title exposes a new quirk.

Contributions that add verified behavior (with source/title + manual cross-reference) are welcome.

This is not a replacement for the official manuals — it is the "things the manuals don't fully explain or that were discovered later" companion.