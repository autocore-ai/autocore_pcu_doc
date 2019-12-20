# AutoCore PCU SDK Installation

## Table of Contents

1. [How to install on MPU](#how-to-install-on-mpu)  
2. [How to install on MCU](#how-to-install-on-mcu)  
3. [How to install Autoware.AI](#how-to-install-autowareai)  

## How to install on MPU

### Pre conditions
You should have a PCU dev board with pre-installed system (Ubuntu 18.04 and ros-melodic). If you would like to flash the image of MPU, please refer to [PCU setup guide](Pcu_setup.md#flash-open-source-mcu-image).

The required SDK package could be found on AutoCore [Resource Downloads page](Resource_download.md)

### Install

1. Download the package from the resource download page, e.g. "ros-melodic-autocore-pcu_0.0.1-1bionic-20191030-135420+0000_arm64.deb".

2. Install the package:

    `$sudo dpkg -i ros-melodic-autocore-pcu_0.0.1-1bionic-20191030-135420+0000_arm64.deb`

3. Source the path:

    There are two ways to source the path, you could choose whichever you like.

    - `$echo “source /opt/autocore/setup.bash” >>~/.bashrc`
    
    - `$source /opt/autocore/setup.bash`

### How to uninstall

If you want to remove the SDK software, please use the following:

`$sudo apt-get –purge remove ros-kinetic-autocore-pcu`


## How to install on MCU

### Pre conditions
You should have a PCU dev board.

The required SDK package could be found on AutoCore [Resource Downloads page](Resource_download.md)

### Install

1. Download the SDK package from the resource download page.

2. Flash the package to MCU:

3. Reset and Run.

### Uninstall

To uninstall MCU SDK package, you need to flash the MCU with original built

## How to install Autoware.AI

The adapted Autoware.AI (removed the modules that SDK covers) for PCU could be downloaded from AutoCore GitHub. 
