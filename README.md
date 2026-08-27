


<h1 align="center">
  <span style="color:#00E5FF;">🔐 NETWORK WALKS</span>
  <br>
  <span style="color:#8B5CF6;">Cybersecurity Internship</span>
</h1>

<p align="center">
  <img src="https://img.shields.io/badge/⚡_CYBERSECURITY-00E5FF?style=for-the-badge&labelColor=0D1117">
  <img src="https://img.shields.io/badge/🔎_RECONNAISSANCE-8B5CF6?style=for-the-badge&labelColor=0D1117">
  <img src="https://img.shields.io/badge/🌐_NETWORK_DISCOVERY-6366F1?style=for-the-badge&labelColor=0D1117">
  <img src="https://img.shields.io/badge/✓_COMPLETED-22C55E?style=for-the-badge&labelColor=0D1117">
</p>

<p align="center">
  <b>Hands-on Cybersecurity Internship Work</b>
  <br>
  <sub>Footprinting • Reconnaissance • DNS Enumeration • Web Fingerprinting • Network Discovery</sub>
</p>



## Module 1: Footprinting & Reconnaissance


This repository contains my practical cybersecurity work completed
during my **Cybersecurity Internship at Network Walks**.

The work documented here covers reconnaissance, information
gathering, DNS enumeration, web technology identification,
WAF detection, domain information gathering, and network host
discovery.

# 📋 Pentester Information


| Field               | Details                                                         |
| ------------------- | --------------------------------------------------------------- |
| Assessment Type     | Reconnaissance & Information Gathering                          |
| Target              | networkwalks.com                                                |
| Testing Environment | Authorized Internship Assessment                                |
| Tools Used          | cURL, DNSRecon, Nslookup, WhatWeb, WAFW00F, WHOIS               |
| Primary Focus       | Domain, DNS, web technology and security-control identification |
| Assessment Scope    | Information gathering only                                      |
| Tester              | Humaira Akram Sheikh                                            |
| Organization        | Network Walks                                                   |

# ⚠️ Liability Disclaimer

This repository documents work completed for **educational and
authorized internship purposes** as part of my Cybersecurity
Internship at Network Walks.

The activities described were limited to the intended assessment
scope and focused on reconnaissance, information gathering, and
network host discovery.

The findings represent observations obtained during the assessment
period and may change as infrastructure, software, configurations,
or security controls are updated.

The information documented in this repository should not be
interpreted as confirmation of vulnerabilities unless explicitly
stated and verified through appropriate authorized testing.

The author assumes no responsibility for misuse of the information
contained in this repository.

Any reproduction, modification, or application of these techniques
against systems or networks without proper authorization is the
sole responsibility of the individual performing such activity.

**Security testing should only be performed against systems and
networks for which explicit authorization has been obtained.**

---



# 📌 Module 1 — Footprinting & Reconnaissance

## 🎯 Objective

The objective of Module 1 was to perform basic footprinting and
reconnaissance against the authorized target:

