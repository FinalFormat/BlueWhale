# BlueWhale
Docker DCA Cram Notes
----------------------

Storage Drivers
---------------

Pluggable framework for managing the temporary internal storage of a containers writable layer. 

	* overlay2 File-based storage. Default for Ubuntu and Centos8+
	* devicemapper Block storage, more efficient for doing lots of writes. Default for Centos7 and earlier. 


Find out which storage driver is configured with docker info. 
---------------------------------------------------
How to override the default storage driver.
Explicitly set your storage driver. Edit the below file in vim 

sudo vi /usr/lib/systemd/system/docker.service

ExecStart=/usr/bin/dockerd --storage-driver devicemapper

#Anytime we do a change to a unit file, we need to run the commands below. 

sudo systemctl daemon-reload

sudo systemctl restart docker

Recommended way to change the config file
sudo vi /etc/docker/daemon.json

{
  "storage-driver": "devicemapper"
  }

sudo systemctl restart docker

sudo systemctl status docker

Running A container
------------------------------
docker run nginx:1.15.11

If you run something like a webserver, then the command will not complete and the only way to get out of it is closing your terminal or ctrl+c

docker run busybox echo hello world 

How rename a docker container so it isn't so long 
2b56d2cf506432221a489506c2450a4de70293683bd3fd4f2db8d42bf269996a(Example of a docker ID)

docker run -d --name nginx --restart nginx


How to 

Docker Commands
----------------------------
docker ps List currently running containers 

docker container stop <container name>  

docker container start <container name> 

docker container rm <container name>

Docker Command Flags
-----------------------------
-d Run the container in detatched mode. The docker run command will immidiately exit the container will run in the back ground. 

--name Give your docker container a name different than the default random name. 

--restart Specify when the container should be automatically restarted. Options: no, on-failure, always, and unless-stopped. 

-p <host port>:<container port>: Expose a containers port by mapping it to a port on the host. 
	
--rm Automatically removes the container when exits. (Cannot be used with --restart.)

--memory Sets a hard limit on memory usage 

--memory-reservation is a soft limit. will only be used if memory begins to run out. 






