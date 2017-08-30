
### Level 0 (optional) - Setup an Ubuntu VM

    Creation of a VM via Vagrant 
    
<a target="_blank" href="https://imageshack.com/i/pmh1MdTlp"><img src="http://imagizer.imageshack.us/v2/1024x768q90/922/h1MdTl.png" border="0"></a>


### Level 1 - Collecting the Data


--> Sign up for Datadog: OK

--> What is the Agent? The Datadog Agent is a service that collects data from applications, servers to ease the monitoring by making a link between the server or application and the Datadog platform. From this link it is possible to define alarms and generate reports.

--> Add tags in the Agent config file: OK

--> Screenshot of the  host and its tags on the Host Map page in Datadog:

<a target="_blank" href="https://imageshack.com/i/pmJmpI5Zp"><img src="http://imagizer.imageshack.us/v2/1024x768q90/922/JmpI5Z.png" border="0"></a>

--> Install a database on your machine: MySQL database installed

--> Install the respective Datadog integration for that database: OK

--> Write a custom Agent check that samples a random value. Call this new metric: test.support.random: OK

```python
from checks import AgentCheck
import random
class RandomCheck(AgentCheck):
	def check(self, instance):
		self.gauge('test.support.random',random.random())
```

### Level 2 - Visualizing the Data

--> Clone your database integration dashboard and add additional database metrics to it as well as your test.support.random metric from the custom Agent check: OK

--> Bonus question: What is the difference between a timeboard and a screenboard?
A timeboard is like common graphs with time as the X-axis and a parameter as the Y-axis whereas a screenboard is a parameter visualization made of images, text, value ranking that is more customizable.

--> Snapshot of the test.support.random graph 

<a target="_blank" href="https://imageshack.com/i/pnaif7UTp"><img src="http://imagizer.imageshack.us/v2/1024x768q90/923/aif7UT.png" border="0"></a>


### Level 3 - Alerting on the Data

--> Set up a monitor on this metric that alerts you when it goes above 0.90 at least once during the last 5 minutes: OK

--> Bonus points: Make it a multi-alert by host so that you won't have to recreate it if your infrastructure scales up: Ok

--> Give it a descriptive monitor name and message (it might be worth it to include the link to your previously created dashboard in the message). Make sure that the monitor will notify you via email: OK
    
--> Screenshot of the email sent:

<a target="_blank" href="https://imageshack.com/i/pnEQb0PNp"><img src="http://imagizer.imageshack.us/v2/1024x768q90/923/EQb0PN.png" border="0"></a>

--> Bonus: Since this monitor is going to alert pretty often, you don't want to be alerted when you are out of the office. Set up a scheduled downtime for this monitor that silences it from 7pm to 9am daily: OK

--> Make sure that your email is notified when you schedule the downtime and take a screenshot of that notification

<a target="_blank" href="https://imageshack.com/i/pncz3Ynmp"><img src="http://imagizer.imageshack.us/v2/1024x768q90/923/cz3Ynm.png" border="0"></a>
