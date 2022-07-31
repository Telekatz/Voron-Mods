# Klipper

## Building and flashing the micro-controller

### menuconfig Settings

* Enable extra low-level configuration options: yes
* Micro-controller Architecture: STMicroelectronics STM32
* Processor model: STM32F072
* Bootloader offset: 8KiB bootloader
* Clock Reference: 8 MHz crystal
* Communication interface: CAN bus (on PB8/PB9)
  * CAN bus speed: 500000

### Flashing
  
Follow the instructions for the [CanBoot bootloader](https://github.com/Arksine/CanBoot).  
  
## Printer configuration

[Example configuration](CW2-CAN.cfg)