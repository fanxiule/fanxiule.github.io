---
title: "License Plate Detection"
excerpt: "License plate detection by using YOLOv3 and Seq-NMS <br/><img src='/images/yolo_plate_detection/sample1.png' width='300'>"
date: 2023-04-16
collection: project
---

In this work, we would like to perform license plate detection on videos. To achieve this, we applied a two-step process. First, we trained an object detection model, [YOLOv3](https://arxiv.org/abs/1804.02767), to detect license plates on images independently. Then we incorporated a post-processing step called [Seq-NMS](https://arxiv.org/abs/1602.08465) so that our pipeline can work better on videos.

YOLOv3 is a popular deep learning-based object detection model. With an RGB image input, it can predict bounding box proposals which encode the size and location of the bounding box, how likely an object is presented in this bounding box, and the object's class inside the box. We trained this model on a dataset with images of vehicles and ground truth bounding boxes of license plates on these vehicles. After training, we achieved an average precision of 0.7525. Some sample output images are shown below. (Blue indicates ground truth and red indicates predicted bounding boxes.)
<br/><img src='/images/yolo_plate_detection/sample2.png' width='250'>
<img src='/images/yolo_plate_detection/sample3.png' width='250'>
<img src='/images/yolo_plate_detection/sample4.png' width='250'>

Applying YOLOv3 alone to detect license plates from videos does not yield very good performance. The model sometimes cannot make consistent predictions for the same license plate at different time steps. To remedy this problem, we incorporated Seq-NMS as a post-processing step. Given bounding box proposals at the current time steps, Seq-NMS incorporates bounding box proposals obtained from previous time steps to improve the proposals at the current time. This procedure improves the consistency of license plate prediction results from videos. The video below demonstrates the difference between just YOLOv3 and YOLOv3 with Seq-NMS on license plate detection from a video.
<iframe width="560" height="315" src="https://www.youtube.com/embed/HJgpg_u922M" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

<br/>
More details can be found in our [code](https://github.com/fanxiule/YOLO3_plate_recognition).