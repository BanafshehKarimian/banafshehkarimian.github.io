---
title: "Multi-agent robotic hand push and grasp"
excerpt: "Python, Vrep_Pro, RL, Multi-agent Robotics<br/><img src='/images/height.png'>"
collection: portfolio
---
<p align="justify"> The main aim of this project was extending the existing visual pushing grasping project of the Princeton university to a multi-agent robotics environment.
<a href="https://vpg.cs.princeton.edu/">The visual pushing grasping project of the Princeton university</a> highlights the importance of pushing objects before grasping them for simplifying the task of grasping. The part of this research that we focused on 
is an R.L. algorithm, which first converts the colored input picture into a height map and rotates it 6 times by 22.5 degrees. These height maps are inputs of two 
Fully Convolutional Networks that are used for calculating Q-values of each pixel. These Q-values show two selected points, one for pushing and one for grasping. The applied R.L algorithm rewards 1 for each successful grasp and 0.5 for each push which results in a noticeable difference to the environment. The outputs of this work was noticeable, so we tried to extend it to a multi-agent environment. 
We added another UR5 arm to the environment and altered the algorithm in two ways. One: we separated the tasks of pushing and grasping so that one robotic arm had only the task of grasping objects and the other had the task of pushing objects, and Two: both performing grasping and pushing at the same time, but without colliding to each other. Although the second case has the advantage of parallel working, learning speed of the first case was about a half less than that of the second case. In addition, after increasing the collision penalty for the second case the average collision reduce by 1/3. </p>