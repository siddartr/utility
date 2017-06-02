Distributed Load Testing
========================

Jmeter and Docker Swarm
------------------------

Input params:
1. vm ip String[] - vms where the containers will be run
2. jmx file path - jmx file to run
3. number of slaves - this would be the number of jmeter server containers that will be spawned across the swarm
4. username - username to ssh into the vms
5. password - pwd to ssh into the vms

compose file will already be present as part of the service. Will be copied over to the leader vm

python module requirements: paramiko, argparse

The vms must have docker, docker-compose installed already.

```
$ python main_scripts --help
usage: main_scripts [-h] [--vmIPList VMIPLIST] [--slavecount SLAVECOUNT]
                    [--jmxfile JMXFILE] [--username USERNAME]
                    [--password PASSWORD]

optional arguments:
  -h, --help            show this help message and exit
  --vmIPList VMIPLIST   comma separated ips of vms
  --slavecount SLAVECOUNT
                        set the number of slaves
  --jmxfile JMXFILE     jmx file path
  --username USERNAME   username to ssh into the vms
  --password PASSWORD   pwd to ssh into the vms 
  ```

### Sample Usage:

```
$ python main_scripts --vmIPList 10.127.72.8,10.127.72.9 --jmxfile SimpleTest.jmx --slavecount 20 --username 'root' --password 'ca$hc0w'
```

0. create docker swarm

1. (on slave) join docker swarm

2. create overlay network for docker swarm

3. create jmeter service on the swarm

4. scale up the jmeter slave

5. get ip addresses of all the containers in the swarm

6. trigger jmeter on leader.
