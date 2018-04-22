#### GO TO *[HOME PAGE](index.md)*


#    Packaging customized container

      
###         Customizing a container      
          
            prems-MacBook-Air:~ premsagar$ docker images
            REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
            nginx               latest              b175e7467d66        12 days ago         109MB
            centos              latest              e934aafc2206        2 weeks ago         199MB
            prems-MacBook-Air:~ premsagar$ docker run -it nginx:latest /bin/bash
            root@4d0d3e7756fa:/# cd /root
            root@4d0d3e7756fa:~# echo "This is version 1" > image_ver.txt
            root@4d0d3e7756fa:~# apt-get update
            ......
            ......
            root@4d0d3e7756fa:~# apt-get install telnet openssh-server
            ......
            ......
            root@4d0d3e7756fa:~# adduser test
            ......
            ......
            root@4d0d3e7756fa:~# which telnet
            /usr/bin/telnet
            root@4d0d3e7756fa:~# which sshd
            /usr/sbin/sshd
            root@4d0d3e7756fa:~# cat /etc/group | grep test
            test:x:1000:
            root@4d0d3e7756fa:~#
            
            root@4d0d3e7756fa:~# exit
            exit
            prems-MacBook-Air:~ premsagar$ docker ps
            CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS               NAMES
            prems-MacBook-Air:~ premsagar$ docker ps -a
            CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS                     PORTS               NAMES
            4d0d3e7756fa        nginx:latest        "/bin/bash"         5 minutes ago       Exited (0) 5 seconds ago                       hungry_keller
            prems-MacBook-Air:~ premsagar$
            prems-MacBook-Air:~ premsagar$ docker restart hungry_keller
            hungry_keller
            prems-MacBook-Air:~ premsagar$ docker ps
            CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS               NAMES
            4d0d3e7756fa        nginx:latest        "/bin/bash"         7 minutes ago       Up 10 seconds       80/tcp              hungry_keller
            prems-MacBook-Air:~ premsagar$ docker attach hungry_keller
            root@4d0d3e7756fa:/# cd /root
            root@4d0d3e7756fa:~# ls | grep ver.txt
            image_ver.txt
            root@4d0d3e7756fa:~#
            root@4d0d3e7756fa:~# exit
            exit
            prems-MacBook-Air:~ premsagar$ 
            
            
###         Packaging customized container

            
            docker commit -m "Installed ssh teslnet and created user" -a "prem" CONTAINER_NAME REPO_NAME:TAG
            
            
            commit - creating a package 
            -m     - comment / message
            -a     - author  / maintaner
            
            
            
            prems-MacBook-Air:~ premsagar$ docker ps -a
            CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS                      PORTS               NAMES
            4d0d3e7756fa        nginx:latest        "/bin/bash"         10 minutes ago      Exited (0) 51 seconds ago                       hungry_keller
            prems-MacBook-Air:~ premsagar$ docker commit -m "Installed ssh teslnet and created user" -a "prem" hungry_keller prem/version1:v1
            sha256:805e779708609cd0b4de64dbccbfb2ecea48031612a1c180fb6ceff69dc54ded
            prems-MacBook-Air:~ premsagar$ docker images
            REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
            prem/version1       v1                  805e77970860        10 seconds ago      161MB
            nginx               latest              b175e7467d66        12 days ago         109MB
            centos              latest              e934aafc2206        2 weeks ago         199MB
            prems-MacBook-Air:~ premsagar$
            
            after pakaging when you do "docker Images" you will see new Image that you packaged
            
            If you want to create Image using docker file:
            
            vi Dockerfile
            
            FROM ubuntu:xenial
            MAINTAINER prem <prem@docker.com>
            RUN apt-get update
            RUN apt-get install -y telnet openssh-server
            
            docker build -t="prem/buildversion:v2" .
            
            
            
#### GO *[BACK](index.md)*           
            
            
            
            
            
            
            
            
            
