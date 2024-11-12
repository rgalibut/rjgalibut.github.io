---
title: Autonomous Vehicle with Optical Character Recognition
layout: post
date_range: January 2023 - March 2023
post-image: "https://raw.githubusercontent.com/rgalibut/rgalibut.github.io/main/assets/images/Autonomous%20Vehicle/Autonomous%20Vehicle%20Cover%20Image.jpg"
description: Autonomous vehicle using OCR to detect numbers and GPS coordinate logging for navigation.

---

In this course, our team was tasked with building, developing, programming, and testing a 1/8-scale robotic car that would navigate autonomously along a racetrack using computer vision, a LiDAR sensor, and a GPS device. Our final project incorporated GPS coordinates and optical character recognition to tell the car which location to navigate to, based on the visual prompt it was given.

To train the car to drive autonomously, we first simulated the car and track in a virtual environment (Donkeycar inside of Donkey Simulator) and manually completed laps around the track using a game controller. This data was sent to UCSD's supercomputer to leverage the computational power of its GPU clusters and train the AI model. This model was returned to the simulator, where the virtual car could then run laps autonomously. We used the same strategy to train the car in a real environment along a real track.

In order to be fully autonomous, we incorporated computer vision and ROS principles so that the car could "see" the lines in the track and stay on either the left or right side of it. The mounted camera provided visual feedback and image processing, the LiDAR provided proximity data, and the GPS provided exact location data. These combined devices allowed the car to adjust its direction and speed to stay on the path and avoid obstacles.

For our group's final project, we wanted to incorporate the position data provided by the GPS and the extensive capabilities of the camera. We decided to utilize the camera's text detection feature which would read numbers that correspond to a specific geographical location, given by sets of GPS coordinate data. The narrative would be that each number represented a table number at a restaurant and the GPS data would represent the path that the waiter-bot would take to reach the designated table.

We were able to achieve the main objectives of our final project. However, given more time, we would have liked to incorporate the LiDAR to detect and avoid obstacles (such as other restaurant patrons or, in reality, students walking around campus).

<p style="text-align: center">
Jump to:
<a href="#ocr">Optical Character Recognition</a> | <a href="#gps">GPS Coordinate Logging</a> | <a href="#videos">Videos</a> | <a href="#presentation">Final Project Presentation</a>
</p>

---

<h1 id="ocr">Optical Character Recognition</h1>

<table>
  <tr>
    <td style="text-align: center" width="65%"><img style="margin: 0 auto" src="https://raw.githubusercontent.com/rgalibut/rgalibut.github.io/main/assets/images/Autonomous%20Vehicle/OCR.jpg" alt="OCR"></td>
    <td style="text-align: left" width="35%">Screenshot of video taken from camera demonstrating real-time text detection. Window on upper-left shows expected text from larger window. It was observed that white letters on black background were more difficult to capture than black letters on white background.</td>
  </tr>
</table>

---

<h1 id="gps">GPS Coordinate Logging</h1>
<table>
  <tr>
    <th>Location 1 Coordinates</th>
    <th>Navigating to Location 1</th>
  </tr>
  <tr>
    <td><img src="https://raw.githubusercontent.com/rgalibut/rgalibut.github.io/main/assets/images/Autonomous%20Vehicle/Path%201.png" alt="Coordinates-1"></td>
    <td><img src="https://raw.githubusercontent.com/rgalibut/rgalibut.github.io/main/assets/images/Autonomous%20Vehicle/Navigating%20to%201.png" alt="Navigation-1"></td>
  </tr>
</table>

<table>
  <tr>
    <th>Location 4 Coordinates</th>
    <th>Navigating to Location 4</th>
  </tr>
  <tr>
    <td><img src="https://raw.githubusercontent.com/rgalibut/rgalibut.github.io/main/assets/images/Autonomous%20Vehicle/Path%204.png" alt="Coordinates-4"></td>
    <td><img src="https://raw.githubusercontent.com/rgalibut/rgalibut.github.io/main/assets/images/Autonomous%20Vehicle/Navigating%20to%204.png" alt="Navigation-4"></td>
  </tr>
</table>

---

<h1 id="videos">Videos</h1>
#### DonkeyCar in DonkeySim
Three autonomous laps completed in virtual environment. The window on the right shows that the car is running on "Full Auto" (no input from me).

<div class="video-container" syle="align:center">
  <iframe src="https://drive.google.com/file/d/1MFuD4B3zvs83UKxiCq4B74QGKUz9X7y9/preview" width="640" height="480" allowfullscreen></iframe>
</div>

#### Navigating Path 001
Waiter-Bot navigating to first location, designated "001."
<div class="video-container">
  <iframe src="https://drive.google.com/file/d/1oQynWgQyOUr9G6peNUZNg_jaXVI5AQT6/preview" width="640" height="480" allowfullscreen></iframe>
</div>

#### Navigating Path 004
Waiter-Bot navigating to first location, designated "004."

<div class="video-container">
  <iframe src="https://drive.google.com/file/d/1sU-K0zyRMx_rfUpsm4Da8Dik9T0qjWRW/preview" width="640" height="480" allowfullscreen></iframe>
</div>

---

<h1 id="presentation">Final Project Presentation</h1>
<center>
  <iframe src="https://docs.google.com/presentation/d/e/2PACX-1vRHOne5akC5NY8yTIySbvbBdFqpIkCEU8QYnfKhFPp3mvACvVGvrEVLf1nhJ6nt5g/embed?start=false&loop=false&delayms=5000" frameborder="0" width="960" height="569" allowfullscreen="true" mozallowfullscreen="true" webkitallowfullscreen="true"></iframe>
</center>

Final notes:
- Waiter-Bot is not truly autonomous, as it still requires human input to start and restart the program. The program doesn't run indefinitely and can only take one input per run.
- OCR program had trouble recognizing single numbers ("1" and "4") so we opted to put zeros in front. We considered using letter recognition instead of number recognition but letters proved to be less consistently successful. It would require further tweaking of the code to increase accuracy.
- Our wireless controller was not working so we are using a wired controller.
- Locations are marked with a black X on the ground.

<div style="text-align: center">
  <a href="#top">Back to top</a>
</div>