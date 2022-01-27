# ELKstackproject

## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![ELK Network Diagram](/Diagrams/ELKProject.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the Ansible file may be used to install only certain pieces of it, such as Filebeat.

/etc/ansible/install-elk.yml

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build

### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting traffic to the network.

What aspect of security do load balancers protect?

Load balancing protects the Availability aspect in the CIA Triad model-- it improves the performance and availability of applications, websites, databases, and other computing resources within a network. A load balancer can also detect and drop distributed denial-of-service (DDoS) traffic before it enters the network by redirecting attack traffic. It can further protect against unauthorized access by requesting a username and password before allowing access into the network. 

What is the advantage of a jump box?

The advantage of a jump box is to allow access to a user from a single node that can be secured/hardened and monitored. It usually resides in a DMZ (demilitarized zone) or another network that can be accessed via the Internet.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the logs and system traffic.

What does Filebeat watch for?

Filebeat monitors log files or locations that you specify, collects log events, and forwards them either to Elasticsearch or Logstash for indexing.

What does Metricbeat record?

Metricbeat takes the metrics and statistics that it collects and ships them to the output that is specified, such as Elasticsearch or Logstash.

The configuration details of each machine may be found below:

| Name     	| Function   	| IP Address 	| Operating System 	|
|----------	|------------	|------------	|------------------	|
| Jump Box 	| Gateway    	| 10.0.0.5   	| Linux            	|
| Web-1     | Web Server 	| 10.0.0.6   	| Linux            	|
| Web-2     | Web Server 	| 10.0.0.7   	| Linux            	|
| Web-3     | Web Server 	| 10.0.0.4   	| Linux            	|
| ELK      	| ELK Server 	| 10.1.0.4   	| Linux            	|

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the jump box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:

Add whitelisted IP addresses:

My Local Machine's Public IP Address...

Machines within the network can only be accessed by SSH (Port 22) and HTTP (Port 80).

Which machine did you allow to access your ELK VM? Jump box machine

What was its IP address? 10.0.0.5

A summary of the access policies in place can be found in the table below.

| Name     	| Publicly Accessible? (Y/N)              	| Allowed IP Addresses                 	|
|----------	|-----------------------------------------	|--------------------------------------	|
| Jump Box 	| Y (SSH Port:22)                         	| My Local Machine's Public IP Address 	|
| Web-1    	| N                                       	| 20.80.179.66                         	|
| Web-2    	| N                                       	| 20.80.179.66                         	|
| Web-3    	| N                                       	| 20.80.179.66                         	|
| ELK      	| Y (Kibana Port:5601 and HTTP Port:9200) 	| 10.1.0.4                             	|

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because it minimizes the potential for error and increases the potential to save time. Roles were used to increase utility and functionality. The setup includes the initial alpha.yml file that references each playbook's install files titled alpha.yml. This main file saves time and effort because it can dictate which playbooks are in use; streamlining any future edits of the machines.

The playbook implements the following tasks:
- Configures the target VM (the machine being configured) to use more memory
  command: sysctl -w vm.max_map_count=262144 
- Installs docker.io 
- Installs python3-pip 
- Installs the docker module using pip 
- Downloads and launches the sebp/elk container over ports 5601, 9200, and 5044
- Enable docker service


The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![ELK Installation](/Diagrams/install-elk yml.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:

Web-1 | 10.0.0.6
Web-2 | 10.0.0.7
Web-3 | 10.0.0.4

We have installed the following Beats on these machines:

Filebeat and Metricbeat

These Beats allow us to collect the following information from each machine:

Filebeat collects and ships log files, such as Apache web server logs. 
Metricbeat collects and reports system-level metrics for various systems and platforms, such as uptime.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the playbook/configuration (.yml) file to the ansible directory.
- Update the hosts file to include the IP addresses of the web servers and ELK server.
- Run the playbook, and navigate to Kibana to check that the installation worked as expected.

Which file is the playbook? 

filebeat-playbook.yml and metricbeat-playbook.yml

Where do you copy it?

/etc/ansible/files/

Which file do you update to make Ansible run the playbook on a specific machine? 

The configuration file, such as: filebeat-config.yml and metricbeat-config.yml

How do I specify which machine to install the ELK server on versus which to install Filebeat on?

Update the /etc/ansible/hosts file to include the IPs of the ELK server and the webservers.

Which URL do you navigate to in order to check that the ELK server is running?

http://<ELK.VM.External.IP>:5601/app/kibana



