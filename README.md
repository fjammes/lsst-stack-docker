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
# clone lsst repositories on your host machine
cd <home_directory>/src
git clone https://github.com/lsst/obs_cfht.git
# Open a shell inside a container containing LSST stack
docker run -it -v <home_directory>/src:/home/vagrant/src lsstsqre/centos:7-stack-lsst_distrib-w_2016_20
# In the container, load LSST stack environment
[vagrant@6ff7f9f2d54e src]$ . /opt/lsst/software/stack/loadLSST.bash
# Host machine volume is available here:
[vagrant@6ff7f9f2d54e src]$ ls /home/vagrant/src
# WARNING: your host user id must be equal to 1000 to have write access
[vagrant@6ff7f9f2d54e src]$ cd $HOME/src/obs_cfht 
[vagrant@6ff7f9f2d54e obs_cfht]$ setup -r .
[vagrant@6ff7f9f2d54e obs_cfht]$ scons
scons: Reading SConscript files ...
EUPS integration: enabled
Checking who built the CC compiler...error: no result
CC is gcc version 4.8.5
Checking for C++11 support
Checking whether the C++ compiler works... yes
C++11 supported with '-std=c++11'
Setting up environment to build package 'obs_cfht'.
scons: done reading SConscript files.
scons: Building targets ...
scons: Nothing to be done for `python'.
running tests/testButler.py... passed
running tests/testColorterms.py... passed
scons: done building targets.
```
