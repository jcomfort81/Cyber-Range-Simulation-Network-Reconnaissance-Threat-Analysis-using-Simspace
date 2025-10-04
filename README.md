# Cyber-Range-Simulation-Network-Reconnaissance-Threat-Analysis-using-Simspace
A simulated network security assessment in the SimSpace Cyber Range using Nmap and other professional tools.
Jordan Comfort
Exploring the SimSpace Cyber Range
September 13th, 2025
Lab One: Exploring the SimSpace Cyber Range
My initial experience with the SimSpace Cyber Range was both familiar and a new challenge. As a service desk technician for a managed service provider, I am accustomed to remoting into virtual machines and servers and working with credentials on a daily basis. At my job, we use temporary administrative accounts that expire, and we often have to force a sync on our on-premises Active Directory using the Start-ADSyncSyncCycle -PolicyType Delta command, particularly for password resets in a hybrid environment. While this is routine for me, this lab offered me a chance to apply my existing technical skills for a completely different purpose: cybersecurity. SimSpace, which was co-founded by William Hutchinson and Lee Rossey in 2015, essentially creates digital replicas of tech stacks and network environments so different companies can train and test cyber attacks in safe, virtual environments. The main purpose behind its development was to allow organizations to practice and simulate cyber attacks without risking their live production systems. My experience here confirmed its value as a fantastic test environment, and it helped me understand its applications for blue, red, and purple teams.

The first part of the lab introduced me to network scanning using Nmap, which was something I have no authority to do at my work. The command nmap -v 172.16.3.0 /24 provided me with a live, verbose view of all the hosts on the network. The output was a lot to take in at once, which is why I was instructed to "pipe" the output to a text file. The command nmap -v 172.16.3.0 /24 > jordancomfortscan1.txt demonstrated a practical way to capture and save the results for later analysis. After viewing the output, I was able to answer the lab's questions about the number of addresses and live hosts on the network.

I also learned the important distinction between the nmap -sU and -sn commands. The -sU command, used in the second scan, is a port scan to discover what specific services are running and what ports are open on a computer. The -sn command, in contrast, is used simply to see if a computer is online. The ability to discover open ports is critical for a security professional. Knowing which ports are open on a network helps a potential attacker find an entry point, but it also helps a security team identify vulnerabilities and secure their network by closing non-essential ports. This dual function of Nmap makes it a valuable tool for both offensive and defensive cybersecurity roles.

My biggest struggle during the lab wasn't with the commands themselves, but with logging into one of the virtual machines, winhunt-06. I just performed a simple reboot and was able to access the machine as instructed—a common troubleshooting step I use at my IT job. The only unclear instruction in the lab was what exactly to do with the Kali-Hunt tools, but a quick review of the rubric clarified that I just needed to open them and provide a screenshot. This showed me the importance of paying attention to all parts of a complex assignment.

Launching and Researching Kali-Hunt Tools
The Kali-Hunt virtual machine provided an opportunity to go beyond simple network scanning and explore specialized cybersecurity applications. I selected three tools that are useful for any security practitioner: Medusa, SPARTA, and netsniff-ng.

Medusa
Medusa is a powerful, parallel, and modular brute-force tool designed to guess passwords against a wide range of network services (Grover & Gagandeep, 2020). It’s not just for malicious attackers; a security professional uses Medusa for a critical purpose: proactive defense. By attempting to crack passwords on a system, a security practitioner can identify weak or default credentials that could be exploited. I constantly see users at my job getting their passwords brute-forced. I analyze sign-in logs and see a significant amount of sign-in attempts from different IP addresses than normal, with "incorrect username and password" as the reason for failure. This is highly likely to be a brute-force attack from a malicious actor who could be using a tool like Medusa. These attacks can sometimes succeed; however, our company enforces other policies to prevent them.

We encourage and highly recommend enforcing multi-factor authentication, which requires another form of authentication beyond a credential, such as a one-time passcode or text. This helps prevent unauthorized sign-ins and increases security, even if it makes the sign-in process longer for users. We also enforce a policy called conditional access, which can block a sign-in from an unusual location, device, or IP address. These policies work together to create a secure environment that can prevent unauthorized access using a tool like Medusa for password cracking. Another precaution we take is enforcing secure passwords. I typically encourage at least 16 characters, with a mix of upper and lowercase characters, a special character, and numbers. With these precautions, it becomes more inconvenient and harder for hackers to compromise accounts. This helps organizations prevent an escalation from a password compromise to a larger attack, such as ransomware or confidential information leakage.

Medusa can also be helpful in a penetration test or a red team exercise to see how quickly a company's virtual environment could be compromised. This is valuable for a security team because Medusa is a real-world tool that simulates a realistic attack on their infrastructure. The findings from a Medusa scan empower a professional to implement countermeasures such as stronger password policies, which ultimately helps prevent a real-world breach. This can help an organization provide training regarding password policies to technicians or create policies for users to have a much more secure environment. Medusa is particularly effective because of its multi-threaded design, which allows it to test multiple hosts, users, or passwords concurrently, making it a highly efficient choice for security assessments. This ability to test an entire organization at once is extremely helpful, as it saves time and increases the potential attack surface for a hacker, helping them achieve their objective, whatever their motivation may be.

