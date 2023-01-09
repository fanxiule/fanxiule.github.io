---
title: "Open Arms"
excerpt: "A low-cost 7-DOF robotic arm designed for educational purposes <br/><img src='/images/open_arms/open_arms_full.jpg' width='300'>"
date: 2020-04-30
collection: project
---

The Open Arms project aims to develop an open source low-cost educational robotic arm with 7 degrees of freedom. It was created by a group of students at the University of Waterloo as a fourth-year design project. With the open source nature and low cost taken into considerations, the goal is to allow educational institutions and the general public to produce and modify this design more easily to promote education in robotics.

### Mechanical Design
All of the mechanical components can be either manufactured by laser cutting or acquired as off-the-shelf products. These design decisions allow the robot to be built more easily by schools and the general public. All manufactured components are made out of either plywood or acrylic sheets.
<br/><img src='/images/open_arms/open_arms_full_1.jpg' width='350'>
<img src='/images/open_arms/open_arms_full_2.jpg' width='350'>

To reduce the rotational speed and increase the output torque of a motor, a gearbox is typically used. Instead of purchasing existing gearboxes that are typically expensive, we designed our own custom cycloidal gearboxes.

<iframe width="560" height="315" src="https://www.youtube.com/embed/hXyF0u0IP_Q" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

### Electrical Design
The motors selected in this project are off-the-shelf stepper motors. Based on some preliminary calculations, the motors at different joints were sized carefully to provide different torque values. Each stepper motor is controlled by a DRV8825 stepper motor controller. 

One disadavantage of using a stepper motor is the lack of positional feedback. To solve this problem, we integrated a digital encoder in the gearbox design. The encoder and the motor are connected by a pinion-gear pair. The encoder can return the actual rotations of the stepper motor.
<br/><img src='/images/open_arms/open_arms_encoder_exploded.png' width='350'>
<img src='/images/open_arms/open_arms_encoder_nonexploded.png' width='350'>

The communication between all of the above electrical hardware is processed by an Arduino Mega board.
<br/><img src='/images/open_arms/open_arms_electrical.png' width='450'>

### Software Design
A ROS package is designed for a user to interface with the robot. ROS acts as an intermediate layer between the user and the robot itself. An overview of this strategy is shown below.
<br/><img src='/images/open_arms/open_arms_control.png' width='450'>

More specifically, the user can define the target pose or target joint positions for the robot. Then, the MoveIt package calculates a feasible path from the robot's current pose to the target one. The joint angles associated with this path are received by Arduino, which can move the corresponding joints on the robot.

To allow the use of the MoveIt library, we also created a MoveIt configuration package.
<iframe width="560" height="315" src="https://www.youtube.com/embed/sDRYHcYuMhA" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>