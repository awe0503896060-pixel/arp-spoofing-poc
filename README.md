# ARP Spoofing Proof of Concept (PoC)

This repository documents a **lab-only ARP spoofing proof of concept** performed in an isolated virtual environment.  
The goal of this project is to understand how ARP-based man-in-the-middle (MITM) attacks behave on a local network,  
and how such activity can be **observed, analyzed, and detected** from a defender/SOC point of view.

> ⚠️ **Disclaimer**  
> All work in this project was done in a controlled **lab environment** on machines owned by me and on a private network.  
> This material is for **learning and defensive understanding** only. Do not use any of these ideas on networks or systems  
> you do not own or do not have explicit permission to test.

---

## 1. Lab Overview

- **Environment:** Virtual lab with multiple VMs
  - Attacker VM
  - Victim VM
  - Gateway/router (or a VM acting as the gateway)
- **Network level:** Local Layer 2 segment where ARP maps IP addresses to MAC addresses.
- **Objective:** Show how ARP spoofing can redirect traffic through an attacker and how this looks in:
  - ARP tables
  - Packet captures
  - Network behavior from a user’s perspective

This project focuses on **observation and documentation**, not on building tools.

---

## 2. PoC Flow (8 Steps)

The PoC is broken down into 8 clear steps, which match the PDF (`poc.pdf`) and the video (`ArpSpoof.mp4`).

1. **Lab setup**  
   Lab setup and initial network view: attacker and victim are on the same LAN segment.

2. **Discovery**  
   Identifying gateway and victim IP/MAC addresses on the local network.

3. **Attacker preparation**  
   Preparing the attacker host for acting as a router in the lab environment.

4. **Gateway ARP poisoning**  
   Poisoning the gateway's ARP table so that it sends traffic to the attacker.

5. **Launching ARP spoofing**  
   Launching the ARP spoofing command to poison the victim's ARP cache and complete the MITM position.

6. **Traffic monitoring**  
   Starting a packet capture tool (e.g., Wireshark) to monitor traffic during the attack.

7. **MITM observation**  
   Observing hijacked traffic flowing through the attacker (man-in-the-middle position).

8. **Cleanup & verification**  
   Stopping the activity and verifying that ARP tables and traffic return to normal.

Each of these steps is illustrated in the PDF with screenshots taken from the video recording.

---

## 3. Repository Contents

Typical structure (you can adjust this section to match your actual folders):

```text
.
├─ poc.pdf             # Step-by-step PoC document with screenshots and explanations
├─ README.md           # This file
