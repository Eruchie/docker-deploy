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

    m. To forcefully remove a container without stopping it:

    - `sudo docker rm -f`

    n. To sab=ve changes to a container and giving it a new container name e.g. test

    - `sudo docker commit 721958fed728 test`

1. Create a new container and install Apache: 

    a. Run the ubuntu image:

    - `sudo docker run -it -d ubuntu`

    b. Confirm running container ID:

    - `sudo docker ps`

    c. Connect to the container via ID

    - `sudo docker exec -it babea267a082 bash`

    d. In the container, run the necessary updates and install apache
    
    - `sudo apt-get update`

    - `sudo apt-get install apache2`

    - `service apache2 status` 

    e. Start Apache

    - `service apache2 start`
    - `exit`

    f. Get the container ID and save the container as an image; use the naming convention `aufora2/apache` required to upload in docker hub.

    - `sudo docker ps`
    - `sudo docker commit babea267a082 aufora2/apache`

    g. Run apache to map host port 82 to container port 80 

    - `sudo docker run -it -p 82:80 -d aufora2/apache`

    h. Get the container ID by `sudo docker ps`, connect to the container and start apache

    - `sudo docker exec -it 92375a8f04ab bash`
    - `service apache2 start`

    i. Test the web page on port 82 using a browser:

    - `http://18.222.29.241:82/`

    j. Exit, stop the container and push the image, `aufora2/apache` to docker hub

    - `exit`
    - `sudo docker stop 92375a8f04ab`
    - `sudo docker login`
    - `sudo docker push aufora2/apache`

1. DockerFile command structure

    a. The following consists of the dockerfile command structure:

    - `FROM`: from image source e.g. ubuntu.
    - `ADD`: Specify location in the container where web files should be kept.
    - `RUN`: To run updates e.g. apt-get update, apt-get -y install apache2
    - `CMD`: This command will get skipped if an argument is specified.
    - `ENTRYPOINT`: This command will NOT get skipped even if an argument is specified.
    - `ENV`: Specify the enviroment variables in the container

  1. Create an image/container using Dockerfile

     a. Create a directory where Docker and html files will be kept and change to the directory 
   - `mkdir dockerfile && cd dockerfile && touch Dockerfile`
   - `nano DOckerfile`

     b. Paste the following shell script and save.

     ```
        FROM ubuntu
        RUN apt-get update
        RUN apt-get -y install apache2
        #the . means files in the pwd
        ADD . /var/www/html 
        #run appache automatically in the background
        ENTRYPOINT apachectl -D FOREGROUND 
        #enviromental variable with name mervintec
        ENV name mervintec 
        sudo nano web.html
     ```
     c. To build the image file, run the following command in nthe directory containing the files; in our case the dir is `dockerfile`

     - `sudo docker build . -t new_dockerfile`

     d. Launch the container

     - `sudo docker run -it -p 84:80 -d new_dockerfile`

     e. Copy the new container ID

     - `sudo docker ps`

     f. Connect to the new container and navigate into `/var/www/html` to check the files

     - `sudo docker exec -it e6947d0a4e30 bash`
     - `cd /var/www/html`
     - `ls`

     g. In the `pwd`, `echo` name; this should give the name of the enviromental variable; `mervintec` in my case.

     - `echo $name`

    