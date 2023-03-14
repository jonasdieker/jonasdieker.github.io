---
title: "Motion Segmentation in Autonomous Driving"
excerpt: "Deep learning approach to produce binary masks for dynamic objects in a camera scene.<br/><img width=800px src='/images/CarlaSamples.jpg'>"
collection: projects
---

The goal of the project was to segment the dynamic objects in a scene. The crux lies in disentangling what motion in the scene comes from ego vehicle transformation and what from actually dynamic objects. The resulting binary masks can then be used downstream for evaluating dynamic objects.

![carla scene](/images/carla_scene.png)
![binary mask](/images/segmentation.png)

A major part of the contribution of this work is the generation of a dataset for the specific task of motion segmentation. As this is not a standard computer vision problem, limited ground truth data is available for training. A realistic multi-modal dataset was generated using the CARLA simulator by adjusting maps to include parked vehicles in addition to spawning a large number of moving vehicles and pedestrians.

Two distinc method were subsequently devised in order to perform motion segmentation on the created dataset. The first is a supervised method based on the U-Net model with focal loss.

The second approach is an unsupervised method, where multiple coupled sub-problems are solved simultaneously to generate its own ground truth. Separate networks predict the depth and optical flow of the scene, which together can be used to compute the ground truth binary mask. Initially, both the optical flow and depth networks were simply simulated by using our multi-modal dataset with future extensions additionally learning these two data.

The project can be found [here](https://github.com/jonasdieker/motion_segmentation).