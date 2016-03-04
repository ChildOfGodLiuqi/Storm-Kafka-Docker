# Building a Development Environment for Storm and Kafka Using Docker Container

  All the documents which I referenced are listed as the following. You'd better to read these documents before taking action.

  1. [endocode: Building a stream processing pipeline with Kafka, Storm and Cassandra – Part 2: Using Docker Containers](https://endocode.com/blog/2015/04/22/building-a-stream-processing-pipeline-with-kafka-storm-and-cassandra-part-2-using-docker-containers/)
  2. [wurstmeister: storm-docker@Github](https://github.com/wurstmeister/storm-docker)
  3. [Docker: Compose file reference](https://docs.docker.com/compose/compose-file/)
  4. [Docker: Networking in Compose](https://docs.docker.com/compose/networking/)
  5. [Docker: Understand Docker container networks](https://docs.docker.com/engine/userguide/networking/dockernetworks/)

## DISCLAIMER

  The copyrights of the softwares and scripts and resources in this article should belongs to their original creators or owners.

## Objective

  1. Zookeeper 3.4.5
      - 3 nodes
  2. Storm 0.10.0
      - nimbus node * 1
      - supervisor node * 1
      - ui node * 1
  3. Kafka 0.8.2
      - broker node * 1

## Preparation
  
### Software

  All of the following are ***required***:

  1. Linux (64bit):
     - CentOS 7.x
     - Ubuntu Willy 15.10
     - Ubuntu Trusty 14.04 (LTS)
     - Ubuntu Precise 12.04 (LTS)
  2. Docker Engine 1.10
  3. Docker Compose 1.6.2

### Hardware

  All of the following are ***minimal*** requirements:

  1. CPU: 2+ cores
  2. Memory: 16+ GBs
  3. Disk: 10+ GBs

## Steps

  1. Install Docker Engine:

    - CentOS 7.x: <https://docs.docker.com/engine/installation/linux/centos/>
    - Ubuntu: <https://docs.docker.com/engine/installation/linux/ubuntulinux/>

  2. Install Docker Compose:

    - Plese refer to: <https://docs.docker.com/compose/install/>

  3. Build the Docker images using this repository


```bash
cd images

# 1. To build the ZooKeeper image
docker build -t endocode/zookeeper zookeeper_docker

# 2. To build the Kafka image
docker build -t endocode/kafka kafka_docker

# 3. To build the Storm images (nimbus, supervisor, ui)
cd storm_docker

./rebuild.sh

# 4. Check the images in your local repository:
docker images

REPOSITORY                      TAG                 IMAGE ID            CREATED             SIZE
wurstmeister/storm-nimbus       latest              75c46dac402d        10 hours ago        587.5 MB
wurstmeister/storm-ui           latest              7b44df375fb7        11 hours ago        587.5 MB
wurstmeister/storm-supervisor   latest              dfeaaad9f569        11 hours ago        587.5 MB
wurstmeister/storm              latest              41e53fb09520        11 hours ago        587.5 MB
endocode/kafka                  latest              f5dc1b95dd58        34 hours ago        401.3 MB
endocode/zookeeper              latest              561d0a0c1266        35 hours ago        382.1 MB
wurstmeister/base               latest              cbbef65f3317        16 months ago       412.1 MB
```

## How to Use

Before using these containers, you might want to edit <a href="docker-compose.yml">```docker-compose.yml```</a> for your needs.

Enter the following command to bring these containers UP:

```bash
docker-compose up

```

Enther the follwoing command to bring these containers DOWN:


```bash
docker-compose down
```

## Happy enjoying!

