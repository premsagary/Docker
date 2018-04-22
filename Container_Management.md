
#### GO TO *[HOME PAGE](index.md)*

# Container Management


    prems-MacBook-Air:~ root# docker images
    REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
    hello-world         latest              e38bc07ac18e        10 days ago         1.85kB
    nginx               latest              b175e7467d66        11 days ago         109MB
    centos              centos6             70b5d81549ec        2 weeks ago         195MB
    centos              latest              e934aafc2206        2 weeks ago         199MB
    docker/whalesay     latest              6b362a9f73eb        2 years ago         247MB
    
    
###Docker remove images

    docker rmi ID
    docker rmi -f ID
    
    prems-MacBook-Air:~ root# docker rmi e934aafc2206
    Untagged: centos:latest
    Untagged: centos@sha256:989b936d56b1ace20ddf855a301741e52abca38286382cba7f44443210e96d16
    Deleted: sha256:e934aafc22064b7322c0250f1e32e5ce93b2d19b356f4537f5864bd102e8531f
    Deleted: sha256:43e653f84b79ba52711b0f726ff5a7fd1162ae9df4be76ca1de8370b8bbf9bb0
    
    
    
##### Method 1: 
 
    docker rm ID (delete the container dependent on Image)
    
    you want to delete base Image but some containers are running which depend on base Image  (remove the containers using "rm")
    
    prems-MacBook-Air:~ root# docker rmi e38bc07ac18e
    Error response from daemon: conflict: unable to delete e38bc07ac18e (must be forced) - image is being used by stopped container 4bcc578a65b2
    prems-MacBook-Air:~ root# docker rm 4bcc578a65b2
    4bcc578a65b2
    prems-MacBook-Air:~ root# docker rmi e38bc07ac18e
    Error response from daemon: conflict: unable to delete e38bc07ac18e (must be forced) - image is being used by stopped container a766d9aa1a6d
    prems-MacBook-Air:~ root# docker rm a766d9aa1a6d
    a766d9aa1a6d
    prems-MacBook-Air:~ root# docker rmi e38bc07ac18e
    Error response from daemon: conflict: unable to delete e38bc07ac18e (must be forced) - image is being used by stopped container 5c4aaee78fc5
    prems-MacBook-Air:~ root# docker rm 5c4aaee78fc5
    5c4aaee78fc5
    prems-MacBook-Air:~ root# docker rmi e38bc07ac18e
    Untagged: hello-world:latest
    Untagged: hello-world@sha256:f5233545e43561214ca4891fd1157e1c3c563316ed8e237750d59bde73361e77
    Deleted: sha256:e38bc07ac18ee64e6d59cf2eafcdddf9cec2364dfe129fe0af75f1b0194e0c96
    Deleted: sha256:2b8cbd0846c5aeaa7265323e7cf085779eaf244ccbdd982c4931aef9be0d2faf
    
    
##### Method 2:    

    prems-MacBook-Air:~ root# docker images
    REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
    nginx               latest              b175e7467d66        11 days ago         109MB
    centos              centos6             70b5d81549ec        2 weeks ago         195MB
    docker/whalesay     latest              6b362a9f73eb        2 years ago         247MB
    prems-MacBook-Air:~ root# docker rmi 6b362a9f73eb
    Error response from daemon: conflict: unable to delete 6b362a9f73eb (must be forced) - image is being used by stopped container 739f815bac79
    prems-MacBook-Air:~ root# docker ps -a -q
    65311eaf3159
    382b94296121
    8471d3559d61
    8e961e71c57a
    da178c27d7b6
    d553589fa9e5
    564c20929831
    3261b8bcb15f
    600de7285659
    739f815bac79
    ee05cfbe3549
    8f67ef314e22
    86c45fd76ac4
    076451e8b9ff
    2ed1b189de67
    prems-MacBook-Air:~ root# docker rm `docker ps -a -q`
    65311eaf3159
    382b94296121
    8471d3559d61
    8e961e71c57a
    da178c27d7b6
    d553589fa9e5
    564c20929831
    3261b8bcb15f
    600de7285659
    739f815bac79
    ee05cfbe3549
    8f67ef314e22
    86c45fd76ac4
    076451e8b9ff
    2ed1b189de67
    prems-MacBook-Air:~ root# docker rmi 6b362a9f73eb
    Untagged: docker/whalesay:latest
    Untagged: docker/whalesay@sha256:178598e51a26abbc958b8a2e48825c90bc22e641de3d31e18aaf55f3258ba
    Deleted: sha256:6b362a9f73eb8c33b48c95f4fcce1b6637fc25646728cf7fb0679b2da273c3f4
    Deleted: sha256:34dd66b3cb4467517d0c5c7dbe320b84539fbb58bc21702d2f749a5c932b3a38
    Deleted: sha256:52f57e48814ed1bb08a651ef7f91f191db3680212a96b7f318bff0904fed2e65
    Deleted: sha256:72915b616c0db6345e52a2c536de38e29208d945889eecef01d0fef0ed207ce8
    Deleted: sha256:4ee0c1e90444c9b56880381aff6455f149c92c9a29c3774919632ded4f728d6b
    Deleted: sha256:86ac1c0970bf5ea1bf482edb0ba83dbc88fefb1ac431d3020f134691d749d9a6
    Deleted: sha256:5c4ac45a28f91f851b66af332a452cba25bd74a811f7e3884ed8723570ad6bc8
    Deleted: sha256:088f9eb16f16713e449903f7edb4016084de8234d73a45b1882cf29b1f753a5a
    Deleted: sha256:799115b9fdd1511e8af8a8a3c8b450d81aa842bbf3c9f88e9126d264b232c598
    Deleted: sha256:3549adbf614379d5c33ef0c5c6486a0d3f577ba3341f573be91b4ba1d8c60ce4
    Deleted: sha256:1154ba695078d29ea6c4e1adb55c463959cd77509adf09710e2315827d66271a

    prems-MacBook-Air:~ root# docker ps -a 
    CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS               NAMES
    prems-MacBook-Air:~ root#
    
    
    Remove Image : docker rmi ID
    Remove container : docker rm ID
    To list all the containes : docker `ps -a -q`
    Remove all the containers : docker rm `docker ps -a -q`
    
    
    
    
    
