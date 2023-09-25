# hmark_linux
Explanation: hmark 4.0 for linux from https://github.com/Korvoe/Hmark-4.0

# Steps to build application
(This is a very rough README example. Please write your own with a little more readability.)

1. Download the Dockerfile from: https://drive.google.com/file/d/1SIHb1NBOC2RkYVlVrEU8wCcvQXhw1CUs/view?usp=drive_link
2. Build an image w/ Dockerfile: docker build -t [image_name] [Dockerfile_directory]
3. Create container from image: docker create -it -e DISPLAY=$DISPLAY -v /tmp/.X11-unix:/tmp/.X11-unix --name [container_name] [image_name]
4. Start container: docker start [container_name]
5. Record started container's ID: export containerId=$(docker ps -l -q)
6. Display settings for GUI: xhost +local:\`docker inspect --format='{{ .Config.Hostname }}' $containerId\`
8. Run application: docker exec -it [container_name] python3 hmark_linux/hmark.py
