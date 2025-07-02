# Task 3: BREACH – Industrial Intrusion Write-up

## Overview
In this task, the goal was to exploit a weakness in the control infrastructure of an industrial control system (ICS) and open a security gate controlled by a badge and motion detection system.

- **Target**: 10.10.40.202
- **Objective**: Bypass badge authentication and open the gate.

## Phases of Exploitation

### Phase 1: Reconnaissance & Initial Enumeration
The first step was to scan the target system for open ports and services. Using **Nmap**, I identified several interesting open ports:

```css
nmap -p- --min-rate=1000 -T4 10.10.40.202 -oN full-port-scan.txt
```

Open Ports Identified: 

- 22/tcp (SSH) 
- 80/tcp (HTTP) 
- 102/tcp (iso-tsap) 
- 502/tcp (Modbus) 
- 1880/tcp (vsat-control) 
- 8080/tcp (HTTP Proxy) 
- 44818/tcp (EtherNetIP-2) 

Phase 2: Web Enumeration (Gobuster)
Next, I ran a Gobuster scan on port 80 to find any hidden directories or endpoints that might lead to the gate control system:

```css
gobuster dir -u http://10.10.40.202 -w /usr/share/wordlists/dirb/common.txt -t 40
```

This uncovered a /console path, which didn't directly expose the gate control. However, I found that Node-RED, running on port 1880, could be pivotal in controlling the system.

Phase 3: Gate Status Check & Exploitation
The goal here was to interact with the gate control system. I found an API endpoint for the gate and accessed the Node-RED dashboard UI:

```css
curl http://10.10.40.202/api/gate
```

The Node-RED dashboard was unauthenticated, and I was able to toggle the gate control without needing to log in. By toggling a switch on the dashboard, I successfully opened the gate.

Phase 4: Verification
Finally, I verified that the gate had been opened by interacting with the Node-RED flows and confirming the gate's open status on the dashboard. The CTF flag was displayed:

THM{s4v3_th3_d4t3_27_jun3}


Conclusion

By exploiting the unauthenticated Node-RED dashboard, I successfully bypassed the badge authentication system and triggered the gate to open. The CTF flag was successfully retrieved, marking the completion of the task.

Tools Used
Nmap for network scanning and enumeration.

Gobuster for directory enumeration on the web server.

curl for interacting with the gate API endpoint.

Node-RED for controlling the industrial gate system.

