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

![test_gazebo](https://github.com/FloodShao/ros-melodic-desktop-vnc/blob/master/fig/test_gazebo.png?raw=true)

#### File system
![test_gazebo](https://github.com/FloodShao/ros-melodic-desktop-vnc/blob/master/fig/file_sys.png?raw=true)

The default user name is 'default', with the home dir is /headless.
If you want to attach a directory to this docker image, add the `-v` param in the command as follow:

`docker run -it -p 5901:5901 -p 6901:6901 -v /<host_dir>:/<docker_dir>  ros_images/melodic-desktop /bin/bash`

where `<host_dir>` is the absolute dir in your host machine, and `<docker_dir>` is the absolute dir in your docker. 

For example, I will use `-v /$(pwd)/workspace:/headless/workspace` to create a link between the host machine and the docker. After you delete the docker (stop the docker ps), the files in your host machine (as in /$(pwd)/workspace) will not disappear. You can use this feature to load your program locally to your docker environment rather than clone from your git repo each time.  
