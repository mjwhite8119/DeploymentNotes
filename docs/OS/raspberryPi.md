# Raspberry Pi

## Install Ubuntu

[Install Ubuntu](https://roboticsbackend.com/install-ubuntu-on-raspberry-pi-without-monitor/) on Raspberry Pi without Monitor.


## ROS2 Install Raspberry Pi
Install docker following [Raspbian docker install](https://dev.to/elalemanyo/how-to-install-docker-and-docker-compose-on-raspberry-pi-1mo) instructions.  After installing docker logout and login.

Install ROS2 clone the docker_images:

    git clone https://github.com/osrf/docker_images.git

Change to the ros2 build directory and build the docker image:

    cd docker_images/ros2/nightly/nightly
    docker build -t ros_docker .

Run the docker image:

    docker run -it osrf/ros:humble-desktop

### Pinout
![Pinout](../images/DeploymentNotes/DeploymentNotes.001.jpeg)

### Use with LG Monitor
edit the `/boot/config.txt` file an set the following parameters:

    hdmi_force_hotplug=1
    config_hdmi_boost=4
    hdmi_group=1

## Remote Access
[Remote Access](https://www.raspberrypi.com/documentation/computers/remote-access.html#secure-shell-from-linux-or-mac-os)

# References

- [Raspberry Pi Configuration](https://www.raspberrypi.com/documentation/computers/configuration.html)