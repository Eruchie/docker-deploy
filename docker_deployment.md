## **DOCKER DEPLOYMENT** ##
_____

**Docker** is a program that performs OS virtualization known as `containerization`. Docker is used to run software packages called `container`. A `container` can be as low as 50MB, it contains apps and corresponding binarries and libaries required to run the container.
 
 Architecture of docker; Hardware, O.S, Container Engine (Docker Software), Apps/Bins/Libs
 
 A `container` engine does not contain all the o.s. files  nor have a kernel inplace but shares that of the O.S where the docker engine is installed.
 
 Depending on the o.s (Mac, Windows, Ubuntu), download and install the appropriate docker toolbox
 
 Docker container lifecycle/eco system.... pull the codebase image from the central repo e.g. Docker hub (holds all container images that are open source) to your system where docker engine is installed, run the image (automatically it becomes a container), when you are done you can stop it, also you can delete it when you have no use for it.
 - Docker lifecycle: Pull image/codebase from docker hub to docker engine, run image. Container stages are run, stop and delete

 a. Installing Docker

 - `sudo apt-get update`
 - `sudo apt-get install docker.io`
 
 b. Confirm the Docker version and if docker is working:

- `docker --version`
 
 c. Here ubuntu is the image name you want to pull from docker hub
 
 - `sudo docker pull ubuntu`

d. Confirm the docker images downloaded
 
 - `sudo docker images`

e. Run the `ubuntu` docker image downloaded using `-it` which makes the terminal interactive and `-d` will run the container as a deamon/run in the background.
 
 - `sudo docker run -it -d`

 f. Check the containers running in the background.
 
 - `sudo docker ps`

