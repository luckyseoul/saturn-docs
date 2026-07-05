# VDP1 Command List

## Official
- ST-013 VDP1 User's Manual: details command table.

## Commands
- Normal Sprite, Scaled Sprite, Distorted Sprite, Polygon, Polyline, etc.
- End command.
- Jump, Call, Return for control flow.

## Format
- 32-byte entries? 
- CMDCTRL, CMDLINK, CMDPMOD, CMDCOLR, CMDSRCA, CMDSIZE, CMDXA etc.
- CMDSRCA: character address /8.
- CMDSIZE: width/8 , height.

## Usage
- Build list in VRAM.
- Set VDP1 regs for start address, etc.
- Draw to framebuffer.

## Quirks from Emulation
- Ymir VDP1: specific handling for zoom, clipping, infinite loops detection in some games.
- Transparent pixels, Gouraud, etc.

## References
- ST-013 full.
- VDP1 viewer in debuggers.
- Ymir VDP1 source.