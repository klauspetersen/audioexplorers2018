=============================
Simulate an embedded platform
=============================

This document
------------
The newest version of this document is found at:


The scenario
------------
When designing hearingaids, we are moving on the edge of what is possible. The size of a hearingaid keeps getting smaller which means that the battery and components also gets smaller. These constraints demands that the chipdesign and firmware must be extremely effective. It must deliver a lifechangeing experience using almost no power and no space.

To get all the performance out of your system, you must have full control of how your firmware is running on the device, therefore all our firmware is coded in C.

The challenge
-------------
Simulate an embedded platform consisting of a RISC-V processor and peripherals. The processor will be running a new open source real-time operating system (RTOS) called Zephyr (https://www.zephyrproject.org/), to which Oticon is an active contributor.

The embedded platform must consist of the following:
- RISC-V
- SPI
    - Serial NOR flash (MT25Q)
- I2S
    - Audio input
- I2S
    - Audio output

Objectives
----------
1.  Write an emulation of the MT25Q using QEMU
    a.  Implement the following functions:
        *   READ
        *   WRITE
        *   ERASE
    b.  Include timing information from the datasheet in the model

2. 

Getting started
---------------
