# drone-ros-docker

**Update: For the latest Images, go to The [MHackers Embedded-Systems Group Github Repos](https://github.com/mh-embed).**

MHackers Embedded 2023 Drone Project ROS Docker Images

## Usage
1. Install [Docker](https://www.docker.com)
2. Get this Github Repo
3. run docker
```bash
$ ./drone_start.sh
```
4. Once the container starts, you should be in directory
```
root@<random_stuff> /embed/catkin_ws $ 
```
This is the catkin workspace where the ROS package builder, catkin, manages your source code, builds, and other stuff. 
Run 
```
$ catkin_init.sh
```
to compile your code and source the workspace (something that is required by ROS to work)

## Update Image
1. When there is a new version of the image available, run
```
$ sudo docker rm drone-ros
```
and then start the dev container following step 3 in Usage.

2. By default, ONLY data in /embed/ directory (inside the container) will be saved in a permanent volume in docker. Changes in other parts of the system will NOT be saved. If your program needs another package, email or @me on Slack and I will update the images within 24 hrs. Please follow step 3 and 4 to use updated images. 
3. Different versions of the images are hosted in [my Dockerhub](https://hub.docker.com/repository/docker/danielhouevr315/mhacker-drone-ros/). You can manually pull different versions of the image by running
```
$ docker pull danielhouevr315/mhacker-drone-ros:<tag>
```

## Build
1. Head to the dev/ directory
```bash
$ cd dev
```
2. Change the tag in makec.sh (I don't know anything about shell this is the best I can do)
3. To build image for your host platform, run
```
$ sudo docker buildx build . -t danielhouevr315/mhacker-drone-ros:<tag>
```
To build for Raspberry Pi, run
```
$ sudo docker buildx build . --platform linux/arm64/v8 -t danielhouevr315/mhacker-drone-ros:<tag>
```

4. To push to Docker Hub, run
```
$ docker push danielhouevr315/mhacker-drone-ros:<tag>
```

## Learn More About ROS Development
This stack is based on ROS noetic. 

I recommend going through the first six of the [Official ROS Tutorials](http://wiki.ros.org/ROS/Tutorials) to get started with ROS development. 
