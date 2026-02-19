---
title: "Passive Reconnaissance Lab Challenges – TryHackMe Walkthrough"
date: 2026-02-19 09:30:00 +0000
categories: [Cybersecurity, TryHackMe]
tags: [passive reconnaissance, osint, whois, dns, shodan, dnsdumpster, cybersecurity labs, threat intelligence]
---

## Introduction

In this post, I’m sharing my experience completing the Passive Reconnaissance module on TryHackMe. This lab focused on gathering intelligence without directly interacting with the target systems — a crucial skill in the early stages of penetration testing and threat intelligence.

Passive reconnaissance allows security professionals to collect valuable information while remaining undetected.

---

## Challenge 1: Social Media Reconnaissance

### Scenario
You visit the Facebook page of the target company to gather employee names.

### Classification
This is **Passive Reconnaissance** because it involves reviewing publicly available information without interacting with the target’s infrastructure.

### Key Takeaways
- Passive reconnaissance relies on publicly accessible information.
- Social media platforms are valuable OSINT sources.
- No packets are sent to the target during this process.

---

## Challenge 2: Ping Test

### Scenario
You ping the IP address of the company webserver to check if ICMP traffic is blocked.

### Classification
This is **Active Reconnaissance** because it involves direct interaction with the target’s system.

### Key Takeaways
- Sending ICMP echo requests constitutes active reconnaissance.
- Even minimal interaction can be logged or detected.
- Active techniques carry a higher risk of detection.

---

## Challenge 3: Social Engineering

### Scenario
You attempt to extract information from an IT administrator during a social event.

### Classification
This is **Active Reconnaissance** because it involves direct engagement with someone connected to the target organization.

### Key Takeaways
- Social engineering is considered active reconnaissance.
- Direct interaction, whether online or offline, qualifies as active engagement.
- Human intelligence gathering is a powerful but detectable method.

---

## Challenge 4: WHOIS Domain Registration Date

### Objective
Determine when tryhackme.com was registered.

### Method Used

```bash
whois tryhackme.com
```

### Key Takeaways

- WHOIS queries operate over TCP port 43.
- The creation date is listed in the domain registration details.
- Many domains use privacy services to redact personal information.

---

## Challenge 5: WHOIS Domain Registrar

### Objective

Identify the registrar of tryhackme.com.

### Method Used

```bash
whois tryhackme.com
```

### Key Takeaways

- The registrar is the company responsible for domain registration.
- Registrar information may be useful in social engineering scenarios.
- WHOIS data reveals domain management details.

---

## Challenge 6: WHOIS Name Servers

### Objective

Identify which company manages the name servers.

### Findings

The name servers pointed to Cloudflare.

### Key Takeaways

- Name servers manage DNS resolution.
- DNS providers often offer CDN and security services.
- DNS information reveals infrastructure dependencies.

---

## Challenge 7: DNS TXT Record Enumeration

### Objective

Retrieve the TXT record from thmlabs.com.

### Method Used

```bash
nslookup -type=txt thmlabs.com
```

### Key Takeaways

- TXT records store arbitrary text such as SPF records or verification strings.
- DNS can contain hidden flags in CTF-style challenges.
- The `-type` parameter specifies which DNS record to query.

---

## Challenge 8: Subdomain Discovery with DNSDumpster

### Objective

Identify additional subdomains for tryhackme.com.

### Method

Used the DNSDumpster online service to enumerate subdomains.

### Findings

Discovered additional subdomains including `remote`.

### Key Takeaways

- Subdomains may expose administrative portals or remote services.
- Online OSINT tools enhance manual DNS enumeration.
- Visual mapping tools help understand domain relationships.

---

## Challenge 9: Shodan – Top Country for Apache Servers

### Objective

Identify the country with the most publicly accessible Apache servers.

### Method

Searched for "Apache" on Shodan and reviewed country statistics.

### Key Takeaways

- The United States hosts the highest number of Apache servers.
- Shodan indexes internet-facing services.
- Geographic data is valuable in threat intelligence analysis.

---

## Challenge 10: Shodan – Third Most Common Apache Port

### Objective

Identify the third most common port used by Apache servers.

### Findings

Port 8080 was identified as the third most common port.

### Key Takeaways

- Apache commonly runs on ports 80 and 443.
- Port 8080 is often used as an alternative HTTP port.
- Port statistics reveal common deployment patterns.

---

## Challenge 11: Shodan – Most Common Port for nginx

### Objective

Identify the most common port used for nginx.

### Findings

Port 80 was identified as the most common.

### Key Takeaways

- nginx primarily serves HTTP traffic on port 80.
- HTTPS commonly runs on port 443.
- Understanding default ports aids in reconnaissance efforts.

---

## Overall Lessons Learned

This module provided hands-on experience with:

- WHOIS enumeration
- DNS record analysis
- Subdomain discovery
- Internet-wide reconnaissance using Shodan
- Distinguishing between passive and active reconnaissance

The most important takeaway is that a significant amount of intelligence can be gathered without directly interacting with a target.

Passive reconnaissance forms the foundation of any security assessment. Mastering these techniques enables security professionals to build a detailed understanding of a target’s external footprint while minimizing detection risk.

---

## Final Thoughts

Completing the Passive Reconnaissance module strengthened my understanding of OSINT techniques and real-world reconnaissance workflows. It reinforced the importance of stealth during the information-gathering phase and demonstrated how publicly available data can reveal critical insights about an organization’s infrastructure.

This experience has further solidified my interest in threat intelligence and ethical hacking.

*Completed as part of the TryHackMe Passive Reconnaissance module.*