SPARTA
SPARTA is a network penetration testing tool that uses a graphical user interface (GUI) to simplify network scanning and enumeration. Its primary purpose is to save security practitioners time by providing a "point-and-click" approach to their toolkit, which allows the tester to focus on analysis rather than manually typing out individual commands. According to a paper by Keski-Korsu (2016), SPARTA uses a five-stage model to scan target networks and automates tests against detected services. This is highly useful for information assurance and security professionals because it streamlines a critical and often time-consuming phase of a security assessment. By combining different tools, it accelerates the speed to recognize services or versions that are open or running and that may have common vulnerabilities. The SPARTA scan helps a team, whether it be the Security Operations Center (SOC) or a penetration testing team, map a network faster than if they used each tool independently.

With the open ports and services that the tool provides, a security team can perform a cross-reference with a list of common vulnerabilities and exploits (CVEs) to see if their network has known exploits. The team can then patch these exploits once they have been identified. This also provides insight into what a hacker would view as possible entry points. The security team could then have a penetration tester perform an attack on an identified vulnerability to see if the network defenses will be compromised and how the team will respond. A security team could also perform segmentation of the network if they analyzed the scan results and found certain areas that carry a higher risk. This would reduce the attack surface on the network. This segmentation can significantly reduce damages if an area on the network is breached, making it much harder for a threat to move laterally across the network. This process also helps a security team prioritize their budget, time, and resources to the highest-risk areas on the network. The biggest benefit of using SPARTA is that it makes a team aware of its vulnerabilities, which allows it to have more control over its network and take the proper precautions.

My job requires me to consistently monitor endpoints and ensure that devices are up-to-date, which helps security by making sure there are no vulnerabilities with the software. I also document when certain devices or servers are not up to date and provide feedback to managers. This information can then be used to update documents like Standard Operating Procedures (SOPs) to help with overall workflow. I typically escalate a ticket to the security or networking team if I discover a port or service open that shouldn't be. Communication is extremely important in a business, especially in cybersecurity, for maintaining a secure environment and a culture of continuous improvement to reduce as much risk as possible. By quickly discovering live hosts and identifying open ports and services, SPARTA provides an efficient overview of a network’s attack surface, allowing professionals to prioritize vulnerabilities and build a more effective defense strategy.

Netsniff -ng

In the field of network forensics, tools for packet analysis are essential for investigating cybercrimes and gathering evidence. netsniff-ng, developed by Daniel Borkmann in 2009, is a high-performance packet sniffing tool that operates by capturing and analyzing network traffic in real time. Security professionals can use this tool to see anomalies, malicious connections, and passwords being transmitted in plaintexts. The tool allows visibility into how hosts communicate via ports, etc., which helps them detect lateral movement and when attackers try to extract sensitive data. The tool also allows professionals to see if policies like encryption, secure protocols, and segmentation are being practiced. After a breach, cyber professionals can analyze packet captures for evidence to see what the attacker did and how the data was potentially manipulated.

In my experience as a service desk professional, this knowledge is applied by enforcing and educating users on the importance of using VPNs, which most of the time use IPsec to encrypt their information, so a tool like netsniff-ng cannot simply capture their information. It is especially important for end-users to use a VPN when in public locations using guest Wi-Fi, like a coffee shop or a college campus. It is common for attackers to sit by and monitor network traffic, potentially using netsniff-ng, to dissect the information for credentials or sensitive information. Even if a VPN is used, they could perform a man-in-the-middle attack. This is why it's important to inform users not to reuse passwords and not to access sensitive information like health or banking websites when using public Wi-Fi. In my role, I enforce strong protocols like HTTPS and VPNs so attackers cannot exploit credentials. I also encounter bigger network connectivity issues and slowness for clients, which I would escalate to our engineering or networking team. They could then use a tool like netsniff-ng to look for suspicious traffic or settings changes. The company I work for uses SentinelOne and Huntress, as well as the principle of least privilege and patching, to prevent an attacker using a tool like netsniff-ng from getting a foothold to compromise our network. I consistently respond to these alerts and am made aware when there is a potential compromise or a need to take action.

An attacker could run this tool on a company's network and figure out who has admin accounts and where servers are located. This is why security professionals ensure that admin privileges are only given to individuals when needed and are put into security groups based on their role or job. The juxtaposition is that a user using netsniff-ng could easily harvest credentials and sensitive information for ransom against unsuspecting or ignorant users with no knowledge of information security best practices. This tool provides a foundational approach to network forensics by allowing security professionals to play back network traffic and reconstruct files that were transmitted across the network. A professional uses netsniff-ng for network monitoring and forensic investigation to detect signs of malicious online behavior, such as unauthorized access, malware infections, and data breaches (Jaipurkar & Marathe, 2022). Its capability to capture packets and acquire host-based evidence is critical for building a comprehensive understanding of a security incident and providing evidence that can be used in a court of law.

