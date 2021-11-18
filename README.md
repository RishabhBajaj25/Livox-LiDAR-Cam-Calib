# Livox-LiDAR-Cam-Calib

## Steps

1. Collect multiple rosbags with checkerboards

2. Extract laser map pcds (using [pcl_ros](http://wiki.ros.org/pcl_ros)) and images from each of the rosbags:

   1. ``` bash
      rosbag play <path_to_bag>
      
      rosrun image_view image_saver image:=/camera/color/image_raw
      
      rosrun pcl_ros pointcloud_to_pcd input:=/livox/lidar _prefix:=<path_to_output_folder>
      ```

3. Combine multiple laser scans to get a denser pointcloud. Open ~15 pcd in CloudCompare>Edit>Merge. And then save one dense pcd per rosbag.

4. Using one representative image and one pcd per rosbag, save them in one folder for images and one for pointclouds.

5. Use the Lidar Camera Calibrator tool in MATLAB 2021.

6. Choose the image and pointcloud directory.

7. Tune the thresholds to help detect the checkerboard in he pointcloud (dimension tolerance seems to be more sensitive than cluster threshold)

