![Toplogy](Image/Topology.png)
# 🔥 Cisco ASA Firepower Lab

## 📌 Overview

This project demonstrates the configuration of a Cisco ASA firewall with Firepower services to secure a small network. It includes inside, outside, and management networks with NAT, access control, and traffic inspection.

---

## 🗺️ Network Topology

### 🌐 Outside (Internet)

* IP: `192.168.22.13/24`
* Gateway: `192.168.22.1`

### 🔥 ASA Firewall (ASAv)

* **Outside (Gi0/2):** `192.168.22.13/24`
* **Inside (Gi0/1):** `10.10.10.1/24`
* **Management (Mgmt0/0):** `172.16.1.1/24`

### 🖥️ Inside Network

* **PC1:** `10.10.10.2/24`
* **PC2:** `10.10.10.3/24`
* **Gateway:** `10.10.10.1`

### 💻 Management PC

* IP: `172.16.1.2/24`

---

## 🔐 Default Credentials

Username: `user`
Password: `Test123`

> ⚠️ Change credentials in production environments.

---

## 🎯 Objectives

* Configure ASA interfaces (inside, outside, management)
* Enable NAT (PAT) for internet access
* Apply basic access control policies
* Enable and configure Firepower services
* Verify connectivity and traffic inspection

---

## ⚙️ ASA Configuration

### 1. Interface Configuration

```bash
interface GigabitEthernet0/1
 nameif inside
 security-level 100
 ip address 10.10.10.1 255.255.255.0

interface GigabitEthernet0/2
 nameif outside
 security-level 0
 ip address 192.168.22.13 255.255.255.0

interface Management0/0
 nameif management
 security-level 100
 ip address 172.16.1.1 255.255.255.0
```

---

### 2. Default Route

```bash
route outside 0.0.0.0 0.0.0.0 192.168.22.1
```

---

### 3. NAT Configuration (PAT)

```bash
object network INSIDE-NET
 subnet 10.10.10.0 255.255.255.0
 nat (inside,outside) dynamic interface
```

---

### 4. Access Control Policy

```bash
access-list INSIDE-OUT extended permit ip any any
access-group INSIDE-OUT in interface inside
```

---

### 5. Enable Firepower Module

```bash
sw-module module sfr recover configure
```

Access Firepower GUI:
https://172.16.1.1

---

## 🛡️ Firepower Configuration

Inside Firepower (FDM or FMC):

* Register device (if using FMC)
* Create Access Control Policy
* Enable Intrusion Policy
* (Optional) Configure URL Filtering
* Deploy policies to the ASA

---

## 🧪 Testing

### Connectivity Tests (PC1 / PC2)

```bash
ping 10.10.10.1
ping 192.168.22.1
ping 8.8.8.8
```

---

### 🔍 Verification Commands (ASA)

```bash
show interface ip brief
show route
show nat
show access-list
show conn
```

---

## 📂 Project Structure

```
asa-firepower-lab/
│── README.md
│── configs/
│   ├── asa-config.txt
│   └── firepower-policy.txt
│── topology.png
```

---

## ⚠️ Notes

* Firepower requires proper licensing
* Configure NTP for accurate logging
* Use strong passwords in real deployments
* Disable unused services for security

---

## 🚀 Future Improvements

* Site-to-Site VPN
* Remote Access VPN
* VLAN segmentation
* Active Directory integration
* Centralized logging (SIEM / Syslog)

---
