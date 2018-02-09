# Nginx-Reverse-Proxy-Rockons
Rock-ons are container definitions that run on the Rockstor network attached storage (NAS) appliance OS. These Rock-ons improve on the official set of Rock-ons by utilizing Docker DNS. With Docker DNS the hostnames of containers will resolve from the other containers. This will make application configuration easier and more resilient. You'll be able to setup database connections using the database container hostname, instead of just using its IP. The hostname will still resolve to the correct IP of the database when the IP of the database host changes. If you configured the database connection with just the IP then the applications would become crippled when the database host's IP changes.

As you may expect, these Rock-ons also setup the needed environment for the jwilder Nginx reverse proxy. A running jwilder Nginx reverse proxy on the Rockstor will then automatically configure a new virtual host in its proxy configuration when starting other Rock-ons that run a web service.

To utilize these Rock-ons, you'll need to have Rockstor running behind a gateway supporting NAT. Visit http://rockstor.com/ for more information about its features and documentation. The offical rockon documentation can be found at http://rockstor.com/docs/docker-based-rock-ons/overview.html

First, you'll need to setup a new docker network on the Rockstor appliance via the Linux terminal. This network can be created with the create_rockon_br0.sh command. These Rock-ons will then be able to take advantage of Docker DNS after the network has been created. 

Before you can use any of these Rock-ons, the cooresponding json from this repository will need to be installed in the /opt/rockstor/rockons-metastore/ directory, and you will not see the Rock-on until you click the update button in the rockon GUI to update the list of all Rock-ons. 

To be able to easily use your applications the Rock-ons install you'll need a domain with DNS. You can setup a local DNS or use host files for a local network or for a lab environment. There is a Rockon to configure dynamic dns for a domain. To use this Rockon you'll want to install the eo-ddclient.json client, run the Rock-on install, and configure the running ddclient service. 

If you want to avoid opening dozens of ports to manage your applications then you'll want a reverse proxy.  Install the eo-letsencrypt-nginx-proxy.json, eo-nginx-reverse-proxy.json, and eo-nginx-reverse-proxy-default-site.json and install the Rock-ons to use the jwilder Nginx reverse proxy. You'll need these running before you start any other Rock-ons you install.

As a last tip, click the name of the Rock-on in the Rockstor GUI to follow the link to the application Web page to get more details about the Rock-on installs.

So, start installing some Rock-ons, and work from your own cloud.
