#### GO TO *[HOME PAGE](index.md)*

#       Commands


        docker ps -a
        docker logs CONTAINER_NAME  (to check log of container)
        docker exec CONTAINER_NAME COMMAND  (to run command from local machine on a container without logging in)
        docker images
        docker inspect CONTAINER_NAME
        docker start
        docker stop
        docker restart
        docker pull IMAGE_NAME:TAG
        docker run -d IMAGE_NAME
        docker run -it IMAGE_NAME /bin/bash
        docker run -itd IMAGE_NAME
        docker run -d -P --name=GIVE_CONTAINER_NAME IMAGE_NAME (assign a random port)
        docker run -d -p 8080:80 --name=GIVE_CONTAINER_NAME IMAGE_NAME (local 8080 to container 80)
        docker run -d -p 8080:80 --name=webserver4 -v /User/premsagar/www/:/usr/share/nginx/html  nginx:latest
        docker commit -m "Installed ssh teslnet and created user" -a "prem" CONTAINER_NAME REPO_NAME:TAG
        docker run ubuntu:latest /bin/echo "Hello from the container" (It will start the container just to echo the message)
        docker run -d ubuntu:latest /bin/bash -c "while true;do echo HELLO;sleep 1;done" (will run echo in container continuesly)
        
        
####  GO *[BACK](index.md)*         
