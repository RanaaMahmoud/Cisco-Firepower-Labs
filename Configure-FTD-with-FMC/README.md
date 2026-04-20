!{FTD with FMC}(Configure-FTD-with-FMC/Image/Configure-FTD-with-FMC.png)

📘 FTD with FMC (Centralized Management)
📌 Overview

This project demonstrates the deployment and configuration of Cisco Firepower Threat Defense (FTD) managed centrally using Firepower Management Center (FMC).

The lab simulates a real-world enterprise setup with:

Separate Management, Inside, and Outside networks
Centralized policy control using FMC
Traffic inspection and access control enforcement

🧩 Network Design
The environment consists of three main segments:

Management Network (172.16.1.0/24)
FMC server
Management PC
Used for device registration and policy management
Inside Network (10.10.10.0/24)
Internal hosts (PC1, PC2)
Connected via switch to FTD
Outside Network (DHCP)
Simulates internet access

⚙️ Key Configurations
🔹 FTD Initial Setup
Interface configuration:
G0/0 → Outside (DHCP)
G0/1 → Inside (10.10.10.1)
Management → 172.16.1.1
Basic connectivity verification
🔹 FMC Setup
FMC configured on management network
Web interface access enabled
Device registration prepared
🔹 FTD Registration to FMC
FTD added to FMC using:
Registration key
FMC IP address
Successful device synchronization
🔹 Access Control Policy
Created and deployed policy from FMC:
Allow HTTP/HTTPS traffic
Block unauthorized traffic
Applied policy to FTD device
🔹 NAT Configuration
Configured dynamic NAT (PAT) for inside network
Enabled internet access for internal hosts


🧪 Testing & Verification
Internal hosts successfully accessed the internet
Traffic matched configured policies
FMC showed real-time logs and events

🛠️ Skills Demonstrated
Firewall deployment and configuration
Centralized security management (FMC)
Access Control Policy design
NAT (PAT) implementation
Network segmentation
Traffic monitoring and validation

🎯 Key Takeaways
Centralized management simplifies firewall policy control
Proper network segmentation improves security
FMC provides visibility and control over traffic
