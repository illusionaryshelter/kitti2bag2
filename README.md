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

