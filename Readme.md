# Testing the applications

## Install Docker
Docker images have been pushed to DockerHub to make the applications easier to run without configuring all of their dependencies on your system. If you do not already have docker on your systems, follow the instructions on how to install docker on your machine - [Install Docker](https://docs.docker.com/get-docker/)

## Clone the Repository
```
git clone https://github.com/sjkchang/CMPE272-Assignment4.git
```

## Run frameworkless application
From the root directory of the cloned repository
```
cd frameworkless-flask
docker compose up
```

## Run vue-express application
From the root directory of the cloned repository
```
cd vue-express
docker compose up
```
