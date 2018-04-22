#### GO TO *[HOME PAGE](index.md)*


#     docker attach
        
          
          REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
          nginx               latest              b175e7467d66        11 days ago         109MB
          centos              latest              e934aafc2206        2 weeks ago         199MB
          prems-MacBook-Air:~ premsagar$ docker run -itd e934aafc2206 /bin/bash
          d022d3da1ed33a0d0e02995884e5fb23ddd1b42fdca946e64b66852dd957c2d6
          prems-MacBook-Air:~ premsagar$ docker ps
          CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS              PORTS               NAMES
          d022d3da1ed3        e934aafc2206        "/bin/bash"              8 seconds ago       Up 10 seconds                           affectionate_mirzakhani
          5ef3ef785614        b175e7467d66        "nginx -g 'daemon of…"   21 minutes ago      Up 21 minutes       80/tcp              vibrant_volhard
          prems-MacBook-Air:~ premsagar$ docker attach affectionate_mirzakhani
          [root@d022d3da1ed3 /]#
          
          when you run container with -itd (--interactive --termainal --disconnected) with shell /bin/bash
          It will be disconnected, but will be still running in the background
          You can use "attach" to attach to the container, as you sepecified shell while running container you dont need to specify while attaching.
          
          
          prems-MacBook-Air:~ premsagar$ docker attach affectionate_mirzakhani
          [root@d022d3da1ed3 /]#
          
          
          when you exit from the container, the container will stop running.
          
          [root@d022d3da1ed3 /]# exit
          exit
          prems-MacBook-Air:~ premsagar$ docker ps
          CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS              PORTS               NAMES
          5ef3ef785614        b175e7467d66        "nginx -g 'daemon of…"   27 minutes ago      Up 27 minutes       80/tcp              vibrant_volhard
          prems-MacBook-Air:~ premsagar$
          
          
          for more info you can use "docker inspect Container_Name"
          
          
#     Why we use restart          
          
          
          
          prems-MacBook-Air:~ premsagar$ docker images
          REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
          nginx               latest              b175e7467d66        11 days ago         109MB
          centos              latest              e934aafc2206        2 weeks ago         199MB
          prems-MacBook-Air:~ premsagar$ docker run -i -t --name=container1 nginx:latest /bin/bash
          root@d5728d84a328:/# ls
          bin  boot  dev	etc  home  lib	lib64  media  mnt  opt	proc  root  run  sbin  srv  sys  tmp  usr  var
          root@d5728d84a328:/# touch test.py
          root@d5728d84a328:/# ls
          bin  boot  dev	etc  home  lib	lib64  media  mnt  opt	proc  root  run  sbin  srv  sys  test.py  tmp  usr  var
          root@d5728d84a328:/# ls | grep .py
          test.py
          root@d5728d84a328:/# exit
          exit
          prems-MacBook-Air:~ premsagar$ docker run -i -t --name=container2 nginx:latest /bin/bash
          root@1acf6ec8d7c4:/# ls | grep .py
          root@1acf6ec8d7c4:/# exit
          exit
          prems-MacBook-Air:~ premsagar$ docker ps
          CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS               NAMES
          prems-MacBook-Air:~ premsagar$ docker ps -a
          CONTAINER ID        IMAGE               COMMAND             CREATED              STATUS                      PORTS               NAMES
          1acf6ec8d7c4        nginx:latest        "/bin/bash"         23 seconds ago       Exited (1) 12 seconds ago                       container2
          d5728d84a328        nginx:latest        "/bin/bash"         About a minute ago   Exited (0) 39 seconds ago                       container1
          d022d3da1ed3        e934aafc2206        "/bin/bash"         17 minutes ago       Exited (0) 11 minutes ago                       affectionate_mirzakhani
          prems-MacBook-Air:~ premsagar$ docker restart container1
          container1
          prems-MacBook-Air:~ premsagar$ docker attach container1
          root@d5728d84a328:/# ls | grep .py
          test.py
          root@d5728d84a328:/#



#### GO *[BACK](index.md)*

           
