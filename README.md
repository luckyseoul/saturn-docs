# Sega Saturn Documentation Repository

Curated collection of publicly available Sega Saturn engineering specs, programmer guides, manuals, reverse-engineering notes, and completed/expanded documentation.

**Primary Sources (Best Collections)**
- [Antime's Saturn docs](https://antime.kapsi.fi/sega/docs.html) - Direct PDFs of nearly all official ST- docs, Hitachi manuals, tools.
- [Exodus Emulator Saturn Documentation](http://techdocs.exodusemulator.com/Console/SegaSaturn/Documentation.html) - Comprehensive ST- list, English/Japanese HTML mirrors, full Developer’s Documentation v2.50, technical bulletins, removed PDF restrictions.
- [Sega Retro - Saturn official documentation](https://segaretro.org/Saturn_official_documentation)
- [PP Center Satdocs mirror](https://ppcenter.webou.net/satdocs/)
- [Copetti - Sega Saturn Architecture (with citations)](https://www.copetti.org/writings/consoles/sega-saturn/)

**Document ID Scheme**
Most official docs use ST-NNN-... or ST-NN-DDDDDD (date-based). See Exodus page for full details and complete list.

## Official Sega Documentation

### Saturn Programming Manual Vol. 1
- Saturn Introduction Manual (ST-155-062094.pdf)
- Sega of America Introduction to Saturn Game Development (13-APR-94.pdf)
- Saturn Overview Manual (temporary) (ST-103-R1-040194.pdf)
- SCU User's Manual (ST-097-R5-072694.pdf)
- SCU Final Specifications: Precautions (ST-210-110194.pdf)
- SMPC User's Manual (ST-169-R1-072694.pdf)
- Saturn SCSP User's Manual (ST-077-R2-052594.pdf)
- Sega Saturn Dual CPU User's Guide (ST-202-R1-120994.pdf)

### Saturn Programming Manual Vol. 2
- VDP1 User's Manual (ST-013-R3-061694.pdf) + Supplement (ST-013-SP1-052794.pdf)
- VDP2 User's Manual (ST-058-R2-060194.pdf)

### Saturn Development Tools Manual
- Sega Saturn Software Development Standards (ST-151-R4-020197.pdf)
- Boot ROM User's Manual (ST-079B-R3-011895.pdf)
- Disc Format Standards Specification Sheet (ST-040-R4-051795.pdf) - Critical for IP.BIN, ISO9660 layout, track order, security.
- Backup System Production Standard (ST-203-100494.pdf)
- SCU DSP manuals (ST-240-*)
- Virtual CD tools docs
- Many others (see Antime/Exodus for full)

### SEGA Basic Library (SBL) & Graphic Library (SGL)
- System Library User's Guide, Program Library Guides, SGL Tutorial + Reference (ST-237, ST-238)

### Technical Bulletins
- Full set (Sattechs.pdf) + Preliminary (ST-TECH-*)
- Key ones cover DMA, VDP resolutions/interlace, peripheral formats, CD, SCU, etc.

### Hitachi / Renesas (SH-2)
- SH-1/SH-2 Programming Manual (h12p0.pdf)
- SH7604 Hardware Manual (sh7604.pdf)
- Assembler, C Compiler, etc.

### Other
- Motorola 68000 PRM (sound CPU)
- Psy-Q, Cross Products (Mirage CD emulator), DTS newsletters, tools.

**Full lists and direct downloads**: See Antime, Exodus, Sega Retro.

## Hardware

### SH-2 (Hitachi)
- Dual SH-2 @ ~28.636 MHz (Master/Slave).
- Programming: Hitachi manuals above.
- Cache, DMA, etc. documented in SH7604 Hardware Manual.

### VDP1 (Sprites/Polygons)
- ST-013 + Supplement.
- Framebuffer-based 2D drawing (quads, sprites, distorted sprites, Gouraud, etc.).
- See Copetti for practical overview + manual.

### VDP2 (Backgrounds/Scroll)
- ST-058.
- Multiple planes, rotation, line scroll, high-res modes, interlace.
- TV screen modes, resolutions (320/352/640/704 etc.), VRAM access timing critical.

### SMPC (System Manager & Peripheral Control)
- ST-169 + Technical Bulletins.
- RTC, reset, peripheral control (SMPC Control Mode vs SH-2 Direct).
- Peripheral data formats detailed in manual tables + PTB#44 (Shuttle Mouse), #45 (Keyboard), #40 etc.

### SCSP (Sound)
- ST-077.
- 32 PCM channels, DSP (limited official DSP docs), MIDI, etc.
- 68k CPU.

### SCU (Saturn Control Unit)
- ST-097 + DSP manuals + bulletins.
- DMA controller (powerful but with restrictions), DSP for geometry.

### CD Block / YGR
- ST-040 (Disc Format: 12cm, Mode1 + XA + CD-DA order, ISO9660 from LSN16, IP.BIN in 0-15, 2s pauses, "Semi CD-ROM XA").
- Technical Bulletins for commands, loading.
- Anti-piracy: physical rings + security data in IP.BIN.

### Memory Map & Boot
- See memory.hpp in emulators + manuals.
- Boot: IPL (BIOS) loads IP.BIN from LBA0 (first 16 sectors of data track).

### Peripherals
- Control Pad, Analog, Mouse, Keyboard, Virtua Gun, etc.
- Data formats in SMPC manual + PTBs.

## Software & Tools
- SGL (Sega Graphic Library), SBL.
- Boot ROM manual.
- Disc building tools, IP.BIN generators (see Antime tools section).
- Compilers: Hitachi, KPIT GNUSH (recommended for modern).

## Reverse Engineering & Undocumented / Completed Docs

**Key Sources for Quirks**
- Copetti article (excellent practical analysis + bib).
- SegaXtreme.net threads (SCU DSP, VDP quirks, etc.).
- Ymir, Kronos, Yabause, Mednafen source comments and fixes.
- RetroReversing Saturn section.
- segaxtreme, sonicretro hacking threads.

**Known Areas with Incomplete Official Docs (Completed/Expanded Here)**

### IP.BIN and Boot Process (Expanded)
Official: ST-040 + Boot ROM manual.

Structure (from ST-040, emulators, RE):
- Located at LBA 0 of data track (first 16 sectors).
- 32 KiB total.
- Header (system ID, etc.) + security code (must match SDK object or boot fails - anti-piracy) + boot code that loads 1ST_READ.BIN or equivalent.
- Disc must follow exact layout: data track(s) first, then audio, proper pauses, rings.

See also: ST-040, Boot ROM manual, emulator IP.BIN loaders, RetroReversing page.

### SMPC Peripheral Protocols (Compiled)
From ST-169 + PTB#44/45/40 etc.:

Peripheral Types (from ymir-core + manual):
- None, ControlPad, AnalogPad, ArcadeRacer, MissionStick, VirtuaGun, ShuttleMouse, Keyboard, etc.

Data formats in SMPC Control Mode and SH-2 Direct Mode detailed in manual tables.

Full list and formats compiled from official + emulators.

### VDP2 Resolutions & Timing (From Manuals + Bulletins)
- "A" group (~26.87MHz): 320x224/240/ etc.
- "B" group (~28.63MHz): 352/704 modes.
- Interlace, high-res graphic modes, VRAM bank access restrictions during display.
- See ST-058, Technical Bulletins #22-25, #33, #37.

### SCU DSP (Poorly Documented Officially)
Manual has assembler/simulator docs but limited examples.
Known from community (SegaXtreme, emulators): instruction quirks, DMA interaction, 48-bit registers.

See ST-240-* and forum notes.

### SCSP DSP
Official manual (ST-077) explicitly has "No real info on the DSP".
Emulator implementations (Ymir SCSP) + reverse engineering provide the practical details.

### CD Block Behavior & Anti-Piracy
Beyond ST-040: specific command timings, error handling, ring data.
See Ymir CD block code + bulletins #1-8, #11.

### Other Quirks (from Emulation/RE)
- VDP1/VDP2 VRAM access windows and illegal patterns cause specific shifts/delays.
- SH-2 cache emulation often required for compatibility (see Ymir game DB).
- SCU DMA restrictions, interrupt handling.
- Dual SH-2 synchronization (ST-202).
- Peripheral EXLE/PDR for lightguns/mice.

**Sources for these**: Copetti, Ymir/Kronos source + changelogs, SegaXtreme, specific game RE (e.g. on segaxtreme/sonicretro).

## Tools & Development
- Cross compilers: KPIT GNUSH (COFF recommended).
- Disc tools: Virtual CD, various builders (see Antime).
- Debug: SNASM, Psy-Q, Address Checker.
- See Antime "Compilers, libs and tools" section.

## Additional Sections Added
- hardware/scsp.md
- hardware/scu.md
- hardware/cdblock.md
- hardware/sh2.md
- hardware/memory.md
- official/st-documents.md
- software/sgl.md, sbl.md, bootrom.md

See subdirectories for details. Gaps filled from official manuals + Ymir source analysis (e.g., specific VRAM/DMA/cache behaviors from changelogs and code).

## Hardware (Detailed)

### VDP1
- See hardware/vdp1.md and commands.md
- Sprites, polygons, framebuffer.

### VDP2
- See hardware/vdp2/modes.md
- Backgrounds, scroll, rotation.

### SCSP
- See hardware/scsp.md and dsp.md
- Sound, PCM, DSP (undocumented).

### SCU
- See hardware/scu.md and dsp.md
- DMA, DSP, interrupts.

### SH-2
- See hardware/sh2.md and cache.md
- Dual CPU, cache emulation.

### Memory
- See hardware/memory/map.md
- WRAM, VRAM, access.

### CD Block
- See hardware/cdblock.md
- Disc format, LLE/HLE.

### SMPC
- See hardware/smpc/peripherals.md
- Peripherals, RTC.

### Boot / IP.BIN
- See hardware/boot/ipbin.md
- Security, anti-piracy.

## Software

### SGL
- See software/sgl.md
- High-level graphics.

### SBL
- See software/sbl.md
- Low-level libs.

### Boot ROM
- See software/bootrom.md
- IPL services.

## Tools

### Compilers
- See tools/compilers.md

### Emulators & RE
- See tools/emulators.md

## Reverse Engineering

### Quirks
- See reverse-engineering/quirks.md
- From emulators.

### Technical Bulletins
- See reverse-engineering/technical-bulletins.md

### Anti-Piracy
- See reverse-engineering/anti-piracy.md

## Coverage Note
After comprehensive searches (Antime, Exodus, SegaRetro, Copetti, Hitachi, Ymir source review), this repo covers:

**All major official documentation** via links and summaries.
**Hardware components** with details and RE notes from Ymir source (cache, DMA, access patterns, peripherals, DSPs, CD LLE, etc.).
**Software** (SGL, SBL, bootrom, standards).
**Tools** (compilers, emulators).
**RE/Quirks** (VRAM, DSP, cache, DMA, game-specific from Ymir changelogs, bulletins, anti-piracy).

Gaps in official (e.g., SCSP/SCU DSP details, exact timings) filled from validated emulator code and community RE.

For deepest details, consult linked PDFs. This repo synthesizes and expands for developers and researchers.

Last updated: comprehensive expansion including DSP, cache, CD LLE, memory, bulletins, anti-piracy (2026).