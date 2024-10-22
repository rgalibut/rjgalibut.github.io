---
title: Autonomous Vehicle with Optical Character Recognition
layout: post
post-image: "https://raw.githubusercontent.com/thedevslot/WhatATheme/master/assets/images/SamplePost.png?token=AHMQUEPC4IFADOF5VG4QVN26Z64GG"
description: DESCRIPTION HERE
---

WORDS HERE

---

# About Project
In this course, our team was tasked with building, developing, programming, and testing a 1/8-scale robotic car that would navigate autonomously along a racetrack using computer vision, a LiDAR sensor, and a GPS device. Our final project incorporated GPS coordinates and optical character recognition to tell the car which location to navigate to, based on the visual prompt it was given.

To train the car to drive autonomously, we first simulated the car and track in a virtual environment (Donkeycar inside of Donkey Simulator) and manually completed laps around the track using a game controller. This data was sent to UCSD's supercomputer to leverage the computational power of its GPU clusters and train the AI model. This model was returned to the simulator, where the virtual car could then run laps autonomously. We used the same strategy to train the car in a real environment along a real track.

In order to be fully autonomous, we incorporated computer vision and ROS principles so that the car could "see" the lines in the track and stay on either the left or right side of it. The mounted camera provided visual feedback and image processing, the LiDAR provided proximity data, and the GPS provided exact location data. These combined devices allowed the car to adjust its direction and speed to stay on the path and avoid obstacles.

For our group's final project, we wanted to incorporate the position data provided by the GPS and the extensive capabilities of the camera. We decided to utilize the camera's text detection feature which would read numbers that correspond to a specific geographical location, given by sets of GPS coordinate data. The narrative would be that each number represented a table number at a restaurant and the GPS data would represent the path that the waiter-bot would take to reach the designated table.

We were able to achieve the main objectives of our final project. However, given more time, we would have liked to incorporate the LiDAR to detect and avoid obstacles (such as other restaurant patrons or, in reality, students walking around campus).

---

# Optical Character Recognition
Screenshot of video taken from camera demonstrating real-time text detection. Window on upper-left shows expected text from larger window. It was observed that white letters on black background were more difficult to capture than black letters on white background.

---

# GPS Coordinate Logging
PICS HERE

---

# Final Project Presentation
SLIDES HERE