In conclusion, this lab provided a valuable introduction to fundamental cybersecurity practices within a controlled environment using the virtual machines. The two main sections, network scanning with Nmap and the research on specialized Kali tools, worked together to provide a holistic view of a security professional's job. My experience with Nmap taught me how a reconnaissance tool can serve a dual purpose for both red and blue teams, while my research into Medusa, SPARTA, and netsniff-ng highlighted the importance of using targeted, specialized tools for each task to reduce time on tasks, help break into a network and secure the network. The process of documenting my work and reflecting on my experience also reinforced the importance of clear communication and consistent procedures. In my professional role, I constantly rely on and contribute to knowledge bases to ensure that tasks are performed consistently across the company, preventing the need to duplicate work and allowing for efficient operations.

Overall, this lab was not just an academic exercise but was also very applicable to the real-world application of information assurance. It connected my existing professional skills in IT to the new and exciting world of cybersecurity, showing me how my knowledge of troubleshooting and documentation can be directly applied to protecting networks and data. The lab demonstrated that even simple commands and tools are part of a much more complex strategy for both defending and attacking systems. The hands-on experience in the SimSpace Cyber Range was extremely useful for solidifying these concepts and demonstrating how they are highly applicable to the IT and cybersecurity fields. I also learned that many tools and commands can be a dual asset, providing critical insights for both hackers and cyber analysts defending the network.




Appendices

Figure 1. Successfully logged in with my credentials assigned to the workstation with win-hunt-06

<img width="512" height="399" alt="screenshot 1 cyber range lab" src="https://github.com/user-attachments/assets/b797da0f-e5df-42db-96fa-17a819f89569" />



Figure 2. Screenshot for Steps 6-7 Running NMAP command displayed below

<img width="512" height="180" alt="screenshot 2 cyber range lab" src="https://github.com/user-attachments/assets/ac582a70-6832-41ce-9552-cf29f7b240f7" />



Figure 3. Screenshot for Steps 8-9 displayed below running nmap v 172.16.3.0 /24

<img width="512" height="220" alt="screen shot 3 cyber range lab" src="https://github.com/user-attachments/assets/f792e3e7-d13d-4b4b-90e4-01574158ea65" />


Figure 4. Screenshot of Steps 10-11 displayed below

<img width="512" height="333" alt="screenshot 4 cyber range lab" src="https://github.com/user-attachments/assets/efaa82d1-a2b8-43b9-84fd-b975cacde840" />


Figure 5. Step 12 displayed below

<img width="512" height="327" alt="screenshot 5 cyber range lab" src="https://github.com/user-attachments/assets/2a18d439-b372-473c-8a65-aaf140667b72" />



Figure 6. Steps 13-14 displayed below (257 Addresses/38 hosts up)


<img width="512" height="193" alt="screenshot 6 cyber range lab" src="https://github.com/user-attachments/assets/51e7aed0-399d-4786-bcd1-c0dae6a5ca5a" />




Figure 7. Step 16 (1 Port is open 137/udp) nmap -v 172.16.3.0 /24 > jordancomfortscan1.txt running this powershell command as instructed in the lab. -sU switch in the Nmap command is used to perform a UDP scan. Its function is to scan for open UDP (User Datagram Protocol) ports on a target host. After trying the command nmap -v -sn 172.16.2.2 it only showed the hosts that were up. It is safe to say the difference between the -sU and -sn is that -sU is for seeing which ports are open on a computer and -sn shows if a computer is online.

<img width="512" height="246" alt="screenshot 7 cyber range lab" src="https://github.com/user-attachments/assets/f4caf252-7e9f-4198-9407-6bb0c48c8b1a" />



Figure 8. Launching Medusa

<img width="512" height="285" alt="screenshot 8 cyber range lab" src="https://github.com/user-attachments/assets/246e98e0-18c9-443c-b9c0-06ab3942fb57" />




Figure 9. Launching Sparta


<img width="512" height="291" alt="screenshot 9 cyber range lab" src="https://github.com/user-attachments/assets/224ca726-bce3-4454-bae6-1ee6311060dc" />


Figure 10. Launching netsniff -ng

<img width="512" height="287" alt="screenshot 10 cyber range lab" src="https://github.com/user-attachments/assets/b383cfcf-f38d-41ca-b1fa-1efb21d1894d" />


Bibliography
Keski-Korsu, P. (2016). Automated port scanning and security testing on a single network host (Master's thesis, University of Oulu). Oulu, Finland.

Grover, V., & Gagandeep. (2020). An efficient brute force attack handling techniques for server virtualization. In Proceedings of the International Conference on Innovative Computing & Communications.

Jaipurkar, A. R., & Marathe, N. (2022). An Analytical Review on Packet Analysis for Network Forensics and Deep Packet Inspection in Network. International Journal of Scientific Research in Science, Engineering and Technology, 9(4), 147–167.

SimSpace. (2023, December 9). SimSpace raises $45M to simulate tech stacks for cyber training. SimSpace Blog. Retrieved from https://simspace.com/blog/simspace-raises-45m-to-simulate-tech-stacks-for-cyber-training
