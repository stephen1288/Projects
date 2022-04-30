## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below. 

[Network Diagram](https://github.com/stephen1288/Projects/blob/main/Diagrams/ELK.PNG)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the roles file may be used to install only certain pieces of it, such as Filebeat.

  - [Elk Deployment](https://github.com/stephen1288/Projects/blob/main/Ansible/install-elk.yml) 

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
- Load blanancers work to keep the flow of traffic distrubuted evenly across the servers while a jump box restricts access to the public internet.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the logs and system metrics.
- 


The configuration details of each machine may be found below.


|   Name   | Function   | IP Address | Operating System |
|:--------:|------------|------------|------------------|
| Jump-Box | Gateway    | 10.0.0.4   | Linux            |
| Web 1    | Webservers | 10.0.0.9   | Linux            |
| Web 2    | Webservers | 10.0.0.5   | Linux            |
| Elk      | Elk Server | 10.1.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump-Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- Localhost

Machines within the network can only be accessed by Jump-box at 20.92.161.24.


A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses        |
|----------|---------------------|-----------------------------|
| Jump-Box | Yes                 | Localhost                   |
| Web 1    | No                  | 10.0.0.1/10.0.0.5/10.1.0.4  |
| WEb 2    | No                  | 10.0.0.1/10.0.0.9/10.1.0.4  |
| Elk      | No                  | Localhost 10.0.0.5/10.0.0.9 |


### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because removes the chance for human errror.

The playbook implements the following tasks:
- Installs docker.io
- Install python3-pip
- Docker module
- increase virtual memory
- download and install the elk container 

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

[Docker_PS](https://github.com/stephen1288/Projects/blob/main/Ansible/Docker_PS.PNG)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- 10.0.0.5 web 1
  10.0.0.9 web 2

We have installed the following Beats on these machines: Web 1, Web 2
- Filebeat and Metricbeat

These Beats allow us to collect the following information from each machine:
- Filebeat watches and collects system log events such as sudo usage and new user creation. Metricbeat helps you monitor your servers by collecting metrics from the system and services running on the server, such as: Apache. Metricbeat is a lightweight agent that can be installed on target servers to periodically collect metric data from your target servers, this could be operating system metrics such as CPU or memory or data related to services running on the server. It can also be used to monitor other beats and ELK stack itself.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the yaml file to etc/ansible.
- Update the config file to include host IP addresses
- Run the playbook, and navigate to http://20.213.250.195:5601/app/kibana to check that the installation worked as expected.


