# BlueWhale
Docker DCA Cram Notes 

*Storage Drivers

Pluggable framework for managing the temporary internal storage of a containers writable layer. 

	* overlay2 File-based storage. Default for Ubuntu and Centos8+
	* devicemapper Block storage, more efficient for doing lots of writes. Default for Centos7 and earlier. 


*Find out which storage driver is configured with docker info. 
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
