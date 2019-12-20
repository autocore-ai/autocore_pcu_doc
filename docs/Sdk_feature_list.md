# AutoCore SDK Feature List

## Feature list

- Platform (integrated in system image)
  - ROS2 support
  - Time synchronization
  - Health management
  - Data security and integrity
  - Redundancy hardware support
- [Drivers](#drivers) (integrated in system image)
  - Robosense
  - Velodyne
  - GNSS(NMEA)
  - Xsens IMU
  - UVC Camera
  - DNN Accelerator Driver
  - CAN Driver 
    - Continental Radar
    - Vehicle CAN Data
- [Perception](#perception)
  - [Voxel Filter](#voxel-filter)
  - [Ray Ground Filter](#ray-ground-filter)
  - [Euclidean Cluster](#euclidean-cluster)
  - [Depth Cluster](#depth-cluster)
  - CNN_LiDAR
  - [Multi LiDAR Fusion](#multi-lidar-fusion)
  - CNN_Camera (with accelerator)
  - Multi Radar Fusion
  - Camera LiDAR Fusion
- [Localization](#localization)
  - [GNSS Localizer](#gnss-localizer)
  - [NDT_LiDAR](#ndt-lidar)
  - [EKF_GPS-IMU-ODOM](#ekf-gps-imu-odom)
  - UKF_ODOM
  - NDT_Radar
- [Control]
  - MPC
  - Vehicle DBW Control
- Map
  - PointCloud Map loader
  - Vector map loader
    - Lanelet2 format support
  - Radar map support
- [Tools](#tools)
  - [IDE](#ide)
  - [Vector Map Editor]
  - [PointCloud Map Editor]
  - [Radar Map Editor]
- Simulation
  - Simulation Tool
  - Map Resources
  - Test Scenarios
  - Automated testing

---

> **Current release only support ROS1 interface/topic, default ROS master is IP address of br0 on PCU.**

---

### Drivers

> The drivers have already been integrated into the system image.

- Robosense
- Velodyne
- GNSS(NMEA)
- Xsens IMU
- UVC camera
- Radar
- Vehicle CAN Data

---

### Perception:

#### Voxel Filter

**Function**  
Voxel filter is used to down sample raw LiDAR point cloud data, reduces the data size while reserves the key information.

**Interfaces**  
Input topic： /points_raw  
Output topic： /filtered_points


**Performance**  
With default parameter leaf_size=2.0, using Robosense 32 LiDAR the CPU usage of PCU is within 10%.

#### Ray Ground Filter

**Function**  
Ray ground filter is a ground remover for LiDAR point cloud data. It splits the raw data into two part: ground, data without ground. 


**Interfaces**  
Input topic： /points_raw  
Output topic： /points_no_ground, /points_ground

**Performance**  
With default parameter settings，using Robosense 32 LiDAR, the CPU usage of PCU is within 20%.

#### Euclidean Cluster

**Function**  
Euclidean cluster is a simple LiDAR point cluster based on the euclidean distance of points. 

**Interfaces**  
Input topic：  
/points_no_ground

Output topic：  
/detection/lidar_detector/cloud_clusters  
/detection/lidar_detector/objects

**Performance**  
With default parameter settings，using Robosense 32 LiDAR, the CPU usage of PCU is about 40-50%.

#### Depth Cluster

**Function**  
Depth cluster LiDAR point cloud clustering module based on the depth information processing algorithm.

**Interfaces**  
Input topic：  
/points_no_ground

Output topic：  
/detection/lidar_detector/cloud_clusters  
/detection/lidar_detector/objects

**Performance**  
With default parameter settings，using Robosense 32 LiDAR, the CPU usage of PCU is about 30-40%.

#### Multi LiDAR Fusion

**Function**  
Based on different position and orientation of all LiDARs, the input of all LiDARs are united to form one point cloud frame. 

> Calibration file should be store in `~/.ros/.`
  Calibration tool and process will be published later.

**Interfaces**  
Input topic：  
/points_raw  
/ns1/rslidar1  
/ns2/rslidar2

Output topic：  
/points_calibrated

---

### Localization

#### GNSS Localizer

> Note: GNSS and EKF_GPS-IMU-ODOM are exclusive, if using high performance integrated navigation module, please launch GNSS function; With low cost GPS, please launch EKF_GPS-IMU-ODOM and disable GNSS.

**Function**  
This GNSS module translates GPS coordinate(in navsatfix formation) into local reference-frame UTM coordinate, and use local reference-frame UTM coordinate to provide initial position information for NDT_LiDAR localization. 


**Interfaces**  
Input topic：  
/micro_dds/gps_raw    --- *navsatfix formation*  
/micro_dds/gga_raw    --- *GGA data of GPS*  
/micro_dds/rmc_raw    --- *RMC data of GPS*  

Output topic：  
/gnss_pose  --- *Local reference-frame location in map*  

#### EKF_GPS-IMU-ODOM

> Note: GNSS and EKF_GPS-IMU-ODOM are exclusive, if using high performance integrated navigation module, please launch GNSS function; With low cost GPS, please launch EKF_GPS-IMU-ODOM and disable GNSS.

**Function**  
This EKF filter is used for multi sensor fusion localization. Based on different frequency and character of input data, EKF aims at provide a stable and accurate output location data even when GPS signal is blocked or drifted temporarily. 


**Interfaces**  
Input topic：  
/micro_dds/imu_raw    --- *IMU data*  
/byd_sdk/twist    --- *Vehicle speed (depends on DBW SDK)*  
/micro_dds/gga_raw    --- *GGA data of GPS*  
/micro_dds/rmc_raw    --- *RMC data of GPS*  

Output topic：  
/map_navsatfix  --- *longitude and latitude*  
/map_odometry  --- *Vehicle starting point in map*  
/gps_odometry  --- *GPS location data for debug and test*  
/gnss_pose  --- *Relative location in map*  

**Performance**  
With short period blocked or drifted GPS signal，e.g. passing a short tunnel with high speed, the filtered data remains stable and smooth. With long period blocked or drifted GPS signal, after GPS signal gets normal, the filtered data may sightly vibrate.

#### NDT_LiDAR

**Function**  
This is a LiDAR localization module based on normal distributions transform (NDT) matching algorithm. It calculates the position of the vehicle through comparing LiDAR data and HD map.

**Interfaces**  
Input topic：  
/points_raw  --- *Raw LiDAR point cloud input*  
/byd_sdk/twist    --- *Vehicle speed (optional)*   
/micro_dds/imu_raw    --- *IMU data*  
/map_odometry  --- *Vehicle starting point in map*  
/gnss_pose  --- *Relative location in map*  

Output topic：  
/ndt_pose --- *NDT estimated position*  
/ndt_stat --- *NDT status*  

---

### Tools

#### IDE

**Function**  
IDE visualizes the current output of relevant autonomous driving modules, e.g. planning trajectory, car localization, chassis status, LiDAR point clouds, etc. It provides human-machine interface for users to view hardware status, turn on/off of modules, calibrate parameters, and start the autonomous driving car. It also integrates debugging tools.

