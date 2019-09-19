# Docker Obsidian Scheduler 4.10.1
This repository contains the Dockerfile and automated configuration file to create an [Obsidian scheduler](http://obsidianscheduler.com/) standalone instance.

## Base Docker Image
[tomcat:jre8](https://github.com/docker-library/tomcat/blob/ed98c30c1cd42c53831f64dffa78a0abf7db8e9a/8-jre8/Dockerfile) from [DockerHub](https://hub.docker.com/_/tomcat/)

## Installation

Install Docker.

Download automated build from public DockerHub Registery:
>docker pull enmobile/obsidian

Alternatively, you can build an image directly from this repository:
>docker build -t="enmobile/obsidian" github.com/EnMobile/docker-obsidian

##Usage

>docker run -d -p 80:8080 enmobile/obsidian

Default user / password are "admin" / "changeme" (see the [Obsidian Scheduler wiki](http://obsidianscheduler.com/wiki/Main_Page) for more information)

##Customization

### Option 1 - docker run
>docker run -d -p 80:8080 -v \<path-to/location-to-persist/tasks-and-config\>:/mnt/db/obsidian enmobile/obsidian

where \<path-to/location-to-persist/tasks-and-config\> is an absolute path of a directory to store the H2 database that contains Obsidian task configuration and history

### Option 2 - docker-compose up
See the docker-compose.yaml file in this repository for a quick example.  Consider adding a volume: section!
```
    volumes:
        - db/obsidian:/mnt/db/obsidian
```

### After starting up

After few seconds, open http://\<host\>:\<port\> to see the Obsidian admin console and log in using "admin" / "changeme".
