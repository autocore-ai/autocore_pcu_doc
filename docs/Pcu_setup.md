# AutoCore PCU setup guide

> The *AutoCore PCU Setup Guide* provides the Instruction of how to set up AutoCore PCU dev board.

---
## Table of Contents

1. [Before you start](#before-you-start)
2. [Power up](#power-up)
3. [Connect from PC](#connect-from-pc)
4. [Flash operating system images](#flash-operating-system-images)
    - [Flash Open Source MCU image](#flash-open-source-mcu-image)  
    - [Flash Base MPU image](#flash-base-mpu-image)  
5. [Advanced network settings](#advanced-network-settings)

## Before you start

You should have a AutoCore PCU dev board set which contains the following items:

- PCU board
- Heat sink with fan
- DC power adapter
- MicroSD card with pre-installed system and software (optional)
- 2x ECU connector breakout harness

Also you need to buy a CR2032 3V battery which is not included in the package.

The default boot device - EMMC has been pre-installed with Ubuntu 18.04, and ros-melodic. If you would like to boot from SD card, you could either request a SD card with pre-installed system or flash by yourself under instructions in below section.

> Note: more advanced users looking to install a particular operating system should use this guide to [Flash operating system images](#flash-operating-system-images).


## Power up

1. Install the heat sink with fan to PCU board, and connect the fan cable to the socket.

2. Get a CR2032 3V battery and place it into the holder on board.  
    ![Battery Install](images/Battery_install.png)

3. Plug in the power supply, and other cables you want to use.  
> For cable pin assignment, please refer to [PCU Cable Diagram](pdf/Pcu_cable_diagram.pdf)

4. Turn on the main switch.


## Connect from PC

On your PCU board, you can see a label attached with IP address, username, password and QR code.  
![PCU Label](images/Pcu_label.png "PCU Label")

1. **Cable connection**  
   Connect PC to `fm1-mac1` / `fm1-mac6` / `fm1-mac10` Eth port (Blue) on PCU board with Ethernet cable (GbE, need Cat.5e or above).

2. **Configure static IP for PC**  
   You need to manually configure static IP for PC in order to connect with PCU, as there is no DHCP server running on PCU. The static IP should be different with PCU and within the same network segment. (e.g. 192.168.1.222)

    For Ubuntu18.04, you could use netplan to configure static IP:

    ```
    $ ls /etc/netplan
    $ sudo nano /etc/netplan/01-network-manager-all.yaml
    # Update the following items in the file:
    * dhcp4: no
    * addresses: [192.168.1.222/24] #IP and mask
    * gateway4: 192.168.1.1  #gateway
    $ sudo netplan apply
    ```
    You could also refer to https://linuxconfig.org/how-to-configure-static-ip-address-on-ubuntu-18-04-bionic-beaver-linux

3. **Connect to MPU via SSH or VNC**  
   SSH and VNC service has been enabled by default on PCU, so you could choose either way:  
    - SSH    
    `$ ssh user@192.168.1.239`   
    `# username and password please find on label`

    - VNC
    Note: If you would like to use VNC, you should start VNC server first:  
    `$ vncserver`  
    VNC server has been pre configured for `user` account.  
    Then you could connect from host PC:  
    `$ remmina`  
    `# Default username is same with ssh, default password is '123456'`

4. **Connect to MCU**  
   The IP of MCU is set to '192.168.1.150', you could also connect to MCU using this IP.

5. **Connect by micro USB port**  
    As an alternative, you could also choose to connect to PCU by micro USB (right one is for MPU as shown in figure below). 

    ![PCU USB MPU](images/Pcu_usb_mpu.png)

    For Linux users, you could use "Minicom" to connect to PCU. Please set as follows:

    ![USBtty Parameters](images/Usbtty_parameters.png)

    For other system users, the parameters are:

    | Parameter | Value |
    | --------- | ----- |
    | Baudrate  | 115200 |
    | Data      | 8 |
    | Stop bit  | 1 |
    | Parity    | None |
    | Hardware flow control | no |
    | Software flow control | no |

6. **Internet access**  
    Please be noted that `fm1-mac5` Eth port (RED) on PCU is used for external network (Internet access), the other 3 Eth ports are used for internal network (Other computing boards or PC). The network segment of internal and external must be different, otherwise, it will cause communication problem.

    Before you connect PCU to the Internet, please make sure to set DHCP server to different network segment from internal IP(192.168.1.x), e.g.: 192.168.2.x.  

    Then you can connect PCU to router, PCU will get automatic IP from it. To check connection status:  
    `$ ifconfig fm1-mac5`

    If you are not able to change the DHCP server network segment, and it conflicts with PCU internal network segment (192.168.1.x), you can follow the guide in **Note 2** to change internal IP. Please be careful when you do this, you may cause lost communication to PCU board, or some issues connecting to LiDAR.

> :information_source:**Note 1**: for Ethernet port assignment, please refer to the [PCU Hardware Manual](Pcu_hardware_manual.md).

> :information_source:**Note 2**: advanced users who want to configure each Ethernet port should follow the [Advanced network settings](#advanced-network-settings).

## Update system clock
Don't forget to update your system clock.

To check the current time status of your system clock: `$ timedatectl status`

To synchronize the system time:
```
# Enable ntp auto synchronize
$ sudo timedatectl set-ntp on

# Show current time and synchronize
$ date

# Syncronize to hardware clock
$ sudo hwclock --systohc
```

## Flash operating system images
PCU board is a heterogeneous platform, there are two individual operating systems running on it -- MCU and MPU. Two operating systems could be flashed individually. 

PCU have already installed OS on MCU and provided SD card card with pre-installed OS for MPU. This step is only required if you would like to re-install OS for MCU or MPU, or would like to do an update.

You will need another computer with an SD card reader or TI debug tool to flash the image.

### Flash Open Source MCU image

To flash OS for MCU(without SDK features), you will need:

- TI XDS-class debug probe, e.g. [XDS100V3](http://dev.ti.com/tirex/explore/node?node=AEFfTlaHQHUWL-seh4M4tA__FUz-xrs__LATEST) and JTAG cable
- PC install Code Composer Studio (CCS) v8.0 or above. [Download link](https://software-dl.ti.com/ccs/esd/documents/ccs_downloads.html#code-composer-studio-version-8-downloads)
- Build MCU_HAL source code

For MCU_HAL source code please go to: https://github.com/autocore-ai/pcu_mcu_hal

Please follow the instruction in the readme file in the Github repository to build and flash MCU.

### Flash Base MPU image

#### Flash EMMC

The on-board EMMC size is 64GB. Be sure to connect Jmp 1-3 to right position (1-2) before you start.

1. Download an image

    Official images with recommended OS and middle-ware are available on AutoCore [Resource Download page](Resource_download.md#mpu-images).

    Extract the zip file to a USB drive. Then plug the USB drive to PCU

2. Boot from QSPI

    Power on the board, and hit any key to enter Uboot mode during start up:  
    `Hit any key to stop autoboot:  10`  
    Then boot from QSPI:  
    `$ run qspi_bootcmd`
    The default user name for QSPI system is `root`.

3. Install from USB
    
    ```bash
     #step 1: 
     # Unzip the archive to your USB drive and run the scipt
     cd /run/media/PATH_TO_USBDRIVE
     source ./setup.env

     #step 2: 
     flex-installer -i pf -d /dev/mmcblk0

     # step 3: 
     cd /run/media/mmcblk0p3
     # move the following files to this path
     # - bootpartition_<arch>_<version>.tgz
     # - rootfs_<OS>_<version>.tgz
     # - firmware_ls1046ardb_uboot_sdboot.img
     
     # step 4: 
     flex-installer -b bootpartition_<arch>_<version>.tgz -r rootfs_<OS>_<version>.tgz -f firmware_ls1046ardb_uboot_sdboot.img -d /dev/mmcblk0
     ```

#### Flash SD card

To install MPU image(without SDK) on an SD card, you will need another PC with an SD card reader. The minimum recommended card size is 64GB, and the speed should be at least class 10 A1, it is strongly recommended to use high speed SD card, e.g. class U3, A2. 

1. Download an image

    Official images with recommended OS and middle-ware are available on AutoCore [Resource Download page](Resource_download.md#mpu-images).

2. Image writing tool

    Install the image writing tool whichever you like to install the downloaded image on SD card.

    **balenaEtcher** is suggested as a very handy tool that works on Mac OS, Linux and Windows.

    To download: https://www.balena.io/etcher/

3. Write the image to SD card

    - Connect an SD card reader with the SD card plugged in
    - Load the MPU image file (.img or .zip) into the tool
    - Flash until finish

    For Linux users, you could also use the following command (replace the path, name, device name with your own):
    `$ sudo gzip -dc yourpath/xxx.gz |sudo dd of=/dev/mmcblk0`

4. Plug and boot

    Make sure to connect Jmp 1-3 to right position (2-3) before you start. Now you can plug in the SD card to PCU and power up. The system should be ready to work. Please be noted that the image only contains OS and middle-ware, if you would like to use more functionalities, please install AutoCore SDK follow this guide: [PCU SDK installation](Sdk_installation.md)

5. If you need to reset

    The MPU reset button (SW1500) lies next to the main switch, press it to reset.

#### Flash QSPI

The on board 64M QSPI flash is reserved for boot and non-volatile data storage. Normally you do not need to flash it. Update of QSPI flash is only required when update boot or the Linux kernel in it. Please only flash it when you understand what you are doing and be aware that re-flash of QSPI incorrectly may cause loss of non-volatile data like MAC address.

To flash QSPI, you need to **boot from EMMC or SD card**. Please refer to [PCU Hardware Manual](Pcu_hardware_manual.md#emmc) for hardware setup.

Before you start, please record the **default MAC address** of all ports, as the flash process will erase the information. To read the current MAC address, enter Uboot:
```bash
bdinfo
...
eth0name    = FM1@DTSEC1
ethaddr     = 00:02:34:23:39:f0
eth1name    = FM1@DTSEC5
eth1addr    = 00:02:34:23:39:f1
eth2name    = FM1@DTSEC6
eth2addr    = 00:02:34:23:39:f2
eth3name    = FM1@DTSEC9
eth3addr    = 00:02:34:23:39:f3
eth4name    = FM1@DTSEC10
eth4addr    = 00:02:34:23:39:f4
...
```

1. Install TFTP tool

   You could install any TFTP tool, for Ubuntu please install tftp and finish the configuration.

   Set the path of image to be flashed.

2. Enter Uboot and setenv

   Power on the board, press any key during start up to enter Uboot mode.

   Make the following configuration:

   ```bash
   setenv ipaddr 10.20.24.113   #PCU IP
   setenv serverip 10.20.24.23  #PC IP
   setenv ethaddr 00:04:9F:06:30:FE #PCU MAC address
   saveenv
   ```

3. Upload image

   `tftpboot 0xa0000000 firmware_ls1046afrwy_uboot_qspiboot.img`

4. Erase memory

   ```bash
   sf probe 0:0
   sf erase 0 +$filesize
   ```

5. Write image

   `sf write 0xa0000000 0 $filesize`

6. Post steps

   As the flash process have erased all data, MAC address need to be set manually. Please set MAC address recored before:
   ```bash
   setenv ethaddr 00:02:34:23:39:f0
   setenv eth1addr 00:02:34:23:39:f1
   setenv eth2addr 00:02:34:23:39:f2
   setenv eth3addr 00:02:34:23:39:f3
   setenv eth4addr 00:02:34:23:39:f4
   saveenv
   ```

## Advanced network settings

The network diagram of PCU is shown in figure below:  
![Network Diagram](images/Network_diagram.png)

By default, `/etc/init.d/firstrun_ac` is executed during start up as below:  
![Firstrun_ac](images/Firstrun_ac.png "Firstrun_ac")

1. **External Eth port**  
    External Eth port is the RJ45 port marked with "red" label, it connects to MPU.

    `dhclient&` is executed to bring up DHCP client, to automatically get IP address from DHCP server.

    This IP address **MUST** be in different segment with internal (192.168.1.x), the reason is that four ETh ports are all connected to MPU, but configured to different subnet. Conflicts of segment will cause switch not be able to distinguish subnet, and will transfer data to the first one in system.

    If you would like to configure static IP manually, remark `# dhclient&` and set IP similarly like above section.

2. **Internal Eth ports**  
    Internal Eth ports are the RJ45 ports that marked with "blue" label, it also connects to the MPU.

    Virtual bridge `br0` is created to bind Eth port `fm1-mac1`, `fm1-mac6`, and `fm-mac10` to it. this forms a sub network, and it connects to the internal switch from MPU.

    Sensors, other computer boards, and PC could connect to PCU through the three GbE ports. 

    If you would like to change the IP, for example `192.168.10.1` just update it in the file `/etc/init.d/firstrun_ac`.  
    `ifconfig br0 192.168.10.1`

    After reboot the system, new IP address will apply.

    In case of forgetting the configured IP, you could also use the Micro USB port to connect to PCU board. Please refer to step 4 in [Connect from PC](#connect-from-pc).

3. **AVB ports**  
    There are 3 AVB ports on Hirose 40pin ECU connector, which connects to the internal switch. They could also be used to connect to internal network.
