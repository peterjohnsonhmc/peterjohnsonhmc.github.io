---
layout: post
title: FastSLAM
subtitle: Solving the Online SLAM Problem
cover-img: /assets/img/lidar_data.jpg
tags: [SLAM, FastSLAM, EKF, Kalman, Particle, Python, LiDAR, IMU, Fusion]
---

I am curently working on a FastSLAM implementation based on the algorithm in Probabalistic Robotics by Sebastian Thrun et al. The Dataset is from E205 State Estimation Course that I took in college. There is a single landmark, a post in an open field. The state to be estimated is pose (x, y, theta). The measurment is landmark range in x-y coordinates. 

The SLAM probem can be factored into estimating the path, and based on the path, estimating the map. In this algorithm, a Rao-Blackwellized Particle filter is used to do this. The particles are used for estimating the pose and each particle has a low dimensional EKF for estimating the landmark location. The first implementation uses known landmark correspondence for simplicity. My next iteration will use maximum liklihood data association to solve the landmark correspondence.

You can checkout the github repository [here](https://github.com/peterjohnsonhmc/SLAM).