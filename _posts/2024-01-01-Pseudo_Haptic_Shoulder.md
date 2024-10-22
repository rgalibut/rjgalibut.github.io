---
title: Pseudo-Haptic Shoulder
layout: post
date_range: January 2024 - June 2024
post-image: "assets/images/SHULDRD%20Cover%20Image.png"
description: Electromechanical human shoulder to be used as training tool for manipulator robot.

---

# About Project
My senior capstone project studied the range-of-motion (ROM) of the human shoulder's rotational degrees of freedom (DOF) and the reaction torques at the end ROM due to tendon and soft tissue limitations. Since our project timeline was limited, we focused on a specific movement called upper-arm repositioning, which is commonly performed during search and rescue operations to extract casualty victims who are found in a prone (face-down) position. The human shoulder experiences resistance when reaching its end ROM and this resistive force changes with the displacement of the arm.

Our project sponsor, a current UCSD PhD student, is training a serial-link robotic manipulator on how to safely reposition a human body for extraction, with the first step being upper-arm repositioning. You can read more about the previous work completed by the sponsor and lab here: Finding Biomechanically Safe Trajectories for Robot Manipulation of the Human Body in a Search and Rescue Scenario.

An important requirement of our senior project was to find alternative ways to safely train the robot without using human test subjects. Additionally, the project should allow the sponsor to collect infinite case studies as opposed to the limited data human subjects can provide.

Our team's solution was to design an electromechanical shoulder mannequin that can measure upper-arm position and apply a reaction torque when reaching the end ROM. The complete system consists of a complex joint that moves with three degrees of freedom and an electrical system that applies torque. The pseudo-haptic capability of the device 

Our team was comprised of mechanical engineering majors assigned to specific team roles: the mechanical design team responsible for creating and iterating on the physical prototype; software/electrical team responsible for building and programming the pseudo-haptic feedback; and the path-planning team responsible for mapping the device movement to the robot manipulator configuration. Along with the sponsor, I worked on the path-planning portion of the project.

---

# Path Planning
Our device is to be used as a training tool for a serial-link manipulator robot, specifically the Franka Emika Panda (right). The Panda has 7 DOF and each joint is either revolute or prismatic. 

The Panda uses Devanit-Hartenberg (DH) parameters, wherein coordinate frames are attached to each joint so that the transformations correspond to either the joint or the link.

For our project, we defined the world space (Cartesian or c-space) in relation to the Panda base. Each joint was then assigned individual joint spaces. Finally, we defined the shoulder space and used vector transformations to relate it to the world space of the Panda.

The end-effector used is the RightHand Robotics ReFlex 1 (left), which has 3 fingers, 5 DOF, and a squishy palm to allow for some compliance. The coordinate frame is defined with the z-axis pointing downwards towards object being gripped, and the x-axis pointed to the side, as shown in the picture of the Panda above.

The shoulder mannequin coordinate frame (left) is defined with the z-axis pointing up towards the "head," and the x-axis pointing outside of the right side of the body.

### Shoulder Mannequin Trajectory
Using the human shoulder ROM values from Table 1 to the left (researched and provided by the mechanical team), the path of the shoulder was simulated in software. Assuming a prone position, the flexion, horizontal abduction, and horizontal adduction directions were not considered. 

In the image on the left, the z-axis points up towards the head, the x-axis points to the outside of the right side of the body (blue line), and the y-axis points towards the front of the body. ϕ is defined as the angle from the z-axis, θ is defined as the angle from the x-axis, and the radial direction is set to 1.

The green circles indicate: 

- $\phi$  = 180$^{\circ}$, $\theta$  = 0$^{\circ}$ (arm down by leg)
- $\phi$  = 130$^{\circ}$, $\theta$  = -80$^{\circ}$ (arm extended backwards)
- $\phi$  = 0$^{\circ}$, $\theta$  = 0$^{\circ}$ (arm up by head)

This trajectory assumes that ROM is not coupled (perfect trajectory). This was done for simplicity, as coupling the ROM would require an external rotation at step 2.

### Manipulator Configuraion Through Trajectory
The Panda has more DOF than our device (7 vs. 3) so there are multiple solutions to the configuration at each point along the desired path. It was important to seed the previous configuration into the next calculation in order to assure a smooth motion and prevent discontinuities.

To make the (numerical) inverse kinematics easier, we constrained the end-effector so that it did not rotate (reference frame remained the same). However, to realistically model upper-arm repositioning, we would need an optimization framework that allowed the end-effector to rotate, which was beyond the scope and timeframe of the project.

### Simulated Path
This overlay demonstrates one series of configurations that the Panda would move through in relation to the shoulder mannequin through the defined trajectory. 

---

# Final Demonstration Video
VIDEO HERE