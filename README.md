# SPI-Master-Transmit-Only-Test
Firmware for the various tests performed with the PIC18F26K83 microcontroller for the SPI module working as the master of a bus where only this device transmits data. Within this firmware there are a couple of test variations for sending a different number of bytes through different ways, after which a LED will be turned on.

## Setup
A breadboard with two PIC18F26K83 microcontrollers connected through two MCP2561 CAN transceivers is used as a testbench. 

![broadboard_can_bus_top_viewjpg](https://github.com/AlbertoRodriguezSanz/CAN-Bus-Test/assets/95371514/c0f4a20e-199d-4b0a-b0b2-8a69f7578277) 

For this test the PICkit4 in-circuit debugger/programmer will be used to load the firmware into the microcontroller. This needs to be connected to the microcontroller with the following pins.
- MCLR (needs to be connected through two series pull-up resistors (10kto Vdd)
- PGD
- PGC
- VDD
- VSS

The microcontrollers are connected through two MCP2561 CAN transceivers. For such short distances, the use of termination resistors is not required. The two connectors represent the PICKIT4 pins required for programming each of the two microcontrollers. 
![protoboard_schematic](https://github.com/AlbertoRodriguezSanz/CAN-Bus-Test/assets/95371514/cc8b1035-44ea-4e5a-bbfc-5b08e4b7b556)

  
## Requirements

Install MPLAB X IDE tool for Windows, Linux or MAC from the following link ([download link](https://www.microchip.com/en-us/tools-resources/develop/mplab-x-ide#tabs)).

## How to download the firmware to the PIC

Once MPLAB is opened, load the project through *File > Open Project* and then select the file `CAN_bus_x.mc3`, where X denotates the firmware for each of the microcontrollers.
This will open the work environment, where `main.c` is the code file that will be compiled into the PIC. The project properties are accessed through *Production > Set Project Configuration > Customize...*, where the PICkit4 needs to be selected in the *Connected Hardware Tool* menu.
![Screenshot from 2023-09-01 14-19-52](https://github.com/AlbertoRodriguezSanz/CAN-Bus-Test/assets/95371514/248a38f8-ebf5-4f62-97c1-47c6fd496216)

Modify the following options from the default parameters for the PICkit4 programmer from the Option categories dropdown menu.
-Power
  - Power target circuit from PICkit4.
  - Voltage Level: 5V.
- PICkit4 Tool Options
  - Program Speed: Low (Otherwise an error will pop up when trying to load the firmware).

Then, follow the next steps:
* Compile: `Production> Build Main Project`
* Program: `Production> Make and Program Device Main Project`
