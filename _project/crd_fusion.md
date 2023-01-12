---
title: "CRD-Fusion"
excerpt: "A fast stereo-based self-supervised deep learning model that can compute both disparity and occlusion mask <br/><img src='/images/crd_fusion/crd_fusion_disp_0.png' width='300'><img src='/images/crd_fusion/crd_fusion_occ_0.png' width='300'>"
date: 2022-06-01
collection: project
---

In this work, we introduced a self-supervised stereo matching pipeline that can be run in real-time. The pipeline consists of two stages: a confidence generation and a self-supervised deep neural network.
<br/>
<img src='/images/crd_fusion/crd_fusion_pipeline.png' width='350'>
<br/>
This pipeline assumes that an initial disparity map (raw disparity map) is available from either a traditional stereo matching algorithm or from a commercial stereo camera. The confidence generation process first computes a confidence map to quantify the correctness of the raw disparity map. Then, the stereo images, raw disparity map, and confidence map are processed by a deep neural network trained in a self-supervised manner. The final outputs include a high-quality predicted disparity map and a corresponding occlusion mask to indicate occluded regions in the disparity map.
<br/>
<img src='/images/crd_fusion/crd_fusion_network.png' width='720'>
<br/>

A demo video of this pipeline is shown below. More details can also be found in our [paper](https://ieeexplore.ieee.org/abstract/document/9867106) published at the Conference on Robots and Vision 2022 and our [code](https://github.com/fanxiule/CRD_Fusion). 
<br/>
<iframe width="560" height="315" src="https://www.youtube.com/embed/axtEBveQJeo" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>