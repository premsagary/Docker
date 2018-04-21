
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






    
      
