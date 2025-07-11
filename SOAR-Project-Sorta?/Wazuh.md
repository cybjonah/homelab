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

Ok so now my machine is up and running and setup im going to begin running some commands to being installing wazuh, fyi I am following the quick start documentation I linked above

<img width="793" height="702" alt="image" src="https://github.com/user-attachments/assets/37fb2715-7f9e-43e3-b875-d576353349b5" />

First step is to upgrade the packages
<pre>sudo apt update && apt upgrade -y</pre>

Once that is complete im going to cd to the /opt directory and make a directory called Wazuh;

<pre>cd /opt</pre>
<pre>mkdir wazuh</pre>
<pre>cd wazuh</pre>

After I've done those I am going to be curling the quick install package from Wazuh by running;
<pre>curl -sO https://packages.wazuh.com/4.12/wazuh-install.sh && sudo bash ./wazuh-install.sh -a</pre>

<img width="947" height="730" alt="image" src="https://github.com/user-attachments/assets/33a5cf93-92b1-4c60-a126-a7d4aad62310" />

