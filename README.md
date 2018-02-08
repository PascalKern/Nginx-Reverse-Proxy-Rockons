# Nginx-Reverse-Proxy-Rockons
Rock-ons are container definitions that run on the Rockstor NAS. These Rock-ons improve on the official set of Rock-ons by utilizing Docker DNS. With Docker DNS the hostnames of containers will resolve from the other container. This will easy the configuration. You'll be able to setup database connections using the database container hostname, instead of just using its IP. The hostname will still resolve to the correct IP of the database when the IP of the database host changes. If you configured the database connection with just the IP then the applications would become crippled when the database host's IP changes.

As you may expect, these Rock-ons also setup the needed environment for the jwilder Nginx reverse proxy. A running jwilder Nginx reverse proxy Rock-on will then automatically configure a new virtual host in its proxy configuration when the Rock-on's application starts.

To utilize these Rock-ons, you'll need to have Rockstor running behind a gateway supporting NAT. Rockstor is a network attached storage (NAS) appliance OS. Visit http://rockstor.com/ for more information about its features and documentation. The offical rockon documentation can be found at http://rockstor.com/docs/docker-based-rock-ons/overview.html

First, you'll need to setup a new docker network. This can network can be created with the create_rockon_br0.sh command. After the network has been created, you'll be able to run the Rock-ons. 

These Rock-ons can be installed in the /opt/rockstor/rockons-metastore/ directory and click the update button in the rockon GUI to see them in the list of all Rock-ons. You'll then want to install the eo-ddclient.json client, run the rockon, and configure the running ddclient service, or you'll want to setup another DNS setup. Then install the eo-letsencrypt-nginx-proxy.json, eo-nginx-reverse-proxy.json, and eo-nginx-reverse-proxy-default-site.json and start the Rock-ons. You'll need these running before you start any other Rock-ons you install.

As a last tip, click the name of the Rock-on in the Rockstor GUI to follow the link to the application Web page to get more details about the Rock-on installs.

So, start installing some Rock-ons, and work from your own cloud.
