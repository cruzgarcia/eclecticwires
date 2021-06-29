---
layout: post
title:  "Zynqberry Hello World (Vitis 2019.2)"
date:   2021-06-28 12:00:00 +0100
categories: fpga zynq zynqberry
---

# Zynqberry

According to Trenz Electronic:

*The Trenz Electronic TE0726-03M is a Raspberry Pi compatible SoC module integrating a Xilinx Zynq-7010, 512 MByte DDR3L SDRAM, 4 USB ports, an Ethernet port and 16 MByte Flash memory for configuration und operation.*

![Zynqberry](/assets/zynqberry_hello_world/TE0726-03M_0.jpg)

## Hello World design 

The idea is to build a minimal Zynq system without any extra logic, bootloader and minimal software as a boilerplate for further designs.
The design sources are in the [zynqberry_hello_world](https://github.com/cruzgarcia/zynqberry_hello_world) repository.

# Vivado


There are some good and detailed tutorials in internet about how to build such a ZYNQ system, for example [Knitronics](https://www.knitronics.com/the-zynqberry-patch/getting-started-with-the-zynqberry-in-vivado-2018-2), I won't go here into detail.


The main steps are the following:

1. Create a block diagram in Vivado
2. Import an IP namely ZYNQ Processing System
3. Create a HDL Wrapper and let Vivado manage it
4. Compile it (synthesize, place and route and bitstream generation)
5. Export XSA

After the last step, you can move to Vitis.

## Vitis

For this project, I created a workspace specifically to allocate the FSBL and the hello world application. 
Main steps:
1. Create a workspace
2. First Stage Bootloader (FSBL), using the exported XSA from Vivado
3. Hello World example project

Some important points:

* When creating the hardware platform, in software specification select as operating system standalone and processor *ps7_cortexa9_0*, fianlly activate "Generate boot components". In Domain, leave it to the default configurations. Selecte "Hello World" template.

* When creating an application project use the previously created hardware platform. For a template, "Hello World" should be selected

* In case the error *"This application requires xilffs library in the Board Support Package"* appears, modify the Board Support Package (BSP) and include xilffs.
        
![Modifying BSP](/assets/vitis_modify_bsp.png)


# Building from the Bash/TCL script

After cloning the repository, the project (Vivado and Vitis) can be built with:

        ./project_build.sh

Grab a glass of red wine, it might take some time.

After the compilation is successful, you might see the "Done" in the terminal's last line, open Vitis and set the workspace to
*repository_path/vitis*. From there you can flash the application image to the QSPI. 
