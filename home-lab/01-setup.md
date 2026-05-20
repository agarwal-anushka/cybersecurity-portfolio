# Home Lab Setup
Date: 20 May 2026

## Goal
Build a safe isolated practice environment to learn 
cybersecurity hands-on without affecting real systems.

## Tools Used
- Oracle VirtualBox — hypervisor to run virtual machines
- Kali Linux 2026.1 — attack machine with built-in security tools
- Metasploitable 2 — deliberately vulnerable target machine

## Network Configuration
Both VMs set to Host-Only Adapter in VirtualBox settings.

This means:
- Kali and Metasploitable can talk to each other
- Neither VM can reach the real internet
- My main PC is protected from any attacks

## Verified Setup
Ran ping from Kali to Metasploitable:
ping 192.168.56.101
Got successful responses confirming both 
machines can communicate.

![Metasploitable ifconfig](https://github.com/agarwal-anushka/cybersecurity-portfolio/blob/main/home-lab/screenshots/01-setup/metasploitable_ifconfig_output.png)

![Ping verification](https://github.com/agarwal-anushka/cybersecurity-portfolio/blob/main/home-lab/screenshots/01-setup/ping_from_kali_to_metasploitable.png)

## What This Lab Allows Me To Practice
- Network scanning and enumeration
- Exploitation of known vulnerabilities
- Defensive techniques and monitoring
- Real tools used by security professionals
