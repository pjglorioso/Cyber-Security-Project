

## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![TODO: Update the path with the name of your diagram](Images/diagram_filename.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the _____ file may be used to install only certain pieces of it, such as Filebeat.

  - _TODO: Enter the playbook file._

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting inbound access to the network.
- The load balancer aids in security by offloading traffic from a corporate server to a public cloud provider. 
Integrating an ELK (Elasticsearch, Logstash, and Kibana) server allows users to easily monitor the vulnerable VMs for changes to the file names and watch system metrics.

Filebeat monitors the logs in the specified locations. It detects changes to the filesystem. It collects logs and forwards them to Elastisearch or Logstash for indexing

Metricbeat detects changes in system metrics such as CPU useage. We use it to detect SSH login attempts

The configuration details of each machine may be found below.


| Name      | Function  | IP Address | Operating System |
|---------- |---------- |------------|------------------|
| Jump Box  | Gateway   | 10.0.0.4   | Linux            |
| Web 1     | server    | 10.0.0.5   | Linux            |
| Web 2     | server    | 10.0.0.6   | Linux            |
| Web 3     | server    | 10.0.0.7   | Linux            |
| ELK Server| Monitoring| 10.1.0.4   | Linux            |             

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jumpbox Provisioner machine can accept connections from the Internet. Access to this machine is only allowed from the designated public IP address. This address changes each time the machine is powered down and restarted. 

Machines within the network can only be accessed by peer servers. The Jumpbox Provisioner connects via SSH to the Webservers (Web 1, Web 2 & Web 3) and the ELK Server. The Web Server machines send logs to the ELK Server to be forwarded for indexing.

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 |Public IP for session |
| Web 1    | No                  | 10.0.0.1-254         |
| Web 2    | No                  | 10.0.0.1-254         |
| Web 3    | No                  | 10.0.0.1-254         |
| ELK      | No                  | 10.0.0.1-254         |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- Using Ansible allowed me to quickly install, update, and add the web servers to the network using the same playbooks

The playbook implements the following tasks:
- Install docker on all network machines so they will be able to recieve and install containers
- Ansible is installed on the Jump Box VM to distribute containers to other VMs on the network
- Ansible playbooks are used to install the ELK stack container on the ELK server and a 'Beats' containers on the Web servers

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.
<screenshot>

![TODO: Update the path with the name of your screenshot of docker ps output](Images/docker_ps_output.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
Web-1 - 10.0.0.5
Web-2 - 10.0.0.6
Web-3 - 10.0.0.7

We have installed the following Beats on these machines:
Filebeat
metricbeat

These Beats allow us to collect the following information from each machine:
Filebeat - Filebeat detects changes to the filesystem. We are using this to monitor our Web Log data.
Metricbeat - Metricbeat detects changes in system metrics, such as CPU usage. We use it to detect SSH login attempts, failed sudo escalations, and CPU/RAM statistics.

The Ansible Playbooks used can be found here

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the _____ file to _____.
- Update the _____ file to include...
- Run the playbook, and navigate to ____ to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?_
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_
- _Which URL do you navigate to in order to check that the ELK server is running?

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._

https://du.bootcampcontent.com/denver-coding-bootcamp/du-den-cyber-pt-06-2020-u-c/blob/master/1%20-%20Lessons/Week13%20-%20Elk%20Stack%20Project/Activities/Stu_Day_3/Solved/Solution.md