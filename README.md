### ros-melodic-desktop-vnc on docker

* Tested under MacOS 10.13.6

* dockerhub: <https://hub.docker.com/r/floodshao/ros-melodic-desktop-vnc>
* github: <https://github.com/FloodShao/ros-melodic-desktop-vnc>

This docker environment is based on :
* osrf/docker_images for [melodic_core](https://github.com/osrf/docker_images/blob/b075c7dbe56055d862f331f19e1e74ba653e181a/ros/melodic/ubuntu/bionic/ros-core/Dockerfile)
* consol/ubuntu-xfce-vnc for [ubuntu-1604-vnc-desktop](https://hub.docker.com/r/consol/ubuntu-xfce-vnc/)

#### Build the image from Dockerfile
1. clone the repository in the github [here](https://github.com/FloodShao/ros-melodic-desktop-vnc)
2. command `docker build -t <image_name>/<tag_name> .` under the 'Dockerfile' directory.

#### VNC
Download the vnc viewer client [here](https://www.realvnc.com/en/connect/download/viewer/macos/)

#### Run the image (mind the tag is not 'latest')
1. `docker pull floodshao/ros-melodic-desktop-vnc:v1.0` or build your own image
2. `docker run -it -p 5901:5901 -p 6901:6901 floodshao/ros-melodic-desktop-vnc:v1.0 /bin/bash`
3. You can reference the [ubuntu-1604-vnc-desktop](https://hub.docker.com/r/consol/ubuntu-xfce-vnc/) for user modification or password modification.
4. open vnc viewer client, type the server address <localhost:5901>, key in the password: **vncpassword**
5. open the terminal and test gazebo

![test_gazebo](./pic/test_gazebo.png)

