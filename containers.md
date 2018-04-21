#### GO TO *[HOME PAGE](index.md)*

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
             CONTAINER ID        IMAGE                COMMAND                  CREATED             STATUS                                       PORTS               NAMES
             739f815bac79        docker/whalesay      "cowsay Hey, how are…"   10 minutes ago      Exited (0) 11 minutes ago                          hardcore_mahavira
            ee05cfbe3549        docker/whalesay      "cowsay Hey, images …"   11 minutes ago      Exited (0) 11 minutes ago                          pedantic_lewin
             8f67ef314e22        docker/whalesay      "cowsay Heydocker im…"   11 minutes ago      Exited (0) 11 minutes ago                          happy_panini
            4bcc578a65b2        e38bc07ac18e         "/hello"                 About an hour ago   Exited (0) About an hour ago                       inspiring_franklin
            5c4aaee78fc5        hello-world:latest   "/hello"                 About an hour ago   Exited (0) About an hour ago                       keen_engelbart
              a766d9aa1a6d        hello-world          "/hello"                 About an hour ago   Exited (0) About an hour ago                       jovial_perlman
            86c45fd76ac4        b28219773b9b         "/sbin/init"             42 hours ago        Exited (255) 6 hours ago                            22/tcp              determined_kapitsa
            076451e8b9ff        910f1a0c505d         "/bin/sh -c 'echo eu…"   42 hours ago        Exited (137) 42 hours ago                          minecraft
             2ed1b189de67        b28219773b9b         "/sbin/init"             42 hours ago        Exited (137) 42 hours ago                          ubuntu-upstart
        


      When you run a container it will be given a name, for example when I ran Whalesay it gave name as "hardcore_mahavira"
      you can use this names for inspecting the container 
      
      prems-MacBook-Air:~ root# docker inspect hardcore_mahavira
      [
        {
            "Id": "739f815bac79079eae11ddd85f965f59cc4fd8a3753003849ac759c6dd63985c",
            "Created": "2018-04-21T20:51:21.2085706Z",
            "Path": "cowsay",
               "Args": [
                   "Hey,",
                   "how",
                   
                  ........
                  ........
                  ........
                  
                  
## Container IP's


       When you do ifconfig on terminal
       you will see docker0:172.17.0.1
       It will assign ip address from 172.17.0.2 - 172.17.0.254
       
## Run container in interactive mode 


      docker run -i -t ID /bin/bash (or) docker run -it ID/REPOSITORY:TAG /bin/bash
            -i = interactive
            -t = terminal
            /bin/bash shell
      
      
      prems-MacBook-Air:~ root# docker images
      REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
      hello-world         latest              e38bc07ac18e        10 days ago         1.85kB
      nginx               latest              b175e7467d66        11 days ago         109MB
      centos              centos6             70b5d81549ec        2 weeks ago         195MB
      centos              latest              e934aafc2206        2 weeks ago         199MB
      docker/whalesay     latest              6b362a9f73eb        2 years ago         247MB
      
      
      prems-MacBook-Air:~ root# docker run -it nginx:latest /bin/bash
      root@600de7285659:/#
      
      If you see I logged into the container 
      
      prems-MacBook-Air:~ root# docker run -it nginx:latest /bin/bash
      root@564c20929831:/# whoami
      root
      root@564c20929831:/# apt-get upgrade
      Reading package lists... Done
      Building dependency tree       
      Reading state information... Done
      Calculating upgrade... Done
      0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
      
      If you open a new terminal and do "docker -ps"
      
      prems-MacBook-Air:~ root# docker ps  
      CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS         NAMES
      564c20929831        nginx:latest        "/bin/bash"         2 minutes ago       Up 2 minutes       80/tcp    sharp_mayer
      
      And it also assigned the name "sharp_mayer"
      
      when you exit from the running container, 
      you will no longer see the container when you do "docker ps", you can see in the history using "docker ps -a"
      
     
## Run container's in the background in the detached mode

      If you wnt to run the containers in the background / if you want to run the container without you being connected to it.
      you can you this:
      
      docker run -d centos:latest /bin/bash
      -d = disconnected 
      
      prems-MacBook-Air:~ root# docker run -d nginx:latest /bin/bash
      d553589fa9e5c9e3d65766cdb91f126f0a5578dd40c9523ca0f1c0d5f3ff4870
      prems-MacBook-Air:~ root#
      
      prems-MacBook-Air:~ root# docker ps
      CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS       NAMES
      prems-MacBook-Air:~ root#
      
      you still dont see because you want to execute /bin/bash
      
      prems-MacBook-Air:~ root# docker run -d nginx:latest          
      da178c27d7b664afb910dfa2d7ebb041dc3cb1f1ee0af9fe8968cb87f5d7fb8c
      prems-MacBook-Air:~ root#
      
      prems-MacBook-Air:~ root# docker ps
      CONTAINER ID        IMAGE               COMMAND                  CREATED                  STATUS              PORTS
         NAMES
      da178c27d7b6        nginx:latest        "nginx -g 'daemon of…"   Less than a second ago   Up 18 seconds       80/tcp              nifty_liskov
      
      prems-MacBook-Air:~ root# docker inspect nifty_liskov
            [
                  {
                  "Id": "da178c27d7b664afb910dfa2d7ebb041dc3cb1f1ee0af9fe8968cb87f5d7fb8c",
                  "Created": "2018-04-21T21:38:43.404377Z",
                  "Path": "nginx",
                  "Args": [
                  "-g",
                  "daemon off;"
                  ..........
                  ..........
                  ..........
                    "Gateway": "172.17.0.1",
                    "IPAddress": "172.17.0.2",
                    "IPPrefixLen": 16,
                    "IPv6Gateway": "",
                    "GlobalIPv6Address": "",
                    "GlobalIPv6PrefixLen": 0,
                    ..........
                    ..........
                    ..........
                    
                    
        you will see an IPAddress "172.17.0.2" and when you do "docker ps" it will show the port "80 / 443"
        
        Install elink (elinks is a text baseed web browser)
        apt-get install elinks
        elinks http://172.17.0.2/ (Command to browse the link)
        you will see Nginx running.
        
       
       
## Stop a running container 

      docker stop NAME (Command to stop running container)
        
      prems-MacBook-Air:~ root# docker ps
      CONTAINER ID   IMAGE               COMMAND           CREATED             STATUS              PORTS              NAMES
      8e961e71c57a   b175e7467d66        "nginx -g 'daemon of…"   3 minutes ago       Up 3 minutes 80/tcp    agitated_lamarr
      prems-MacBook-Air:~ root# docker stop agitated_lamarr
      agitated_lamarr
      prems-MacBook-Air:~ root# docker ps
      CONTAINER ID   IMAGE               COMMAND             CREATED             STATUS            PORTS                 NAMES
      prems-MacBook-Air:~ root#


        
#### GO *[BACK](index.md)*
        
        
        
        
      
      
                  

    
      
