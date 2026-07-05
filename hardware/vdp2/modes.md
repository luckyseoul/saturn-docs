# VDP2 TV Screen Modes, Resolutions, and Timing

## Official Sources
- VDP2 User's Manual (ST-058-R2-060194, Version 1.1)
- Technical Bulletins #22–25, #33, #37 (resolution changes, interlace, bank splitting, additional restrictions).

## Dot Clock Groups ("A" and "B")
- Group A (~26.87 MHz NTSC / PAL equivalent): Common 320-pixel modes.
- Group B (~28.63 MHz): 352-pixel and high-res/704 modes.

Changing between groups requires SMPC clock change commands (SYS_CHGSYSCK etc.) and affects both VDP1 and VDP2.

## Common Resolutions
From VDP2 manual Chapter 2 + bulletins:

**Non-interlace / Normal**
- 320x224, 320x240, 320x256 (and variants)
- 352x240, 352x256
- 640x224/240/256 (high horizontal res)
- 704x240/256 (Group B high res)

**Interlace / Dedicated High-Res Graphic Modes**
- Effective 640x448/480, 704x448/480 etc.
- Requires specific TV screen mode register + interlace settings.
- VDP1 and VDP2 must be configured compatibly.

**HDTV / 31kHz modes**
- Supported on some hardware; higher dot clocks.

See VDP2 "TV screen mode register", "Interlace mode", external signals, and H/V counter registers for exact control.

## VRAM Access & Timing Restrictions
- VRAM is divided into banks with cycle patterns.
- During display period, access is strictly scheduled (CPU, VDP1, VDP2 sprite/background fetches).
- Illegal access patterns cause shifts, garbage, or delays (detailed in bulletins).
- Specific rules for bitmap vs cell, coefficient tables, line color screen, etc.

Key restrictions documented in ST-058 + Bulletins #13, #14, #33, etc.

## Practical Notes from Emulation & Titles
- High-res + interlace often requires game-specific timing tweaks.
- VDP2 resolution changes mid-frame or on VBlank have specific latching behavior.
- Coefficient tables (for rotation) have per-dot/line restrictions on VRAM access.

## References
- ST-058 full Chapter 2 (TV screen) and Chapter 3 (RAM access).
- Technical Bulletins listed above.
- Copetti article section on VDP2.
- Ymir/Kronos VDP2 renderer code for validated cycle-accurate behavior.

This page consolidates the manual + bulletins for quick reference. Always consult the original PDFs for register bitfields.