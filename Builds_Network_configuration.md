#### GO TO *[HOME PAGE](index.md)*


#   Network


          
          prems-MacBook-Air:~ root# docker network ls
          NETWORK ID          NAME                DRIVER              SCOPE
          71c3dff4677e        bridge              bridge              local
          6a418a191984        host                host                local
          5f41f992ea76        none                null                local
          
          prems-MacBook-Air:~ root# docker network ls --no-trunc
          NETWORK ID                                                         NAME                DRIVER              SCOPE
          71c3dff4677eed77b116d71a818810d9364b4fbc9c811ac9f5e5482eb6928df8   bridge              bridge              local
          6a418a1919849d1af52723ace89d368355e24026124eab786879570b3d9026bd   host                host                local
          5f41f992ea768124d55a7e461a11e5b527e9b22d95293ae8e2cd6388d9703ce6   none                null                local
          prems-MacBook-Air:~ root#
          
          
          prems-MacBook-Air:~ root# docker network inspect
          "docker network inspect" requires at least 1 argument.
          See 'docker network inspect --help'.
          Usage:  docker network inspect [OPTIONS] NETWORK [NETWORK...] [flags]
          
          
          prems-MacBook-Air:~ root# docker network inspect bridge             (bridge = NETWORK_NAME)
          [
            {
             "Name": "bridge",
             "Id": "71c3dff4677eed77b116d71a818810d9364b4fbc9c811ac9f5e5482eb6928df8",
             "Created": "2018-04-21T14:36:15.521651183Z",
             "Scope": "local",
             "Driver": "bridge",
             .......
             .......
             .......
             
             
##    Create a network

              
              
            for man page "man docker-network-create"
            
            prems-MacBook-Air:~ root# docker network create --subnet 10.1.0.0/24 --gateway 10.1.0.1 mybridge01
            79c059631bc456b8b18bd8bc5e098da1a4cb8ad37837c64fbd3fed2bcb23a862
            prems-MacBook-Air:~ root# docker network ls
            NETWORK ID          NAME                DRIVER              SCOPE
            71c3dff4677e        bridge              bridge              local
            6a418a191984        host                host                local
            79c059631bc4        mybridge01          bridge              local
            5f41f992ea76        none                null                local
            
            
 ##    Remove a network
 
 
                
             prems-MacBook-Air:~ root# docker network ls
             NETWORK ID          NAME                DRIVER              SCOPE
             71c3dff4677e        bridge              bridge              local
             6a418a191984        host                host                local
             79c059631bc4        mybridge01          bridge              local
             5f41f992ea76        none                null                local
             prems-MacBook-Air:~ root# docker network rm mybridge01
             mybridge01
             prems-MacBook-Air:~ root# docker network ls
             NETWORK ID          NAME                DRIVER              SCOPE
             71c3dff4677e        bridge              bridge              local
             6a418a191984        host                host                local
             5f41f992ea76        none                null                local
             prems-MacBook-Air:~ root# 
             
   
###    Create network and run container on that network



          
             prems-MacBook-Air:~ root# docker network create --subnet 10.1.0.0/24 --gateway 10.1.0.1 mybridge01
             0b163b731d438597cc71e6261c8ce015be61dcf1da15d768c5d509fcd135c852
             
             prems-MacBook-Air:~ root# docker run -d --name=networktest1 --net mybridge01 centos:latest /bin/bash
             8beb69ca73a6fa7c714661508eb5ce27939478f52cacab2a36efbb344e40c230
             
             
             
###     Run a container with a static IP from the network you created



             
             I am assigning container IP=10.1.0.100 from mybridge01 network
             
             prems-MacBook-Air:~ root# docker run -itd --name=net_test --net mybridge01 --ip 10.1.0.100 nginx:latest /bin/bash
             6bd17127b077efa6400f011840661d87609806d5f02d7c2c07da3421fc288b05
             
             prems-MacBook-Air:~ root# docker ps
             CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS               NAMES
             6bd17127b077        nginx:latest        "/bin/bash"         37 seconds ago      Up 45 seconds       80/tcp              net_test
             
             
             Let's check the IP for container
             
             prems-MacBook-Air:~ root# docker inspect net_test | grep IPAddress
                                       "SecondaryIPAddresses": null,
                                          "IPAddress": "",
                                          "IPAddress": "10.1.0.100"
                                          
                                  
                                  
                                                                          
####  GO *[BACK](index.md)*               
             
             
             
             
          
