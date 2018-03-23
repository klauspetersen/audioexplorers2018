===================================
Simulate an embedded audio platform
===================================

This document
------------
The newest version of this document is found at:
https://github.com/klauspetersen/audioexplorers2018/blob/master/challenge.rst

The scenario
------------
When designing hearingaids, we are moving on the edge of what is possible. The size of a hearingaid keeps getting smaller which means that the battery and components also gets smaller. These constraints demands that the chipdesign and firmware must be extremely effective. It must deliver a lifechangeing experience using almost no power and no space.

To get all the performance out of your system, you must have full control of how your firmware is running on the device, therefore all our firmware is coded in C.

The challenge
-------------
Simulate an embedded platform consisting of a RISC-V processor and peripherals. The processor will be running a next-generation open source real-time operating system (RTOS) called Zephyr (https://www.zephyrproject.org/), to which Oticon is an active contributor.
The challenge consists of multiple objectives. Feel free to complete any number of them.

The setup
---------
The embedded *hardware* platform will consist of the following:
- RISC-V
- SPI
    - Serial NOR flash (MT25Q)
- I2S
    - Audio input
- I2S
    - Audio output
- Timer

.. image:: https://github.com/klauspetersen/audioexplorers2018/blob/master/hw_diagram.png

The embedded *software* platform will consist of the following:
-   Application 
-   Zephyr RTOS
-   Drivers
-   Emulation models

Objectives
----------
Write an emulation of the MT25Q using QEMU. Feel free to be inspired by similar code found online.
    - Implement the following functions:
      * READ
      * WRITE
      * ERASE
    - Include timing information from the datasheet in the model

Write an emulation of the audio-path using QEMU:
    - Write an emulation of audio input at the I2S peripheral. Feel free to be inspired by similar code found online.
    - Write an application running in a zephyr thread that manipulates the audio data in some way.
    - Write an emulation of audio output at the I2S peripheral. Feel free to be inspired by similar code found online.

Write an application that performs write/reads from the serial NOR flash while streaming audio through the I2S:
    - Read and write at random intervals to the serial NOR flash.
    - Use the Zephyr kernel to guarantee that the real-time requirements are complied with.
    

Getting started
---------------
Follow the getting started guide:
https://github.com/klauspetersen/audioexplorers2018/blob/master/gettingstarted.rst
