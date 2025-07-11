## Wazuh

In this file im going to be documenting my quick steps to deploying wazuh and "configuring" it for my experiment, 
at the end of the day I just need it deployed, and very minially setup with a working agent or 2 (my computers) so I can being testing with n8n automation.

So lets begin.

## Installation

So first step is im going to be deploying a VM, this VM is going to be a Ubuntu 24.04 LTS ISO, and im going to be using the pre requsites provided on their quick start guide
with a little change to the cores since my server only has 6 and I don't want to max it out.

https://documentation.wazuh.com/current/quickstart.html

<img width="537" height="277" alt="image" src="https://github.com/user-attachments/assets/d5864351-26e9-45c7-8591-2e528fac3668" />

Usally if I was deploying Wazuh I would configure a server per wazuh setup (manager, dashboard, indexer) but since im mainly doing this for experimentation purposes
im going to be doing the quick start which puts everything on the same server, this is bad on a actually production environment because if one piece goes down or the whole server
you wont have a SIEM anymore


<img width="736" height="557" alt="image" src="https://github.com/user-attachments/assets/cc2e8c15-3c83-4900-8272-d7ad89a3292d" />
