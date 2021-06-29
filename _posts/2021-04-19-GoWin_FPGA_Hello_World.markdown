---
layout: post
title:  "GoWin FPGA Hello World!"
date:   2021-04-19 19:30:00 +0100
categories: fpga hdl
---

# GoWin LittleBee

Key Features:
    - GOWIN LittleBee 1NR9 FPGA 
    - 8 MByte internal SDRAM

Further information:
https://shop.trenz-electronic.de/en/TEC0117-01-FPGA-Module-with-GOWIN-LittleBee-and-8-MByte-internal-SDRAM?c=508

## Programmer
The first try with a an example design was not succesful. Unfortunately, my
wish to enjoy . Unfortunately there seems to be a couple of issues when running 
under linux above certain kernels. The good thing is that there is an open 
source alternative, namely openFPGALoader

        https://github.com/trabucayre/openFPGALoader

![Elegoo SmartRobot v4.0](/assets/gowin_hello_world/programmer_failed.png)

The procedure is pretty much straight forward. After the installation (which is well documented), 
it is a fresh breeze to flash the FPGA without trouble. 

openFPGALoader --board littleBee hello_world.fs

# Problems

* Console message:
        ../libkmod/libkmod-module.c:799 kmod_module_remove_module() could not remove 'ftdi_sio': Operation not permitted

In multiple post in internet seems that the Programme have problems in kernels above 5.* 
## Hardware 

![Elegoo SmartRobot v4.0](/assets/gowin_hello_world/littlebee_device_specs.png)

# Creating a Hello Worl application
The GUI offers directly the option to create a new Project. 

# TODO :)