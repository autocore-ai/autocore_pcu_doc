# AutoCore PCU Documentation

**AutoCore Autonomous Driving Platform**


![autoCore](docs/images/Logo.png "AutoCore")


AutoCore is a modularized, flexible, and heterogeneous platform which simplifies the development, testing, and deployment of Autonomous Driving Technology. With automotive grade hardware and built-in safety mechanisms, this system is suitable for testing, demonstration or series production with minimized effort.

> We put real intelligence in every car. Because in our mind, autonomous driving is not only for selected few, but everyone.  
 --- The AutoCore People

For business and partnership, please visit our website: [www.autocore.ai](http://www.autocore.ai "AutoCore Homepage").
## Table of Contents

1. [Overview](#overview)  
   - [Hardware](#hardware)  
   - [System Architecture](#system-architecture) 
2. [Quick Start Guide](#quick-start-guide)  
3. [Technical specifications](#technical-specifications)  
   - [System block diagram](#system-block-diagram)  
   - [PCU system diagram](#pcu-system-diagram)  
   - [AutoCore SDK features list](#autocore-sdk-features-list)  

## Overview

### Hardware

AutoCore supports multiple computing hardware platforms based on Linaro 96Boards open standard (e.g. NXP, Renesas, HiSilicon, Xilinx) and also provide customized development boards (PCU Dev board). Customers could make their own choices among different platforms.

For more details please refer to:

* [Supported Hardware list](docs/Supported_hardware_list.md)  
* [AutoCore PCU Specification](docs/Pcu_specification.md)  

### System Architecture

As a customized project of Autoware.IO, part of the Autoware "Eco system", AutoCore aims to combine the Autoware software with automotive level computing hardware organically. AutoCore provides standard SDKs of the middle-ware, framework, "safety backbone" and relevant configuration tools which are fully compatible with Autoware.AI and Autoware.Auto open-source software.

To know about Autoware software and Autoware Foundation, please refer to:

* [Autoware.AI WiKi](https://gitlab.com/autowarefoundation/autoware.ai/autoware/wikis/home)  
* [Autoware Foundation](https://www.autoware.org/)

 AutoCore also provides variety of ready to use SDKs of autonomous driving features which are developed based on state of the art technology with full test and verification. To use the SDKs, just replace the corresponding features in Autoware. In current phase, SDKs mainly cover the middle-ware, framework, IDE tools, and some modules: "Safety Backbone", "Control", "Perception", and "Localization".A detailed system architecture is shown in the diagram below. In the future, AutoCore will continue to enrich the SDKs.

 Heterogeneous hardware + AutoCore SDKs + AutoWare.AI/Autoware.Auto, together they form an automotive level and ready to use platform. AutoCore also provide very handy tools like simulation environment, HD map/vector map editor, real-time calibration IDE etc.

![System Architecture](docs/images/System_architecture.png "System architecture")

With standardized hardware architecture and optimized SDK, AutoCore could support developers or customers to easily start based on various hardware solutions and Autoware open-source software, so together you could easily get a ready to use platform for autonomous driving development. 

## Quick Start Guide

1. [Hardware setup](docs/Hardware_setup.md "Hardware setup") -A customer guide for setting up AutoCore hardware components.

2. [PCU setup](docs/Pcu_setup.md "PCU setup") - Instruction of how to set up AutoCore PCU dev board.

3. [PCU Hardware Manual](docs/Pcu_hardware_manual.md) - User manual of AutoCore PCU dev board hardware.

4. [PCU SDK installation](docs/Sdk_installation.md)  -Steps to install the the SDK package of AutoCore.

5. [PCU SDK usage guide](docs/Sdk_guide.md) -AutoCore SDK usage manual.

6. [Simulation guide](docs/Simulation.md) -Test run AutoCore SDK in simulation environment with simulator.

7. [Simulation with Autoware.AI](docs/Simulation_autoware.md) -Test Autoware.AI with Autocore Simulator.

8. [Vehicle test guide](docs/Vehicle_test_guide.md) -To setup test vehicle and run a simple field test.


## Technical Specifications

### System block diagram

![Block diagram](docs/images/System_block_diagram.png "Block diagram")

### PCU system diagram

![PCU system diagram](docs/images/Pcu_sys_diag.png "PCU system diagram")

[PCU Schematics](docs/pdf/Pcu_schematics.pdf "PCU Schematics")  

[PCU Cable Diagram](docs/pdf/Pcu_cable_diagram.pdf "PCU Cable Diagram")  

### AutoCore SDK features list

[AutoCore SDK Feature List](docs/Sdk_feature_list.md)

## FAQs

