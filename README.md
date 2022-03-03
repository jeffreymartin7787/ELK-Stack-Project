## Automated ELK Stack Deployment

This is a collection of Linux Scripts and Ansible Scripts from my CyberClass. Most of the scripts are used to configure cloud servers with differnt docker containers.

The final setup was 4 servers running vulnerable DVWA containers along with a jump box and a server running an ELK stack container.
Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![alt text][logo]

[logo]: https://github.com/jeffreymartin7787/ELK-Stack-Project/blob/main/diagrams/Elk%20Machine.png "ELK Machine"


These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the YAML file may be used to install only certain pieces of it, such as Filebeat.

   ELK-Playbook.yml

This document contains the following details:

    Description of the Topology
    Access Policies
    ELK Configuration
        Beats in Use
        Machines Being Monitored
    How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly effective, in addition to restricting Access to the network.
-Load balancers prevent unwanted or unauthorized traffic from reaching the application.

-Jump boxes add a layer of security to the web servers, preventing the jump boxes from being exposed to the public.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the configuration files_ and system files_.

  Filebeat watches for log files or log events
  Metricbeat records metrics from on going services on the server

The configuration details of each machine may be found below. Note: Use the Markdown Table Generator to add/remove values from the table.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Job-Provisioner | Gateway  | 10.1.0.4   | Linux            |
| Web-1   | Webserver         | 10.1.0.5           | Linux                 |
| Web-2    | Webserver         | 10.1.0.6           | Linux                  |
| Elk Machine    | Monitoring         | 10.2.0.4           | Linux                 |



### Access Policies

The machines on the internal network are not exposed to the public Internet.

Only the Job-Provisioner can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses: 23.240.222.177

Machines within the network can only be accessed by Job Provisioner: 23.240.222.177

A summary of the access policies in place can be found in the table below:
| Name            | Publicly Accessible | Allowed IP Addresses |
|-----------------|---------------------|----------------------|
| Job_provisioner | Yes                 | 10.0.0.1 10.0.0.2    |
| Web-1           | No                  | 23.240.222.177       |
| Web-2           | No                  | 23.240.222.177       |
| Elk Machine     | Yes (HTTP)          | 23.240.222.177       |        

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because it allows changes to be made within any of the VMs associated with it.

The playbook implements the following tasks:

    TODO: In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc.

   1. Install Docker.io
   2. Install python3-pip
   3. Install Docker Python Module
   4. Download and launch a Docker web container
   5. Download and launch a docker web container

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![TODO: Update the path with the name of your screenshot of docker ps output](Images/docker_ps_output.png)

### Target Machines & Beats

This ELK server is configured to monitor the following machines:

:10.1.0.4, 10.1.0.5 10.1.0.6 

We have installed the following Beats on these machines:

 :Filebeat and Metricbeat

These Beats allow us to collect the following information from each machine:


Filebeat monitors log files and log events. Examples would be Inputs and harvesters. 
Metric beat looks out for any information in the file system that have been manipulated.

### Using the Playbook

In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned:

SSH into the control node and follow the steps below:

    Copy the ansible configuration file to run playbooks.
    Update the ansible host file to include default user to run playbook 
    Run the playbook, and navigate to Job-Provisioner to check that the installation worked as expected.


    _Which file is the playbook? The Elk-Playbook.yml Where do you copy it?_filebeat-playbook.yml file to /etc/ansible/roles

    _Which file do you update to make Ansible run the playbook on a specific machine? Elk-playbook.yml file

How do I specify which machine to install the ELK server on versus which to install Filebeat on?_By using the IPs of the respective servers

    _Which URL do you navigate to in order to check that the ELK server is running? http://[ELK-VM-IP]:5601/app/kibana

_As a Bonus, provide the specific commands the user will need to run to download the playbook, update the files, etc.
-ansible-playbook elk-playbook.yml