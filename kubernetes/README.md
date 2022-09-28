# a9s homework: Deploy a go app to kubernetes
what have I done: 

- create a dockerfile that contain two stages:
    - building stage: build a golang:alpine image.
    - deployment stage: copy the binary files form the first image and run it.

- use docker-compose to test out my image with a postgres database.

- create two kubernetes services: 
    - app service: running our go-app image.
    - database service: running postgres database.

- test the kubernetes pods using minikube.

# notes: 

docker-compose is only used for testing purposes.

I uploaded the docker image for the go-app to docker hub, you can find it here: https://hub.docker.com/repository/docker/mow97/todo-go
