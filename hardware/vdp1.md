# Sega Saturn VDP1 (Video Display Processor 1)

## Official
- ST-013-R3-061694: VDP1 User's Manual
- Supplement ST-013-SP1
- Bulletins #15, #22 etc.

## Overview
- Handles sprites, polygons (quads), textures, Gouraud shading, distortion.
- Frame buffer based (double buffered).
- Commands in VRAM command table.
- 16-bit color, various modes.

## Key Commands
- Normal/distorted sprites, polygons, polylines.
- Clipping, user clipping.
- Texture, color modes (palette, RGB).

## Quirks (from Ymir/RE)
- Specific zoom point undocumented behaviors.
- Transparent pixel handling in Gouraud.
- VRAM write stalls in certain games.
- Command table issues (zero size, jumps).

## References
- ST-013
- Ymir VDP1 renderer for fixes (e.g. scaled sprites, clipping).
- Copetti for overview.