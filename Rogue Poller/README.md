# TryHackMe — Rogue Poller: Modbus Network Capture Analysis
## Overview

This repository contains the solution for the Rogue Poller challenge from TryHackMe, which focuses on analyzing Modbus traffic in a network capture (PCAP file). The task involves identifying what data was accessed by an attacker who was polling Modbus registers via TCP/502. The challenge highlights the importance of securing industrial control systems (ICS) and understanding vulnerabilities in Modbus, a widely used industrial protocol.

## Challenge Breakdown
### Scenario

An attacker has gained access to an Operational Technology (OT) network and is polling Modbus registers. Your task is to analyze the provided network traffic capture (rogue-poller-1750969333044.pcapng) and extract the accessed data, which includes important register values and possibly a hidden flag.

#### Steps

TShark Modbus Traffic Filtering

The first step was to isolate the Modbus traffic from the provided PCAP file using TShark, a command-line version of Wireshark. This filtering allowed us to focus on the Modbus interactions by isolating packets based on the relevant port (TCP/502) and extracting key fields like source and destination IP addresses, function codes, and reference numbers.

Extracting Response Register Values

The next step was to focus on the response packets, which contained the actual Modbus register values. We filtered these packets further by source IP to identify the specific registers of interest.

Identifying Non-Zero Register Values

Among the filtered response data, several non-zero register values were identified as noteworthy. These values likely contained significant information or the hidden flag. A careful analysis of these values was performed to identify which ones stood out.

Decoding the Flag

After identifying the relevant register values, these were converted into hexadecimal and analyzed, revealing the hidden flag:

THM{Industrial_registers}

## Tools and Techniques

TShark: Used for filtering and analyzing Modbus traffic from the PCAP file.

Modbus Protocol: Focused on analyzing Modbus register values, an industrial protocol used for communication with PLCs.

## Key Takeaways

Modbus Vulnerabilities: Modbus lacks encryption or authentication by default, making it highly vulnerable when exposed to a network. This highlights the importance of securing industrial control systems (ICS).

TShark: A powerful tool for network traffic analysis, useful in extracting and automating data for forensic analysis.

Memory Access in ICS: Modbus read requests, when intercepted, can expose sensitive data such as flags, configuration secrets, and more.