# RStudio
Steps to build and edit the Dockerfiles.

To pull the RStudio docker file, we use the Rocker-Org's account from hub.docker.com. The username is rocker

		docker pull rocker/rstudio

To start and fire up the docker simply enter the following command. The d flag is to run container in background. It stands for detach. And it prints the container ID.

		docker run -d -p 8787:8787 rocker/rstudio:latest

On linux you can head directly to http://localhost:8787/ which will redirect you to a login screen.
Enter the following credentials

		username: rstudio
		password: rstudio

The docker starts running invisibly, to kill the current instance use these two commands
	
		docker ps
		docker kill <psid>

**To check and create volumes**
To create a named Volume, which would help the Host and the Docker to communicate via files.

		docker volume create --name RData

To change the source directory of the Volume :

		????

To check the source files and meta data of your Volume 

		docker volume inspect RData

To remove a volume 

		docker volume rm <volumeID>

**To run using a volume**

To link the volume along with the RData folder in the /home/rstudio directory. To set the working directory use the -w flag

		docker run -p 8787:8787 -v $(pwd)/RData/:/home/rstudio/RData -e USERID=1001 bombear/rockers:latest

Do not forget to run the following command in RStudio.

		setwd("~/RData")

**Interactive**

Interactive shell

		docker run --rm -it --user rstudio -v $(pwd)/RData/:/home/rstudio/RData/ -w /home/rstudio/RData/ bombear/rockers:latest R

Start Bash

		docker run --rm -it --user rstudio -v $(pwd)/RData/:/home/rstudio/RData/ -w /home/rstudio/RData/ bombear/rockers:latest bash

Starting a bash shell along with the container. A docker command to start a bash shell in your container

		docker exec -it <container-id> bash



