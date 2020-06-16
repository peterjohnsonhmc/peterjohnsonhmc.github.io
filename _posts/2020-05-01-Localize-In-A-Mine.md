---
layout: post
title: UKF Localization in a Chilean Mine
subtitle: State estimation in a GPS denied environment
cover-img: /assets/img/path.jpg
tags: [ukf, unscented, kalman, particle, filter, probabalistic, robotics, python, mining, autonomy]
---

For the final project in our State Estimation class, my partner and I built an Unscented Kalman Filter (UKF) to localize a robot in a Chilean copper mine. We already had experience with an Extended Kalman Filter (EKF) and wanted to try out the unscented transform approach to linearizing a system. The unscented transform sounded appealing because it yields better results than a taylor series and does not require taking a large amount of partial derivatives for a Jacobian. 

The public Chilean Mine [dataset](http://dataset.amtc.cl/) that we used included LiDAR and encoder data. Integrating the wheel encoder data provided a good prediction step for our robot and the LiDAR measurements could be compared to an occupancy grid map for the corection step of the filter. The LiDAR was an older model which scanned a full 3-D rotation once every 6 seconds. Based on the speed of the robot, we determined that we could not assume a full scan occuerd at a single time step. This meant that we would be unable to do complete scan matching. We played around with the fractions of a scan and found that 1/3 of a scan produced the best results.  

We succesffully implemented and tuned the UKF as well as a particle filter in the same style as the previous one. You can checkout an overview of the project and our results in this video:

![video]()

You can checkout the github repository [here](https://github.com/peterjohnsonhmc/E205/tree/master/Final%20Project).
