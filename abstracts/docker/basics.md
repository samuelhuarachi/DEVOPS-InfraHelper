# docker.md

## Remove dangling images
docker rmi $(docker images --filter "dangling=true" -q --no-trunc)

## Run container
docker run -it --name=ubuntu_container_name start_ubuntu /bin/bash

## Network IPv6
docker network create --subnet="2001:db8:1::/64" --gateway="2001:db8:1::1" --ipv6 my-net1

## Remove all containers
docker rm $(docker ps -a -q) -f

## Build image
docker build --rm -t [image name] .
docker build --rm --no-cache -t [image name] .
docker build -i -t samuelhuarachi/nodeapp .
docker build --no-cache -t samuelhuarachi/nodeapp .

## Run images
docker run -itd -p 8086:8086 --privileged [image name]
docker run -d -p 27017:27017 [container name/id]
docker run -i -t -p 3001:3001 samuelhuarachi/node1-k8s /bin/bash
docker run -d -p 3001:3001 samuelhuarachi/nodeapp
docker run -d -p 3001:3001 -it a1ef8ef759d9

## Docker Hub
docker login
docker push samuelhuarachimyappnode:latest
https://hub.docker.com/

## Exec
docker exec -it [container id] /bin/bash
docker exec -it <mycontainer> bash

## MongoDB
docker run -d -p 27017:27017 mongo
docker run -d -p 27017:27017 --mount source=mongo-vol,target=/app mongo
docker run -d --mount source=mongo-vol,target=/app mongo
docker run -d -p 27017:27017 -v mongodata:C:\\Users\\samu1\\OneDrive\\Área de Trabalho\\[]\\mongodata mongo
docker run -d -p 27017:27017 -v mongodata:\\wsl$\docker-desktop-data\version-pack-data\community\docker\volumes
docker run -d --name dbm -v ~/mongoDBData:/data/db -p 27017:27017 mongo

## Volumes
docker volume create mongo-vol
docker volume inspect mongo-vol
docker volume ls

## Containers control
docker start dbs
sudo docker restart discourse_app
sudo docker stop discourse_app
sudo docker start discourse_app
sudo docker rename discourse_app disc_app

## Change docker data path
sudo systemctl stop docker
sudo mount --rbind ./mnt/docker /var/lib/docker
sudo systemctl start docker

## Logs
docker attach [container id]
docker inspect --format='{{.LogPath}}' <container_name_or_id>
