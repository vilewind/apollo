# Introduction
The radar4d detection module receives the 4d radar driver message, which includes the radar point cloud and the tracked objects (optional).
The original tracked objected are not used. Instead, obstacles are detected and tracked through the radar point cloud, then sent to the multi-sensor fusion module.

# Directory Structure
```
radar4d_detection
├── BUILD     // bazel build file
├── README.md
├── app       // main process
├── conf      // dag config file
├── cyberfile.xml  // package description file
├── dag
├── data      // lib's configuration file
├── interface
├── launch
├── lib       // algorithm library
├── proto     // proto file
├── radar4d_detection_component.cc  // component
└── radar4d_detection_component.h
```

# Input and Output
## Input
| Channel              | Type                            | Description         |
| -------------------- | ------------------------------- | -----------------   |
| `/apollo/sensor/oculii/PointCloud2`  | `OculiiPointCloud`  | 4d radar drive message |

## Output
| Channel              | Type                            | Description          |
| -------------------- | ------------------------------- | -------------------- |
| `/perception/inner/PrefusedObjects`  | `onboard::SensorFrameMessage`  | frame contains object detection |

# How to run
In most cases, the radar4d detection module needs to work with the multi-sensor fusion module. If you want to debug the radar4d detection module separately and view the detected obstacle information, you can combine the `msg_adapter` module.

Run the command as follows.
```
cyber_launch start modules/perception/launch/perception_radar4d.launch
```
