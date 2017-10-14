# RStudio
Steps to build and edit the Dockerfiles.

To pull the RStudio docker file, we use the Rocker-Org's account from hub.docker.com. The username is rocker

		docker pull rocker/rstudio

To start and fire up the docker simply enter the following command

		docker run -d -p 8787:8787 rocker/rstudio:latest

On linux you can head directly to http://localhost:8787/ which will redirect you to a login screen.
Enter the following credentials

		username: rstudio
		password: rstudio


