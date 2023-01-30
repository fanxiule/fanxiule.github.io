---
title: "Adaptive Path Following"
excerpt: "An adaptive path following controller to allow a mobile robot to follow an initially unknown circular path <br/><img src='/images/adap_path_follow/Exp_Setup.jpg' width='300'>"
date: 2022-10-20
collection: project
---

In this work, we introduced a path following controller used by a differential drive mobile robot to follow a circular path whose parameters are initially unknown to the robot. Additionally, we incorporated localization ability such that the robot can identify its own pose by using landmarks with known positions. 
<br/>
<img src='/images/adap_path_follow/robot_path.png' width='250'>
<br/>

Our proposed design consists of three major components: an least-squares (LS) path estimator, a localization unit, and a cascade motion controller. The path estimator adopts a least-sqaures algorithm with a forgetting factor to estimate the center location and radius of the unknown circular path online. Meanwhile, the localization unit estimates the robot's pose based on the distance and bearing angle between the robot and the landmarks via an extended Kalman filter (EKF). The estimated path parameters and robot pose are used by the cascade motion controller with an inner loop and an outer loop to gerenate the appropriate control signals to move the robot.
<br/>
<img src='/images/adap_path_follow/arch.png' width='350'>
<br/>

We performed both simulation and experiment to verify the design. The results showed that the robot was able to correctly estimate the circular path, estimate its own pose, and follow the path. 
<br/>
<img src='/images/adap_path_follow/result.png' width='400'>
<br/>

More details can be found in our [paper](https://www.sciencedirect.com/science/article/pii/S2405896323001581) published at the IFAC Symposium on Robot Control 2022.