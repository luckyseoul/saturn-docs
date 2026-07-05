# Sega Saturn IP.BIN and Boot Process

## Official Sources
- ST-040-R4-051795 (Disc Format Standards) — primary spec for layout.
- Boot ROM User's Manual (ST-079B-R3-011895).
- Saturn Programming Manual Vol.1 / Development Tools.

## IP.BIN Location and Size
- Always located at the start of the data track (LBA 0).
- Exactly 32 KiB (16 sectors of 2048 bytes).
- Contains:
  - Header / system information.
  - Security / anti-piracy code (must match a specific object from the official SDK or the console refuses to boot the disc).
  - Boot code that loads the actual game executable (typically 1ST_READ.BIN or equivalent at a defined offset).

## Disc Layout Requirements (from ST-040)
- 12 cm disc only.
- Inner track(s): CD-ROM Mode 1 (data) + optional CD-ROM XA.
- Outer tracks: CD-DA (audio).
- At least one audio track recommended if any CD-DA area is present (or a warning message track).
- 2-second pauses before/after data tracks and audio tracks per Yellow Book.
- LSN 0–15: special (boot/IP.BIN + protection info). ISO9660 filesystem starts at LSN 16.
- No multisession.
- Specific lead-in/readout timing and linear speed/track pitch for reliability.

## Security / Anti-Piracy
- The security code in IP.BIN is a compiled object that must be present exactly as provided in the Sega SDK.
- Physical disc anti-piracy: pressed rings on the outer edge (visible "anti-piracy rings").
- Boot ROM checks both the IP.BIN security data and (in some implementations) physical characteristics.

## Boot Sequence (High Level)
1. Hardware reset → IPL (BIOS) runs from ROM.
2. IPL reads the first sectors of the data track.
3. Loads IP.BIN into work RAM.
4. IP.BIN security check + boot code executes.
5. Boot code loads the main executable from the filesystem and transfers control.

See also:
- Boot ROM User's Manual for low-level IPL behavior.
- Emulator implementations (Ymir, Kronos) for precise loading of IP.BIN + 1ST_READ.BIN.
- ST-040 for exact sector layout and volume descriptor expectations.

## Tools & Notes for Homebrew/RE
- Tools exist for generating valid IP.BIN for GNU toolchains (see Antime collection).
- Many homebrew use custom or patched IP.BIN; the security code must still be valid for real hardware.
- Emulators often relax or log the security check for development.

For reverse engineering the exact security code layout and boot code, refer to:
- ST-040 + Boot ROM manual.
- Public IP.BIN analyzers and loaders in open-source Saturn emulators and tools (e.g. Pseudosaturn, various disc builders).
- SegaXtreme and RetroReversing discussions on IP.BIN structure.