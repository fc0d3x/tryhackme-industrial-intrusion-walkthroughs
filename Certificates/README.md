# 🎯 TryHackMe - Industrial Intrusion CTF | My Solo Journey

Welcome to the documentation of my journey through the TryHackMe Industrial Intrusion CTF — a deep dive into real-world cybersecurity challenges blending ICS (Industrial Control Systems), OSINT, network forensics, web exploitation, and reverse engineering.

This challenge wasn’t just about solving technical problems — it was about proving something to myself.

✅ I completed 8 complex CTF tasks entirely on my own — no walkthroughs, no hints, no help.

And I’m damn proud of it.

## 🌟 Why This CTF Mattered to Me

This is only my second CTF ever, but it was the first one where I pushed through everything solo. No handholding. Just me, the challenges, and the grind.

Each task forced me to grow — to think differently, to research harder, and to execute more precisely. I went beyond just following tools and techniques: I understood the logic, identified patterns, and broke systems open by connecting the dots myself.

## 🔍 What I Learned

Here’s a snapshot of the areas I tackled and the skills I developed:

### 🔓 Offensive Security

Bypassed badge authentication mechanisms in OT systems.

Exploited web vulnerabilities like LFI, exposed dashboards, and credential reuse.

Gained root access via privilege escalation (e.g., insecure sudo configurations).

### 🧠 OSINT & Threat Intelligence

Investigated phishing infrastructure using tools like Shodan, DNSDumpster, and GitHub recon.

Decrypted and decoded obfuscated data in subdomains, DNS TXT records, and PGP metadata.

### 📡 Network & Protocol Analysis

Analyzed Modbus traffic from PCAPs to extract meaningful data.

Used TShark to dissect OT communications and identify sabotage indicators.

### 🔐 Cryptography

Performed known plaintext attacks on AES-GCM encrypted telemetry packets.

Wrote Python scripts to extract and decrypt binary data payloads.

## 🧰 Tools & Techniques Used

nmap, tshark, ffuf, gobuster, dig

Python scripting for decryption and automation

Wireshark, Shodan, DNS lookup tools

gpg, Base64, Hex decoding

OSINT platforms + manual investigation

## 🧩 Highlights from My CTF Experience

✅ Opened a gate by exploiting an unauthenticated Node-RED dashboard

✅ Found and used leaked SSH keys to gain system access

✅ Escalated to root via sudo misconfigurations

✅ Traced attacker infrastructure via GitHub and DNS

✅ Decoded telemetry sabotage commands hidden in encrypted packets

✅ Identified PGP key metadata used for covert signaling

✅ Extracted flags from Modbus registers through traffic analysis

## 🧠 Final Thoughts

This CTF wasn’t just a checklist of solved tasks — it was a mental battle. There were moments of doubt, frustration, and pure confusion. But I kept showing up. I kept solving.

And every breakthrough felt earned.

I didn't just complete challenges — I built skill, confidence, and momentum.

If you're looking at this and wondering if you can do it — you can. But only if you're willing to push through the discomfort and do the work. Alone.

## 🚀 What's Next?

I'm not stopping here.

This experience has fueled my drive to:

Tackle more advanced CTFs and red team scenarios

Deepen my knowledge in ICS security and exploit development

Share my learnings and support others in the community

Thanks for reading — now go hack something (ethically).