```text
networkwalks.com
````

The assessment focused on collecting information about:

* Domain registration
* DNS infrastructure
* IP address resolution
* HTTP responses and headers
* Web technologies
* Web application security controls

---

# 🛠️ Tools Used

| # | Tool     | Purpose                                |
| - | -------- | -------------------------------------- |
| 1 | cURL     | Analyze HTTP responses and headers     |
| 2 | DNSRecon | Enumerate DNS records                  |
| 3 | Nslookup | Verify DNS resolution                  |
| 4 | WhatWeb  | Identify web technologies              |
| 5 | WAFW00F  | Detect Web Application Firewalls       |
| 6 | WHOIS    | Gather domain registration information |

---

# 1️⃣ cURL

## Why was cURL used?

cURL was used to inspect the HTTP response returned by the target
website and examine its HTTP response headers.

## Command

```bash
curl -I https://networkwalks.com
```

## Findings

The response returned:

```text
HTTP/2 200
server: Apache
content-type: text/html; charset=UTF-8
```

Other observations included:

* WordPress-related headers
* Cookies
* Security-related HTTP headers
* WordPress REST API reference
* HTTPS response

### Key Finding

The website was reachable and returned:

```text
HTTP/2 200 OK
```

This confirmed that the target website was accessible during
the assessment.

---

# 2️⃣ DNSRecon

## Why was DNSRecon used?

DNSRecon was used to enumerate DNS records associated with the
target domain.

It helped identify information about the domain's DNS
infrastructure and associated services.

## Command

```bash
dnsrecon -d networkwalks.com
```

## Findings

The enumeration identified:

* SOA record
* NS record
* A record
* MX record
* TXT records
* SRV records
* SPF configuration

### Important Results

```text
networkwalks.com → 192.232.216.135
```

SOA:

```text
ns6135.hostgator.com
```

Name Server:

```text
ns6135.hostgator.com
```

Mail Server:

```text
mail.networkwalks.com → 192.232.216.135
```

An SPF TXT record was also identified.

The tool also reported:

```text
ERROR No answer for DNSSEC query for networkwalks.com
```

---

# 3️⃣ Nslookup

## Why was Nslookup used?

Nslookup was used to independently verify the IP address
associated with the target domain.

## Command

```bash
nslookup networkwalks.com
```

## Finding

```text
Name: networkwalks.com
Address: 192.232.216.135
```

### Key Finding

The domain resolved to:

```text
192.232.216.135
```

This confirmed the IP address identified during DNS enumeration.

---

# 4️⃣ WhatWeb

## Why was WhatWeb used?

WhatWeb was used to perform web technology fingerprinting.

It helped identify the technologies, frameworks, CMS, server
software, and other components used by the website.

## Command

```bash
whatweb networkwalks.com
```

## Findings

The scan identified:

* Apache
* Bootstrap 7.1
* WordPress 7.1
* WordPress Download Manager 3.3.58
* jQuery 3.7.1
* Google Tag Manager
* HTML5
* Open Graph Protocol
* Website cookies
* JavaScript components

### Website Title

```text
Networkwalks Academy
```

### Key Finding

The website was identified as a WordPress-based website
running on Apache.

---

# 5️⃣ WAFW00F

## Why was WAFW00F used?

WAFW00F was used to determine whether a Web Application Firewall
was protecting the target website.

Identifying a WAF provides information about the security controls
placed in front of a web application.

## Command

```bash
wafw00f networkwalks.com
```

## Finding

The tool reported:

```text
The site is behind ModSecurity (SpiderLabs) WAF.
```

### Key Finding

A:

```text
ModSecurity (SpiderLabs)
```

Web Application Firewall was detected.

---

# 6️⃣ WHOIS

## Why was WHOIS used?

WHOIS was used to gather publicly available domain registration
information.

It provided information about the registrar, domain dates,
name servers, domain status, and registration privacy.

## Command

```bash
whois networkwalks.com
```

## Findings

| Information   | Result                |
| ------------- | --------------------- |
| Domain        | networkwalks.com      |
| Registrar     | GoDaddy.com, LLC      |
| Creation Date | November 6, 2019      |
| Expiry Date   | November 6, 2027      |
| Name Server   | NS6135.HOSTGATOR.COM  |
| Name Server   | NS6136.HOSTGATOR.COM  |
| DNSSEC        | Unsigned              |
| Registrant    | Registration Private  |
| Organization  | Domains By Proxy, LLC |

### Domain Status

```text
clientDeleteProhibited
clientRenewProhibited
clientTransferProhibited
clientUpdateProhibited
```

### Key Finding

The domain registration information was privacy protected
and GoDaddy was identified as the registrar.

---

# 📊 Module 1 — Findings Summary

| Finding              | Result                   |
| -------------------- | ------------------------ |
| Website Availability | HTTP 200 OK              |
| Web Server           | Apache                   |
| CMS                  | WordPress 7.1            |
| Website IP           | 192.232.216.135          |
| WAF                  | ModSecurity (SpiderLabs) |
| DNSSEC               | Unsigned                 |
| HTTP → HTTPS         | 301 Redirect             |
| Registrar            | GoDaddy                  |
| WHOIS Privacy        | Enabled                  |

---

# 🖼️ Module 1 — Evidence

## cURL

<img src="/screenshots/results-of-curl-I.png" alt="cURL Results" width="800">

---

## DNSRecon

<img src="./screenshots/results-of-dns-recon.png" alt="DNSRecon Results" width="800">

---

## Nslookup

<img src="./screenshots/Results-of-nslookup.png" alt="Nslookup Results" width="800">

---

## WAFW00F

<img src="./screenshots/results-of-wafw00f.png" alt="WAFW00F Results" width="800">

---

## WhatWeb

<img src="./screenshots/results-of-whatweb.png" alt="WhatWeb Results" width="800">

---

## WHOIS

<img src="./screenshots/results-of-whois.png" alt="WHOIS Results" width="800">

---

# 🌐 Module 1 — Reconnaissance Flow

```text
                    Target
              networkwalks.com
                     │
          ┌──────────┴──────────┐
          │                     │
        WHOIS                DNSRecon
          │                     │
          │              DNS Information
          │                     │
          └──────────┬──────────┘
                     │
                  Nslookup
                     │
                IP Resolution
                     │
             ┌───────┴────────┐
             │                │
            cURL           WhatWeb
             │                │
        HTTP Headers    Technologies
             │                │
             └───────┬────────┘
                     │
                  WAFW00F
                     │
               WAF Detection
