# cyart_soc-team-week-1

PART 1 — DETAILED THEORY 
________________________________________
1️⃣ SOC Fundamentals 

1.1 What is a SOC?

A Security Operations Center (SOC) is a centralized unit that:

•	Monitors network and endpoint activity 24/7

•	Detects threats

•	Investigates alerts

•	Responds to incidents

•	Maintains compliance and reporting

Core Objective:

Reduce Mean Time To Detect (MTTD) and Mean Time To Respond (MTTR).
________________________________________
1.2 SOC Operational Model

SOC works in layered defense model:

🔹 Detection Layer

•	SIEM

•	EDR

•	IDS/IPS

•	Threat Intelligence feeds

🔹 Analysis Layer

•	Log correlation

•	IOC matching

•	MITRE mapping

🔹 Response Layer

•	Isolation

•	Blocking IP

•	Disabling account

•	Malware removal

1.3 SOC Roles 

Tier 1 Analyst (Alert Analyst)

•	Monitor dashboard

•	Validate alerts

•	Close false positives

•	Escalate real incidents

Tier 2 Analyst (Incident Responder)

•	Log analysis

•	Timeline reconstruction

•	Determine scope of attack

Tier 3 Analyst (Threat Hunter)

•	Advanced investigation

•	Malware analysis

•	Behavioral detection engineering

SOC Manager

•	KPI tracking

•	Compliance reporting

•	Team coordination
________________________________________
2️⃣ SOC Frameworks 
________________________________________
🔹 NIST Cybersecurity Framework

Developed by National Institute of Standards and Technology

Five Functions:

1.	Identify
2.	
3.	Protect
4.	
5.	Detect
6.	
7.	Respond
8.	
9.	Recover
    
🔹 Incident Response Lifecycle (NIST SP 800-61)

Preparation → Identification → Containment → Eradication → Recovery → Lessons Learned

•	Why containment must happen before eradication

•	Why documentation is critical
________________________________________
🔹 MITRE ATT&CK Framework

Created by MITRE

ATT&CK = Adversary tactics & techniques knowledge base.

Example:

•	T1110 → Brute Force

•	T1059 → Command & Scripting Interpreter

•	T1003 → Credential Dumping

SOC uses MITRE for:

•	Threat mapping

•	Detection engineering

•	Reporting to management
________________________________________
 
3️⃣ Security Monitoring 
________________________________________
3.1 What is SIEM?

SIEM = Security Information and Event Management.

Functions:

•	Log collection

•	Normalization

•	Correlation

•	Alerting

•	Dashboarding

Examples:

•	Elastic SIEM

•	Wazuh

•	Splunk
________________________________________
3.2 Key Metrics

Metric	Meaning

MTTD	Time to detect threat

MTTR	Time to respond

False Positive	Alert but not real attack

False Negative	Attack but no alert
________________________________________
 
4️⃣ Log Management 
________________________________________
4.1 Log Lifecycle

1️⃣ Collection

Logs are gathered from various sources such as servers, firewalls, endpoints, applications, and network devices.
This is typically done using agents, syslog, APIs, or log forwarders.

2️⃣ Parsing

Raw log data is broken down into structured fields like IP address, timestamp, username, and event type.
This makes unstructured logs readable and usable for analysis.

3️⃣ Normalization

Logs from different devices are converted into a common format.
This ensures consistency so events from multiple vendors can be compared and correlated.

4️⃣ Enrichment

Additional context is added to logs, such as geolocation, threat intelligence, or asset criticality.
This improves detection accuracy and helps analysts understand the impact.

5️⃣ Storage

Processed logs are securely stored in databases or SIEM platforms.
Storage must ensure integrity, availability, and fast retrieval for investigations.

6️⃣ Retention

Logs are kept for a defined period based on compliance and business requirements.
Retention policies balance legal obligations, forensic needs, and storage costs.

7️⃣ Analysis

Logs are examined using rules, correlation, and behavioral detection techniques.
This helps identify security incidents, anomalies, and potential threats.
________________________________________

4.2 Important Log Types

Windows Logs

•	4625 → Failed login

•	4624 → Successful login

•	7045 → New service installed

Linux Logs

•	/var/log/auth.log

•	/var/log/syslog

Web Logs

•	Apache access.log
________________________________________

5️⃣ IDS / IPS 

Example: Snort

How it works:

•	Signature-based detection

•	Rule-based matching

•	Packet inspection

Rule structure:

action protocol sourceIP sourcePort -> destIP destPort (options)
________________________________________
6️⃣ Vulnerability Management 

Example tool:

Nessus

Vulnerability Management is a continuous security process used to identify, assess, prioritize, remediate, and verify security weaknesses in IT systems. Tools like Nessus automate vulnerability scanning by comparing system configurations and software versions against known security flaws.

