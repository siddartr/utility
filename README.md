Distributed Load Testing

Using Jmeter


Input params:
vm ip String[] - vms where the containers will be run.
jmx file path - jmx file to run
username - username to ssh into the vms
password - pwd to ssh into the vms
number of slaves - this would be the number of jmeter server containers that will be spawned across the swarm
compose file will already be present as part of the service. Will be copied over to the leader vm

Usage:

$ python main_scripts --vmIPList 10.127.72.8,10.127.72.9 --jmxfile SimpleTest.jmx --slavecount 20 --username 'root' --password 'ca$hc0w'



0. create docker swarm

1. (on slave) join docker swarm

2. create overlay network for docker swarm

3. create jmeter service on the swarm

4. scale up the jmeter slave

5. get ip addresses of all the containers in the swarm

6. trigger jmeter.
