---
layout: post
title:  "Zynqberry Hello World on Vitis 2019.2"
date:   2021-02-14 12:50:00 +0100
categories: fpga zynq zynqberry
---

## Vivado Project

## Vitis
In Vitis, first of all it is necessary to create a hardware platform. 

![Kit's parts](/assets/vitis_create_hw_platform.png)

Select the option "Create from hardware specification (XSA)". This has been exported in Vivado.
Locate the XSA file.

After the hardware pltform has been created, it should look similar to the following:

![Created HW Platform](/assets/vitis_hw_platform_created.png)

Create an application project, and use the previouly created hardware platform.

![Creating an application](/assets/vitis_application.png)

In Domain, leave it to the default configurations. Selecte "Hello World" template.

To create a FSBL.

In case the error "This application requires xilffs library in the Board Support Package" appears.

![Modifying BSP](/assets/vitis_modify_bsp.png)

Include the xilffs for both!


![Creating a boot image](/assets/vitis_creating_a_boot_image.png)

## Launching Vitis



