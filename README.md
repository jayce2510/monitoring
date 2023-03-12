# MONITORING

# Grafana data volume
Change the permission to 775 for grafana folder so the it can read files in docker

# Configure influxdb.conf file
Connect to cli of influxdb in container

   ```
   docker exec -it influxdb /bin/bash
   ```

Install nano and edit conf file
   ```
   apt update
   apt install nano
   nano /etc/influxdb/influxdb.conf
   ```

Add this one to the conf file
```
[[udp]]
   enabled = true
   bind-address = ":8089"
   database = "proxmox"
   batch-size = 5000
   batch-timeout = "1s"
```   
Restart the influxdb container  

