# SCU DSP Details

## Official
- ST-097 SCU Manual
- ST-240-A SCU DSP Assembler User's Manual
- ST-240-B Simulator
- Addendums.

## DSP Architecture
- Fixed point DSP in SCU.
- Used for 3D geometry calculations (matrix, vector).
- 32-bit?
- Program and data RAM.
- DMA transfers to/from DSP RAM.

## Instructions
- From assembler manual: ALU ops, multiply, etc.
- Ymir has tests for ALU, instructions, DMA, loop, end.

## Usage
- In SGL for transforms.
- Games load DSP program, data, execute.
- Interleaved with DMA.

## Emulation in Ymir
- Detailed tests in tests/ymir-core-tests/src/hw/scu/scu_dsp_tests.cpp
- ALU operations, instructions execute correctly, loop, end, DMA.

## Quirks
- DMA to Program RAM.
- Pause and access RAM.
- 48-bit registers in some ops.

See Ymir source for accurate behavior not fully in manuals.