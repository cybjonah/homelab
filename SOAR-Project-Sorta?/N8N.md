## N8N

So the goal of this part is going to be to try and have alerts pushed from Wazuh into N8N for automation to process the alerts and validate them.

Orignally I was going to self host N8N but I do have time left on my cloud trail version and for some convinence of my time im just going to use that (also so my server doesn't explode)

So obivously log into your N8N instance and create your workflow, our first node is going to be a webhook trigger since that's how im going to get Wazuh to send the alerts to N8N

I found this github repo online; https://github.com/maikroservice/wazuh-integrations which has a N8N integreation that im going to try and see if I can install to get a idea of what data will be sent to 
N8N before I try and use the code blocks to cypher out important info.

So first step is we have to CD too, **/var/ossec/integrations**
Once we're in that directory we have to create 2 files, custom-n8n which is the wrapper and custom-n8n.py which is the integration python file which will send the alert JSON data to n8n.

You can find these files in the github link I provided above, once you create those files make sure you change the permissions of the file;

<pre>
chown root:wazuh /var/ossec/integrations/custom-n8n /var/ossec/integrations/custom-n8n.py
chmod 750 /var/ossec/integrations/custom-n8n /var/ossec/integrations/custom-n8n.py
</pre>

