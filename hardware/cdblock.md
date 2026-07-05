# Sega Saturn CD Block (CD Drive Controller)

## Official Sources
- ST-040-R4-051795: Disc Format Standards
- ST-129 series: Virtual CD manuals
- Technical Bulletins #1-8, #11, #26, #29, #30, #35 for commands and behavior.
- Boot ROM and SBL CD library docs.

## Hardware
- Double-speed CD-ROM drive
- YGR (CD block controller?)
- Handles ISO9660, CD-XA, CD-DA, PhotoCD, etc.
- Anti-piracy: physical rings on disc outer edge, data in lead-in.

## Key Features
- Data transfer rates, access times.
- Supports Mode 1, Mode 2 Form 1/2, interleaved audio/data.
- Commands for seek, read, play CD-DA, etc.

## Format (from ST-040)
- 12cm only, specific linear speed 1.25 m/s, track pitch.
- Track layout: lead-in, data (Mode1 first), XA, CD-DA, lead-out.
- LSN 0-15 special (IP.BIN/boot), ISO9660 from 16.
- Max ~63 min, no multisession.

## Emulation Quirks (Ymir)
- LLE CD Block for accuracy (requires CD block ROMs).
- Clock ratios for drive state.
- Specific fixes for path table, FMV, etc.
- HLE vs LLE differences.

## Commands & Interface
- Via SCU or direct.
- Status, errors, sector reads.

## References
- ST-040 primary.
- Ymir CD block implementation.
- SBL CD comms manual.
- Bulletins for updates.