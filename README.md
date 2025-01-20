# Info
This is the fork of original u-boot

Original readme [here](README_original-uboot.md)
    This is the attempt to port the original u-boot to Tang Mega 138k board.
    Currently, serial port is working and we have got u-boot prompt

# How to load ?
- You will need to load proper bitstream file with RV350 core.
  You can use: [My project](https://github.com/mlapaj/vhdl_playground/tree/main/mega138k/project2_ae350_risc_gpio)
- You will need to use a debugger to load this to RAM.
```
gdb-multiarch
file u-boot
target remote localhost:2331
mon reset
restore u-boot
restore u-boot.dtb binary 0x00200000
```

You should get:
```
U-Boot 2025.01-00772-gae259b7f5b86-dirty (Jan 21 2025 - 11:28:13 +0100)

CPU:   riscv
Model: andestech,a25
DRAM:  1 GiB
Core:  20 devices, 15 uclasses, devicetree: board
Flash: ## Unknown flash on Bank 1 - Size = 0x00000000 = 0 MB
0 Bytes
MMC:
Loading Environment from SPIFlash... jedec_spi_nor flash@0: unrecognized JEDEC id bytes: ff, ff, ff
*** Warning - spi_flash_probe_bus_cs() failed, using default environment

In:    serial@f0300000
Out:   serial@f0300000
Err:   serial@f0300000
Net:   no alias for ethernet0

Warning: mac@e0100000 (eth0) using random MAC address - b6:e1:15:14:88:ac
eth0: mac@e0100000
Hit any key to stop autoboot:  0
RISC-V # 

```
