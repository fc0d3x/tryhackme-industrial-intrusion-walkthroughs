### OSINT 1 – Tracing a Phishing Campaign

Tags: #TryHackMe #OSINT #Phishing #CyberThreatIntel #DigitalForensics #CTF #Infosec

Overview
In this task, the goal was to investigate a phishing attack that occurred three months ago. The threat actor reportedly hijacked the domain virelia-water.it.com and used it to host their infrastructure during the campaign. My objective was to identify any subdomains tied to virelia-water.it.com and extract critical infrastructure details.

Phases of OSINT Collection

### Phase 1: Recon via Subdomain Enumeration
The first step in the investigation was to enumerate subdomains of the target domain. For this, I used popular web-based tools like Shodan, DNSDumpster, and Pentest-Tools to quickly identify any subdomains associated with the target domain.

One of the most interesting findings was the subdomain:

54484d7b5375357373737d.virelia-water.it.com.

The subdomain’s odd format stood out immediately—it appeared to be a hexadecimal string, which is not typical for most domain names.

### Phase 2: Decoding the Hex String

A quick hexadecimal conversion of this string revealed that it was the CTF flag I was looking for. This type of obfuscation is common in red-teaming exercises, where hex strings or encoded data are used to hide information in plain sight.

Decoded Flag:

```css
THM{Su5sss}
```

This flag was found using a simple decoding technique and was critical to solving the task.

### Tools Used:

Shodan: A search engine for internet-connected devices that helped find exposed services tied to subdomains.

DNSDumpster: A DNS enumeration tool that helped uncover subdomains associated with the target domain.

Pentest-Tools Subdomain Finder: A web-based subdomain enumeration tool used to identify subdomains of virelia-water.it.com.


### Conclusion

The task involved using OSINT tools and techniques like subdomain enumeration and hexadecimal decoding to uncover hidden infrastructure used in a phishing campaign. By identifying the obfuscated hex string and decoding it, I successfully retrieved the flag.

Tools Used:

Shodan for network reconnaissance and discovering exposed subdomains.

DNSDumpster for DNS enumeration and discovering subdomains.

Pentest-Tools Subdomain Finder for scanning for subdomains tied to the target domain.

Hexadecimal decoding to reveal the hidden flag.