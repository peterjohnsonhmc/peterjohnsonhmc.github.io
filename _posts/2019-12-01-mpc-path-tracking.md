---
layout: post
title: Model Predictive Control for Path Tracking
subtitle: How a self-driving car follows a path
cover-img: /assets/img/path.jpg
tags: [mpc, robotics, matlab, optimization, control, planning, self-driving]
---

Fall Semester of my senior year I took a nonlinear controls and optimization course. Topics included nonlinear systems, dynamics, stability and optimization with applications to control systems. For our final project, my partner and I decided to implement Model Predictive Control (MPC) for a vehicle following a path. We based our vehicle on the popular bicycle model of a car. We developed the system kinematics, cost function, constraints and integrated them using MATLAB's nonlinear MPC Toolbox. We also built a simple simulator to visualize the results. 

To formulate the path following problem as an optimization problem, we created a cost function that would minimize the bicycle's deviation from the path (the cross track error.) We also included costs for not moving at the desired speed and having an error in the heading. We also included terms to minimize the amount of control actions such as accelerating or steering and minimized the rate of change in these control actions. These costs are for efficiency and rider comfort.

The controller was given a set of predetermined waypoints (as if they had come from a higher level planner) and the path that was followed was generated by fitting a spline to these waypoints. This was the least ideal part of our system. We simulated the robot's motion as noiseless, so the final controller was able to perfectly follow a path. The unsatisfying part was that the path was not an optimal path between points as we were simply fitting some third order polynomial. Nonetheless, I am proud that we got our controller to work even if the paths it follows arent the prettiest. 

Here are some gifs of the controller in action. The red line represents the vehicle and its orientation, the circles are the waypoints, and the dashed line is the path taken.
![figure8](/assets/img/figure_eight.gif){: .center-block :}

![hexagon](/assets/img/hexagon.gif){: .center-block :}

In the future, it would be fun to integrate this controller on its own hardware platform as well as develop some other optimization based high level path planner!
If you are interested in reading more about the details of our project, here is the [final report with attached code](/assets/img/MPC_Path_Tracking.pdf).

