## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

[AWS Diagram](https://github.com/aramejan/sweetlime/blob/b086d36e96a54a18a02c82d913007641c74fa059/Diagram0211.PNG) 

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the playbook file may be used to install only certain pieces of it, such as Filebeat.

  - Enter the playbook file._
  - [Playbook](https://github.com/aramejan/sweetlime/blob/fb3f7c9866a8227ee0c4c10e1502362d3e7fc954/apache-playbook)
    

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the Dmn Vulnerable Web Application.

Load balancing ensures that the application will be highly functional, in addition to restricting high traffic to the network.
- What aspect of security do load balancers protect? What is the advantage of a jump box?_

Load Balancer to give access to the user from a single node that can be secured and monitored and distributes network or application traffic across the servers
Jumpbox is allow us to have a secure access and monitor the servers and single box.  

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the network and system logs.
- What does Filebeat watch for?
- Logs the file data and send them to ELK.
- What does Metricbeat record?
- It records metrics data and send them to the output that you specifics thrugh ELK Server.


The configuration details of each machine may be found below.
Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.1   | Amazon Linux     |
|webserver1| AWS vm1  | 10.0.0.233 | Amazon linux     |                  
|webserver2| AWS vm1  | 10.0.1.139 | Amazon linux     |                  
|ElK server|Analyisplt| 10.0.0.221 | Amazon linux     |                                 

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the jumpbox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
-  Add whitelisted IP addresses
-   54.202.182.165

Machines within the network can only be accessed by Jumpbox.
-  Which machine did you allow to access your ELK VM? What was its IP address?
- JumpBox
-  10.0.0.174

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | 54.202.182.165       |
| VM1-WS1  | NO                  |    10.0.0.174        |
| VM2-WS2  | NO                  |    10.0.0.174        |
| ELK      | NO                  |    10.0.0.174        |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
-  What is the main advantage of automating configuration with Ansible?
-  We can manage/automate the configuration with YAMl Playbooks
-  Setup the servers with open ssh 

The playbook implements the following tasks:
- In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
- Install docker.io
- Install docker by useing Phyton-pip 
- Increase the virtual memory size 
- Download and lunch Docker for ELK 
- Publish ports 5601,9200 and 5400 

[ELK-Setup](https://github.com/aramejan/sweetlime/blob/main/ELK-Setup)

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

[Update the path with the name of your screenshot of docker ps output](https://github.com/aramejan/sweetlime/blob/main/Capture211141.PNG)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
| Name          | IP address    | 
| ------------- |:-------------:| 
| Webserver1    | 10.0.1.139    |
| Webserver2    | 10.0.0.233    |  
 

We have installed the following Beats on these machines:

[filebeat](https://github.com/aramejan/sweetlime/blob/main/filebeat)

[metricbeat](https://github.com/aramejan/sweetlime/blob/main/metricbeat)

These Beats allow us to collect the following information from each machine:
Filebeat: check and monitor Webserver1 & webserver2 and collect the logs and forwarding them to ELK server 
Metricbeat: collect metric information like Cpu info running on the server 

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the filebeat configuration file to /etc/ansible/files/filebeat-config.yml
- Update the hots file on /etc/ansible/hosts file to include for elk server 10.0.0.174
- Run the playbook, and navigate to http://10.0.0.174/app/kibana to check that the installation worked as expected.

   Answer the following questions to fill in the blanks:_
- Which file is the playbook? Where do you copy it? filebeat-playbook.yml 
- Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on? /etc/ansible/hosts 
- Which URL do you navigate to in order to check that the ELK server is running?
- http://54.212.89.166:5601/app/kibana

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
