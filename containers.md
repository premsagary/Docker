
## Whalesay


      ### docker search whalesay
      
      prems-MacBook-Air:~ root# docker search whalesay
      NAME                            DESCRIPTION                                     STARS               
      docker/whalesay                 An image for use in the Docker demo tutorial    627                                     
      mendlik/docker-whalesay         Docker whalesay image from training material…   6    
      
      
      
      ### docker pull docker/whalesay
      
      After search I will pull the image with highest starts
      docker pull NAME
      
      prems-MacBook-Air:~ root# docker pull docker/whalesay
      Using default tag: latest
      latest: Pulling from docker/whalesay
      e190868d63f8: Pull complete 
      909cd34c6fd7: Pull complete 
      0b9bfabab7c1: Pull complete 
      a3ed95caeb02: Pull complete 
      00bf65475aba: Pull complete 
      c57b6bcc83e3: Pull complete 
      8978f6879e2f: Pull complete 
      8eed3712d2cf: Pull complete 
      Digest: sha256:178598e51a26abbc958b8a2e48825c90bc22e641de3d31e18aaf55f3258ba93b
      Status: Downloaded newer image for docker/whalesay:latest
      
## Run Images

      
      docker run hello-world:latest
      docker run e38bc07ac18e
      
      When you "run" a container my passing an INPUT, you will get output and you will be exited from the container
                  
      prems-MacBook-Air:~ root# docker run docker/whalesay cowsay Hey, how are you Prem?
                   ________________________ 
                  < Hey, how are you Prem? >
                   ------------------------ 
                      \
                       \
                        \     
                                      ##        .            
                                ## ## ##       ==            
                             ## ## ## ##      ===            
                         /""""""""""""""""___/ ===        
                    ~~~ {~~ ~~~~ ~~~ ~~~~ ~~ ~ /  ===- ~~~   
                         \______ o          __/            
                          \    \        __/             
                            \____\______/   


       cowsay is the actual application which container is running
       run is just a way to run a container
       
       
       
## How to check what containers you are running


        docker ps (command to check the running containers)
        
        prems-MacBook-Air:~ root# docker ps
        CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS 
        prems-MacBook-Air:~ root# 
        
        Why would it say it's not running anything? when you just did Whalesay???
        It's because it's exiting the container after running input on it.
        
        But you can check the History of what containers you ran.
        
        docker ps -a (command to see history of containers that you ran)
        
        prems-MacBook-Air:~ root# docker ps -a
      CONTAINER ID        IMAGE                COMMAND                  CREATED             STATUS                                        PORTS               NAMES
      739f815bac79        docker/whalesay      "cowsay Hey, how are…"   10 minutes ago      Exited (0) 11 minutes ago                          hardcore_mahavira
      ee05cfbe3549        docker/whalesay      "cowsay Hey, images …"   11 minutes ago      Exited (0) 11 minutes ago                          pedantic_lewin
      8f67ef314e22        docker/whalesay      "cowsay Heydocker im…"   11 minutes ago      Exited (0) 11 minutes ago                          happy_panini
      4bcc578a65b2        e38bc07ac18e         "/hello"                 About an hour ago   Exited (0) About an hour ago                       inspiring_franklin
      5c4aaee78fc5        hello-world:latest   "/hello"                 About an hour ago   Exited (0) About an hour ago                       keen_engelbart
      a766d9aa1a6d        hello-world          "/hello"                 About an hour ago   Exited (0) About an hour ago                       jovial_perlman
      86c45fd76ac4        b28219773b9b         "/sbin/init"             42 hours ago        Exited (255) 6 hours ago                            22/tcp              determined_kapitsa
      076451e8b9ff        910f1a0c505d         "/bin/sh -c 'echo eu…"   42 hours ago        Exited (137) 42 hours ago                          minecraft
      2ed1b189de67        b28219773b9b         "/sbin/init"             42 hours ago        Exited (137) 42 hours ago                          ubuntu-upstart
        





    
      
