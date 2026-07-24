# Sega Saturn Documentation Repository

Curated **offline** collection of Sega Saturn engineering specs, programmer guides, manuals, reverse-engineering notes, and expanded documentation.

**All official PDFs are local** under [`files/`](files/) (103 manuals mirrored from Antime). Full index: [`official/st-documents.md`](official/st-documents.md).

## Local Primary Sources

| Source | Local path |
|--------|------------|
| Antime ST- / Hitachi / tools PDFs | [`files/*.pdf`](files/) (103 files) |
| Antime index HTML snapshot | [`files/html/antime-docs-index.html`](files/html/antime-docs-index.html) |
| PPCenter HTML mirror (zip) | [`files/html/ppcenter-satdocs-html.zip`](files/html/ppcenter-satdocs-html.zip) |
| Copetti Saturn architecture | [`files/html/copetti-saturn.html`](files/html/copetti-saturn.html) |

## Core Official Manuals (quick links)

### Programming Manual Vol. 1
- [Saturn Introduction Manual](files/ST-155-062094.pdf) (`ST-155-062094.pdf`)
- [SOA Introduction to Saturn Game Development](files/13-APR-94.pdf)
- [Saturn Overview Manual](files/ST-103-R1-040194.pdf)
- [SCU User's Manual](files/ST-097-R5-072694.pdf)
- [SCU Final Specs: Precautions](files/ST-210-110194.pdf)
- [SMPC User's Manual](files/ST-169-R1-072694.pdf)
- [SCSP User's Manual](files/ST-077-R2-052594.pdf)
- [Dual CPU User's Guide](files/ST-202-R1-120994.pdf)

### Programming Manual Vol. 2
- [VDP1 User's Manual](files/ST-013-R3-061694.pdf) + [Supplement](files/ST-013-SP1-052794.pdf)
- [VDP2 User's Manual](files/ST-058-R2-060194.pdf)

### Development tools / standards
- [Software Development Standards](files/ST-151-R4-020197.pdf)
- [Boot ROM User's Manual](files/ST-079B-R3-011895.pdf)
- [Disc Format Standards](files/ST-040-R4-051795.pdf) — IP.BIN, ISO9660, track order, security
- [Backup System Production Standard](files/ST-203-100494.pdf)
- SCU DSP: `files/ST-240-*.pdf`
- [Technical Bulletins (Sattechs)](files/Sattechs.pdf) + `files/ST-TECH-*.pdf`

### Libraries
- SBL / SGL: [ST-237](files/ST-237-R1-051795.pdf), [ST-238](files/ST-238-R1-051795.pdf)

### Hitachi / Renesas (SH-2)
- [SH-1/SH-2 Programming Manual](files/h12p0.pdf)
- [SH7604 Hardware Manual](files/sh7604.pdf)
- Assembler / C compiler / simulator: `files/shccomp.pdf`, `files/e702090_superh.pdf`, `files/e702186_shsimulator.pdf`, …

### Other
- [Motorola 68000 PRM](files/M68000PRM.pdf) (sound CPU)
- DTS newsletters: `files/DTS-*.pdf`
- Tools manuals: `files/3DEdit.pdf`, `MapEdit.pdf`, `SprEdit.pdf`, …

**Complete enumerated list:** [`official/st-documents.md`](official/st-documents.md)

## Hardware (detailed MD in this repo)

| Topic | Summary | Local manuals |
|-------|---------|---------------|
| SH-2 | [`hardware/sh2.md`](hardware/sh2.md) | `h12p0.pdf`, `sh7604.pdf` |
| VDP1 | [`hardware/vdp1.md`](hardware/vdp1.md) | `ST-013-*.pdf` |
| VDP2 | [`hardware/vdp2/modes.md`](hardware/vdp2/modes.md) | `ST-058-R2-060194.pdf` |
| SMPC | [`hardware/smpc/peripherals.md`](hardware/smpc/peripherals.md) | `ST-169-R1-072694.pdf`, `ST-TECH-44/45` |
| SCSP | [`hardware/scsp.md`](hardware/scsp.md) | `ST-077-R2-052594.pdf` |
| SCU | [`hardware/scu.md`](hardware/scu.md) | `ST-097-R5-072694.pdf`, `ST-240-*` |
| CD Block | [`hardware/cdblock.md`](hardware/cdblock.md) | `ST-040-R4-051795.pdf` |
| Memory | [`hardware/memory/map.md`](hardware/memory/map.md) | manuals above |
| Boot / IP.BIN | [`hardware/boot/ipbin.md`](hardware/boot/ipbin.md) | `ST-040`, Boot ROM |

## Software
- SGL: [`software/sgl.md`](software/sgl.md) → `ST-237` / `ST-238`
- SBL: [`software/sbl.md`](software/sbl.md)
- Boot ROM: [`software/bootrom.md`](software/bootrom.md) → `ST-079B-R3-011895.pdf`
- Standards: [`software/development-standards.md`](software/development-standards.md) → `ST-151-R4-020197.pdf`

## Reverse Engineering
- Quirks: [`reverse-engineering/quirks.md`](reverse-engineering/quirks.md)
- Technical bulletins: [`reverse-engineering/technical-bulletins.md`](reverse-engineering/technical-bulletins.md) → `files/Sattechs.pdf`, `ST-TECH-*`
- Anti-piracy: [`reverse-engineering/anti-piracy.md`](reverse-engineering/anti-piracy.md)
- Offline architecture write-up: [`files/html/copetti-saturn.html`](files/html/copetti-saturn.html)

## Tools
- Compilers: [`tools/compilers.md`](tools/compilers.md) — Hitachi / KPIT docs in `files/`
- Emulators: [`tools/emulators.md`](tools/emulators.md)

## Coverage Note

Official ST- documents are **local PDFs** (no external download required for the Antime set). Markdown under `hardware/`, `software/`, and `reverse-engineering/` synthesizes manuals + validated emulator RE (Ymir/Kronos-class).

Last updated: 2026-07-24 — full Antime PDF harvest; URLs replaced with `files/` paths.
