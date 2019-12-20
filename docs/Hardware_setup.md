# AutoCore Hardware Setup Guide

*The "AutoCore Hardware Setup Guide" provides the required hardware components to set up an autonomous driving system, including computing platform, sensors, and simulation environment or test vehicle.*

---

### Key Hardware Components

The key hardware components required to get the system working include:

- Central Computing System ─ [AutoCore PCU dev board v1.0](Pcu_specification.md)
    - For other options please refer to [Supported Hardware List](Supported_hardware_list.md)
- Global Navigation Satellite System (GNSS) —  Support standard NMEA, like:
    - Broadgnss RAC-P1
    - Topgnss GN-507 
    - U-Blox NEO-M8 products
- Inertial Measurement Unit (IMU) ─ [Xsens MTI-30](https://wiki.ros.org/ethzasl_xsens_driver)
- Light Detection and Ranging System (LiDAR) ─  You can select one of the following options, Robosense RS-Fusion_P3 is used for our case:
    - [Robosense RS-Fusion-P3, RS-LiDAR-32, RS-LiDAR-16](https://github.com/RoboSense-LiDAR/ros_rslidar/blob/master/doc/readme.md)
    - [Velodyne HDL-64E, VLP16, VLP32](https://wiki.ros.org/velodyne)
- Cameras —  Select from:
    - USB cameras （720p）
    - GMSL cameras (with CCU Board)
- Radar —  Continental ARS408-21

### Additional Hardware Components

The following additional components may be required for additional features:

- DC power supply
- An Ethernet switch
- A 4G router for Internet access
- A USB hub for extra USB ports
- A laptop or NUC for visualization or debugging
- Cables

### Simulation environment

We suggest to start from using simulation environment to build up your autonomous driving system. 

All that you need is a PC (i5 CPU, 16G ram, standalone graphics card preferred) that connect to central computing system via Ethernet or micro-USB cable. 

No sensors will be required in this case, AutoCore provides simulation tool and resources that compatible with Autoware software stack. 

For more information about how to use simulation tool, please refer to:

- [Simulation guide](Simulation.md).

### Test vehicle

If you are planning to deploy in vehicle for test purpose, the vehicle must be modified with "drive-by-wire" technology either provided by OEMs or professional modification service company like TierIV or AutonomouStuff. In our case, we use a special version of BYD Qin EV provided by BYD, which is capable of controlling steering, acceleration, braking and some other actuators over CAN through pre-defined protocol.

- A power distributor panel must be installed to provide power to boards and sensors. It is suggested to add fuse protection to each line in case of short circuit.
- A CAN cable connected to vehicle CAN network and relevant CAN protocol are required. PCU board (or other central computing board) need to get vehicle information from it.
- A custom-made rack in the trunk to mount the power distributor panel, AutoCore PCU ,other computing boards, and additional components.
- An Emergency stop button is required to be mounted on the dashboard to trigger pre-defined safety actions.

> :warning:**Warning: Please be noted that this system could only be use for test purpose with speed < 40 km/h in disclosed testing field, safety drivers (one or two) are mandatory to monitor the system and take proper reactions when required.**


### AutoCore default

TO DO
