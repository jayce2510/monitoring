# monitoring

# grafana data volume
change permission for grafana folder so the it can read files in docker

# configure influxdb.conf file
connect to cli of influxdb in container

   docker exec -it influxdb /bin/bash

install nano and edit conf file
   
   sudo apt update
   sudo apt install nano
   sudo nano /etc/influxdb/influxdb.conf

add this one to the conf file
[[udp]]
   enabled = true
   bind-address = ":8089"
   database = "proxmox"
   batch-size = 5000
   batch-timeout = "1s"
   
restart the influxdb container  

Once configurations are done let's start it up. From the /prometheus project directory run the following command:

    $ HOSTNAME=$(hostname) docker stack deploy -c docker-stack.yml prom


That's it the `docker stack deploy' command deploys the entire Grafana and Prometheus stack automagically to the Docker Swarm. By default cAdvisor and node-exporter are set to Global deployment which means they will propogate to every docker host attached to the Swarm.

The Grafana Dashboard is now accessible via: `http://<Host IP Address>:3000` for example http://192.168.10.1:3000

	username - admin
	password - foobar (Password is stored in the `/grafana/config.monitoring` env file)

In order to check the status of the newly created stack:

    $ docker stack ps prom

View running services:

    $ docker service ls

View logs for a specific service
