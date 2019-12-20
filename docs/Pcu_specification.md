# AutoCore PCU Specification

> **Perception Computer Unit Dev Board v1.0** -- Designed by AutoCore

## Table of Contents

1. [Overview](#overview)  
2. [Hardware](#hardware)  
3. [Interfaces](#interfaces)  
4. [Block diagram](#block-diagram)
5. [Software](#software)
6. [Applications](#applications)
7. [User Guide](#user-guide)

## Overview

![PCU Dev board](images/PCU_top_view.png "PCU Dev board")

PCU (Perception computer unit) Dev Board v1.0, designed by AutoCore under 96Boards open standard, is a development board for automotive applications as high-performance domain controller designed by AutoCore. PCU board integrates a lock-step MCU and an high performance MPU with it. Based on the MCU-MPU architecture, different ADAS / AD or relevant functions can be integrated with different functional safety levels up to ASIL D after ISO 26262. A wide variety of interfaces are provided to support vehicle networks connection, sensors and peripherals. Additional hardware accelerator could be connected via PCIe with additional computing power.

## Hardware
| Item           | Description   |
| -------------  | ------------- |
| MCU            | TI TMS570LC4357 (32-bit ARM Dual-Core Cortex-R5F) Automotive-grade micro controller |
| MPU            | NXP LS1046A (64-bit ARM Quad-Core Cortex-A72) |
| Memory         | 8GB DDR4 |
| Storage        | 64MB QSPI NOR, 64GB eMMC flash, Micro SD |
| Ethernet switch| NXP SJA1105s Automotive Ethernet Switch(5 1000M ports) |
| Power management| NXP advanced automotive power management IC|
| Input Voltage  |     9-30V        | 
| Environmental    |  Operating temperature: -40°C ~ +75°C ; Storage temperature: -55°C ~ +105°C  |
| Power Source:  | DC power: +9V to +30V, typical: 12V,5A |

## Interfaces
| Item           | Description   |
| -------------  | ------------- |
| CAN bus port   | x4            |
| FlexRay port   | x1            |
| Ethernet RJ45 jack | x4：100BASE-T1/ 1000BASE-T1 |
| Ignition input | x1            |
| USB3.0  Host connector | x2            |
| Micro USB connector    | x2            |
| Mini PCIe slot | x1: PCIe Gen2; USB2.0 |
| M.2 NGFF slot  | x1: PCIe Gen2 |
| Micro USB Connector| x2 |
| UART ports     | x6 RS232 serial interface ports|
| PPS IO ports   | x1 PPS input port; x4 PPS output ports|
| ADC input      | x1            |
| JTAG  debug connector | x2 |
| FAN connector  | x4 |
| Expansion Interface | low speed 40Pins expansion connector (3.3V I/O level) |
| SIM Card slot  | x1 (optional) |
| RF Antenna Interface |4G-LTE: x4;  C-V2X: x2; WiFi 2.4G/5G: x4 (optional) |
| Micro SD card slot   | x1 (optional) |
| Digital IO ports | x3 (optional) |

## Block diagram
![PCU block diagram](images/PCU_block_diagram.png "PCU block diagram")

## Software

### MCU Software

| Item           | Description                     |  System image  | Open Source | AutoCore SDK   |
| -------------  | -------------                   | :------------: | :---------: | :------------: |
| Operation System| FreeRTOS 8.2                   |        x       |      x      |                |
| MiddleWare     | eProsima Micro XRCE-DDS         |        x       |             |                |
| GNSS Driver    | NMEA Standard driver            |        x       |             |                |
| IMU Driver     | Xsens IMUs driver               |        x       |             |                |
| Radar          | Continental ARS408/208 driver   |        x       |             |                |
| Ultrasonic     | Ultrasonic sensor driver        |                |             |                |
| Time service   | Time service                    |        x       |             |                |
| Vehicle info   | Vehicle information from CAN    |                |             |        x       |
| Vehicle DBW    | Vehicle drive-by-wire CAN interface|             |             |        x       |
| Runtime framework| AutoCore runtime framework    |                |             |        x       |

### MPU Software
| Item           | Description                     |  System image  | Open Source | AutoCore SDK   |
| -------------  | -------------                   | :------------: | :---------: | :------------: |
| Operation System| Ubuntu 18.04                   |        x       |      x      |                |
| Kernel         | LTS kernel 4.14                 |        x       |      x      |                |
| MiddleWare     | ROS Melodic, ROS2 Dashing       |        x       |      x      |                |
| PCI-E Driver   | PCI-E driver to support Accelerators (edgeTPU, Movidius) |   x       |             |                |
| LiDAR driver   | Velodyne driver, Robosense driver|       x       |             |                |
| Camera driver  | UVC camera driver, GigE camera  |        x       |             |                |
| Localization   | LiDAR NDT                       |                |             |        x       |
| Localization   | GNSS/IMU/ODOM EKF fusion        |                |             |        x       |
| LiDAR detector | Euclidean cluster, depth cluster|                |             |        x       |
| LiDAR tracker  | IMM UKF PDA tracker             |                |             |        x       |
| Camera (with accelerator)| Object detection, traffic light, lane mark |  |      |        x       | 
| Fusion/Filter  | Multi LiDAR fusion, EKF, points down sampler, points preprocessor|  |     |  x  |
| Fusion/Filter  | LiDAR/Radar/Camera fusion       |                |             |        x       |
| Map            | Vector map / HD map support port|                |             |        x       |
| Runtime IDE client | AutoCore runtime IDE tool   |                |             |        x       |

### Tools
| Item           | Description    | Open Source Code | AutoCore SDK   |
| -------------  | -------------  | :------------: | :------------: |
| V-Map          | Vector map editor|         x    |        x       |
| PCD Map         | Point cloud map builder|       |        x       |
| Simulation     | Simulation tool and test scenarios|  |  x       |
| Runtime IDE    | AutoCore runtime framework management tool|  | x |


## Applications
PCU board follows 96Boards open standard, and it is compatible with Autoware open-source autonomous driving software. It could be used in several different ways in AD/ADAS application scenarios:

1. **Single board application:**   
    - Central ECU for L2/L3 ADAS functions.
    - Drive-by-wire safe controller of autonomous driving vehicle.
    - Object detection and fusion based on LiDAR and radar.
    - High resolution localization module.
    - HD map construction.

2. **Double board application:**
    - Full redundancy system.
    - L4 AD perception, localization, planning and control.  

3. **Multi board application:**    
    - Full L4 AD functions. (with extra ADCU)
    - Work together with other hardware platform or IPC.

## User Guide

Please go to the documentation page of AutoCore platform:

[AutoCore Documentation Page](../README.md)  
[PCU Hardware Manual](../pdf/Pcu_hardware_manual.pdf)  
[PCU setup](Pcu_setup.md)  

