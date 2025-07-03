Task 2: OSINT-2 – Open Source Intelligence Walkthrough

### Overview
In this task, the goal was to expand the investigation from Task 5 by identifying additional infrastructure and connections related to a phishing campaign targeting virelia-water.it.com. Through the use of OSINT techniques, I was able to gather valuable data, including subdomain identification, session token analysis, and DNS query analysis to confirm a possible uplink channel used by the attackers.

Target: virelia-water.it.com

Objective: Investigate the additional infrastructure linked to a phishing campaign by analyzing subdomains, HTTP traffic, DNS records, and other attack traces.

Phases of OSINT Collection

### Phase 1: Accessing the ICS Operator Console

I started the task by investigating the stage0.virelia-water.it.com subdomain, which hosted an ICS (Industrial Control System) operator console. Upon accessing it, I encountered an expired session token error. However, I continued my investigation by inspecting the page source, as attackers often leave traces behind even after their access has been invalidated.

Findings: The page source didn’t show any obvious flags, but it led me to further investigative steps.

### Phase 2: Examining HTTP Traffic

I then used the browser's developer tools to inspect the network traffic. One request caught my attention:

Request to: https://raw.githubusercontent.com/SanTzu/uplink-config/refs/heads/main/init.js

This file was hosted on GitHub and contained crucial information, including a session ID and a fallback DNS entry, which could potentially help in understanding the attacker’s setup.

### Phase 3: Extracting the Token

Inside the GitHub-hosted file, I noticed a base64-encoded string under the token field. I quickly decoded it to reveal the value "hello".

Decoded Value: hello

Although this wasn't a CTF flag, it was part of the attacker's token data and likely played a role in their infrastructure setup.

### Phase 4: Investigating Uplink Channel – DNS Query Analysis

In the next phase, I decided to investigate the DNS records related to the attacker's fallback channel. I queried the uplink-fallback.virelia-water.it.com subdomain for TXT records using the dig command.

Command used for DNS lookup:

```css
dig txt uplink-fallback.virelia-water.it.com
```

The output returned the following base64-encoded string:

```css
eyJzZXNzaW9uIjoiVC1DTjEtMTcyIiwiZmxhZyI6IlRITXt1cGxpbmtfY2hhbm5lbF9jb25maXJtZWR9In0=
```

After decoding this, it was a flag THM{uplink_channel_confirmed}.

### Conclusion

By performing a combination of subdomain enumeration, HTTP traffic analysis, and DNS query analysis, I confirmed the presence of an uplink channel used by the attackers for maintaining a persistent backdoor. This provided valuable insights into their tactics, techniques, and procedures (TTPs) for further exploitation.

### Tools Used:

GitHub: To identify hosted files and extract session-related information.

Browser Developer Tools: For inspecting network traffic and uncovering hidden requests.

Base64 Decoding: For decoding hidden information in the token field.

DNS Lookup: To query the uplink-fallback.virelia-water.it.com subdomain and reveal attack-related data.