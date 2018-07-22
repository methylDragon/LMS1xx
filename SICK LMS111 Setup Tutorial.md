## Steps to Setup a SICK LMS111 LiDAR

Author: methylDragon

1. Connect the SICK LMS111 LiDAR to an Ethernet port on a computer **running Windows.** (Remember to turn the laser on!)

2. Install the [SICK SOPAS Engineering Tool](https://www.sick.com/sg/en/sopas-engineering-tool-2018/p/p367244)

3. Use the SICK SOPAS Engineering Tool to **configure the parameters for your LiDAR** (remember to install the correct LiDAR drivers (In my case, I had to install the LMS11x_FieldEval - V1.36-21.10.2010))

   - **Note!!: Ensure** that you change scan angle resolution in the basic settings to "25hz, 0,25°". This is both so the laser works properly with ROS and so that ROS gets a scan with the highest resolution possible.

   - Default login passwords are as such: 

   - > Maintenance personnel: main
     >
     > Authorized client: client

   - Set the IP address parameters (Use the automatic setting, and save it!) and adjust your measuring parameters
   - Mine was 169.254.202.62

4. Install the ROS wrapper

   (Do NOT do it via sudo apt-get install! That one has some bugs and doesn't work properly.)

   Instead, clone it from https://github.com/methylDragon/LMS1xx

5. Swap to an Ubuntu computer, and configure the wired connection using the GUI network configurer

   - Go to Edit Connections and make sure that the IP address of the ethernet connection is DIFFERENT from the laser scanner's. (Set a manual IP that is different)

     You might then need to configure the MAC address and settings for the LiDAR connection

     > On edit connections, click add, go to ethernet tab, set device MAC  address to the right ethernet port, got to IPv4 Settings tab, set method to Manual and enter these settings: Address: 192.168.0.1 Netmask: 255.255.255.0 Leave Gateway open and click save.

6. Then, edit the launch file if need be to fit your configured laser's IP address

7. Go to the root directory of your workspace, run `catkin_make`, and source the devel space's setup.bash

8. Then run `rospack profile` if this is the first time you're running the LMS1xx node

9. Then run `roslaunch lms1xx lidar_bringup.launch` to test!

   - Remember to `rostopic echo /scan` or visualise in RViz to confirm!
