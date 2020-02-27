# How to Build MPU Image

> QorIQ Layerscape Software Development Kit (LSDK) is a complete Linux kit for NXP QorIQ ARM-based SoCs. LSDK can be built with flex-builder and be deployed with flex-installer. This page will use flex-builder to build MPU image.

For image deploy, please refer to [Flash EMMC](Pcu_setup.md#flash-emmc)

## Download Source Code

VCS  tool will be used for code download.

Download `1046a.repos` from MPU github project page.

```bash
# Install VCS
$ sudo  apt install python3-vcstool
# Code download
$ mkdir 1046a
$ vcs import 1046a<1046a.repos
```
If have errors when installing vcs tool, try to add the following key:  
`$ sudo apt-key adv --keyserver 'hkp://keyserver.ubuntu.com:80' --recv-key C1CF6E31E6BADE8868B172B4F42ED6FBAB17C654`

## How to build LSDK from scratch with flex-builder

Build tool: 1046a/flexbuild/tools/flex-builder  
Deploy tool: 1046a/flexbuild/tools/flex-installer  
Built target files: 1046a/flexbuild/build/images  
> Note: root access is required for building, so use `sudo` when building.

Some different build options are listed as below, please choose according to your requirement.
```bash
$ cd 1046a/flexbuild
$ source setup.env

# Autobuild all images (uboot, linux, apps, rootfs)
$ flex-builder -m ls1046afrwy -a arm64

# Build Linux
$ flex-builder -c linux -a arm64

# Build ubuntu rootfs
$ flex builder-i mkrfs-a arm64  

# Build uboot for sd card of ls1046afrwy
$ flex builder-c uboot-m ls1046afrwy-b sd 

# Build uboot for QSPI of ls1046afrwy
$ flex builder-c uboot-m ls1046afrwy-b qspi

# Compress ubuntu rootfs to *.tgz
$ flex-builder -i compressrfs -a arm64 

# Clean files except ubuntu rootfs
$ flex builder clean 
```
## Target Files

Compiled files: 1046a/flexbuild/build  
Build image files: 1046a/flexbuild/build/images

The following three files will be required for installation of the built image.

1. `bootpartition_LS_arm64_Its_4.14.tgz` is for SD card or EMMC partition  
   Note: `bootpartition_LS_arm64_Its_4.14_time.tgz` is generated according to build time, `bootpartition_LS_arm64_Its_4.14.tgz` is the latest.

2. `firmware_ls1046afrwy_uboot_sdboot.img` is Boot for SD card
   `firmware_ls1046afrwy_uboot_qspiboot.img` is Boot for QSPI  
   Please choose according to your boot device.
   
3. `rootfs_ubuntu_bionic_LS_arm64.tgz` is the image for file system.  
   Note: `rootfs_ubuntu_bionic_LS_arm64_time.tgz` is generated according to build time, `rootfs_ubuntu_bionic_LS_arm64.tgz` is the latest.

