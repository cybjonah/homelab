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

After you created and added the required permissions now you have to nano into the configuration file;

<pre>nano /var/ossec/etc/ossec.conf</pre>

Once you are in there go down in the file and add this integration;

<pre> ```xml <integration> <name>custom-n8n</name> <hook_url>https://your-n8n-instance/webhook/your-webhook-id</hook_url> <alert_format>json</alert_format> </integration> ``` </pre>


Make sure you save the file and back out, once you have the correct permissions on the 2 n8n files, and added the integration you should be done, restart the manager and go to your N8N and start seeing if events are flowing in.

And boom!

<img width="1360" height="621" alt="image" src="https://github.com/user-attachments/assets/53f72a96-4c2b-44ec-932f-8046bc5ef162" />

We can see in this log it the wazuh server started and there are a bit more logs flowing in;

<img width="1128" height="576" alt="image" src="https://github.com/user-attachments/assets/ec5065b7-f99d-4d60-a4ca-b7bc600be1ca" />

so now are have to fine tune this a bit because we obviously don't want every alert flying in here, as well as Tune the wazuh alerts to make sure we aren't spamming wazuh/n8n, and last part create templates that validate alerts.

Im going to also deploy OpenCTI since they have a OpenCTI node to try and ulitize threat intel for alert validation
