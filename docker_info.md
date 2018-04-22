  #### GO TO *[HOME PAGE](index.md)*
  
  
  # Docker info 
  
  
          docker info (command to get more info on docker)
          
            prems-MacBook-Air:~ root# docker info            
            Containers: 1
            Running: 1
            Paused: 0
            Stopped: 0
            Images: 2
            Server Version: 18.03.0-ce
            Storage Driver: overlay2
            Backing Filesystem: extfs
            Supports d_type: true
            Native Overlay Diff: true
            Logging Driver: json-file
            Cgroup Driver: cgroupfs
            Plugins:
            Volume: local
            Network: bridge host ipvlan macvlan null overlay
            Log: awslogs fluentd gcplogs gelf journald json-file logentries splunk syslog
            Swarm: inactive
            Runtimes: runc
            Default Runtime: runc
            Init Binary: docker-init
            containerd version: cfd04396dc68220d1cecbe686a6cc3aa5ce3667c
            runc version: 4fc53a81fb7c994640722ac585fa9ca548971871
            init version: 949e6fa
            Security Options:
            seccomp
            Profile: default
            Kernel Version: 4.9.87-linuxkit-aufs
            Operating System: Docker for Mac
            OSType: linux
            Architecture: x86_64
            CPUs: 2
            Total Memory: 1.952GiB
            Name: linuxkit-025000000001
            ID: CAYQ:XBJ6:Z52N:5DI3:5OWI:NXS2:TE6K:RMP5:7UBU:YXUA:PR33:7WYO
            Docker Root Dir: /var/lib/docker
            Debug Mode (client): false
            Debug Mode (server): true
            File Descriptors: 29
            Goroutines: 49
            System Time: 2018-04-22T16:19:46.9743103Z
            EventsListeners: 2
            HTTP Proxy: docker.for.mac.http.internal:3128
            HTTPS Proxy: docker.for.mac.http.internal:3129
            Registry: https://index.docker.io/v1/
            Labels:
            Experimental: true
            Insecure Registries:
            127.0.0.0/8
            Live Restore Enabled: false
            
            You will get info about everything. how many Images are there, how many containers are there.
           
            Mostly all the containers and files will be in /var/lib/docker 
           
            
#### GO *[BACK](index.md)*            
            
            
