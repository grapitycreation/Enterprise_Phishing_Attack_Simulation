# Simulation and Implementation of Enterprise Network Attacks via Email Phishing

## 🛠️ Introduction
This project demonstrates a simulated cyber attack on an enterprise network using email-based phishing techniques. It is designed as part of a university capstone project focused on understanding the impact of social engineering and advanced post-exploitation techniques within a corporate environment.

### 🎯 Objectives
- Simulate a real-world phishing attack that compromises an employee workstation.
- Demonstrate how attackers can move laterally within the internal network, access critical services such as Active Directory, and exfiltrate sensitive data.
- Explore and apply the full Cyber Kill Chain methodology, including initial access, privilege escalation, persistence, command and control (C2), and data exfiltration.

### 🔍 Key topics
- Phishing Email Campaigns (Spear Phishing)
- Command & Control (C2) Infrastructure (TCP-Based)
- Active Directory Attacks
- Post-Exploitation Techniques (Privilege Escalation, Lateral Movement, Persistence)
- MITRE ATT&CK Mapping

### 📚 Educational Value:
This project not only showcases offensive security techniques in a controlled lab environment but also highlights the importance of email security awareness and proactive defense strategies for enterprise systems.

⚠️ **Disclaimer**: This project is created strictly for educational and research purposes. All testing was performed in an isolated lab environment. Do not attempt any unauthorized attacks on real systems.

![Network Diagran](https://github.com/grapitycreation/Enterprise_Phishing_Attack_Simulation/blob/main/Network_Diagram.png)
## 📡 Network Architecture Overview
The network diagram illustrates a simulated enterprise environment used to demonstrate a phishing email attack scenario. This setup enables a red team to test how attackers can infiltrate an organization via social engineering and email-based delivery.

### 🔐  Victim Side:
- **Internal Network**: 10.10.20.0/24
- **Assets**:
  - Windows 10 Client (10.10.20.12): Simulates a regular employee workstation, targeted by phishing emails.
  - Windows Server 2016 (10.10.20.11): Functions as a Domain Controller, Web Server, and Mail Server (MDAEMON).
  - Windows Server 2012 (10.10.20.13): Hosts application and file sharing services.
- All devices are connected through an internal LAN and are managed as part of the same domain (via Active Directory).

### 🌍 Internet Access:
- **Router (Ubuntu Server)**:
  - Acts as a NAT router bridging the attacker network and victim network.
  - Internal IP: 10.10.20.10
  - External IP: 192.168.5.254
  - Provides outbound Internet access for the victim side.

### 🧠 Attacker Side:
- **Attacker Network**: 192.168.5.0/24 (NAT)
- Kali Linux: Used as the attacker machine to craft phishing payloads and launch the campaign.
- C2 Server (Command & Control):
  - Controlled via TCP port 40056.
  - Used to receive callbacks from infected hosts and issue remote commands.

This architecture simulates a realistic scenario where phishing emails are used as the initial attack vector, with goals of gaining initial access, establishing persistence, and moving laterally within the enterprise network, all under the framework of the Cyber Kill Chain.

## 🚨 Attack Execution Summary
The simulated attack follows the **Cyber Kill Chain** model and is structured into several phases, starting from information gathering to data exfiltration. Below is an overview of the attack steps:
1. 🔎 **Reconnaissance**
- Gathered public information about the organization and employees.
- Identified a vulnerable employee using social engineering techniques.
- Crafted a spear-phishing email targeting the selected victim.

2. 🎯 **Initial Access (Phishing Email)**
- Sent a fake email embedded with a malicious payload disguised as a legitimate document or link.
- Upon opening, the payload established a reverse shell back to the C2 server.

3. 🛠️ **Exploitation & Payload Deployment**
- Executed shellcode on the victim's machine using tools such as Havoc C2 and Metasploit.
- Deployed post-exploitation frameworks to maintain access and gather credentials.

4. 🔐 **Privilege Escalation**
- Exploited local misconfigurations to escalate privileges from user to administrator.
- Utilized tools like Mimikatz to dump credentials from memory.

5. 🔄 **Lateral Movement**
- Used stolen credentials to pivot from the compromised client to internal servers, including the Domain Controller.
- Employed tools like PsExec to move across machines.

6. ♻️ **Persistence**
-Created scheduled tasks and registry keys to ensure access survives reboots.
- Established additional backdoors for remote access continuity.

7. 📤 **Data Exfiltration**
- Extracted sensitive user and group data from Active Directory (NTDS.dit, SAM).
- Exfiltrated the data to the attacker-controlled machine through an encrypted channel.

## 🧰 Tools & Platforms Used
The following tools and platforms were utilized throughout the simulated phishing attack to replicate real-world offensive security scenarios:

### 🖥️ Operating Systems & Network Infrastructure
- **Windows 10**: Targeted user workstation for phishing payload delivery.
- **Windows Server 2016**: Domain Controller (AD DS), DNS Server, Mail Server (MDAEMON), Web Server (IIS).
- **Windows Server 2012**: Application and File Server.
- **Kali Linux**: Used as the attacker's machine for reconnaissance, phishing, and C2 operations.
- **Ubuntu Server**: Acted as a NAT router between the attacker and enterprise network segments.

### 🧪 Offensive Security Tools
- **Zphisher**: Automated phishing toolkit used to create and send fake login pages and emails.
- **Havoc C2 Framework**: Command & Control platform for managing infected hosts and issuing remote commands.
- **Metasploit Framework**: Used to craft payloads, deliver exploits, and perform post-exploitation tasks.
- **Mimikatz**: Extracted credentials, tokens, and password hashes from Windows memory.
- **PsExec (Impacket)**: Facilitated remote code execution and lateral movement within the network.
- **netcat**: Lightweight tool for simple reverse shells and file transfers.
- **Resource Hacker**: Modified file metadata and icons to disguise payloads as legitimate documents.

### 🧩 Additional Technologies
- **Active Directory (AD DS)**: Simulated centralized identity and access management.
- **MITRE ATT&CK Framework**: Used for mapping each attack stage to known adversarial techniques.
- **IIS (Internet Information Services)**: Hosted a fake or vulnerable web application for post-exploitation.
- **FTP & SMTP Services**: Simulated typical enterprise protocols and services for realistic attack flow.

## ✅ Results & Conclusion
### 🔬 Results:
- Successfully delivered a spear-phishing email that bypassed user awareness and basic antivirus detection.
- Gained initial access to an internal Windows 10 workstation.
- Achieved privilege escalation and obtained administrator-level access on the victim machine.
- Maintained persistence through scheduled tasks and registry modification.
- Performed lateral movement to access the Domain Controller and exfiltrated sensitive information, including:
  - Domain user lists
  - Password hashes
  - NTDS.dit & SAM files
- Mapped each attack step to the MITRE ATT&CK framework, showcasing a complete chain of techniques used in real-world APT scenarios.

### 🧩 Conclusion:
This project successfully demonstrates how a well-crafted phishing campaign can be used to infiltrate an enterprise network and escalate access to critical systems. Through a hands-on lab simulation, we replicated an end-to-end attack chain from initial access to data exfiltration, using real offensive tools and techniques.

### 🔐 Key Takeaways:
- Phishing remains a highly effective initial attack vector.
- Weak endpoint protection and poor user awareness are major risk factors.
- Lateral movement and privilege escalation are key to compromising the entire domain.
- Continuous security training, email filtering, and network segmentation are essential for defense.

# Demo
Link: https://youtu.be/vrkkW1OO6ug
