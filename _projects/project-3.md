---
title: "3D Reconstruction from Scratch"
excerpt: "Classical computer vision approach to detect key-points in a pair of images; establish correspondences between key-points in both images; compute the essential matrix and finally recover 3D coordinates of key-points.<br/><img width=800px src='/images/key_point_matching.png'>"
collection: projects
---

An exercise to refresh my mind on theory from multi-view geometry and apply that knowledge. Main reference literature for this project was [1].

# Depth Reconstruction from Scratch

The first goal of this project is to provide a modular way to the 3D reconstruction problem. Any of the intermediate steps listed below can be replaced by different algorithms of the same task. The second goal is to write everything from scratch, i.e. using numpy only.

## Feature Matching

 - Corner detection (Shi-Tomasi)
 - Feature descriptor (Histogram of Oriented Gradients)
 - Finding feature correspondences

## Determine Relativ Transformation of Cameras (Direct Approach)

 - Computing fundamental matrix E from point correspondences using coplanarity constraint $x'^T E x'' = 0$
 - Solve least squares problem to find E
 - From E can recover R, T but not the scale

## Depth Reconstruction

 - Recover the scaling by again leveraging a linear sytem of $n$ equations:

$$  M \lambda = 0 \rightarrow  \min_{\lambda} || M \lambda ||^2 = \min_{\lambda} (M \lambda)^{\top} M \lambda \;\; s.t. \; |\lambda| = 1 $$

- Scaling is still only defined up to a global scale (cannot distinguish between camera having moved by $d$ or $2d$.)

[1] Ma, Y. and Soatto, S. and Koseck, J. and Sastry, S.S., An Invitation to 3-D Vision: From Images to Geometric Models. 2005. Springer New York.