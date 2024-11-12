---
title: Pseudo-Haptic Shoulder
layout: post
date_range: January 2024 - June 2024
post-image: "https://raw.githubusercontent.com/rgalibut/rgalibut.github.io/main/assets/images/Haptic%20Shoulder/SHULDRD%20Cover%20Image.png"
description: Electromechanical human shoulder to be used as training tool for manipulator robot.

---

My senior capstone project studied the range-of-motion (ROM) of the human shoulder's rotational degrees of freedom (DOF) and the reaction torques at the end ROM due to tendon and soft tissue limitations. Since our project timeline was limited, we focused on a specific movement called upper-arm repositioning, which is commonly performed during search and rescue operations to extract casualty victims who are found in a prone (face-down) position. The human shoulder experiences resistance when reaching its end ROM and this resistive force changes with the displacement of the arm.

Our project sponsor, a current UCSD PhD student, is training a serial-link robotic manipulator on how to safely reposition a human body for extraction, with the first step being upper-arm repositioning. You can read more about the previous work completed by the sponsor and lab here: Finding Biomechanically Safe Trajectories for Robot Manipulation of the Human Body in a Search and Rescue Scenario.

An important requirement of our senior project was to find alternative ways to safely train the robot without using human test subjects. Additionally, the project should allow the sponsor to collect infinite case studies as opposed to the limited data human subjects can provide.

Our team's solution was to design an electromechanical shoulder mannequin that can measure upper-arm position and apply a reaction torque when reaching the end ROM. The complete system consists of a complex joint that moves with three degrees of freedom and an electrical system that applies torque. The pseudo-haptic capability of the device 

Our team was comprised of mechanical engineering majors assigned to specific team roles: the mechanical design team responsible for creating and iterating on the physical prototype; software/electrical team responsible for building and programming the pseudo-haptic feedback; and the path-planning team responsible for mapping the device movement to the robot manipulator configuration. Along with the sponsor, I worked on the path-planning portion of the project.

<p style="text-align: center">
Jump to:
<a href="#pathplanning">Path Planning</a> | <a href="#videos">Videos</a> | <a href="#finaldemo">Final Demonstration Video</a>
</p>

---

<h1 id="pathplanning">Path Planning</h1>
<table>
  <tr>
    <td style="text-align: left" width="35%" rowspan="2">Our device is to be used as a training tool for a serial-link manipulator robot, specifically the Franka Emika Panda (right). The Panda has 7 DOF and each joint is either revolute or prismatic. <br><br> The Panda uses Devanit-Hartenberg (DH) parameters, wherein coordinate frames are attached to each joint so that the transformations correspond to either the joint or the link. <br><br> For our project, we defined the world space (Cartesian or c-space) in relation to the Panda base. Each joint was then assigned individual joint spaces. Finally, we defined the shoulder space and used vector transformations to relate it to the world space of the Panda.</td>
    <td style="text-align: center" width="65%"><img style="margin: 0 auto" src="https://raw.githubusercontent.com/rgalibut/rgalibut.github.io/main/assets/images/Haptic%20Shoulder/Franka%20Emika%20Panda.png" alt="Panda"/></td>
  </tr>
  <tr>
    <td style="text-align: center; font-size: 12px">Image courtesy of <a href="https://frankaemika.github.io/docs/control_parameters.html">Franka Robotics</a></td>
  </tr>
</table>

<table width="100%">
  <tr>
    <td style="text-align: center" width="60%"><img style="margin: 0 auto" src="https://raw.githubusercontent.com/rgalibut/rgalibut.github.io/main/assets/images/Haptic%20Shoulder/ReFlex%201%20Coordinate%20Frame.png" alt="End-Effector"/></td>
    <td style="text-align: left" width="40%">The end-effector used is the RightHand Robotics ReFlex 1 (left), which has 3 fingers, 5 DOF, and a squishy palm to allow for some compliance. The coordinate frame is defined with the z-axis pointing downwards towards object being gripped, and the x-axis pointed to the side, as shown in the picture of the Panda above.</td>
  </tr>
</table>

<table width="100%">
  <tr>
    <td style="text-align: center" width="60%"><img style="margin: 0 auto" src="https://raw.githubusercontent.com/rgalibut/rgalibut.github.io/main/assets/images/Haptic%20Shoulder/Shoulder%20Coordinate%20Frame.png" alt="Shoulder"/></td>
    <td style="text-align: left" width="40%">The shoulder mannequin coordinate frame (left) is defined with the z-axis pointing up towards the "head," and the x-axis pointing outside of the right side of the body.</td>
  </tr>
</table>

