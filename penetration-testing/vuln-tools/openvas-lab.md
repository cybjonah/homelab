# OpenVAS - 7/10/2025

Hello, today I'm going to be installing OpenVAS a open sourced vulnerabilitly scanner on my homelab network. 

**This document will cover:**
  - Installation steps of the OS/Software
  - Inital configuration
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

*So like I mentioned before I will be following the installation guide for Kali Linux off the Greenbone community installation guide, and as promised it will be linked along side all the other resources I used below.*

After upgrading and updating our packages we can begin with the install, the first command we need to run is the install for the Greenbone community eddition

<pre>sudo apt install gvm -y</pre>

<img width="700" height="555" alt="image" src="https://github.com/user-attachments/assets/e4eae908-c68e-4cbe-9517-9171684d03de" />

After wards we must install OpenVAS its self

<pre>sudo apt install openvas -y</pre>

So I will be using the quicker option by doing the automatic configuration script, you can run this by;

<pre>sudo gvm-setup</pre>

<img width="697" height="549" alt="image" src="https://github.com/user-attachments/assets/0fcdc375-410d-438d-b176-90e4b3d4d834" />

So now the setup has been complete and the terminal has spat out the password for the admin user, remeneber to take note of this else we won't be able to long in. it also tells us we can verify our installation by running the command <pre>gvm-check-setup</pre> to make sure everything is configured correctly.

<img width="724" height="562" alt="image" src="https://github.com/user-attachments/assets/ceb8587e-b6cb-4138-89eb-a4a1fc7707e8" />

So I ran the command to verify and the step 4 returned a error that the download SCAP data did not complete / work.
Im going to solve this by running the fix it provided <pre>greenbone-feed-sync</pre>

<img width="678" height="544" alt="image" src="https://github.com/user-attachments/assets/42f47667-ce68-48f2-a618-7b10b78c8aaa" />

So after the check as said our instllation is OK we can proceed.

Now since our installation is complete we have to start the service / application by running

<pre>gvm-start</pre>

Thats it for the installation time to connect to the web page.

## Sources

- [Kali Linux Official Docs](https://www.kali.org/docs/)
- [OpenVAS Installation Guide](https://greenbone.github.io/docs/latest/22.4/kali/index.html)
