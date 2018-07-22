LMS1xx
======

ROS driver for the SICK LMS1xx family of laser scanners. Originally from [RCPRG](https://github.com/RCPRG-ros-pkg/RCPRG_laser_drivers).

---

This is my fork of the LMS1xx driver from Clearpath Robotics. But because several bugs needed to be ironed out, and the pull request didn't go through, I'm leaving the changes here for posterity's sake and for use with my club.



It features the following changes:

- Scan frequencies of 25Hz are now allowed.
- A static transform for the laser is added in the ROS launch file for placing the laser upside down and forward on a robot.



CH3EERS!