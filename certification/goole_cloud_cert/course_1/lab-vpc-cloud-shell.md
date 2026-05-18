# Lab Writeup - Create a VPC using Cloud Shell
**Course:** Introduction to Security Principles in Cloud Computing - Course 1

**Date:** 18 May 2026
**Difficulty:** Beginner

---

## What is a VPC?
A Virtual Private Cloud (VPC) network is a private cloud hosted 
within a public cloud. It lets organizations use public cloud 
resources while staying completely isolated from other cloud users.
Think of it like having your own private room inside a huge 
shared building — others are in the building but cannot enter 
your room.

---

## What I did in this lab
Created a custom VPC network with a subnet using Google Cloud 
Shell, then verified both were created successfully.

---

## Commands I used

### 1. Create the network
gcloud compute networks create labnet --subnet-mode=custom

What this did: Created a new VPC network called "labnet". 
The --subnet-mode=custom means I manually control what subnets 
exist inside it instead of Google creating them automatically.

---

### 2. Create a subnet inside that network
gcloud compute networks subnets create labnet-sub \
   --network labnet \
   --region us-central1 \
   --range 10.0.0.0/28

What this did: Created a subnet called "labnet-sub" inside labnet. 
The range 10.0.0.0/28 means this subnet can hold up to 
14 usable IP addresses.

---

### 3. List all networks
gcloud compute networks list

What this did: Showed all VPC networks in my project so I could 
verify labnet was created successfully.

---

### 4. List subnets of labnet
gcloud compute networks subnets list --network=labnet

What this did: Confirmed labnet-sub was created inside 
the correct network.

---

## What I saw in the Google Cloud console
- After running the commands labnet appeared in the 
  VPC networks section
- labnet-sub showed under subnets with the correct 
  IP range 10.0.0.0/28
- Cloud Shell ran all commands directly in the browser 
  without needing any local setup

---

## Key concepts I learned

- **VPC** = your own isolated private network inside 
  Google's public cloud
- **Subnet** = a smaller division inside a VPC network, 
  used to organize and control traffic
- **Network vs Subnet** = network is the big container, 
  subnet is a smaller section inside it
- **Custom subnet mode** = you decide what subnets to create 
  instead of Google doing it automatically
- **10.0.0.0/28** = an IP range that allows up to 14 usable 
  addresses inside the subnet
- **Cloud Shell** = a browser based terminal that lets you 
  control Google Cloud entirely through commands

---

## How this connects to cybersecurity
VPCs are a core security tool. By isolating resources inside 
a private network you reduce the attack surface — resources 
inside the VPC are not directly exposed to the public internet 
unless you explicitly allow it. As a cloud security analyst 
understanding VPC architecture is essential because almost 
every security decision in the cloud involves network isolation.

