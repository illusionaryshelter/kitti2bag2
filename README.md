## Build

```
cd ~/your_ws/src
git clone https://github.com/illusionaryshelter/kitti2bag2.git
cd ..
colcon build --packages-select kitti2bag2
```

## Run

First you need to go to the [KITTI website]([The KITTI Vision Benchmark Suite](https://www.cvlibs.net/datasets/kitti/raw_data.php)) and download the raw data package(including [synced+rectified data] and [calibration]).

The extracted directory looks like:

```
├── 2011_09_30_drive_0018_sync
│   ├── image_00
│   ├── image_01
│   ├── image_02
│   ├── image_03
│   ├── oxts
│   └── velodyne_points
├── calib_cam_to_cam.txt
├── calib_imu_to_velo.txt
└── calib_velo_to_cam.txt
```

You can then run kitti2bag2 in the following format:

```
ros2 run kitti2bag2 kitti2bag [calibration_path] [dataset_path] [output_path] [threshold(unrecommand)]
```

such as:

```
ros2 run kitti2bag2 kitti2bag 2011_09_26/ 2011_09_26/2011_09_26_drive_0084_sync/ ./kitti07
```

## Output

The following topics are included in the output bag:

```
topics_with_message_count:
    - topic_metadata:
        name: /kitti/velodyne_points
        type: sensor_msgs/msg/PointCloud2
        serialization_format: cdr
        offered_qos_profiles: ""
      message_count: 2762
    - topic_metadata:
        name: cam01/camera_info
        type: sensor_msgs/msg/CameraInfo
        serialization_format: cdr
        offered_qos_profiles: ""
      message_count: 2762
    - topic_metadata:
        name: cam02/camera_info
        type: sensor_msgs/msg/CameraInfo
        serialization_format: cdr
        offered_qos_profiles: ""
      message_count: 2762
    - topic_metadata:
        name: cam00/camera_info
        type: sensor_msgs/msg/CameraInfo
        serialization_format: cdr
        offered_qos_profiles: ""
      message_count: 2762
    - topic_metadata:
        name: cam00/image_raw
        type: sensor_msgs/msg/Image
        serialization_format: cdr
        offered_qos_profiles: ""
      message_count: 2762
    - topic_metadata:
        name: kitti/oxts/imu
        type: sensor_msgs/msg/Imu
        serialization_format: cdr
        offered_qos_profiles: ""
      message_count: 2762
    - topic_metadata:
        name: cam03/image_raw
        type: sensor_msgs/msg/Image
        serialization_format: cdr
        offered_qos_profiles: ""
      message_count: 2762
    - topic_metadata:
        name: /tf
        type: tf2_msgs/msg/TFMessage
        serialization_format: cdr
        offered_qos_profiles: ""
      message_count: 2762
    - topic_metadata:
        name: /kitti/transform_imu
        type: geometry_msgs/msg/TransformStamped
        serialization_format: cdr
        offered_qos_profiles: ""
      message_count: 2762
    - topic_metadata:
        name: cam03/camera_info
        type: sensor_msgs/msg/CameraInfo
        serialization_format: cdr
        offered_qos_profiles: ""
      message_count: 2762
    - topic_metadata:
        name: cam02/image_raw
        type: sensor_msgs/msg/Image
        serialization_format: cdr
        offered_qos_profiles: ""
      message_count: 2762
    - topic_metadata:
        name: cam01/image_raw
        type: sensor_msgs/msg/Image
        serialization_format: cdr
        offered_qos_profiles: ""
      message_count: 2762
    - topic_metadata:
        name: /kitti/pose_imu
        type: geometry_msgs/msg/PoseStamped
        serialization_format: cdr
        offered_qos_profiles: ""
      message_count: 2762
```

## TODO

add the Gps msg to bag.