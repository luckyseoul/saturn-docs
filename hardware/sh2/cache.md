# SH-2 Cache

## Official
- SH7604 Hardware Manual, Programming Manual.

## Cache in Saturn
- Each SH-2 has 4KB cache (I + D?).
- Associative, LRU.
- Cache through addresses: 0x20000000+ for uncached access.
- Important for dual CPU shared data.

## Behavior
- Cache line fills.
- Write back?
- Purge, address array access.

## Emulation Notes from Ymir
- SH2 cache emulation critical for many games (palette glitches, FMV, etc.).
- Fixes for cache address array reads/writes (8/16-bit).
- Byte order in direct cache data.
- LRU update mask.
- TAS.B bypass cache.
- DMAC burst with cache.
- GameDB forces for many titles: Astal, Dark Savior, etc.

## Dual CPU
- Cache snooping? No.
- Use cache-through for shared WRAM.

References: Ymir SH2 cache code, ST-202, Hitachi manuals.