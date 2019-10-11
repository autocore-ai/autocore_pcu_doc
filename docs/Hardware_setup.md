# Autocore Hardware Setup Guide

## About This Guide

The *Autocore Hardware Setup Guide* provides the instructions to install all of the hardware components for the system.

## Key Hardware Components

The key hardware components include:

- Central Computing System ─ Autocore PCU dev board v1.0
    - For other options please refer to [Supported Hardware List](docs/Supported_hardware_list.md)
- Global Navigation Satellite System (GNSS) —  Select from:
    - Broadgnss RAC-P1
    - Topgnss GN-507 
    - U-Blox NEO-M8 products
- Inertial Measurement Unit (IMU) ─ [Xsense MTI-30](https://wiki.ros.org/ethzasl_xsens_driver)
- Light Detection and Ranging System (LiDAR) ─  You can select one of the following options, Robosense RS-Fusion_P3 is used for our case:
    - [Robosense RS-Fusion-P3](https://github.com/RoboSense-LiDAR/ros_rslidar/blob/master/doc/readme.md)
    - Robosense RS-LiDAR-32
    - [Velodyne HDL-64E](https://wiki.ros.org/velodyne)
    - Velodyne Puck series
- Cameras —  Select from:
    - USB cameras
    - GMSL cameras (with CCU Board)
- Radar —  Continental ARS408-21

## Additional Hardware Components

The following additional components may be required for additional features:

- An Ethernet switch
- A 4G router for Internet access
- A USB hub for extra USB ports
- A Laptop or NUC for visualization or debugging

## In vehicle

The vehicle must be modified with "drive-by-wire" technology either provided by OEMs or professional modification service company like TierIV or AutonomouStuff. In our case, we use a special version of BYD Qin EV provided by BYD, which is capible of controlling steering, accelaration, braking and some other actuators over CAN through pre-defined protocal.

- A power distributor panel must be installed to provide power to boards and sensors. It is suggested to add fuse frotection to each line in case of short circuit.
- A CAN cable connected to vehicle CAN network and relavant CAN protocal are required. PCU board (or other central computing board) need to get vehicle information from it.
- A custom-made rack in the trunck to mount the power distributor panel, AutoCore PCU ,other computing boards, and additional components.
- An Emergency stop button is requried to be mounted on the dashboard to trigger pre-defined safety actions.

