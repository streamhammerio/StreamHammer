#Stream Hammer Auto Data Extractors (SHADEs)

Stream Hammer utilizes Docker to deploy its remote applications which automatically extract and transmit data in real-time.  In order to utilize these applications, you'll first need to install the Docker runtime.  More information about Docker can be found on the [Docker Project Page](https://www.docker.com/what-docker).  
  
A prerequisite for all StreamHammer Auto Data Extractors is the installation of the [Docker Engine](https://www.docker.com/products/docker-engine).  Installation instructions can be found on the Docker website for [MAC](http://www.docker.com/products/docker#/mac), [Windows](http://www.docker.com/products/docker#/windows), [Linux](http://www.docker.com/products/docker#/linux), [AWS](http://www.docker.com/products/docker#/AWS), [Azure](http://www.docker.com/products/docker#/azure) and [Windows Server](https://blog.docker.com/2016/09/dockerforws2016/).  Additionally, command line instructions can be found below for the environments that the StreamHammer Auto Data Extractors have been tested on.  
  
###Install Docker on CentOS 7 - Command Line How-To
```
sudo su
uname -r
curl -fsSL https://get.docker.com/ | sh
sudo service docker start
sudo docker run hello-world
sudo chkconfig docker on
```  
  
  
##StreamHammer Auto Data Extractors
###SHADE #1 - Unix File System Watcher
####Installation on CentOS 7
#####Create directory to write files for transmission
```
sudo mkdir /watchout
sudo mkdir /watchout/files
sudo chmod 777 /watchout
sudo chmod 777 /watchout/files
```
#####Download and Run the Stream Hammer Unix File Watcher, with Auto-Restart on Error
```
docker run -it --restart=on-failure:10 --name streamhammer-unix-fs-watcher -v /watchout/files:/watch/file streamhammer/unix-fs-watch:stable
```
#####Configure 
Stream Id: Get at [StreamHammer.io](https://app.streamhammer.io/).  
Cleanup: y  

#####Usage
Using any mechanism you choose, write files to the directory you created in step 1.  Those files will be automatically read, analyzed and transmitted to their destination configured in at https://app.streamhammer.io/

###SHADE #2 - Oracle Watcher
#####TBD
###SHADE #3 - MSSQL Watcher
#####TBD
###SHADE #4 - MYSQL Watcher
#####TBD
###SHADE #5 - PostgresSQL Watcher
#####TBD
###SHADE #6 - HDFS Watcher
#####TBD
###SHADE #7 - Event Hub Watcher
#####TBD

##Docker Commands to Use with StreamHammer Auto Data Extractors
######Docker manual restart
```
docker restart streamhammer-unix-fs-watcher
```
######To see output, attach to the running container
```
docker attach streamhammer-unix-fs-watcher
```
######To detatch from the running container
```
ctrl-p, ctrl-q
```
######To see running docker containers
```
docker ps -a
```
######To stop and remove the container
```
docker stop streamhammer-unix-fs-watcher
docker rm streamhammer-unix-fs-watcher
```
