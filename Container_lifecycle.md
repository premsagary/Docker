#### GO TO *[HOME PAGE](index.md)*

# Lifecycle

      
      prems-MacBook-Air:~ root# docker ps
      CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS               NAMES
      prems-MacBook-Air:~ root# 


      prems-MacBook-Air:~ root# docker ps -a
      CONTAINER ID        IMAGE                COMMAND                  CREATED             STATUS                         PORTS               NAMES
      382b94296121        nginx:latest         "nginx -g 'daemon of…"   About an hour ago   Exited (0) About an hour ago                       mynginx2
      8471d3559d61        nginx:latest         "nginx -g 'daemon of…"   About an hour ago   Exited (0) About an hour ago                       mynginx1
      8e961e71c57a        b175e7467d66         "nginx -g 'daemon of…"   2 hours ago         Exited (0) 2 hours ago                             agitated_lamarr

      prems-MacBook-Air:~ root# docker images
      REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
      hello-world         latest              e38bc07ac18e        10 days ago         1.85kB
      nginx               latest              b175e7467d66        11 days ago         109MB
      centos              centos6             70b5d81549ec        2 weeks ago         195MB
      centos              latest              e934aafc2206        2 weeks ago         199MB
      docker/whalesay     latest              6b362a9f73eb        2 years ago         247MB

      prems-MacBook-Air:~ root# docker run -d --name=cycle nginx:latest
      65311eaf3159c49f2a89f071311ec4f7de861734e0cf6b9c404c4bce35a8266b
      prems-MacBook-Air:~ root#
      
      prems-MacBook-Air:~ root# docker ps
      CONTAINER ID        IMAGE               COMMAND                  CREATED              STATUS              PORTS               NAMES
      65311eaf3159        nginx:latest        "nginx -g 'daemon of…"   About a minute ago   Up About a minute   80/tcp               cycle
      
##    docker exec
      
      
      docker exec -it cycle /bin/bash (Command to exec)
      
      exec - execute something without effecting the running container 
      
     prems-MacBook-Air:~ root# docker ps
      CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS              PORTS               NAMES
      65311eaf3159        nginx:latest        "nginx -g 'daemon of…"   3 hours ago         Up 3 hours          80/tcp              cycle
      prems-MacBook-Air:~ root# docker exec -it cycle /bin/bash
      root@65311eaf3159:/# whoami
      root
      root@65311eaf3159:/#
      root@65311eaf3159:/# exit
      
      prems-MacBook-Air:~ root# docker ps
      CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS              PORTS               NAMES
      65311eaf3159        nginx:latest        "nginx -g 'daemon of…"   3 hours ago         Up 3 hours          80/tcp              cycle

      When you exit from "exec -it /bin/bash" it will not affect the running container
      
###   Docker stop
      
      prems-MacBook-Air:~ root# docker stop 65311eaf3159
      65311eaf3159
      prems-MacBook-Air:~ root# docker ps
      CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS                     NAMES
      
      you don't see anything running when you stop the running container
      
###   Docker restart 
      
      prems-MacBook-Air:~ root# docker restart 65311eaf3159
      65311eaf3159
      prems-MacBook-Air:~ root# docker ps
      CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS              PORTS               NAMES
      65311eaf3159        nginx:latest        "nginx -g 'daemon of…"   3 hours ago         Up 2 seconds        80/tcp              cycle
      prems-MacBook-Air:~ root# 
      
      
###   Docker start

      prems-MacBook-Air:~ root# docker start 65311eaf3159
      65311eaf3159
      prems-MacBook-Air:~ root# docker ps
      CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS              PORTS               NAMES
      65311eaf3159        nginx:latest        "nginx -g 'daemon of…"   3 hours ago         Up 2 seconds        80/tcp              cycle
      


#### GO *[BACK](index.md)*