```

---

# 🖥️ Module 5 — Network Discovery with Zenmap

## 🎯 Objective

In Module 5, **Zenmap**, the graphical interface for Nmap, was used
to perform a **Ping Scan / Host Discovery** on the local network.

The purpose of the scan was to identify active hosts within the
network.

The scan focused on host discovery rather than detailed port,
service, or vulnerability enumeration.

---

# 🛠️ Scan Details

| Field             | Details                    |
| ----------------- | -------------------------- |
| Tool              | Zenmap / Nmap 7.991        |
| Scan Type         | Ping Scan / Host Discovery |
| Target Range      | 192.168.1.0/24             |
| Addresses Scanned | 256                        |
| Hosts Detected    | 7                          |
| Scan Duration     | 3.87 seconds               |

---

# 🔎 Module 5 — Zenmap Findings

The Ping Scan identified **7 hosts that were up**.

| IP Address    | Status              | MAC Address       | Vendor                   |
| ------------- | ------------------- | ----------------- | ------------------------ |
| 192.168.1.1   | Up — 0.012s latency | 98:3F:60:2B:72:60 | Huawei Technologies      |
| 192.168.1.13  | Up — 0.063s latency | F2:2A:E7:F9:2C:9B | Unknown                  |
| 192.168.1.16  | Up — 0.026s latency | 50:21:EC:13:89:E6 | Huawei Device            |
| 192.168.1.22  | Up — 0.032s latency | 04:E2:29:89:27:B8 | Qingdao Haier Technology |
| 192.168.1.147 | Up — 0.10s latency  | 6A:B1:75:E2:03:E4 | Unknown                  |
| 192.168.1.254 | Up — 0.022s latency | 88:76:B9:0C:6A:45 | D-Link                   |
| 192.168.1.126 | Up                  | Not reported      | Not reported             |

---

# 📋 Raw Zenmap Result

The scan was completed with:

```text
Starting Nmap 7.991 ( https://nmap.org )
at 2026-08-27 22:45 +0500
```

The final result reported:

```text
Nmap done: 256 IP addresses (7 hosts up) scanned in 3.87 seconds
```

---

# 🔎 Module 5 — Additional Findings

The scan produced the following observations:

* **256 IP addresses** were scanned.
* **7 hosts were identified as active.**
* Several MAC addresses were associated with device manufacturers.
* Huawei Technologies was identified.
* Huawei Device was identified.
* Qingdao Haier Technology was identified.
* D-Link was identified.
* Two devices returned an **Unknown** vendor.
* One host did not have MAC/vendor information reported in the
  provided output.
* The scan provided information about active hosts on the network.
* The scan did not determine which ports were open.
* The scan did not identify running services.
* The scan did not establish whether any discovered host was
  vulnerable.

---

# 🌐 Module 5 — Network Information

## IP Address

<img src="./screenshots/ip-address.png" alt="IP Address" width="800">

---

## Network Topology

<img src="./screenshots/topology.png" alt="Network Topology" width="800">

---

## Zenmap Results

<img src="./screenshots/zenmap-results.png" alt="Zenmap Results" width="800">

---

# 📊 Module 5 — Findings Summary

| Finding              | Result              |
| -------------------- | ------------------- |
| Network Range        | 192.168.1.0/24      |
| Addresses Scanned    | 256                 |
| Active Hosts         | 7                   |
| Scan Type            | Ping Scan           |
| Tool                 | Zenmap / Nmap 7.991 |
| Scan Duration        | 3.87 seconds        |
| Huawei Devices       | Identified          |
| D-Link Device        | Identified          |
| Qingdao Haier Device | Identified          |
| Unknown Vendors      | 2                   |

---

# 💡 Module 5 — Interpretation

The Ping Scan provided an initial map of the local network by
identifying responsive hosts within the scanned address range.

The IP addresses, MAC addresses, latency values, and vendor
information provided an initial understanding of the devices
present on the network.

Because this was a **Ping Scan / Host Discovery scan**, the results
should not be interpreted as a port scan or vulnerability
assessment.

---

# 🧠 Key Learning Outcomes

Through these practical exercises, I gained hands-on experience
with:

* DNS enumeration
* Domain reconnaissance
* HTTP header analysis
* Web technology fingerprinting
* WAF detection
* WHOIS reconnaissance
* IP address resolution
* Network host discovery
* MAC address identification
* Vendor identification
* Basic network mapping

The main takeaway from these modules was that reconnaissance is
not simply about running commands and collecting output.

The real value comes from interpreting information from different
tools and connecting individual findings to build a clearer picture
of the target environment.

---


# 👩‍💻 Author

**Humaira Akram Sheikh**

Cybersecurity Intern
**Network Walks**

---

# 📚 Internship Progress

| Module   | Topic                         | Status      |
| -------- | ----------------------------- | ----------- |
| Module 1 | Footprinting & Reconnaissance | ✅ Completed |
| Module 5 | Network Discovery — Zenmap    | ✅ Completed |

---

⭐ **Documenting my hands-on cybersecurity learning and practical
experience throughout my internship at Network Walks.**


