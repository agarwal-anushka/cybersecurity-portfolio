# Nmap Scan - Metasploitable 2
Date: 20 May 2026
Target: 192.168.56.101
Tool: nmap -sV

---

## What is Nmap?
Nmap is a security tool used to scan ports on a computer. 
Security professionals use it to detect open ports and 
services which may have vulnerabilities. It tells us what 
ports are open and what services run on them by scanning 
up to 65535 ports. It is useful for both offensive and 
defensive security.

We can use Nmap with different flags (specialised options 
that change what the scan does). Common flags are listed below:

| Flag | What it does |
| --- | --- |
| -sV | Version detection |
| -sC | Run default scripts |
| -p- | Scan all 65535 ports |
| -O | Detect Operating System |
| -A | Aggressive scan (all of above combined) |

---

## Command Used
nmap -sV 192.168.56.101

## What the flag does
The -sV flag detects what software version is running 
on each open port. This is important because specific 
versions may have known vulnerabilities.

---

## Results

These are the ports I found interesting and why:

| Port | Service | Risk |
| --- | --- | --- |
| 21 | FTP (vsftpd 2.3.4) | Known backdoor — most critical finding |
| 23 | Telnet | No encryption, passwords sent in plain text |
| 1524 | Bindshell | Open backdoor shell — anyone can get full system access |
| 3306 | MySQL | Database directly exposed — should never be public |
| 5432 | PostgreSQL | Database directly exposed — should never be public |
| 5900 | VNC | Remote desktop exposed and unprotected |


---

## Most Interesting Finding

**vsftpd 2.3.4 — CVE-2011-2523**

The vsftpd 2.3.4 backdoor is a critical supply chain 
vulnerability. This backdoor was intentionally introduced 
through a malicious download archive for a few days 
in July 2011.

**How the exploit works:**

- An attacker logs into the FTP server and appends 
  the characters :) (a smiley face) to any username
- The malicious code detects this combination and 
  opens a backdoor shell on TCP port 6200
- The attacker then connects to port 6200 and gets 
  full root level access to the system
- No password or authentication required

This means anyone who knows about this vulnerability 
can completely take over the machine just by sending 
a smiley face in the username field.

---

## What I Learned

- How to use nmap to scan a target machine for open ports
- Open ports are not vulnerabilities themselves but can 
  expose services that have vulnerabilities
- Software versions matter — vsftpd 2.3.4 looks normal 
  but is critically dangerous due to CVE-2011-2523
- Databases like MySQL and PostgreSQL should never be 
  directly exposed to a network
- Telnet is insecure because it sends everything including 
  passwords in plain text — SSH replaced it for this reason
- Always research service versions after scanning — 
  knowing a version number can reveal known exploits

---

## References
- CVE-2011-2523: https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2011-2523