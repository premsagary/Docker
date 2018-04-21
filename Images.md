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
     
  
## Run docker Images

     
     You can use any of these commands to run image
     
     docker run REPOSITORY:TAG    
     docker run IMAGE ID          
     
     **Example**
     *docker run hello-world:latest*
     *docker run e38bc07ac18e*
     


         
