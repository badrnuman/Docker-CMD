# Docker CMD
## Download container to local and access it using bash
### Ubuntu image
```bash
$docker run –it ubuntu bash
```
or
### nginx image
```bash
$docker run --name mywebserver -it -p 80:80 nginx bash
```
## to remove the container
```bash
$docker rm -f <Container_ID>
```
## Running the container in Daemon mode (deattached)
```bash
$docker run --name mywebserver -d -p 80:80 nginx
```
## run container with encrypted password
```bash
$docker run -d -p 3306:3306 --name my-mysql -e MYSQL_ROOT_PASSWORD=supersecret my-mysql
```
## To list running and stopped containers
```bash
$docker ps -a
```
## to enter the docker image
```bash
$docker exec -it mynewwebserver1 bash
```
## to start container with volumes
```bash
$docker run -d -p 80:80 --name devtest --mount source=myvol,target=/usr/share/nginx/html nginx:latest
```
## to check volume created
```bash
$docker inspect devtest
```
## copy file to the container
```bash
$docker cp index.html 2044f5e8c817:/usr/share/nginx/html
```
## create custom image
```bash
$docker commit 2044f5e8c817 nginx-test1
```
## run container with deferent public port 8080
```bash
$docker run -d --name new -p 8080:80 nginx-test1
```
## to list all images
```bash
$docker images
```
## to backup the image
```bash
$docker save -o nginx-test1.tar nginx-test1
```
## to delete image
```bash
$docker rmi -f nginx-test1
```
## to restore image .tar
```bash
$docker load -i nginx-test1.tar
```
## to see logs from the container
```bash
$docker logs -f bd30d8cc2ca7
```
## to build docker image from dockerfile
```bash
$docker build . -t sample
```
or
```bash
$docker build -t badrn/mysql-custom:v1 .
```
## if the container is stopped and can't be started due to an error,
you'll need to commit it to an image. Then you can launch bash in the new image:
```bash
$docker commit [CONTAINER_ID] temporary_image
$docker run --entrypoint=bash -it temporary_image
```
## to push image to docker hub
```bash
$docker push <account>/<RepoName>:tagname
```
## to pull image from docker hub
```bash
$docker pull <account>/<RepoName>:tagname
```
## create and link to an ubuntu container
```bash
$docker run -it --link myjenkins:alias-src --name myubuntu ubuntu:latest /bin/bash
```
## list all docker networks
```bash
$docker network ls
```
## More details on the network
```bash
$docker inspect <network_name>
```
## create own network
```bash
$docker network create mynetwork
```
## connect new container to mynetwork
```bash
$docker run -it --network mynetwork --name myubuntu ubuntu:latest /bin/bash
```
