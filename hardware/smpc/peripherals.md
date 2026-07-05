# Sega Saturn SMPC Peripherals (Compiled from Official Docs + Validated RE)

## Official Sources
- SMPC User's Manual (ST-169-R1-072694)
- Preliminary Technical Bulletins:
  - PTB #40, #44 (Shuttle Mouse Data Format), #45 (Saturn Keyboard), others.
- Saturn Programming Manual Vol.1 sections on SMPC.
- Various Technical Bulletins on peripheral IDs and EXLE/PDR.

## Peripheral Control Modes
SMPC supports two main modes for peripherals:
1. SMPC Control Mode (recommended for most use) — SMPC automatically polls and collects data into output registers (OREG).
2. SH-2 Direct Mode — direct access to the parallel I/O ports by the SH-2 (used for some devices or low-level).

See ST-169 Section 3 for block diagrams, command sequences (INTBACK etc.), and timing.

## Peripheral Types
From SMPC manual + PTBs + emulator implementations (validated across titles):

- None (0x00 or no device)
- Saturn Standard Digital Pad (Control Pad)
- Saturn 3D Control Pad (Analog Pad)
- Arcade Racer
- Mission Stick
- Virtua Gun / Light Gun
- Shuttle Mouse
- Keyboard
- Sega Tap (multitap)
- Other (some unreleased or region-specific)

Exact ID bytes and data packet sizes are defined in the SMPC manual tables (Control Mode and Direct Mode).

## Data Formats (Summary)
**Saturn Standard Pad (most common)**:
- Digital pad + Start + A/B/C/X/Y/Z + L/R.
- Active-low or specific bit encoding detailed in manual Table for "SATURN Standard PAD Data Format in SMPC Control Mode".

**Analog / Other**:
- Analog pads report additional axis bytes.
- Mouse: relative X/Y + button bits (see PTB#44).
- Keyboard: scan codes + modifiers (PTB#45).
- Lightgun: X/Y position + trigger (special handling with SMPC EXLE).

Full bit-by-bit layouts, port status bytes, multitap chaining, and SH-2 Direct Mode equivalents are in:
- ST-169 Section 3 (tables 3.10–3.39 etc.)
- PTB #44, #45, #40.

## SMPC Commands Related to Peripherals
- INTBACK (with appropriate parameters) for collecting peripheral data.
- SMPC commands for setting port modes, EXLE (enable external latch for lightguns), etc.
- See manual for IREG/OREG usage and timing relative to VBlank/HBlank.

## Common Quirks & Notes (from Emulation + RE)
- EXLE/PDR registers must be handled correctly for lightguns and some mice.
- Multitap (Sega Tap) uses specific port status bytes; games poll for connected devices.
- Some peripherals require exact timing or specific SMPC PLL settings.
- SH-2 cache behavior can affect peripheral polling code.

## References for Full Details
- SMPC User's Manual (ST-169) — primary.
- PTB #44, #45, #40 and related bulletins.
- Emulator source (Ymir peripheral report code, Kronos SMPC) for validated bit mappings.
- SegaXtreme threads on specific devices.

This page compiles the scattered official tables into one place for developers and reverse engineers. For bit-exact layouts always cross-reference the original ST-169 PDF + relevant PTBs.