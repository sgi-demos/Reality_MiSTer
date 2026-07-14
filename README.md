# Reality_MiSTer

This project aims to create a retro-modern FPGA-based SGI workstation ('the SGI Reality') based on the [N64_MiSTer](https://github.com/MiSTer-devel/N64_MiSTer) work.  The goal is to get IRIX (probably 6.2) running on this system, with minimal hardware capability departures from the N64 (though probably more RAM will be necessary as IRIX demands it).  Graphics can leverage the IRIS GL software reference rasterizer work done for the [Alice4](https://lkesteloot.github.io/alice/alice4/) project and extended by the [sgi-demos](https://github.com/sgi-demos) project.  And of course SGI emulation with [MAME](https://github.com/mamedev/mame/tree/master/src/mame/sgi) and [IRIS](https://github.com/techomancer/iris) will be immensely helpful too.

The name 'Reality' is chosen as it alludes to SGI's 'Project Reality' code name for the N64 work, along with SGI's Reality Engine and Infinite Reality systems.  And unlike emulation, it brings SGI hardware back to reality.

Probably a multi-year project!

# N64_MiSTer readme

## Hardware Requirements
SDRAM of any size is required.
32Mbyte SDRAM can only be used for games up to 16Mbyte in size.

## Bios
Rename your PIF ROM file (e.g. `pif.ntsc.rom` ) and place it in the `./games/N64/` folder as `boot.rom`

## Error messages

If there is a recognized problem, an overlay is displayed, showing which error has occured.
Errors are hex encoded by bits, so the error code can represent more than 1 error.

List of Errors:
- Bit 0 - Memory access to unmapped area
- Bit 1 - CPU Instruction not implemented, currently used for cache command only
- Bit 2 - CPU stall timeout
- Bit 3 - DDR3 timeout    
- Bit 4 - FPU internal exception    
- Bit 5 - PI error
- Bit 6 - critical Exception occurred (heuristic, typically games crash when that happens, but can be false positive)
- Bit 7 - PIF used up all 64 bytes for external communication or EEPROM command have unusual length
- Bit 8 - RSP Instruction not implemented
- Bit 9 - RSP stall timeout
- Bit 10 - RDP command not implemented
- Bit 11 - RDP combine mode not implemented
- Bit 12 - RDP combine alpha functionality not implemented
- Bit 13 - SDRAM Mux timeout
- Bit 14 - not implemented texture mode is used
- Bit 15 - not implemented render mode (2 pass or copy) is used
- Bit 16 - RSP read Fifo overflow
- Bit 17 - DDR3 - RSP write Fifo overflow
- Bit 18 - RSP IMEM/DMEM write/read address collision detected
- Bit 19 - One fo the DDR3 requesters wants to write or read outside of RDRAM 
- Bit 20 - RSP DMA wants to write outside of RDRAM 
- Bit 21 - RDP pixel writeback wants to write outside of RDRAM
- Bit 22 - RDP Z writeback wants to write outside of RDRAM
- Bit 23 - RSP PC is modified by register access while RSP runs
- Bit 24 - VI line processing wasn't able to complete in time
- Bit 25 - RDP Mux missed request
- Bit 26 - CPU Writefifo full (should never happen, internal CPU logic bug)
- Bit 27 - TLB access from multiple sources in parallel (should never happen, internal CPU logic bug)
- Bit 28 - PI DMA wants to write outside of RDRAM*
