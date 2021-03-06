# Network

## Drivers
- bridge: 
- host: 

## Basic Manipulation
- list: `docker network list`
- inspect: `docker network inspect bridge`
- create: `docker network create Network_NAME`
- attach a container to a network: `docker container run --name vm1 -ti --net=Network_ID ubuntu:xenial`
- connect: `docker network connect Network_ID Container_ID`, one container can be connected to multiple docker networks 
- disconnect: `docker network disconnect Network_ID Container_ID`

## port exposition
- NAT port of container to a random port of host: `docker container run -d -P training/webapp python app.py`
- NAT port of container to port of host: `docker container run -d -p 8888:5000 training/webapp python app.py`

## TP
### Inter-VM Communication
- `docker network create test_net`
- `docker container run --name vm1 -ti -d --net=test_net ubuntu:xenial`
- `docker container run --name vm2 -ti --net=test_net ubuntu:xenial /bin/bash`
- in the container `vm2`: 
    - `apt update`
    - `apt install iputils-ping`
    - `ping vm1`

### Web Server
- `docker container run -ti --rm -p 8888:80 ubuntu:xenial`
- install and launch apache2 in the container
    - `apt update`
    - `apt install apache2 vim`
    - `vim /var/www/html/index.html`
- find your container IP:
    - `apache2ctl -D FOREGROUND`
- access the web page from host OS at IP:80 

