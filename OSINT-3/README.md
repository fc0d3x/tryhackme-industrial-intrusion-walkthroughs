OSINT 3 – Investigating a Signed PGP Message
Tags: #TryHackMe #OSINT #PGP #ThreatHunting #CTF #Infosec #DigitalForensics #CyberSecurity

Overview
In this task, the goal was to investigate a PGP-signed maintenance message that briefly appeared in Virelia’s internal OT alert system. The message was removed by corporate auditors fearing it could be malicious. My objective was to uncover more details hidden in the PGP signature or key metadata and extract the flag.

Phases of Investigation

### Phase 1: Locate the PGP-Signed Message

The first step was to search for any mention of the PGP-signed message in relevant platforms, such as pastebins, PDF file metadata, and archived internal documents. After a thorough search, I eventually found the PGP-signed message within an archived maintenance digest that was initially missed.

### Phase 2: Extracting the PGP Key

Once the message was located, I examined the signature block, which contained a PGP key ID. I used this key ID to fetch the key from a keyserver.

### Command used to retrieve the key:

```css
gpg --keyserver hkps://keyserver.ubuntu.com --recv-keys 88DEDE7B730513BD5EDD6D9FA4F0FEB084A311E5
```

The key was retrieved successfully, and I could now analyze the associated metadata.

### Phase 3: Analyzing the Key Metadata

After retrieving the PGP key, I analyzed the metadata. The key was signed under a suspicious alias and included a comment field. Hidden within this comment field was a subtle flag-like message:

Hidden Message in Metadata:

### THM{hope_this_k3y_doesnt_le4d_t0_m3}
This flag was intentionally embedded by the threat actor in the PGP key's comment field.

### Lessons Learned

PGP keys contain more than just encrypted content: Often, key signatures and associated metadata provide valuable clues, like hidden messages and aliases.

Malicious actors may use PGP signatures as covert communication methods. Even seemingly innocuous metadata may hold vital information about their infrastructure and operations.

Historical snapshots and removed content can sometimes hold key evidence during an OSINT investigation, emphasizing the importance of examining everything, including deleted or archived files.

Real-World Relevance
PGP has been used in historical cyber attacks for various purposes, such as:

Signing malware.

Signaling other actors.

Leaking sensitive data under a cover of legitimacy.

By examining keyserver metadata, you can uncover aliases, timestamps, IP leaks, and even organizational identifiers — valuable clues that can help in tracing back the attacker’s communications and infrastructure.

### Summary

This task combined traditional OSINT techniques with crypto-forensics. By thoroughly examining PGP metadata, I was able to uncover the flag hidden within the comment section of the key. This task reinforced the importance of detailed metadata analysis during OSINT investigations and highlighted how attackers sometimes leave clues in places we don't typically expect.

### Tools Used:

Keyserver (keyserver.ubuntu.com): For retrieving the PGP key.

GPG (GNU Privacy Guard): For interacting with and analyzing the PGP key.
