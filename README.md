# lsst-stack-docker
Tools to run LSST stack inside Docker containers

## Pre-requisites

* Install Docker latest release: https://docs.docker.com/engine/installation
* Add your user to Docker group:
```bash
 sudo usermod -aG docker <user_name>
```

## Launch LSST stack container

Select a version tag here:
https://hub.docker.com/r/lsstsqre/centos/tags/


```bash
docker run -ti -v -v <home_directory>/src:/home/vagrant/src lsstsqre/centos:7-stack-lsst_distrib-w_2016_20
# In the container, load LSST stack environment
. /opt/lsst/software/stack/loadLSST.bash
# Host machine volume is available here:
# your host user id must be equal to 1000 to have write access
ls /home/vagrant/src
```
