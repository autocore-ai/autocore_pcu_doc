# AutoCore PCU SDK Installation

## Table of Contents

1. [How to install on MPU system](#how-to-install-on-arm-system)  
2. [How to install on MCU](#how-to-install-on-x86-64-computer)  
3. [How to uninstall](#how-to-uninstall)
3. [How to install Autoware.AI](#how-to-install-autowareai)  

## How to install on Arm system

### Pre conditions
You should have a Arm system with (Ubuntu18.04 and ros-melodic) or (Ubuntu16.04 and ros-kinetic) intalled, e.g. a PCU dev board with pre-installed system.

The required SDK package could be found on AutoCore [Resource Downloads page](Resource_download.md)

### Install

1. Download the package according to your system, e.g. "ros-melodic-autocore-pcu_0.0.1-1bionic-20191030-135420+0000_arm64.deb" from the resource download page. Please double check the package is for "Arm64".

2. Install the package:

    `$sudo dpkg -i ros-melodic-autocore-pcu_0.0.1-1bionic-20191030-135420+0000_arm64.deb`

3. Source the path:

    There are two ways to source the path, you could choose whichever you like.

    - `$echo “source /opt/autocore/setup.bash” >>~/.bashrc`
    
    - `$source /opt/autocore/setup.bash`

## How to install on x86-64 computer

### Pre conditions
You should have a x86-64 computer with (Ubuntu18.04 and ros-melodic) or (Ubuntu16.04 and ros-kinetic) intalled. For ROS insatallation, please refer to www.ros.org.

The required SDK package could be found on AutoCore [Resource Downloads page](Resource_download.md)

### Install

1. Download the SDK package according to your system, e.g. "ros-kinetic-autocore-pcu_0.1.1-1xenial-20191030-135420+0000_amd64.deb" from the resource download page. Please double check the package is for "Amd64".

2. Install the package:

    `$sudo dpkg -i ros-kinetic-autocore-pcu_0.1.1-1xenial-20191030-135420+0000_amd64.deb`

3. Source the path:

    There are two ways to source the path, you could choose whichever you like.

    - `$echo “source /opt/autocore/setup.bash” >>~/.bashrc`
    
    - `$source /opt/autocore/setup.bash`


## How to uninstall

If you want to remove the software, please use the following:

`$sudo apt-get –purge remove ros-kinetic-autocore-pcu`


## How to install Autoware.AI

