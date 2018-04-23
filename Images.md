#### GO TO *[HOME PAGE](index.md)*

# Images


## Check available Images


     docker images (command to check existing images)

     prems-MacBook-Air:~ root# docker images
     REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
     prems-MacBook-Air:~ root# 


## Search for docker image to pull 


    docker search IMAGE_NAME (command to search for image)

    
    prems-MacBook-Air:~ root# docker search nginx
    NAME                                                   DESCRIPTION                                     STARS               
    nginx                                                  Official build of Nginx.                         8341  
    jwilder/nginx-proxy                                    Automated Nginx reverse proxy for docker con…    1321   
    richarvey/nginx-php-fpm                                Container running Nginx + PHP-FPM capable of…    546 

    
    The one with the most stars is a good one
    
## Pull docker Images

     
     prems-MacBook-Air:~ root# docker pull hello-world
     Using default tag: latest
     latest: Pulling from library/hello-world
     9bb5a5d4561a: Pull complete 
     Digest: sha256:f5233545e43561214ca4891fd1157e1c3c563316ed8e237750d59bde73361e77
     Status: Downloaded newer image for hello-world:latest
     prems-MacBook-Air:~ root# 
     
     
     Default tag will be latest, it will pull the latest image
     
   
     prems-MacBook-Air:~ root# docker images
     REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
     hello-world         latest              e38bc07ac18e        10 days ago         1.85kB
     
     
     When you say "docker pull centos". It's going to pull latest version of CentOS as the default tag is "latest"
     
     prems-MacBook-Air:~ root# docker pull centos 
     Using default tag: latest
     latest: Pulling from library/centos
     469cfcc7a4b3: Pull complete 
     Digest: sha256:989b936d56b1ace20ddf855a301741e52abca38286382cba7f44443210e96d16
     Status: Downloaded newer image for centos:latest
     
     When you specify tag "docker pull centos:centos6" it will pull CentOS6 
     
     prems-MacBook-Air:~ root# docker pull centos:centos6
     centos6: Pulling from library/centos
     987d765a926d: Pull complete 
     Digest: sha256:67b491e26d566ee9c55578bfd6115554a6e1b805a49502ead32cb1a324466f2c
     Status: Downloaded newer image for centos:centos6
     
     prems-MacBook-Air:~ root# docker images
     REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
     hello-world         latest              e38bc07ac18e        10 days ago         1.85kB
     centos              centos6             70b5d81549ec        2 weeks ago         195MB
     centos              latest              e934aafc2206        2 weeks ago         199MB
     
     prems-MacBook-Air:~ root# docker pull nginx:latest
     latest: Pulling from library/nginx
     2a72cbf407d6: Pull complete 
     04b2d3302d48: Pull complete 
     e7f619103861: Pull complete 
     Digest: sha256:18156dcd747677b03968621b2729d46021ce83a5bc15118e5bcced925fb4ebb9
     Status: Downloaded newer image for nginx:latest
     
     If you see when I pulled nginx:latest its pulling multiple layers for base image(2a72cbf407d6,04b2d3302d48,e7f619103861)
     The reason is 2a72cbf407d6 would be underlying operating system 
     04b2d3302d48 would be Nginx package installation on the image
     e7f619103861 may be nginx configuration
     
     When you build/customize a container after pulling the base image, each change you make will become a layer or 
     snapshot that are added to the image. It will be more clear when we start commiting the images.
     
## Inspect Images

     If you want to know more about the image you can use this command, output will be in JSON.
     docker inspect IMAGE ID / REPOSITORY:TAG 
     prems-MacBook-Air:~ root# docker inspect nginx:latest
     [
          {
        "Id": "sha256:b175e7467d666648e836f666d762be92a56938efe16c874a73bab31be5f99a3b",
        "RepoTags": [
            "nginx:latest"
          ],
        "RepoDigests": [
            "nginx@sha256:18156dcd747677b03968621b2729d46021ce83a5bc15118e5bcced925fb4ebb9"
            .........
            .........
            .........
            .........
            .........
     
     
     
  
## Run docker Images
     You can use any of these commands to run image:
     
     docker run REPOSITORY:TAG
     docker run IMAGE ID  
     
### Example   
     docker run hello-world:latest
     docker run e38bc07ac18e
     
     
## Image history 

          docker history IMAGE_NAME

          prems-MacBook-Air:~ root# docker history prem/version1:v1
          IMAGE               CREATED             CREATED BY                                      SIZE                COMMENT
          805e77970860        2 hours ago         /bin/bash                                       52.2MB                     Installed ssh teslnet and created user
          b175e7467d66        12 days ago         /bin/sh -c #(nop)  CMD ["nginx" "-g" "daemon…   0B                  
          <missing>           12 days ago         /bin/sh -c #(nop)  STOPSIGNAL [SIGTERM]         0B                  
          <missing>           12 days ago         /bin/sh -c #(nop)  EXPOSE 80/tcp                0B                  
          <missing>           12 days ago         /bin/sh -c ln -sf /dev/stdout /var/log/nginx…   22B                 
          <missing>           12 days ago         /bin/sh -c set -x  && apt-get update  && apt…   53.7MB              
          <missing>           12 days ago         /bin/sh -c #(nop)  ENV NJS_VERSION=1.13.12.0…   0B                  
          <missing>           12 days ago         /bin/sh -c #(nop)  ENV NGINX_VERSION=1.13.12…   0B                  
          <missing>           5 weeks ago         /bin/sh -c #(nop)  LABEL maintainer=NGINX Do…   0B                  
          <missing>           5 weeks ago         /bin/sh -c #(nop)  CMD ["bash"]                 0B                  
          <missing>           5 weeks ago         /bin/sh -c #(nop) ADD file:e3250bb9848f956bd…   55.3MB  
     
     
#### GO *[BACK](index.md)*

         
