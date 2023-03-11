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
