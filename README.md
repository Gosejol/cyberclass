## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

`Azure-vNet.jpg` 

![](diagrams/Azure-vNet.jpg)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the YAML file may be used to install only certain pieces of it, such as Filebeat.

  - _[link to YAML files!](ansible)_

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting access to the network.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the log files and system metrics.

The configuration details of each machine may be found below.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.4   | Linux            |
| DVWA-VM1 | DVWA     | 10.0.0.9   | Linux            |
| DVWA-VM2 | DVWA     | 10.0.0.10  | Linux            |
| DVWA-VM3 | DVWA     | 10.0.0.7   | Linux            |
| ELK Server | ELK stack | 10.1.0.5  | Linux            | 

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresse:
- _Home-Office ipv4_

Machines within the network can only be accessed by a shell on an ansible container within the Jump Box.

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | home office ip    |  
| ELK server| No                |10.0.0.4 10.0.0.7 10.0.0.9 10.0.0.10 |
| DVWA-VM1 |  No                 | 10.0.0.4  10.1.0.5                   |
| DVWA-VM2 |  No                 | 10.0.0.4  10.1.0.5                   |
|DVWA-VM3  |  No                 | 10.0.0.4  10.1.0.5                   |  
### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- _Ansible ensures uniformity on all provisioned scripts, leading to susscesfull instalation of curated YAML files. Furthermore, ansible 
-provides ample oportunities for scalability, as it allows for a streamline deployment of applications to multiple servers at the same time.
redundancy.  _

The playbook implements the following tasks:
- _TODO: In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
- ...
- ...

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![](ansible/Images/DockerPS.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- _10.0.0.7_
- _10.0.0.9_
- _10.0.0.10_

We have installed the following Beats on these machines:
- _Filebeat_
- _Metricbeat_

These Beats allow us to collect the following information from each machine:
- _TODO: In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc._

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:

![](ansible/Images/ansiblenode.png)
- Copy the `ELk.yml` file to the `roles` directory in the ansible control node.
- Update the `hosts` file to include the internal ip adresses of the targeted virtual machines.
- Run the playbook, and navigate to http://[your.VM.IP]:5601/app/kibana to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?_
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_
- _Which URL do you navigate to in order to check that the ELK server is running?

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
_curl https://raw.githubusercontent.com/Gosejol/cyberclass/main/ansible/ELK/elk-playbook.yml?token=AQORTIXPSWR5GEUULMYLXUS77USYA > /etc/ansible/files/filebeat-config.yml




