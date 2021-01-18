# mall-and-more

#Vitual Box Configuration

`vagrant init centos/7` Use vagrant to build and manage a virtual box in a single flow
`vagrant up` to start the virtual box
`vagrant ssh` to communicate local machine with the virtual box
`ip addr` to check ip address

#Docker

Install docker https://docs.docker.com/engine/install/centos/
use `su root` swich to user root, default password is "vagrant"
OR
`sudo systemctl start docker` to start docker
`sudo docker images` to check all the images
`sudo systemctl enable docker` will enable docker to start once the virtual machine starts

MySQL Container

`docker run --name mysql -p 3306:3306 \
-v /home/wen/docker/mysql/log:/var/log \
-v /home/wen/docker/mysql/data:/var/lib/mysql \
-v /mydata/mysql/conf:/etc/mysql \
-e MYSQL_ROOT_PASSWORD=root \
-d mysql:5,7`  create and run mysql 5.7 as well as monitoring coresponding data from mysql container to linux
`docker exec -it mysql /bin/bash` go to mysql container console, `exit` to get back to vagrant

Redis Container

`docker run -p 6379:6379 --name redis -v /mydata/redis/data:/data \
-v/mydata/redis/conf/redis.conf:/etc/redis/redis.conf \
-d redis redis-server /etc/redis/redis.conf` create and run redis as well as monitoring coresponding data from redis container to linux
`docker exec -it redis redis-cli` use redis through docker
Notice if we want to make data persistent after restarting redis image, open redis.conf file and add "appendonly yes"

`docker ps` check all running images
`docker start CONTAINER_NAME` start the container, `docker restart CONTAINER_NAME` to restart


go to nacos file and `startup.sh` to start registration center https://github.com/alibaba/nacos

`npm run dev` to start web server




