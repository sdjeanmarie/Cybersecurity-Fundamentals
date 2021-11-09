# Cybersecurity-Fundamentals
Linux, Diagrams, and Ansible
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

<a href="https://drive.google.com/file/d/1pM2n5yP3j7d3UVtHTCKwpP0tOBvhQGH9/view?usp=sharing"> Virtual Machine for Elk Server </a>
 These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the ansible-playbook file may be used to install only certain pieces of it, such as Filebeat.

  - ansible-playbook install-elk.yml ansible-playbook filebeat-playbook.yml, ansible-playbook metribeat-playbook.yml

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use/Users/shani/Downloads/README 7/README.md
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting accessto the network.
- What aspect of security do load balancers protect? Load balancers protect security across websites protecting against DDos attacks 
What is the advantage of a jump box? The advantage of a jump box is that it can be used as an originated point to connect to when connecting to untrusted wifi's

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the data and system logs.
- What does Filebeat watch for? Filebeat monitors log files or locations that is specified, collects log events, forwarding them to Elasticsearch or Logstash for indexing  
-What does Metricbeat record? Metricbeat takes metrics and statistics that is collected and sends them to elsticsearch or logstash.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.4   | Linux            |
|Webserver1| SSH      | 10.0.0.5   | Linux            |
|Webserver2| SSH      | 10.0.0.6   | Linux            |
|Elk Server| SSH      | 10.1.0.5   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the virtual machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses: 
-10.0.0.6, 10.0.0.5, 10.0.0.7, 10.0.04

Machines within the network can only be accessed by SSH into the virtual machine. 
-Which machine did you allow to access your ELK VM? The Jump box 
What was its IP address? 20.185.219.221

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes/No              | 10.0.0.4 20.185.39.185
|Webserver1|                     | 10.0.0.5             |
|Webserver2|                     | 10.0.0.6             |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
-What is the main advantage of automating configuration with Ansible? Ansible automation helps with the IAC and it also gives easy to read automation languge 

The playbook implements the following tasks:
- _TODO: In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
- First you want to open up the container used to SSH into the server
- You will then start the container and attach it 
- Once you get your SSH key you will then use that to log into your machine from the Virtual machine 
- Once you are connected to the virtual machines you will then write the playbook for the Elk.yml file.
- Once the Elk playbook is created the ansible-playbook install-elk.yml will be ran to connect to the ELK server 

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

<a href="https://drive.google.com/file/d/1xLqxvBcU4XpuCrvG6dLz9ODcxaUq7Vaw/view?usp=sharing"> The docker ps output file </a>

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
-List the IP addresses of the machines you are monitoring 
- 10.1.0.5, 10.0.0.5, 10.0.0.4, 10.0.0.6

We have installed the following Beats on these machines:
-Specify which Beats you successfully installed. We installed filebeat and metricbeat 

These Beats allow us to collect the following information from each machine:
-In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc._
The filebeat collects audit logs, deprecation logs, server logs, and gc logs. Audit logs keeps track of security related events and typically used for diagnostic performance.
Metricbeat collects metric data such as CPU or memory or data related to services running on the server. 
### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the Filebeat-conf.yml file to files .
- Update the nano filebeat-playbook.yml and filebeat-config.yml file to include the IP adresses 
- Run the playbook, and navigate to Kibana to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? ansible-playbook Filebeat-playbook.yml Where do you copy it? The file was copied from elastic.co
- _Which file do you update to make Ansible run the playbook on a specific machine? You will update the nano filebeat-playbook.yml and the nano filebeat-config.yml How do I specify which machine to install the ELK server on versus which to install Filebeat on? You will install the Elk server on the Elk stack machine whereas the filebeat woud be install using the jumpbox machine 
- _Which URL do you navigate to in order to check that the ELK server is running? http://23.99.177.217:5601/app/kibana#/home/tutorial_directory/logging
_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._

