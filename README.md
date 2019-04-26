# azure-swarm
Scripts to deploy a working swarm cluster within 5 minutes in Azure with configured Swarm and Rex-ray storage

## What do you need before creating a cluster

- installed AZ CLI https://docs.microsoft.com/en-us/cli/azure/install-azure-cli?view=azure-cli-latest
- logged in AZ CLI (az login)


## Patch a script for you

you can change vm instance sizes, number of master/workers, vm os disk size, etc

## Run it

After you have AZ CLI installed and logged in, run a script and specify your deployment name

```$ ./create-cluster-only-ssd swarm-ssd```

It take about 5 mins to deploy and configure. You will get all the output in STDOUT and in a file ```swarm-ssd.log``` where are all the IPs, keys, etc. Save it for later use.

## Example of logs

```
2019.04.25 15:32:25: HELLO
2019.04.25 15:32:28: CREATED Resource Group swarm-ssd in westeurope
2019.04.25 15:32:50: CREATED Storage Account swarmssddiskssd with key XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
2019.04.25 15:32:51: CREATED Container disks for swarmssddiskssd Storage Account
2019.04.25 15:33:13: CREATED Storage Account swarmssddatassd with key XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
2019.04.25 15:33:14: CREATED Container volumes for swarmssddatassd Storage Account
2019.04.25 15:33:30: CREATED VNET swarm-ssd-vnet
2019.04.25 15:34:24: CREATED Network Security Group swarm-ssd-master-nsg with open ports: 22,80,443
2019.04.25 15:34:53: CREATED Network Security Group swarm-ssd-worker-nsg with open ports: 22
2019.04.25 15:35:07: CREATED Static IP swarm-ssd-master-1-ip XXX.XXX.XXX.XXX for swarm-ssd-master-1
2019.04.25 15:35:40: CREATED NIC swarm-ssd-master-1-nic for swarm-ssd-master-1 with NSG swarm-ssd-master-nsg
2019.04.25 15:35:45: CREATED VM swarm-ssd-master-1 with disk OS swarmssddiskssd/disks/swarm-ssd-master-1-os-disk 80gb with user swarm. => ssh swarm@XXX.XXX.XXX.XXX
2019.04.25 15:35:57: CREATED Static IP swarm-ssd-master-2-ip XXX.XXX.XXX.XXX for swarm-ssd-master-2
2019.04.25 15:36:30: CREATED NIC swarm-ssd-master-2-nic for swarm-ssd-master-2 with NSG swarm-ssd-master-nsg
2019.04.25 15:36:34: CREATED VM swarm-ssd-master-2 with disk OS swarmssddiskssd/disks/swarm-ssd-master-2-os-disk 80gb with user swarm. => ssh swarm@XXX.XXX.XXX.XXX
2019.04.25 15:36:44: CREATED Static IP swarm-ssd-master-3-ip XXX.XXX.XXX.XXX for swarm-ssd-master-3
2019.04.25 15:37:17: CREATED NIC swarm-ssd-master-3-nic for swarm-ssd-master-3 with NSG swarm-ssd-master-nsg
2019.04.25 15:37:21: CREATED VM swarm-ssd-master-3 with disk OS swarmssddiskssd/disks/swarm-ssd-master-3-os-disk 80gb with user swarm. => ssh swarm@XXX.XXX.XXX.XXX
2019.04.25 15:37:31: CREATED Static IP swarm-ssd-worker-1-ip XXX.XXX.XXX.XXX for swarm-ssd-worker-1
2019.04.25 15:38:04: CREATED NIC swarm-ssd-worker-1-nic for swarm-ssd-worker-1 with NSG swarm-ssd-worker-nsg
2019.04.25 15:38:08: CREATED VM swarm-ssd-worker-1 with disk OS swarmssddiskssd/disks/swarm-ssd-worker-1-os-disk 80gb with user swarm. => ssh swarm@XXX.XXX.XXX.XXX
2019.04.25 15:38:18: CREATED Static IP swarm-ssd-worker-2-ip XXX.XXX.XXX.XXX for swarm-ssd-worker-2
2019.04.25 15:38:51: CREATED NIC swarm-ssd-worker-2-nic for swarm-ssd-worker-2 with NSG swarm-ssd-worker-nsg
2019.04.25 15:38:55: CREATED VM swarm-ssd-worker-2 with disk OS swarmssddiskssd/disks/swarm-ssd-worker-2-os-disk 80gb with user swarm. => ssh swarm@XXX.XXX.XXX.XXX
2019.04.25 15:38:58: CREATED RBAC appId: XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX secret: XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX tenantId: XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
2019.04.25 15:40:07: GRANTED RBAC Permissions appId: XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX secret: XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX tenantId: XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
2019.04.25 15:40:07: SETTING UP ALL NODES
2019.04.25 15:40:07: Waiting swarm-ssd-master-1 IP:XXX.XXX.XXX.XXX to become alive
2019.04.25 15:40:10: Connected to swarm-ssd-master-1 IP:XXX.XXX.XXX.XXX as swarm
2019.04.25 15:40:47: Installed docker to swarm-ssd-master-1
2019.04.25 15:40:52: Installed lsscsi to swarm-ssd-master-1
2019.04.25 15:40:54: swarm-ssd-master-1 Initialized SWARM
2019.04.25 15:40:57: Written JOIN TOKENS
2019.04.25 15:40:57: Waiting swarm-ssd-master-2 IP:XXX.XXX.XXX.XXX to become alive
2019.04.25 15:40:59: Connected to swarm-ssd-master-2 IP:XXX.XXX.XXX.XXX as swarm
2019.04.25 15:41:33: Installed docker to swarm-ssd-master-2
2019.04.25 15:41:38: Installed lsscsi to swarm-ssd-master-2
2019.04.25 15:41:40: swarm-ssd-master-2 Joined SWARM as MASTER
2019.04.25 15:41:40: Waiting swarm-ssd-master-3 IP:XXX.XXX.XXX.XXX to become alive
2019.04.25 15:41:42: Connected to swarm-ssd-master-3 IP:XXX.XXX.XXX.XXX as swarm
2019.04.25 15:42:17: Installed docker to swarm-ssd-master-3
2019.04.25 15:42:22: Installed lsscsi to swarm-ssd-master-3
2019.04.25 15:42:25: swarm-ssd-master-3 Joined SWARM as MASTER
2019.04.25 15:42:25: Waiting swarm-ssd-worker-1 IP:XXX.XXX.XXX.XXX to become alive
2019.04.25 15:42:27: Connected to swarm-ssd-worker-1 IP:XXX.XXX.XXX.XXX as swarm
2019.04.25 15:42:59: Installed docker to swarm-ssd-worker-1
2019.04.25 15:43:03: Installed lsscsi to swarm-ssd-worker-1
2019.04.25 15:43:05: swarm-ssd-worker-1 Joined SWARM as WORKER
2019.04.25 15:43:05: Waiting swarm-ssd-worker-2 IP:XXX.XXX.XXX.XXX to become alive
2019.04.25 15:43:07: Connected to swarm-ssd-worker-2 IP:XXX.XXX.XXX.XXX as swarm
2019.04.25 15:43:45: Installed docker to swarm-ssd-worker-2
2019.04.25 15:43:51: Installed lsscsi to swarm-ssd-worker-2
2019.04.25 15:43:53: swarm-ssd-worker-2 Joined SWARM as WORKER
2019.04.25 15:43:56: INSTALLED REX-RAY plugins for ssd
2019.04.25 15:43:56: ALL WORK DONE!
2019.04.25 15:43:56: HOSTS:
2019.04.25 15:43:56: MASTERS:
2019.04.25 15:43:56: XXX.XXX.XXX.XXX
2019.04.25 15:43:56: XXX.XXX.XXX.XXX
2019.04.25 15:43:56: XXX.XXX.XXX.XXX
2019.04.25 15:43:56: WORKERS:
2019.04.25 15:43:56: XXX.XXX.XXX.XXX
2019.04.25 15:43:56: XXX.XXX.XXX.XXX
2019.04.25 15:43:56: connect to docker via:
2019.04.25 15:43:56: export DOCKER_HOST=ssh://swarm@XXX.XXX.XXX.XXX
2019.04.25 15:43:56: export DOCKER_HOST=ssh://swarm@XXX.XXX.XXX.XXX
2019.04.25 15:43:56: export DOCKER_HOST=ssh://swarm@XXX.XXX.XXX.XXX
2019.04.25 15:43:56: disconnect from docker via:
2019.04.25 15:43:56: unset DOCKER_HOST
2019.04.25 15:43:56: BYE BYE!

```