1️⃣ Scan & Asset Identification

The process begins with identifying assets such as servers, endpoints, network devices, and web applications. A scan is configured in Nessus (preferably a credentialed scan for deeper visibility). During the scan, the tool:

•	Detects open ports and services

•	Identifies operating systems

•	Checks installed software versions

•	Compares them against known vulnerabilities

The output lists affected hosts, vulnerability names, plugin IDs, and references to CVEs.
________________________________________
2️⃣ Identify CVE

Each vulnerability is mapped to a CVE (Common Vulnerabilities and Exposures) ID, which is a globally recognized identifier for publicly disclosed security flaws. CVEs provide:

•	Description of the vulnerability

•	Affected software versions

•	Impact details

•	References to vendor advisories

This ensures standardization and consistency in vulnerability tracking.
________________________________________


3️⃣ Check CVSS Score

Each CVE includes a CVSS (Common Vulnerability Scoring System) score ranging from 0 to 10, indicating severity:

•	0.1–3.9 → Low

•	4.0–6.9 → Medium

•	7.0–8.9 → High

•	9.0–10 → Critical

The score is calculated based on factors such as attack vector (network/local), complexity, privileges required, user interaction, and impact on confidentiality, integrity, and availability. Higher scores indicate higher risk.
________________________________________
4️⃣ Risk-Based Prioritization

Organizations should not rely only on CVSS. Effective prioritization considers:

•	Whether the system is internet-facing

•	Business criticality of the asset

•	Availability of public exploits

•	Active exploitation in the wild

For example, a High vulnerability on a public web server may be prioritized over a Critical vulnerability on an isolated test machine.
________________________________________
5️⃣ Remediation (Patching & Mitigation)

After prioritization, remediation actions are taken:

•	Apply vendor security patches

•	Upgrade vulnerable software

•	Fix misconfigurations

•	Disable unused services

•	Implement firewall or IPS rules

If immediate patching is not possible, compensating controls and documented risk acceptance may be applied.
________________________________________
6️⃣ Verification & Reporting

After remediation, a re-scan is performed to confirm the vulnerability has been resolved. Results are documented in reports for IT teams, SOC teams, and compliance audits (e.g., ISO 27001, SOC 2). Metrics such as total vulnerabilities, severity distribution, and remediation timelines are tracked.
________________________________________
🔄 Continuous Process

Vulnerability management is not a one-time activity. Regular scanning (weekly/monthly), continuous monitoring, and trend analysis ensure ongoing security improvement and reduced risk exposure.
In summary, vulnerability management using Nessus follows a structured lifecycle: Scan → Identify CVE → Evaluate CVSS → Prioritize → Remediate → Verify → Monitor continuously.

________________________________________
7️⃣ Incident Response 

Identification

•	Alert triggered

•	Confirm malicious

Containment

•	Block IP

•	Disable account

•	Isolate machine

Eradication

•	Remove malware

•	Patch vulnerability

Recovery

•	Restore systems

•	Monitor closely

Lessons Learned

•	Improve detection rule

•	Update SOP
________________________________________
 
# PART 2 — LAB SETUP REQUIREMENTS
Need:

•	VirtualBox

•	Ubuntu VM

•	Windows VM

•	Metasploitable VM

•	Internet connection
________________________________________
PRACTICAL 1 — Log Collection with Elastic SIEM
________________________________________
Step 1: Install Elastic Stack (Ubuntu)

    sudo apt update

    sudo apt install elasticsearch kibana logstash
Enable services:
    
    sudo systemctl enable elasticsearch
    sudo systemctl start elasticsearch

 <img width="759" height="498" alt="image" src="https://github.com/user-attachments/assets/394d7b9e-af7b-4702-b71d-314587e31f3b" />

Screenshot- elasticsearch.service is enabled and avtive (running)
________________________________________

Step 2: Install Filebeat

    sudo apt install filebeat
Enable system module:

    sudo filebeat modules enable system
Start filebeat:

    sudo systemctl start filebeat

<img width="941" height="459" alt="image" src="https://github.com/user-attachments/assets/52826a7a-ee3e-4a89-b744-d22a1862973c" />
 
Screenshot – filebeat is enabled and active (running)
________________________________________
Step 3: Generate Logs

    logger "Test message"

 <img width="544" height="265" alt="image" src="https://github.com/user-attachments/assets/0d96568d-e622-4007-9121-afa0a1c6da95" />

Screenshot – sample log is generated using logger.

Step 4: Verify in Kibana

•	Open: http://localhost:5601

•	Go to Discover

•	Search: message: "Test message"

<img width="945" height="533" alt="image" src="https://github.com/user-attachments/assets/ffbf4872-790e-43c0-b30c-0ef6824d4b7d" />

