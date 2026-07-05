# Sega Saturn SCSP (Saturn Custom Sound Processor)

## Official Documentation
- ST-077-R2-052594: Saturn SCSP User's Manual (main reference)
- Limited DSP details in the manual (explicitly notes little info on the DSP itself).

## Overview
- Yamaha YMF292 (SCSP)
- 32 PCM channels
- 68EC000 sound CPU @ ~11.3 MHz
- 512 KB sound RAM (waveform + program)
- 16-bit stereo output, up to 44.1 kHz
- MIDI, DSP for effects, reverb, etc.
- Direct access from SH-2s via SCU or direct.

## Key Features from Manual
- PCM playback with looping, envelope, modulation.
- 8/16-bit samples, various formats.
- Timer, interrupt sources.
- Sound stack for mixing.

## DSP Section
The official manual provides very little on the DSP programming model, coefficients, or algorithms. Most practical knowledge comes from reverse engineering games and emulator implementations (Ymir, Kronos).

Known:
- 64-step microcode-like DSP.
- Used for reverb, filters, 3D sound positioning in some titles.
- Memory mapped access.

## Emulation Notes & Quirks (from Ymir source)
- Threaded SCSP option for performance.
- Specific bugs fixed: attack stuck (KRS=0xF), MVOL=0 silence, SBCTL on sound RAM slots, M68K fetching from registers.
- CD-DA routing through SCSP EXTS.
- 44.1 kHz standard rate.

## References
- Antime collection: ST-077
- Ymir SCSP implementation for cycle-accurate behavior.
- SegaXtreme and forums for DSP reverse engineering.
- Copetti article for high-level overview.

For full details, consult the ST-077 PDF. DSP specifics often require game disassembly.