### Shoulder Mannequin Trajectory
<table>
  <tr>
    <td rowspan="2"><img style="margin: 0 auto" src="https://raw.githubusercontent.com/rgalibut/rgalibut.github.io/main/assets/images/Haptic%20Shoulder/Shoulder%20Limits.png" alt="Shoulder-Limits"/></td>
    <td>Using the human shoulder ROM values from Table 1 to the left (researched and provided by the mechanical team), the path of the shoulder was simulated in software. Assuming a prone position, the flexion, horizontal abduction, and horizontal adduction directions were not considered.<br><br>In the image on the left, the z-axis points up towards the head, the x-axis points to the outside of the right side of the body (blue line), and the y-axis points towards the front of the body. ϕ is defined as the angle from the z-axis, θ is defined as the angle from the x-axis, and the radial direction is set to 1.<br><br></td>
  </tr>
  <tr>
    <td>
      The green circles indicate: 
      <table>
        <tr>
          <th>NAME</th>
          <th>NAME</th>
          <th>Explanation</th>
        </tr>
        <tr>
            <td>&phi; = 180&deg;</td>
            <td>&theta;  = 0&deg;</td>
            <td>Arm down by leg</td>
        </tr>
        <tr>
            <td>&phi; = 130&deg;</td>
            <td>&theta;  = -80&deg;</td>
            <td>Arm extended backwards</td>
        </tr>
        <tr>
            <td>&phi; = 0&deg;</td>
            <td>&theta; = 0&deg;</td>
            <td>Arm up by head</td>
        </tr>
      </table>
    </td>
  </tr>
</table>

This trajectory assumes that ROM is not coupled (perfect trajectory). This was done for simplicity, as coupling the ROM would require an external rotation at step 2.

### Manipulator Configuration Through Trajectory
<table width="100%">
  <tr>
    <td style="text-align: center" width="65%"><img style="margin: 0 auto" src="https://raw.githubusercontent.com/rgalibut/rgalibut.github.io/main/assets/images/Haptic%20Shoulder/Panda%2050pt%20Traj.gif" alt="Panda-GIF"/></td>
    <td style="text-align: left" width="34%">The Panda has more DOF than our device (7 vs. 3) so there are multiple solutions to the configuration at each point along the desired path. It was important to seed the previous configuration into the next calculation in order to assure a smooth motion and prevent discontinuities.<br><br>To make the (numerical) inverse kinematics easier, we constrained the end-effector so that it did not rotate (reference frame remained the same). However, to realistically model upper-arm repositioning, we would need an optimization framework that allowed the end-effector to rotate, which was beyond the scope and timeframe of the project.</td>
  </tr>
</table>

### Simulated Path
<table width="100%">
  <tr>
    <td style="text-align: center" width="65%"><img style="margin: 0 auto" src="https://raw.githubusercontent.com/rgalibut/rgalibut.github.io/main/assets/images/Haptic%20Shoulder/Shoulder%20Path%20GIF.gif" alt="Shoulder-GIF"/></td>
    <td style="text-align: left" width="34%">This overlay demonstrates one series of configurations that the Panda would move through in relation to the shoulder mannequin through the defined trajectory. </td>
  </tr>
</table>

---

<h1 id="videos">Test Videos</h1>

#### Range of Motion
No motors or torque feedback are enabled.

This video shows the ROM achieved by the mannequin, which is lying the prone position with the right arm being moved. Motors are not enabled for this test.

<div class="video-container">
  <iframe src="https://drive.google.com/file/d/1FflOuQJx5hJFXuBeVlhCH2aXD9UeOMPP/preview" width="640" height="480" allowfullscreen></iframe>
</div>

#### Haptics Test
Software/electrical team testing coupled haptics capabilities (2 DOF). The motor hum that can be heard indicates when reaction torques are applied. Note that there is a baseline hum when the device is in the neutral position, which was fixed in the final prototype.

<div class="video-container">
  <iframe src="https://drive.google.com/file/d/1zPLwcjsRzOSxJXYmlK4wb1nNQqObEwQk/preview" width="640" height="480" allowfullscreen></iframe>
</div>


#### Coupled ROM with Haptics
Torque feedback is enabled and the motors are coupled. 

As the arm first moves upward, you can hear the motor which indicates the end ROM is reached and the arm can't be raised further. However, after rotating the arm, we are able to access a larger range of motion, allowing the movement to be completed.

<div class="video-container">
  <iframe src="https://drive.google.com/file/d/1oF4nWT5byMTzDuVATKuBoGfn01-oVoEo/preview" width="640" height="480" allowfullscreen></iframe>
</div>


#### Manipulator Test
Torque feedback is enabled and the manipulator robot is performing the movement on its own. 

The motor hum that you hear indicates that resistance is being "felt" by the mannequin, which corresponds to nearing the end ROM.

<div class="video-container">
  <iframe src="https://drive.google.com/file/d/16vwnGSEiqtszwHPAF0vGXlc7WbQEmde1/preview" width="640" height="480" allowfullscreen></iframe>
</div>


---

<h1 id="finaldemo">Final Demonstration Video</h1>
<center>
  <iframe src="https://drive.google.com/file/d/1Wf9PO0gi0CDb_t1odyUjYmFxq1hYghD3/preview" width="100%" height="500px" allowfullscreen></iframe>
</center>

<div style="text-align: center">
  <a href="#top">Back to top</a>
</div>