Screenshot – The Test log is found in kibana dashboard.
________________________________________
PRACTICAL 2 — Brute Force Detection (Windows)
________________________________________
Step 1: Generate Failed Logins

On Windows VM:

•	Attempt wrong password
________________________________________
Step 2: Open Event Viewer

•	Windows Logs → Security

•	Filter Current Log

•	Event ID: 4625

 <img width="945" height="533" alt="image" src="https://github.com/user-attachments/assets/b3723885-0b75-4dce-9f42-bafe4666dc4a" />

Screenshot – failed login is seen in the Event Viewer.

________________________________________
PRACTICAL 3 — Snort Rule Testing
________________________________________
Step 1: Install Snort
    
    sudo apt install snort
________________________________________
Step 2: Add Custom Rule
Edit:

    sudo nano /etc/snort/rules/local.rules
<img width="945" height="191" alt="image" src="https://github.com/user-attachments/assets/2bb04ee4-2695-48a6-ad9f-b63f687d1d91" />

 
Step 3: Restart Snort

    sudo systemctl restart snort
________________________________________
Step 4: Test Rule
curl http://malicious.com
 <img width="895" height="362" alt="image" src="https://github.com/user-attachments/assets/c2d82221-cd50-44e1-a419-fa1eb72038ab" />

Check alerts:
 <img width="893" height="541" alt="image" src="https://github.com/user-attachments/assets/a73abdd2-3ed3-4d1b-a8dc-c16508f277b4" />

________________________________________
PRACTICAL 4 — Nessus Scan
________________________________________
Step 1:

Install Nessus Essentials.
________________________________________
Step 2:

•	Create new scan

•	Target: Metasploitable IP

 <img width="945" height="436" alt="image" src="https://github.com/user-attachments/assets/1b88f797-e1c2-4cb0-9e66-54d30c671c63" />

Screenshot – Target setup in nessus

Step 3:

<img width="945" height="302" alt="image" src="https://github.com/user-attachments/assets/dab2da6c-a4ea-497e-8ed7-28310d8073bf" />

Run scan.
 
Screenshot – Basic network scanning started on Metasploitable2.

Step 4:

Sort by CVSS score.

Document:

•	Vulnerability name

•	CVE

•	CVSS score

•	Recommendation

 <img width="945" height="391" alt="image" src="https://github.com/user-attachments/assets/0838d328-616f-4be3-b30b-2e6d8a9631aa" />

Screenshot – Vulnerabilities found with CVE, CVSS score and name.
________________________________________
 
PRACTICAL 5 — Wazuh Alert Rule
________________________________________
Step 1:

Install Wazuh manager.

Sudo apt install wazuh-manager
________________________________________
Step 2:

Edit rule file:

    sudo nano /var/ossec/etc/rules/local_rules.xml
Add rule:

<rule id="100010" level="10">
  <if_sid>5716</if_sid>
  <frequency>3</frequency>
  <timeframe>120</timeframe>
  <description>Multiple SSH failed logins</description>
</rule>
________________________________________
Step 3:

Restart Wazuh

    sudo systemctl restart wazuh-manager

 <img width="945" height="392" alt="image" src="https://github.com/user-attachments/assets/2395227e-d5e0-46d9-8a33-2aed2c666470" />

Screenshot – Wazuh started monitoring the logs.
Step 4:

Test failed SSH logins:

    ssh user@target-ip

<img width="720" height="222" alt="image" src="https://github.com/user-attachments/assets/d3b374e8-26b6-4956-baf3-a4bc7a75db85" />

Screenshot - Enter wrong password multiple times for non-existing user.
Check alerts in Wazuh dashboard.

<img width="1188" height="479" alt="image" src="https://github.com/user-attachments/assets/e427b6d9-5d54-40f8-a050-e6e501e777da" />

Screenshot – Wazuh detect the non-existing user try to login.

________________________________________
 
PRACTICAL 6 — Dashboard Creation

In Kibana:

1.	Go to Visualize

2.	Create Bar Chart

3.	Field: SourceIP

4.	Metric: Count

5.	Save dashboard

 <img width="944" height="454" alt="image" src="https://github.com/user-attachments/assets/da653f6e-783b-4006-9936-bf5d319ea770" />

________________________________________
PRACTICAL 7 — Incident Documentation

Create template:

| Date | Source IP | Event ID | Description | Action Taken |

Practice example:

<img width="944" height="247" alt="image" src="https://github.com/user-attachments/assets/5f61b367-6482-4947-bd81-f00fce05cd98" />


________________________________________
FINAL STUDY CHECKLIST 

•	How SIEM correlates logs

•	Difference between IDS and EDR

•	What is MITRE ATT&CK used for

•	What is CVSS

•	What is brute-force detection logic

•	How to reduce false positives

•	Full incident response lifecycle
________________________________________















