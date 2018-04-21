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
     Digest is the SNAPSHOT. when we pull, it will download one or more snapshots to download the base images completely.
     
     
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
     
  
## Run docker Images
     You can use any of these commands to run image:
     
     docker run REPOSITORY:TAG
     docker run IMAGE ID  
     
### Example   
     docker run hello-world:latest
     docker run e38bc07ac18e
     


         
