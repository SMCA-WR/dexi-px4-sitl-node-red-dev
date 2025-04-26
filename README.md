## Overview
Repo for experimenting with PX4 SITL using Node-RED

## Clone
Clone this repo:

https://github.com/SMCA-WR/dexi-px4-sitl-node-red-dev.git

cd into the cloned directory:

cd dexi-px4-sitl-node-red-dev

## Code

We will clone two repos into our local workspace so that development can happen from our host machine and our changes will not be lost if/when we kill the docker containers.

1. Get the DEXI ROS source code. For now grab the develop branch since it has the latest and greatest:

git clone -b develop https://github.com/droneblocks/dexi --recursive

2. Get the DEXI Node-RED source code:

git clone https://github.com/droneblocks/node-red-dexi

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
