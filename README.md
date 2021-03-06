# Docker-Container-Exposer

Expose docker containers to public network

#### Network Topology
![](https://i.imgur.com/Uw9Imix.png)

#### Usage
1. Modify `.env` file to fit on your network topology
```bash
#!/bin/bash

# Docker image to use to start containers
IMAGE=centos
# Number of containers
CONTAINERS=4
# Container name prefix (eg: iot_0, iot_1, ..., iot_N)
CONTAINER_NAME_PREFIX=iot

# Interface name of physical interface to connect to the public network
PUBLIC_IFNAME=eth0
# Virtual Network Bridge interface name
BRIDGE_IFNAME=br0
# Public network id
NETWORK_ID=192.168.1
# Public IP address of the previous interface (eg: 192.168.1.5)
BRIDGE_IP=192.168.1.22
# Public network gateway (eg: 192.168.1.1)
GATEWAY_IP=192.168.1.1
# Mask for public network
CIDR=24
# Container IP range (eg: containers ip will be: 192.168.1.100-103)
CONTAINER_IP_START=100
```

2. run `./up` to launch new docker container instance and bridge them into real network
3. run `./down` to revert the changes
4. run `./test` to test the network connection to docker containers/public network/real network/gateway etc.
