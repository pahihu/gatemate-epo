# Embedded Project Oberon for GateMate

In the src/ directory you can find the sources.

The SD card image works as is if you compile BootLoad.Mod and synthesise
with the resulting prom.mem file the RISC5 FPGA CPU. I've modified the
BootLoad.Mod from the Astrobe for RISC5 v8.0 ArtyA7-100 board package
and replaced the SPI code with the HCDrive.Mod SPI routines from Astrobe
for RISC5 v11.0.

In the inner code I have only modified the Kernel.Mod source: I used there
the HCDrive.Mod SPI routines as well.

If you use the v11.0 compiler you should recompile every module in the
EPO sources, not just the inner core because of the changed module keys.

**Note**: Good luck!
