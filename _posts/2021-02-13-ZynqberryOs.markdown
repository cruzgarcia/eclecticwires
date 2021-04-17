---
layout: post
title:  "Compiling ZynqberryOS"
date:   2021-02-13 22:00:00 +0100
categories: fpga zynq os
---

## Vivado project

Download the example porject from Trenz

After vivado has generated a bitstream, the hardware design can be exported to SDK. For that click on "Export Hardware".

    ![Export Hardware](/assets/vivado_export_hardware.png)
Following that, Launch SDK.

## Petalinux
        petalinux-create --type project --template zynq--name

This [SRC] should be the Vivado root folder project location, otherwise it will fail
        petalinux-config --get-hw-description /home/cgz/Projects/Zynqberry/zynqberrydemo2/prebuilt/hardware/m_512MB/zynqberrydemo2_m_512MB.xsa

For the Petalinux configuratio, follow the instructions from:

        https://www.hackster.io/news/an-fpga-take-on-the-raspberry-pi-petalinux-on-the-zynqberry-67dd421d25aa

## Loading the Booting images

        etalinux-package --boot --fsbl /home/cgz/Projects/Zynqberry/zynqberrydemo2/prebuilt/software/m_512MB/fsbl.elf --fpga /home/cgz/Projects/Zynqberry/zynqberrydemo2/vivado/zynqberrydemo2.runs/impl_1/zsys_wrapper.bit --u-boo


## Important concepts

* FSBL
    Zynq First Stage Boot Loader: Configures the FPGA with the bitstream and loads the OS.
