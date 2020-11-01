# 3D_ObjectDetection

3D Object detection is an active research problem for Perception of Autonomous Vehicles. The goal of our project is to understand the Frustum PointNet architecture and experiment with possible design modifications and evaluate their influence on performance metrics. There are various components in the 3D Object Detection Pipeline and we have experimented with a few modifications in the architecture and loss functions.

# DATASET

The dataset is collected from KITTI vision benchmark suite, which has been captured from a VW station wagon for use in mobile robotics and autonomous driving research. In total, the data of 6 hours of traffic scenarios has been recorded at 10-100 Hz using a variety of sensor modalities such as high-resolution color and grayscale stereo cameras, a Velodyne 3D laser scanner and a high-precision GPS/IMU inertial navigation system. 

The data contains 7481 training point-cloud data and images and 7518 testing point cloud data and images. The data falls into 2 types of classifications: 
- Based on the difficulty which depends on the amount of occlusion. 
- Based on the object type - Car, Pedestrian and Cyclist.

In this project we have add and integrated SqueezeDet architecture that was designed particularly for carrying out 2D object detection which can be deployed on embedded systems in Autonomous vehicles. Our motivation to use SqueezeDet was due to its significant low memory model size and high speed.

Also, most architectures which deal with 3D point clouds use Smooth L1 loss for regression, we investigated the use of L2 loss over this as well.

# EXPERIMENTS
For the Frustum PointNet architecture, 2D region proposals are extruded in the form of a frustum in the point cloud which helps to localize the objects of interest. We replaced the original Fast-RCNN 2D proposals by proposals from SqueezeDet. This would lead to different 3D frustum point cloud regions of interest and hence would change the overall results of the model as well.

# Results
We analyzed the performance of the network using 2 kinds of losses:

- Smooth L1 loss

![image](https://user-images.githubusercontent.com/49041896/97794385-9fe99e00-1bcf-11eb-88fc-b3deb3e2179f.png)

- MSE Loss

![image](https://user-images.githubusercontent.com/49041896/97794392-aed05080-1bcf-11eb-98b6-ee770b18d431.png)

The above figures show the 3D object detections with the two kinds of losses discussed in our approach. The pink color denotes the actual ground truth bounding box with blue color denoting the actual heading directions whereas the yellow and red color denote the predicted bounding box and heading direction respectively. We used Adam Optimiser with a learning rate of 10-3 with a batch size of 32 to get the following graphs. The MSE loss function initially gave a huge loss value before converging down to an optimum value both in the training and validation losses.


