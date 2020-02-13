# using_multiple_realsense
Basic intructions on how to use multiple realsense cameras on ROS, future work will include example codes.


First, get the realsense *installed* and run:

>$ roslaunch realsense2_camera rs_camera.launch 

Now check the output:

>ROS_MASTER_URI=http://localhost:11311
>process[camera/realsense2_camera_manager-1]: started with pid [4969]
>process[camera/realsense2_camera-2]: started with pid [4970]
>[ INFO] [1581599124.594151116]: Initializing nodelet with 8 worker threads.
>[ INFO] [1581599124.877904223]: RealSense ROS v2.2.8
>[ INFO] [1581599124.877992873]: Running with LibRealSense v2.32.1
>[ INFO] [1581599124.921944668]: getParameters...
>[ INFO] [1581599125.182607318]: setupDevice...
>[ INFO] [1581599125.182699543]: JSON file is not provided
>[ INFO] [1581599125.182801804]: ROS Node Namespace: camera
>[ INFO] [1581599125.182893944]: Device Name: Intel RealSense D435
>[ INFO] [1581599125.182970159]: Device Serial No: 944122074477  <<<<<<<<<<<<<<<<<<<<<<<

copy the serial number of each camera!

now, to run that specific "944122074477" camera:

>$ roslaunch realsense2_camera rs_camera.launch camera:=cam_1 serial_no:=944122074477 filters:=spatial,temporal,pointcloud_

the image topic for that camera will be " /cam_1/color/image_raw " instead of the regular "camera/color/image_raw"

that's it! that way you can run as many cameras as you want! just remember to update the topic names when subscribing! (/cam_1/...)



