# CarND Capstone Project
  This is the capstone project for Udacity's Self Driving Car Nanodegree. 
  This Code was developed and tested using the Udacity - Simulator.


[//]: # (Image References)
[image1]: ./imgs/architektur.jpg
[image2]: ./imgs/image1_inf.png
[image3]: ./imgs/image2_inf.png
[image4]: ./imgs/image3_inf.png
##  SW - Architecture 
  
 The project consists of following Subsystems:
![][image1]
### Perception
For the traffic light detection was a node of the same name implemented. The used model bases on the Tensorflow object detection API. It ist a very reasonable decision to train the classifier using the provided workspace. When using AWS or local GPU one falls into troubles with dependecies (tf==1.3.0), nVidia Drivers and Tensorflow models. 

The training and evaluation data were extracetd from the provided rosbag. labelImg was used for labeling the data.  

The classifier was trained using simulator data only. Examples of the evaluation:

![][image2]
![][image3]
![][image4]


### Waypoint Updater

The waypoint updater publishes the waypoints corresponding to the trajectory to be controlled with the control subsystem. It decides about the velocity of the vehicle based on the data provided from the map( traffic light position) and traffic light detection module (state of the traffic light). There are three basic modi implemented: 1 constant drive - no traffic light in sight. 2 - slow down to classify the upcoming traffic light, 3 - stop on the traffic light if it is red or if the classifier is not able to detect the light state.

### Reference:

https://github.com/tensorflow/models/tree/master/research/object_detection

https://github.com/EdjeElectronics/TensorFlow-Object-Detection-API-Tutorial-Train-Multiple-Objects-Windows-10

https://github.com/tzutalin/labelImg
