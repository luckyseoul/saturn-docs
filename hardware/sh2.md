# Sega Saturn SH-2 CPUs (Hitachi)

## Official
- Hitachi SH-1/SH-2 Programming Manual (h12p0.pdf)
- SH7604 Hardware Manual (sh7604.pdf)
- Dual CPU User's Guide (ST-202-R1-120994)

## Specs
- 2x SH-2 @ 28.63636 MHz
- Master/Slave configuration
- 32-bit RISC, 5-stage pipeline
- 4KB cache each?
- Little endian support
- Division unit, etc.

## Dual CPU
- Master controls slave via commands.
- Shared bus, contention issues.
- Synchronization critical.

## Cache
- Instruction + data cache.
- Emulation often needed for compatibility (palette issues, etc.).
- Specific cache behaviors for writes, purges.

## Emulation Notes (Ymir)
- SH2 cache emulation option.
- Fixes for 8/16-bit reads/writes to cache areas.
- Byte order in direct cache access.
- Clock ratio for speed.

## References
- Hitachi manuals from Antime.
- ST-202
- Ymir SH2 core.
- Copetti for overview.