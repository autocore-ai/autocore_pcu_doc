# AutoCore Resource Download

> This page lists all the resources released from AutoCore for download.

## AutoCore Release Package

### PCU 2.0

- [20230315 Release Package](https://mega.nz/folder/Y311lJiR#FFUO6TWve7cEehOjCf8kFA)
  - MPU image -> 0.5.0
  - MCU image -> 0.2.0

- [20201214 Release Package](https://mega.nz/folder/Gv4ghCwT#icz3xgfPDNcGPMyJNoaRgA/folder/S3BzRYBJ)
  - MPU image -> 0.5.0
  - MCU image -> 0.1.1

### PCU 1.0

- [20201214 Release Package](https://mega.nz/folder/Gv4ghCwT#icz3xgfPDNcGPMyJNoaRgA/folder/DjZ11SzK):  
  - MPU image -> 0.4.0  
- [20200417 Release Package](https://drive.google.com/drive/folders/1x5wRi-TlNaRCmvdS16eKSSMXALdyP52_):  
  - MPU image -> 0.3  
  - MPU SDK   -> 0.2.0   
  - IDE Tool  -> 0.2.17  
  - Simulator -> 0.1.11  
- [20200115 Release Package](https://drive.google.com/drive/folders/1F0tlbMCM7lO5IDlPPUWFtif8Xhl8I2G7):
  - MPU image -> 0.2  
  - Simulator -> 0.1.7
- [20191220 Release Package](https://drive.google.com/drive/folders/1bpyKItOvdNnwq9LrJNWNsJiK1Cw5GEaG):  
  - MPU image -> 0.1  
  - MPU SDK   -> 0.1.2  
  - MCU image   -> 0.1.0  
  - IDE Tool  -> 0.1.53  

### MPU Image

MPU images for PCU dev board v1.0 is based on Ubuntu 18.04 and ROS Melodic.  
For more information about the features of the image, please go to: [PCU Specification](Pcu_specification.md)

#### MPU Image for EMMC

| Version   | Notes     | Link |
| :-------: | --------- | ---- |
|**0.5.0** <br> 15/Mar/2023| 1.PCU2.0 support <br> 2.4 Channel Eth-CAN support <br> 3.Change flash method from flexbuild to dd  | [autocore-1046-ubuntu20.04-emmc-pcu2.0-sw0.5.0-20201210](https://mega.nz/folder/Gv4ghCwT#icz3xgfPDNcGPMyJNoaRgA/file/jvpmALJR) <br> Md5: 7914a8adf1da3ba3573c43bc5bcfe8df |
|**0.4.0** <br> 10/Dec/2020| 1.Update to Ubuntu 20.04 <br> 2. Add ptp server service <br> 3.ROS-foxy-desktop support | [autocore-mpu-ubuntu20.04-emmc-pcu1.0-sw0.4.0-20201210](https://mega.nz/folder/Gv4ghCwT#icz3xgfPDNcGPMyJNoaRgA/file/PzoWQJZD) <br> Md5: 73d1c48643eff146c96c195a53e0509b |
|**0.3** <br> 16/Apr/2020| Minor fixes   | [autocore-mpu-ubuntu-emmc-18.04-0.3-20200416](https://drive.google.com/file/d/1FJnRPxh_mpJ7Qoy2i9k5hi4OsfF1ZuDE/view) <br> Md5: b3e2e121eb18157e623b69ed2402ad3b|
|**0.2** <br> 16/Jan/2020| 1. Add EMMC support <br> 2. PCIe driver | [autocore-mpu-ubuntu18.04-0.2-20200116](https://drive.google.com/file/d/1Pl5UcRnBJ83lGZ8qg7_hdLSfWDwRtLyV/view) <br> Md5: 1607ec26dae2653b6f02f7e80107161d|

#### MPU Image for SD card

| Version   | Notes     | Link |
| :-------: | --------- | ---- |
|**0.5.0** <br> 10/Dec/2020| 1.PCU2.0 support <br> 2.4 Channel Eth-CAN support <br> 3.Change flash method from flexbuild to dd   | [autocore-1046-ubuntu20.04-sd-pcu2.0-sw0.5.0-20201210](https://mega.nz/folder/Gv4ghCwT#icz3xgfPDNcGPMyJNoaRgA/file/DzRh2YZD) <br> Md5: 56c0b923ffc16f481471ae7d9c243b38 |
|**0.4.0** <br> 10/Dec/2020| 1.Update to Ubuntu 20.04 <br> 2. Add ptp server service <br> 3.ROS-foxy-desktop support   | [autocore-1046-ubuntu20.04-sd-pcu1.0-sw0.4.0-20201210](https://mega.nz/folder/Gv4ghCwT#icz3xgfPDNcGPMyJNoaRgA/file/6n5HiAqA) <br> Md5: c49b17138900903170e3e9fd1e4f70a5 |
|**0.3** <br> 16/Apr/2020| Minor fixes   | [autocore-mpu-ubuntu-sd-18.04-0.3-20200416](https://drive.google.com/file/d/1hB1NBYjzUwYekgjXNGqbefEdTY1bsXa9/view) <br> Md5: 675e8cd4cf01ccc8a10c20985adead5d|
|**0.1** <br> 23/Dec/2019| Initial version | [autocore-mpu-ubuntu18.04-0.1-20191223](https://drive.google.com/file/d/14NLV8Xa01IUx5aRhvm6GW-ZFCZOtWcWw/view) <br> Md5: a255e74b9c0e0b9fc608f07d61feff5f|

### AutoCore SDK

SDK package releases for PCU dev board v1.0.  
To get the full feature list of these packages, please go to: [SDK feature list](Sdk_feature_list.md)

#### MPU SDK

- **Ubuntu 18.04, ROS Melodic**

|      Version               |   Notes    | Link |
| :------------------------: |  --------- | ---- |
| **0.2.0** <br> 15/Apr/2020 |  1. New feature: Ukf_fusion_Localizer, Radar_Localizer, Radar_Mapping <br> 2. Update module: Gnss_ekf_fusion, Gnss_Localizer <br> 3. Bug fix, performance and stability imporvement | [ros-autocore-pcu_0.2.0-1bionic-20200415](https://drive.google.com/file/d/1hwqg3iIWK-48E55n_M8yyo8rP0rwsENo/view) <br> Md5: 54d05970185bd656d4aa8d62cdcde349 |
| **0.1.2** <br> 21/Dec/2019 |  1. Update Runtime, localization, map <br> 2. Update simulation interfaces <br> 3. Update file system | [ros-autocore-pcu_0.1.2-1bionic-20191221](https://drive.google.com/file/d/175QmSnpV1Wru8KOyzM1bWAGTdlG9_2Nu/view) <br> Md5: 76d3b40a163c873bac804737b05cd468 |
| **0.0.1** <br> 30/Oct/2019 |  1. Initial version <br> 2. Modules: LiDAR detection, tracking, localization| Not available |

#### MCU Image

|      Version               |   Notes    | Link |
| :------------------------: |  --------- | ---- |
| **0.1.1** <br> 10/Dec/2020 |  1. Update FreeRTOS kernel version to 9.0 <br> 2. Add EEPROM <br> 3. Add 4 channel CAN-Eth router <br> 4. Add PTP client <br> 5. Add time zone conversion code <br> 6. Add remote IP address setting command <br> 7. Other debug commands | [PCU20_mcu_hw2.0_sw0.1.1_20201210](https://mega.nz/folder/Gv4ghCwT#icz3xgfPDNcGPMyJNoaRgA/file/L3xwnRKR) <br> Md5: 0c6fabaab5c98f77b0d57823abea5fdb |
| **0.1.0** <br> 20/Dec/2019 |  1. Initial version <br> 2. Modules: Drivers, BYD dbw, DDS, NTP | [pcu_mcu_hw2_sw0.1.0_20191220](https://drive.google.com/file/d/1fpJQY6kKG5-EArtChLajd4FS1bfZrEJK/view) <br> Md5: 96b5511614491f529219637a7c950207 |

### AutoCore IDE tool

|      Version                | OS    |  Notes    | Link |
| :------------------------:  | :---: | --------- | ---- |
| **0.2.17** <br> 23/Mar/2020 | Win   | **SDK version must be greater than 0.2**  <br> Support ROS2 <br> Add components navaigation by name <br> Compressed image msg visualization <br> Add visual console <br> Display component cpu usage, message freq <br> Improve performance and stability <br> | [autocore-ide-windows-0.2.17-20200323](https://drive.google.com/file/d/1gA38BLNpfnSENg7Q21BsgVPQabL-V34u/view) <br> Md5: 03a5877af6bc7a9329f84c2a88756af3 |
|                             | Linux |           | [autocore-ide-linux-0.2.17-20200323](https://drive.google.com/file/d/1rOg2yxU7Uvh6R6uEmE90BcimfXWdbk5H/view) <br> Md5: 6c37a07418e000d2cc29e0c58ba8d844 |
| **0.1.53** <br> 21/Dec/2019 | Win   | **SDK version must be greater than 0.1** | [autocore-ide-windows-0.1.53-20191221](https://drive.google.com/file/d/12X9zVqbQQIvNGs1aRTAlI1KpOOV9uTGd/view) <br> Md5: e030bbcfea0d60481fc367a1fb0a4f80 |
|                             | Linux |           | [autocore-ide-linux-0.1.53-20191221](https://drive.google.com/file/d/1gNOxzZZ-XOFg78Ki6o7urVNnsw-pAf2Y/view) <br> Md5: aa5a09a477c676d8a48a93521dd5fe6c |

### Simulation

AutoCore Simulator is now open source on Github, so later versions will not be updated here. Please download from AutoCore Simulator Github release page:

https://github.com/autocore-ai/autocore_sim/releases

|      Version               | OS  |  Notes    | Link |
| :------------------------: |:---:| --------- | ---- |
| **0.1.11** <br> 19/Feb/2020| Win | Bug fix  | [simu-0.1.11-20200219](https://drive.google.com/file/d/1rsO1O1no-DhFAadZFFMuWRZkP-cc4t_7/view) <br> Md5: 481c9b83617abb6f7232cdcd133cfa4c |
| **0.1.7** <br> 16/Jan/2020 | Win | Initial release  | [simu-0.1.7-20200116](https://drive.google.com/file/d/1zJPvnKSwlYfVd_1DS0GrwskQh6KDcyM_/view) <br> Md5: 2922c5f80bae4d10af07ba7e7f59fa5f |

### Map resources

Will be available soon.
