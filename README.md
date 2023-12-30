# Linkedin
[![My Skills](https://skillicons.dev/icons?i=linkedin)](https://www.linkedin.com/in/gauravss03/)
# Portfolio 
[![](https://skillicons.dev/icons?i=gamemakerstudio)](https://gauravsuryawanshi.pages.dev/)

# Building a Virtual Security Operation Center Lab

![1_5KC8Y4ckfI5m5peDTazfbA (1)](https://github.com/astroxhacker/SOC-Lab/assets/109857735/1a1fea1d-214c-40a7-9918-6628f3136f7c)

# Introduction
  In this laboratory scenario, the focus will be on generating and analyzing a malicious file. Specifically, the malicious file will serve as a Command and Control (C2) payload via Sliver, facilitating a C2 session on a Windows Virtual Machine (VM) through an Ubuntu Server. The objective is to explore privileges, identify password locations, and extract critical information within this Command and Control session.

Furthermore, participants will gain insights into detecting such malicious activities. LimaCharlie will be utilized as a tool for detection, enabling the creation of detection rules to identify and respond to this type of threat. The lab aims to provide hands-on experience in both offensive and defensive cybersecurity measures, emphasizing the importance of proactive detection and response strategies.

# What is LimaCharlie?
     
![download](https://github.com/astroxhacker/SOC-Lab/assets/109857735/de8899dc-ff56-482b-8844-c8ead54e1e61)

LimaCharlie is a SecOps Cloud Platform. LimaCharlie comes with a cross-platform EDR agent, handles log shipping/ingestion and has built in threat detection.

# Working on the Payload
![1_q60fJrWV-YzLuWYKvyLvcg](https://github.com/astroxhacker/SOC-Lab/assets/109857735/8cf14d98-65b7-4638-aba5-93e9b83c2fb2)

In the context of this project, the process of creating a Command and Control (C2) payload using Sliver involves several key steps. Initially, Sliver is configured with specific parameters to tailor the payload for the targeted system, ensuring compatibility with the Windows VM and the Ubuntu Server. Once configured, Sliver generates the malicious payload, embedding it with functionalities designed to establish a covert communication channel between the compromised Windows VM and the Ubuntu Server. This payload enables the operator to gain unauthorized access, explore system privileges, and locate critical information within the Command and Control session. It is crucial to execute this process ethically and responsibly within the confines of the lab environment, with the primary objective being educational insight into offensive cybersecurity techniques and subsequent defensive measures using tools like LimaCharlie for detection.
TO KNOW IN DETAIL, VISIT THE MEDIUM PAGE [HERE](https://google.com)

# Observing the EDR Telementry
In the journey of observing our Endpoint Detection and Response (EDR) telemetry, it's like unlocking a treasure trove of insights into the digital realm. As an early graduate navigating the vast landscape of cybersecurity, delving into EDR telemetry feels like deciphering a secret language that exposes the activities happening on our systems. It's not just about spotting anomalies; it's about understanding the pulse of our digital environment. The EDR telemetry is like our digital heartbeat, revealing patterns, irregularities, and potential threats. It's this data that empowers us to detect and respond to cyber threats effectively. It's a bit like being a digital detective, piecing together clues from the EDR telemetry to stay one step ahead of potential adversaries. And amidst this exploration, tools like LimaCharlie serve as our trusty sidekick, helping us make sense of the digital narrative and fortifying our defenses.

In our process tree, we can see everything that is running. It is important as an analyst to know what should normally be running. If you know what is normal, you will know what isn’t suppose to be there.
![1_BRq6ayIWtUkYFVMH4E9QPQ](https://github.com/astroxhacker/SOC-Lab/assets/109857735/c590fe67-d18b-4c96-9986-863dde2806ee)
TO KNOW IN DETAIL, VISIT THE MEDIUM PAGE [HERE](https://google.com)

# Detection
Detecting threats in the cybersecurity landscape is akin to being a vigilant guardian of the digital realm. It's about crafting a keen awareness of the intricate footprints left by potential adversaries. As someone freshly graduated, diving into the world of detection feels like developing a sixth sense for recognizing anomalies and suspicious activities within our network. It's not just about finding a needle in a haystack; it's about understanding the language of threats and anticipating their next move. Tools like LimaCharlie become our allies, providing us with the means to create detection rules that act as our guardians, watching over the digital landscape. It's like setting up invisible tripwires and alarms, ready to signal any unusual behavior that might hint at a looming cyber threat. In this dynamic dance between offense and defense, detection becomes the shield that safeguards our digital assets, allowing us to respond swiftly and decisively to protect the integrity of our systems.

Let’s detect this incident. On the timeline menu, we can now search for “SENSITIVE_PROCESS_ACCESS” events.
![1_FX9a3m2YL1ZTIlZcd0_cYA](https://github.com/astroxhacker/SOC-Lab/assets/109857735/75cfbca3-ae31-4559-a95d-e7b69ea24819)

Clicking on one of the incidents, we can view the event when credentials were accessed. Now let’s build a Detection and Reponse (D&D) rule that will alert us if this occurs again.

![1_sbi8MjDIiv7Y8PimdKvnYQ](https://github.com/astroxhacker/SOC-Lab/assets/109857735/f47c04bf-a587-4ff3-86c4-c51a541281b9)

In the detect section we want to add this:
```
event: SENSITIVE_PROCESS_ACCESS
op: ends with
path: event/*/TARGET/FILE_PATH
value: lsass.exe
```
We can see the rule worked and was detected.
![0_p0e1emm_3iBqLjoR](https://github.com/astroxhacker/SOC-Lab/assets/109857735/be955c5f-a77e-46bc-b74f-bfd71a6e7d2e)

# Blocking Attacks
Now let’s work on blocking an attack. In order to to do this we would normally want to properly baseline the environment for false positives in order to prevent issues.

We will be attempting to block Volume Shadow Copies. Volume Shadow Copies are used to restore individual files or even an entire file system to a previous state. This is a very popular option for recovering from a ransomware attack, the also being a reason a ransomware attack would want to delete the shadow copies.
TO KNOW IN DETAIL, VISIT THE MEDIUM PAGE [HERE](https://google.com)

# Conclusion
This marks the conclusion of our lab exploration, but the journey doesn't end here; it's just the beginning. As an enthusiastic aspiring SOC analyst, I see these home lab experiences as invaluable opportunities to immerse myself in the practical intricacies of the cybersecurity landscape. The hands-on encounters with creating and detecting threats have been both enlightening and exhilarating. This home lab isn't just a stopping point; it's a launchpad for continuous learning and experimentation. The thrill of navigating through malicious scenarios and crafting defense strategies fuels my passion for understanding the ever-evolving world of cybersecurity. I trust you found this walkthrough as engaging and insightful as I did, and I'm excited to carry these lessons forward in my journey toward becoming a proficient SOC analyst.

[LINKEDIN](https://www.linkedin.com/in/gauravss03/)    
[PORTFOLIO WEBSITE](https://gauravsuryawanshi.pages.dev/)
