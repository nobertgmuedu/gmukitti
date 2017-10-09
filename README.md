GMU Cartographer setup to read Kitti Database.

Kitti Raw Datafiles available at: http://www.cvlibs.net/datasets/kitti/raw_data.php

Kitti2bag available at: https://github.com/tomas789/kitti2bag

I made minor modifications to Kitti2bag, and its source is included in scripts directory.

Top of my head things.

#1 - I removed all the stuff it was packaging into the bag file except the IMU & Velodyne Points.
#2 - I renamed the frame_ids, and topics to my liking.  (they match the configurations)
#3 - I removed the tf topic it was publishing and instead created a robot URDF file.

Note: the layout of the URDF file should be based off: http://www.cvlibs.net/datasets/kitti/setup.php

Both Lidar, and IMU.  X is direction travelled in car, Y points to driver side of car, and Z points straight up.

Lidar is in center of car, IMU is 0.32m to the driver side (left) of car in Y direction.
IMU is also positioned behind Lidar 0.81m (in negative X direction)
Lidar is at height (z) 1.73m, while IMU is at height 0.93m

I am using the  as the 'base link'

For convience of google, I have uploaded one of the bag files.
https://s3.amazonaws.com/kittigmu

There should be 5 loop closures, and if you play the bag through to the end, it should end up roughly where it started.  I have provided a PNG file for reference.

Any help or suggestions would be apprechated.

Examples:

roslaunch gmu kitti.launch bag_filenames:=/home/user/kitti.bag
roslaunch gmu kitti_write.launch bag_filenames:=/home/user/kitti.bag pose_graph_filename:=/home/user/kitti.bag.pbstream

