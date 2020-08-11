---
layout: post
title: FastSLAM
subtitle: Solving the Online SLAM Problem
cover-img: /assets/img/Dibotics-3D-SLAM-696x365.jpg
tags: [SLAM, FastSLAM, EKF, Kalman, Particle, Python, LiDAR, IMU, Fusion]
---

I am curently working on a FastSLAM implementation based on the algorithm presented in Probabalistic Robotics by Sebastian Thrun et al. The Dataset is from the E205 State Estimation Course that I took in college. There is a single landmark, a post in an open field. The state to be estimated is the robot pose (x, y, theta). The measurment is landmark range in x-y coordinates. 

The SLAM probem can be factored into estimating the path, and based on the path, estimating the map. In this algorithm, a Rao-Blackwellized Particle filter is used to do this. The particles are used for estimating the pose and each particle has a low dimensional EKF for estimating the landmark location. The first implementation I did uses known landmark correspondence for simplicity. 

One issue that arose in my naive implementation was a mismatch between the accuracy and precision of the measurment model compared to those of the motion model. The symptom of this was very low weights. We can illustrate this problem with the pretend measurment model below. 

![measure_model](/assets/img/measurment_model.PNG){: .center-block :}

Since the measurment is very precise, it has very little area under its curve. Therefore, when the state of each particle is propagated through the motion model, very few will fall under the curve of the measurment model, if any. This can be illustrated by the following diagram.

![prop_vs_post](/assets/img/bad_proposal_vs_posterior.PNG){: .center-block :}

Figure (a) depicts the particles after sampling from the motion model (the proposal distribution) and which of those fall under the measurment model's ellipse (the posterior distribution). Figure (b) shows the result of resampling. This results in very few particles surviving with a relatively high importance weight, and it is very possible the true state is not captured. The solution is to sample from a distribution which more closely matches the measurment model. To do this, the measurement will be included in calculating the posterior. With this change, the algorithm was able to function corectly. In the figure below, you can see the estimation of the path done with only 10 particles.

![10particles_path](/assets/img/FastSLAM_known_10particles.png){: .center-block :}

My next iteration which is currently underway will use maximum likelihood data association to solve the landmark correspondence problem.

You can checkout the github repository [here](https://github.com/peterjohnsonhmc/SLAM).