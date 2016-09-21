#Stream Hammer Auto Data Extractors

Stream Hammer utilizes Docker to deploy its remote applications which automatically extract and transmit data in real-time.  In order to utilize these applications, you'll first need to install the Docker runtime.  

###Install Docker on CentOS 7
```
sudo su
uname -r
curl -fsSL https://get.docker.com/ | sh
sudo service docker start
sudo docker run hello-world
sudo chkconfig docker on
```
##Unix File System Watcher
#####Create directory to write files for transmission
```
mkdir /tmp/watch4
```
#####Run the Stream Hammer Unix File Watcher, with Auto-Restart on Error
```
docker run -it --restart=on-failure:10 --name streamhammer-unix-fs-watcher -v /tmp/watch4:/tmp/watch streamhammer/unix-fs-watch:latest
```
#####Configure 
API: Get at [StreamHammer.io](https://app.streamhammer.io/).  
Location: Get at [StreamHammer.io](https://app.streamhammer.io/).  
Cleanup: y  

#####Usage
Write files to the directory you created in step 1.  Those files will be automatically read, analyzed and transmitted to their destination configured in at https://app.streamhammer.io/

###Docker Help
######Docker manual restart
    docker restart streamhammer-unix-fs-watcher
######To see output, attach to the running container
    docker attach streamhammer-unix-fs-watcher
######To detatch from the running container
    ctrl-p, ctrl-q
######To see running docker containers
    docker ps -a
######To stop and remove the container
```
docker stop streamhammer-unix-fs-watcher
docker rm streamhammer-unix-fs-watcher
```
