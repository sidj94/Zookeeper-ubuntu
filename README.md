# Zookeeper cluster running in Docker containers

## Zookeeper Ubuntu image
This is a Zookeeper 3.4.14 image which uses Ubuntu as base image.\
This image is embedded with Java version 'openjdk-11' which is being used to run Zookeeper process.

File `docker-compose.yml`for a 3 node Zookeeper cluster:

```
version: '3.1'

services:
  zoo110:
    image: sidj94/zookeeper-ubuntu:3.4.14
    restart: always
    hostname: zoo110
    ports:
      - 2184:2183
    environment:
      MY_ID: 110
      LEADER_PORT: 2777
      FOLLOWER_PORT: 3777
      CLIENT_PORT: 2183
      ZOO_DATA_DIR: /zk-data
      ZOO_LOG_DIR: /zk-logs
      ENABLE_ZK_AUTH: "ENABLE"
      ZOO_SERVER_LIST_PORT: 110=zoo110 120=zoo120 130=zoo130

  zoo120:
    image: sidj94/zookeeper-ubuntu:3.4.14
    restart: always
    hostname: zoo120
    ports:
      - 2185:2183
    environment:
      MY_ID: 120
      LEADER_PORT: 2777
      FOLLOWER_PORT: 3777
      CLIENT_PORT: 2183
      ZOO_DATA_DIR: /zk-data
      ZOO_LOG_DIR: /zk-logs
      ENABLE_ZK_AUTH: "ENABLE"
      ZOO_SERVER_LIST_PORT: 110=zoo110 120=zoo120 130=zoo130

  zoo130:
    image: sidj94/zookeeper-ubuntu:3.4.14
    restart: always
    hostname: zoo130
    ports:
      - 2186:2183
    environment:
      MY_ID: 130
      LEADER_PORT: 2777
      FOLLOWER_PORT: 3777
      CLIENT_PORT: 2183
      ZOO_DATA_DIR: /zk-data
      ZOO_LOG_DIR: /zk-logs
      ENABLE_ZK_AUTH: "ENABLE"
      ZOO_SERVER_LIST_PORT: 110=zoo110 120=zoo120 130=zoo130
```

## Setting up a 3 node Zookeeper cluster using docker-compose 
### Step 1 :
Make a directory and create docker-compose.yaml file
### Step 2 :
Run docker-compose command so as to start 3 Zookeeper containers\
```$ docker-compose up```
