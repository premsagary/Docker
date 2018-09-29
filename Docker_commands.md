#### GO TO *[HOME PAGE](index.md)*


#       Commands

        docker
        docker --version
        docker info
        docker pull IMAGE_NAME:TAG
        docker ps -a
        docker run -d IMAGE_NAME
        docker run -it IMAGE_NAME /bin/bash
        docker run -itd IMAGE_NAME
        docker logs CONTAINER_NAME  (to check log of container)
        docker exec CONTAINER_NAME COMMAND  (to run command from local machine on a container without logging in)
        docker images
        docker history CONTAINER_NAME
        docker inspect CONTAINER_NAME
        docker inspect CONTAINER_NAME | grep IPAddress
        docker start
        docker stop
        docker restart
        docker run -d -P --name=GIVE_CONTAINER_NAME IMAGE_NAME (assign a random port)
        docker run -d -p 8080:80 --name=GIVE_CONTAINER_NAME IMAGE_NAME (local 8080 to container 80)
        docker run -d -p 8080:80 --name=webserver4 -v /User/premsagar/www/:/usr/share/nginx/html  nginx:latest
        docker commit -m "Installed ssh teslnet and created user" -a "prem" CONTAINER_NAME REPO_NAME:TAG
        docker run ubuntu:latest /bin/echo "Hello from the container" (It will start the container just to echo the message)
        docker run -d ubuntu:latest /bin/bash -c "while true;do echo HELLO;sleep 1;done" (will run echo in container continuesly)
        docker network ls
        docker network ls --no-trunc
        man docker-network-create
        docker network create --subnet 10.1.0.0/24 --gateway 10.1.0.1 NETWORK_NAME
        docker network rm NETWORK_NAME
        docker run -d --name=CONTAINER_NAME --net NETWORK_NAME centos:latest /bin/bash
        docker run -itd --name=CONTAINER_NAME --net NETWORK_NAME --ip 10.1.0.100 nginx:latest /bin/bash
        docker tag IMAGE_NAME REPOSITORY_NAME
        login to docker 
        docker push REPOSITORY_NAME   (It will push images that tagged)
        docker logout
        dockre info | grep Storage
        /etc/docker  file - daemon.json -- /var/lib/docker
        docker info | grep Logging
        docker logs CONTAINERID (To change logs location edit daemon.json)
        docker swarm init --advertise-addr IP ( To add manager )
        docker swarm join-token worker (If you forget token)
        docker swarm join-token manager (to create a new manager for the node)
        docker system info | more 
        docker node ls
        
        
        
        
        
        
####  GO *[BACK](index.md)*         
