## N8N

So the goal of this part is going to be to try and have alerts pushed from Wazuh into N8N for automation to process the alerts and validate them.

Orignally I was going to self host N8N but I do have time left on my cloud trail version and for some convinence of my time im just going to use that (also so my server doesn't explode)

So obivously log into your N8N instance and create your workflow, our first node is going to be a webhook trigger since that's how im going to get Wazuh to send the alerts to N8N

I found this github repo online; https://github.com/maikroservice/wazuh-integrations which has a N8N integreation that im going to try and see if I can install to get a idea of what data will be sent to 
N8N before I try and use the code blocks to cypher out important info.

<img width="925" height="167" alt="image" src="https://github.com/user-attachments/assets/a835acdc-5673-4f4f-869d-8db130ebd101" />

<img width="654" height="138" alt="image" src="https://github.com/user-attachments/assets/8d87b02d-a0c9-4904-be71-7de6635ef482" />

<img width="1357" height="207" alt="image" src="https://github.com/user-attachments/assets/204f37f4-c6a3-4b3a-927c-c0b464b4e67d" />

<img width="983" height="516" alt="image" src="https://github.com/user-attachments/assets/c1604978-6a5b-4ed1-8372-92b275079bea" />

<img width="984" height="572" alt="image" src="https://github.com/user-attachments/assets/efe3f437-a222-4c80-b785-14d92b26a646" />

