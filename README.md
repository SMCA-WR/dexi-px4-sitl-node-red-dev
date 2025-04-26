## Overview
Repo for experimenting with PX4 SITL using Node-RED

## Clone
Clone this repo:

git clone https://github.com/SMCA-WR/dexi-px4-sitl-node-red-dev.git --recurse-submodules

cd into the cloned directory:

cd dexi-px4-sitl-node-red-dev

## Docker Compose

docker compose up

## Get SITL Running

Go to http://localhost:6080

Open Terminator

Run ./edit_rcS.bash

cd PX4-Autopilot

make px4_sitl gz_x500

Open QGC and voila

## Build DEXI ROS Project

Open a new terminal and do the following:

cd ~/dexi_ws

colcon build --packages-select dexi_interfaces dexi_py px4_msgs

source install/setup.bash

ros2 launch dexi_py offboard_sitl_rosbridge.launch.py

This launch file witll start the microdds agent, rosbridge, and the DEXI PX4 Offboard Manager node.

## Access Node-RED

Open a new tab and access Node-RED:

http://localhost:1880

Get the docker internal IP of the dexi-dev container and configure Node-RED websocket server with the IP address.
