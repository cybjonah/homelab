# OpenVAS - 7/10/2025

Hello, today I'm going to be installing OpenVAS a open sourced vulnerabilitly scanner on my homelab network. 

**This document will cover:**
  - Installation steps of the OS/Software
  - Inital configuration
  - Scan setup/execution
  - Results & analysis
  - Any troubleshooting / Recommendations

## Inital Setup

First off I obviously need a machine to run this on, the machine of my choice is going to be *kail linux* version 2025.2.

<img width="574" height="355" alt="image" src="https://github.com/user-attachments/assets/9c525f99-7cfd-47b3-aedd-fbef70357e3b" />

These are the requirements for the VM, I'll be using the minimal recommendations for now, I found these on the Greenbone community documentation which will be linked at the end of this file.

So after logging into proxmox I clicked on create VM and setup my VM to be on my specified pre-configured network and configured the correct requirements to insure the software will function.

<img width="734" height="550" alt="image" src="https://github.com/user-attachments/assets/67e1d006-d24f-4816-9f00-a347a0d37d84" />

<img width="1918" height="916" alt="image" src="https://github.com/user-attachments/assets/596a7b8b-93b9-497c-b3b8-02ef1f5c5ffb" />

Now my machine has been configured and deployed and in the task below I can see the creation of the VM with the VM ID of **100** has been created successfully.

So for now I will be using the built in console in proxmox to access the machine and do the inital installation of the VM but afterwards I may switch over to putty to allow copy / pasting of commands and inputs.

<img width="653" height="565" alt="image" src="https://github.com/user-attachments/assets/9d42348a-360f-4173-b16e-cda8f9facf77" />

So the deployment is now done, the machine is now up and running and I will be onto the inital configuration

## Inital configuration

Firstly I will be opening a command prompt, I need to do this to obviously run the install commands for **OpenVAS** but I still also need to do some maintance items like updating the packeges etc.

First step, I will cd to the /opt directory,
<pre>cd /opt</pre>

After I need to update and upgrade my systems packages to ensure everythings up to date before doing the install
<pre>sudo apt update && apt upgrade -y</pre>

<img width="1720" height="1077" alt="image" src="https://github.com/user-attachments/assets/f6c00c63-3dfa-40a9-99f4-811c66e0f091" />
