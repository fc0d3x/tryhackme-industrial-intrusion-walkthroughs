# Under Construction (Boot2Root) — TryHackMe

This repository contains the walkthrough and solutions for the "Under Construction" Boot2Root challenge from TryHackMe.

## Overview

The "Under Construction" Boot2Root challenge involves a series of security challenges, including reconnaissance, web enumeration, and privilege escalation, with the objective of bypassing badge authentication to gain root access to a target machine.

## Target Machine Details

IP Address: 10.10.20.251

Challenge Type: Boot2Root, Privilege Escalation, Credential Reuse

Tags: #TryHackMe, #Boot2Root, #PrivilegeEscalation, #CTF, #Linux

## Objectives

Bypass badge authentication and gain access to the target system.

Perform reconnaissance to identify open ports and attack vectors.

Exploit vulnerabilities such as Local File Inclusion (LFI) and improperly configured SSH keys.

Escalate privileges and capture the root flag.

## Steps Taken
### Phase 1: Initial Reconnaissance & Port Scan

A comprehensive port scan was performed using Nmap to identify open ports on the target machine.

### Phase 2: Web Enumeration & LFI Discovery

Discovered Local File Inclusion (LFI) vulnerability through the web app by inspecting the page source and manipulating URL parameters.

Exploiting LFI allowed the discovery of critical system information, including user accounts (dev, ubuntu).

### Phase 3: Directory Fuzzing & Key Discovery

### Using a web fuzzer (ffuf), a /keys directory was found containing an unprotected SSH private key (key_09), enabling SSH access to the system.

### Phase 4: Gaining Initial Foothold

With the private SSH key, direct access was gained as the dev user, and the user flag was retrieved.

### Phase 5: Privilege Escalation

Privilege escalation was achieved by exploiting misconfigured sudo permissions, which allowed the dev user to run vi as root without a password prompt.

Using vi to execute a bash shell as root allowed access to the root directory and retrieval of the root flag.

## Final Flags:

User Flag: THM{nic3_j0b_You_got_it_w00tW00t}

Root Flag: THM{you_got_it_welldoneeee}

## Conclusion

By completing reconnaissance, exploitation, and privilege escalation steps, the challenge was successfully completed. The main steps involved exploiting LFI, using SSH keys for access, and leveraging sudo misconfigurations for privilege escalation to gain root access.