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

To get all the performance out of your system, you must have full control of how your firmware is running on the device.

The challenge
-------------
Simulate an embedded platform consisting of a RISC-V processor and peripherals. The processor will be running a next-generation open source real-time operating system (RTOS) called Zephyr (https://www.zephyrproject.org/), to which Oticon is an active contributor.

The RISC-V processor will be emulated using QEMU. This emulator is an integrated part of the Zephyr project.

Emulation and simulation is key when designing cutting edge embedded systems where the firmware development begins before the hardware platform is ready. 

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

The finished embedded *software* platform will consist of the following:
- Application 
- Zephyr RTOS
- Drivers
- Emulation models

QEMU implements a funcitonal model of the RISC-V processor but it does not emulate cycle-true timing. To include timing behavior we can make use of the Zephyr RTOS functions like threads and delays.

Objectives
----------
Write an emulation of the MT25Q.
    - Implement the following functions:
      * READ
      * WRITE
      * ERASE
    - Include timing information from the datasheet in the model. The datasheet can be found on github 
      - Use a separete zephyr thread with delays to emulate the timing. 

Write an emulation of the audio-path.
    - Write an emulation of audio input at the I2S peripheral. 
      - I2S audio input could be modeled as a simple thread pushing data onto a queue at regular intervals.
    - Write an emulation of audio output at the I2S peripheral. 
      - I2S audio output could be modeled as a queue to which data is pushed. The queue is emptied at regular intervals. 
    - Write an application running in a zephyr thread that does the following:
      - Reads audio data from the I2S input
      - Manipulates the audio data in some way. Be creative.
      - Write audio data to the I2S output

Write an application that performs write/reads from the serial NOR flash while streaming audio through the I2S:
    - Read and write at random intervals to the serial NOR flash.
    - Use the Zephyr kernel to guarantee that the real-time requirements of the audio path are complied with.
      - Play around with delays in the code and number of writes to flash, sizes of writes etc, to see how far you can push it before it affects the audiostream.

Getting started
---------------
Follow the getting started guide:
https://github.com/klauspetersen/audioexplorers2018/blob/master/gettingstarted.rst
