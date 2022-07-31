# PCB design files 

![Image of Clockwork2 CAN board](/../Images/Clockwork2 CAN.jpg)

The board is designed with [Circuitmaker](https://www.altium.com/circuitmaker)

The design and fabrication files are available on the Circuitmaker page:

* [Clockwork2 board](https://workspace.circuitmaker.com/Projects/Details/Telekatz/Clockwork2-CAN-Silentstepstick-Rev-C)
* [Stealthburner board](https://workspace.circuitmaker.com/Projects/Details/Telekatz/SB-Headerboard-Rev-B)

## How to order PCB

Fabrication files are available for JLCPCB. Choose the following settings:

### PCB

* Gerber file: Select `FAB*.zip`
* PCB Thickness
  * Clockwork2 board: 1.6 mm
  * Stealthburner board: 1.0 mm
* Remove Order Number: Specify a location

### PCB Assembly

* Assembly Side:
  * Clockwork2 board: Bottom Side
  * Stealthburner board: Top Side
* Tooling holes: Added by Customer
* BOM file: Select `BOM*.csv`
* CPL file: Select `Pick Place for*.zip`

# Bootloader

The [CanBoot bootloader](https://github.com/Arksine/CanBoot) is recommended for the board.

## menuconfig Settings

* Processor model: STM32F072
* Clock Reference: 8 MHz crystal
* Communication interface: CAN bus (on PB8/PB9)
  * CAN bus speed: 500000
* Application start offset: 8KiB offset
* Support bootloader entry on rapid double click of reset button: yes
* Enable bootloader entry on button (or gpio) state: no
* Enable Status Led: yes
  * Status LED GPIO Pin: PB5

## Flash CANBoot
  
To flash the CANBoot bootloader connect the board via USB. Because the board can not be powered over USB connect also 24V to the board. To enter the STM32F072 build in DFU bootloader connect the two BOOT0 pads on the board while pressing reset. Use dfu-util to flash CanBoot:

`dfu-util -d 0483:df11 -a 0 -R -D  canboot.bin -s0x08000000:leave`

# Pinout

## Top Layer

![Pinout Top Layer](/../Images/PCB pinout top.jpg)

## Bottom Layer

![Pinout Bottom Layer](/../Images/PCB pinout bottom.jpg)

## Mating Connectors

| Connector | Type | P/N |
| --------- | ---- | --- |
| Power/CAN | Micro-Fit 3.0 | 0430250410 |
| Hotend | Micro-Fit 3.0 | 0430250410 |
| Extruder Stepper | JST-PH | PHR-4 |
| Probe | JST-PH | PHR-3 |
| Endstop 1 | JST-PH | PHR-3 |
| Endstop 2 | JST-PH | PHR-2 |
| T1 | JST-PH | PHR-2 |
| Fan 3 | PicoBlade | 0510210300 |
| Filament Switch | JST-SH | SHR-03V-S-B |
| Serial | JST-SH | SHR-04V-S-B |
  
## SB Fan Connection

| Solder Pad | 2 Wire Fan | 3 Wire Fan | 4 Wire Fan |
| ---------- | ---------- | ---------- |----------- |
| V+         | V+         |  V+        | V+         |
| PWM        | GND        |  GND       | PWM In     |
| RPM        |            |  RPM Out   | RPM Out    |
| GND        |            |            | GND        |

![Image of SB Header Board](/../Images/SB Header Board.jpg)

## CAN bus termination

Connect the two solder pads marked CAN to activate the 120 Ohm termination resistor.