# ELKstackproject
Project 1

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
| Web1     	| Web Server 	| 10.0.0.6   	| Linux            	|
| Web2     	| Web Server 	| 10.0.0.7   	| Linux            	|
| Web3     	| Web Server 	| 10.0.0.4   	| Linux            	|
| ELK      	| ELK Server 	| 10.1.0.4   	| Linux            	|

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:

Add whitelisted IP addresses:

My Local Machine's Public IP Address

Machines within the network can only be accessed by SSH (Port 22) and HTTP (Port 80).

Which machine did you allow to access your ELK VM? Jump Box machine

What was its IP address? 10.0.0.5

A summary of the access policies in place can be found in the table below.

| Name     	| Publicly Accessible? (Y/N)              	| Allowed IP Addresses                 	|
|----------	|-----------------------------------------	|--------------------------------------	|
| Jump Box 	| Y (SSH Port:22)                         	| My Local Machine's Public IP Address 	|
| Web1     	| N                                       	| 20.80.179.66                         	|
| Web2     	| N                                       	| 20.80.179.66                         	|
| Web3     	| N                                       	| 20.80.179.66                         	|
| ELK      	| Y (Kibana Port:5601 and HTTP Port:9200) 	| 10.1.0.4                             	|

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
Ansible models your IT infrastructure by describing how all of your systems inter-relate, rather than just managing one system at a time. 

The playbook implements the following tasks:
- _TODO: In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
- ...
- ...

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![TODO: Update the path with the name of your screenshot of docker ps output](Images/docker_ps_output.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:

Web1 (10.0.0.6)
Web2 (10.0.0.7)
Web3 (10.0.0.4)

We have installed the following Beats on these machines:

Filebeat and Metricbeat

These Beats allow us to collect the following information from each machine:
- _TODO: In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc._

Filebeat: log events,  
Metricbeat: system metrics and statistics, 

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the install-elk.yml file to _____.
- Update the hosts file to include...
- Run the playbook, and navigate to ____ to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?_
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_
- _Which URL do you navigate to in order to check that the ELK server is running?

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
