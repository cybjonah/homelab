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

After the installation is done you sh ould see something like this

<img width="937" height="391" alt="image" src="https://github.com/user-attachments/assets/37f5aa16-a44e-4c35-8287-b1e538f69d1e" />

So lets go connect to the dashboard and login

<img width="942" height="934" alt="image" src="https://github.com/user-attachments/assets/da7b9645-daec-417c-bfce-7deddc89206b" />

So now we are logged in and connected to the dashboard; Wazuh has a very senstive would be the nice word for it, out the box set of rules, I already have 152 Low alerts and the machines been on for 2 minutes;
Hopefully down the road I can do a bit of detection engineering and setup a nice rule set;

<img width="1914" height="947" alt="image" src="https://github.com/user-attachments/assets/30c4c0fc-80bb-43a2-aa33-a06d9bc64105" />

So pretty much we are finished with our very basic and minial configuration of Wazuh, last thing I need to do to begin testing with automation is deploy a agent on my device (oh lord)

To do this go to the side bar on the left side and select Agent Management and Summary

<img width="1919" height="949" alt="image" src="https://github.com/user-attachments/assets/efa2da6f-c495-4fe7-9791-a43e995bd3c0" />

After select the OS it will be getting deployed to and run the command / file provided.

<img width="1008" height="150" alt="image" src="https://github.com/user-attachments/assets/4b534d47-b5e2-4866-a323-38de6620f81d" />
(Dont forget to run that start command or else your agent will not be on)

And now that we have deployed our agent I can go back to the summary tab and I should see my agent there

<img width="1914" height="582" alt="image" src="https://github.com/user-attachments/assets/6d6325ea-2ec3-47c2-92a8-dc4ed4dfc88a" />

And just to verify now when I go over to Wazuh and the discover tab I can see info coming in from my agent;

<img width="1484" height="499" alt="image" src="https://github.com/user-attachments/assets/78fa1e4c-e16c-4f8e-8c0b-59d7f6fae122" />

So let's move on to the N8N part.
[Link Text](SOAR-Project-Sorta?/N8N.md)
