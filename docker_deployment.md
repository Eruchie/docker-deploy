## **DOCKER DEPLOYMENT** ##
_____

**Docker** is a program that performs OS virtualization known as `containerization`. Docker is used to run software packages called `container`. A `container` can be as low as 50MB, it contains apps and corresponding binarries and libaries required to run the container.
 
 Architecture of docker; Hardware, O.S, Container Engine (Docker Software), Apps/Bins/Libs
 
 A `container` engine does not contain all the o.s. files  nor have a kernel inplace but shares that of the O.S where the docker engine is installed.
 
 Depending on the o.s (Mac, Windows, Ubuntu), download and install the appropriate docker toolbox
 
 Docker container lifecycle/eco system.... pull the codebase image from the central repo e.g. Docker hub (holds all container images that are open source) to your system where docker engine is installed, run the image (automatically it becomes a container), when you are done you can stop it, also you can delete it when you have no use for it.

- Docker lifecycle: Pull image/codebase from docker hub to docker engine, run image. Container stages are run, stop and delete

1. Installing Docker

    a. Update, inatsll and confirm the Docker version and if docker is working:

    - `sudo apt-get update`
    - `sudo apt-get install docker.io`
    - `docker --version`
 
    b. Here ubuntu is the image name you want to pull from docker hub
 
    - `sudo docker pull ubuntu`

    c. Confirm the docker images downloaded
 
    - `sudo docker images`

    d. Run the `ubuntu` docker image downloaded using `-it` which makes the terminal interactive and `-d` will run the container as a deamon/run in the background.
 
    - `sudo docker run -it -d ubuntu`

    f. Check the containers running in the background.
 
    - `sudo docker ps`

    g. To stop a container; 721958fed728 container ID

    - `sudo docker stop  
721958fed728`

    h. To see all containers running and stopped.

   - `sudo docker ps -a`

     ![step][./imageFiles/dociMG9.JPG]

    i. To start a container 

    - `sudo docker start 721958fed728`

    j. To access a container ID 721958fed728 run the bekow command and `exit` to exit the container; bash tells the container to use the current CLI

    - `sudo docker exec -it 721958fed728 bash`
    - `exit`

    k. To delete/remove a container ID 721958fed728

    -  `sudo docker rm 721958fed728`

    l. To remove a docker image

    - `sudo docker rmi`

    m. TO forcefully remove a container without stopping it:

    - `sudo docker rm -f`

    n. To sab=ve changes to a container and giving it a new container name e.g. test

    - `sudo docker commit 721958fed728 test`

1. Installing Docker

    a. Update, inatsll and confirm the Docker version and if docker is working:

    - `sudo apt-get update`
