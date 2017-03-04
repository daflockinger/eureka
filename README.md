# Heureka - Simple Eureka Server for Docker

A simple eureka server with the possibility to have 2 peers running 
that are aware of each other (server failover). For the peers the hosts and
the ports can be specified. 

The docker image can be found on: https://hub.docker.com/r/daflockinger/heureka/

The docker can be started with either by creating it from the source: 
```sh
mvn clean package docker:build 
```
or by pulling the latest from the docker hub:
```sh
docker pull daflockinger/heureka
```
and started with: 
```sh
docker run -d daflockinger/heureka
```

For peers add this to the docker run command: 
```sh
 -Dspring.profiles.active=peer1
 -Dspring.profiles.active=peer2
 -Dspring.profiles.active=peer3
```

All 3 instances can be started with docker compose:
```sh
cd heureka/
docker-compose up
```

The peers hostname and port can be configured with adding these environment variables to the docker:

| Path             | Description  |
|------------------|--------------|
| PEER1_PORT | Port of the first peer (default is 8761) |
| PEER1_HOSTNAME | Hostname of the first peer (default is 'peer1') |
| PEER2_PORT | Port of the second peer (default is 8762) |
| PEER2_HOSTNAME | Hostname of the second peer (default is 'peer2') |
| PEER3_PORT | Port of the second peer (default is 8763) |
| PEER3_HOSTNAME | Hostname of the second peer (default is 'peer3') |
