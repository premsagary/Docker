#### GO TO *[HOME PAGE](index.md)*

# Ports and Volumes


      prems-MacBook-Air:~ premsagar$ docker run -d nginx:latest
      2e1e666b113a302a770cd6fd1e89962386e89855ecfd371cb316fc5b753a7d9d
      prems-MacBook-Air:~ premsagar$ docker ps
      CONTAINER ID        IMAGE               COMMAND                  CREATED                  STATUS              PORTS               NAMES
      2e1e666b113a        nginx:latest        "nginx -g 'daemon of…"   Less than a second ago   Up 2 seconds        80/tcp              eloquent_boyd
      prems-MacBook-Air:~ premsagar$ docker inspect eloquent_boyd | grep IPAddress
                          "SecondaryIPAddresses": null,
                          "IPAddress": "172.17.0.2",
                                "IPAddress": "172.17.0.2",
      
      prems-MacBook-Air:~ premsagar$ elinks http://172.17.0.2/ (You will see default nginx site)
      prems-MacBook-Air:~ premsagar$ elinks http://localhost   (You will get nothing)
      
      prems-MacBook-Air:~ premsagar$ docker ps
      CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS              PORTS               NAMES
      2e1e666b113a        nginx:latest        "nginx -g 'daemon of…"   4 minutes ago       Up 5 minutes        80/tcp              eloquent_boyd
      prems-MacBook-Air:~ premsagar$ docker stop eloquent_boyd
      
      
      prems-MacBook-Air:~ premsagar$ docker rm -f 2e1e666b113a
      2e1e666b113a
      prems-MacBook-Air:~ premsagar$
      
      
      prems-MacBook-Air:~ premsagar$ docker images
      REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
      nginx               latest              b175e7467d66        11 days ago         109MB
      centos              centos6             70b5d81549ec        2 weeks ago         195MB
      


###   Link nginx open port to some random port on localhost       
      
      prems-MacBook-Air:~ premsagar$ docker run -d --name=webserver1 -P nginx:latest
      d8b947b9e648674adb1790cdfb0086285846e09cfa854b978fd1b450cdc4f284
      
      -P : Link nginx open port to some random port on localhost 
      
      prems-MacBook-Air:~ premsagar$ docker ps
      CONTAINER ID        IMAGE               COMMAND                  CREATED              STATUS              PORTS                   NAMES
      d8b947b9e648        nginx:latest        "nginx -g 'daemon of…"   About a minute ago   Up About a minute   0.0.0.0:32768->80/tcp   webserver1
      
      Now you see nginx 80 port is linked to 32768 port of local host
       
      prems-MacBook-Air:~ premsagar$ elinks http://172.17.0.2/ (You will see default nginx site)
      prems-MacBook-Air:~ premsagar$ elinks http://localhost:32768 (you will see nginx default page)
      
      prems-MacBook-Air:~ premsagar$ docker port webserver1 $CONTAINERPORT
      80/tcp -> 0.0.0.0:32768
      


###   Link nginx open port to specifc port on localhost

      prems-MacBook-Air:~ premsagar$ docker run -d -p 8080:80  --name=webserver2 nginx:latest
      98e4f9696ebf15c748083c13de68c3ff6af57d5edebc89de1f161951b984d1a3
      
      -p : Link nginx open port to specific port on localhost

      prems-MacBook-Air:~ premsagar$ elinks http://172.17.0.2/ (You will see default nginx site)
      prems-MacBook-Air:~ premsagar$ elinks http://localhost:8080 (you will see nginx default page)
      
      prems-MacBook-Air:~ premsagar$ docker port webserver2 $CONTAINERPORT
      80/tcp -> 0.0.0.0:8080
      
###   Mount your local volume on the container volume when you run it

      prems-MacBook-Air:~ premsagar$ docker run -d -p 8080:80 --name=webserver4 -v /User/premsagar/www/:/usr/share/nginx/html  nginx:latest 
      a4ead16efdeaf24cb239194705cdc0ae522bb8f0ed21a0f13d547f91d4630b26
      prems-MacBook-Air:~
      
      -d      : disconnected mode
      -p      : Link container port to specific local host
      8080    : localhost port
      80      : container port 
      --name  : name for the container 
      -v      : mount local volume on container volume 
      
      
      you can add your website files to local folder which is monted on container, nginx will use it
      

##   Docker file for building container

            prems-MacBook-Air:~ premsagar$ vi Dockerfilevi dockerfile
            
            FROM debian:stable
            MAINTAINER prem <prem@docker.com>                                    
            
            RUN apt-get update                                   
            RUN apt-get upgrade
            RUN apt-get install telnet
      
            docker build -t premsagar/myapache .  ( "." will help where to look for dockerfile)
            
            it will use cached copies if you remove one "RUN" and run again although if you deleted the Image.
            
            Best practice:
            
            FROM debian:stable
            MAINTAINER prem <prem@docker.com>
            RUN apt-get update && apt-get upgrade -y && apt-get install -y apache2 telnet elinks openssh-server
            (This will help to create lesss dependent images when you run script) 
            
            
            
            
      


#### GO *[BACK](index.md)*      
      
