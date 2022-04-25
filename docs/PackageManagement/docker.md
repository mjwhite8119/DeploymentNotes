# Docker
For the Mac you need to install from the [Docker site](https://docs.docker.com/desktop/mac/install/).  There is an Intel chip and Apple chip version.  The brew install doesn't work.

>Note: Some applications that bring-up a UI application such as Roboflow Inference and ROS RViz don't run on MasOS since the containers run in an isolated sandbox.

Do NOT run the command as sudo. 

    docker pull roboflow/oak-inference-server:latest

Connect to running container:

    docker exec -it <container name> /bin/bash

## References
- [Docker Cheat Sheet](https://dockerlabs.collabnix.com/docker/cheatsheet/)