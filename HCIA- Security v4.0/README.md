# 🛡️ HCIA-Security V4.0 — Huawei Certified ICT Associate: Security

> Course completion certificate proving foundational knowledge of network security: Huawei USG firewall configuration, security policies, NAT, high availability, intrusion prevention, user authentication, and encryption/PKI.

![Provider](https://img.shields.io/badge/Provider-Huawei%20ICT%20Academy-C7000B?style=for-the-badge&logo=huawei&logoColor=white)
![Level](https://img.shields.io/badge/Level-Associate%20(HCIA)-blue?style=for-the-badge)
![Domain](https://img.shields.io/badge/Domain-Network%20Security-0A7E8C?style=for-the-badge)
![Date](https://img.shields.io/badge/Issued-July%202026-informational?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-Earned-success?style=for-the-badge)


---

## 📋 Certificate Details

| Field | Value |
|-------|-------|
| **Certificate Name** | HCIA-Security V4.0 |
| **Issuing Organization** | Huawei ICT Academy |
| **Issue Date** | July 13, 2026 |
| **Credential ID** | EBG20260713000004 <!-- confirm against the certificate --> |
| **Certificate Type** | Course Completion |
| **Validity** | No expiry printed on this course certificate. *(The separate HCIA-Security exam credential, H12-711, is reported to be valid for 3 years. Confirm on Huawei Talent.)* |
| **Verification** | [Verify credential](https://REPLACE-WITH-YOUR-VERIFICATION-LINK) |
| **My Context** | IT Support professional transitioning into Cloud Networking |

> **📝 Transparency note:** This is a **course completion** certificate from the Huawei ICT Academy program. It is not the same as passing the proctored **H12-711 V4.0** exam.

---

## 📚 What I Learned

The V4.0 curriculum covers security concepts and standards, network fundamentals, threats and defenses, Huawei USG firewall technologies (security policies, NAT, hot standby, IPS, user management), and encryption/PKI. I've labelled each module's **🧠 Theory** and **🛠️ Hands-on** content separately.

<!-- Trim the hands-on bullets below to the labs you actually completed. -->

### Module 1 — Network Security Concepts & Standards

This module introduced why network security matters and the frameworks that guide it. It covered the security triad, common risk terminology, and how compliance standards shape enterprise security programs.

**🧠 Key Concepts**
- CIA triad: confidentiality, integrity, availability, plus authenticity and non-repudiation
- Asset, threat, vulnerability, and risk, and how they relate
- Defense-in-depth: layering controls across network, host, application, and data
- Security lifecycle models (PDCA, P2DR-style adaptive security)
- Standards and regulations: ISO/IEC 27001, China's Multi-Level Protection Scheme (MLPS 2.0), GDPR-style data protection
- Security evolution: from perimeter firewalls to zero-trust thinking and cloud-era threats

**🛠️ Hands-on Skills Gained**
- I can classify an incident by which CIA property it violates
- I can map a real-world control (firewall, MFA, backup) to the risk it mitigates
- I can explain compliance requirements in plain language to non-technical stakeholders

**Tools/Technologies:** ISO 27001, MLPS 2.0, risk assessment worksheets

---

### Module 2 — Network Fundamentals for Security

A refresher on the protocols that attackers exploit and defenders must understand. This module made sure I could read a packet and know where it could be abused.

**🧠 Key Concepts**
- OSI and TCP/IP models, and where each security control sits
- Ethernet frames, VLANs, and ARP behavior
- IPv4 addressing, subnetting, and ICMP
- TCP three-way handshake, flags, and UDP characteristics
- Routing basics: static routes and OSPF
- Application protocols: HTTP/HTTPS, DNS, FTP, Telnet vs. SSH
- ACLs (basic and advanced) as the precursor to firewall policies

**🛠️ Hands-on Skills Gained**
- I can subnet a network and plan security zones around the subnets
- I can trace a TCP session and identify normal versus abnormal flag patterns
- I can configure basic VRP interface IP addressing and static routes

**Tools/Technologies:** Huawei VRP CLI, eNSP, Wireshark, `ping`, `tracert`, `display ip routing-table`

```bash
<Huawei> system-view
[Huawei] interface GigabitEthernet 0/0/1
[Huawei-GigabitEthernet0/0/1] ip address 192.168.10.1 24
[Huawei] ip route-static 0.0.0.0 0 203.0.113.1
[Huawei] display ip routing-table
```

---

### Module 3 — Common Network Threats & Defense

This module catalogued the attack landscape and matched each attack class with a defense on the firewall.

**🧠 Key Concepts**
- Malware types: virus, worm, trojan, ransomware, botnet, APT
- Reconnaissance: IP sweep, port scanning
- Packet-based attacks: Land, Smurf, Ping of Death, Teardrop, IP spoofing
- Flood attacks: SYN, UDP, and ICMP flood, and DDoS at scale
- Layer-2 and local threats: ARP spoofing, MAC flooding
- Application-layer attacks: SQL injection, XSS, CC (HTTP flood) attacks
- Social engineering and phishing
- Defenses: SYN cookie/TCP proxy, source detection, traffic limiting, fingerprint learning

**🛠️ Hands-on Skills Gained**
- I can match a symptom (half-open connection spike, ARP table flapping) to an attack type
- I can enable attack-defense features on a USG and read the statistics
- I can prioritize mitigations by attack layer

**Tools/Technologies:** Huawei USG anti-DDoS/attack defense, Wireshark, `display firewall statistics defend`

---

### Module 4 — Firewall Fundamentals & Security Policies

The core of the course. I learned how a stateful firewall makes forwarding decisions using zones, sessions, and ordered policy rules.

**🧠 Key Concepts**
- Packet filtering vs. stateful inspection vs. proxy firewalls
- Security zones: Trust (85), DMZ (50), Untrust (5), Local (100), and custom zones
- Interzone and intrazone traffic direction (inbound/outbound by priority)
- Session table mechanics: first-packet check, then session-based fast forwarding
- Security policy matching: source/destination zone, address, user, application, service, time, action
- Top-down rule matching, and how the default policy denies unmatched traffic
- ASPF and server-map for multi-channel protocols (FTP, SIP)
- Policy best practices: least privilege, rule ordering, hit counts

**🛠️ Hands-on Skills Gained**
- I can assign interfaces to zones and build a three-zone (LAN/DMZ/WAN) design
- I can write, order, and troubleshoot security policy rules
- I can read the session table to confirm whether traffic is being allowed
- I can diagnose "traffic blocked" tickets using policy hit counts and session output

**Tools/Technologies:** Huawei USG (USG6000V in eNSP), web UI and CLI

```bash
[USG] firewall zone trust
[USG-zone-trust] set priority 85
[USG-zone-trust] add interface GigabitEthernet 1/0/1

[USG] security-policy
[USG-policy-security] rule name lan_to_wan
[USG-policy-security-rule-lan_to_wan] source-zone trust
[USG-policy-security-rule-lan_to_wan] destination-zone untrust
[USG-policy-security-rule-lan_to_wan] source-address 192.168.10.0 24
[USG-policy-security-rule-lan_to_wan] action permit

[USG] display security-policy rule all
[USG] display firewall session table verbose
```

---

### Module 5 — Network Address Translation (NAT)

This module covered how the firewall translates addresses to conserve IPv4 space and publish internal services.

**🧠 Key Concepts**
- Private vs. public addressing (RFC 1918) and why NAT exists
- Source NAT: NAPT (PAT), address-pool mode, Easy-IP, No-PAT
- Destination NAT and NAT Server (port mapping) for publishing DMZ services
- Bidirectional NAT and NAT hairpinning (internal users reaching an internal server via its public IP)
- NAT policy processing order relative to security policies
- Blackhole routes to prevent routing loops with NAT pools
- NAT ALG for protocols that embed IPs in payloads

**🛠️ Hands-on Skills Gained**
- I can configure outbound PAT for a LAN and verify translations in the session table
- I can publish an internal web server with NAT Server
- I can explain why a NAT rule works but traffic is still dropped (missing security policy)

**Tools/Technologies:** USG NAT policy, `nat address-group`, `nat server`, `display firewall session table`

```bash
[USG] nat address-group natpool 0
[USG-address-group-natpool] mode pat
[USG-address-group-natpool] section 0 203.0.113.10 203.0.113.20

[USG] nat-policy
[USG-policy-nat] rule name lan_snat
[USG-policy-nat-rule-lan_snat] source-zone trust
[USG-policy-nat-rule-lan_snat] destination-zone untrust
[USG-policy-nat-rule-lan_snat] action source-nat address-group natpool

[USG] nat server web protocol tcp global 203.0.113.5 80 inside 192.168.20.10 8080
```

---

### Module 6 — Firewall Hot Standby (High Availability)

This module covered eliminating the firewall as a single point of failure with active/standby and load-sharing designs.

**🧠 Key Concepts**
- Why hot standby: fast failover, session continuity
- VRRP and VGMP (VRRP Group Management Protocol) for coordinating state across interfaces
- HRP (Huawei Redundancy Protocol) for backing up configuration and session tables
- Heartbeat links and failover triggers (interface/link monitoring)
- Active/standby vs. active/active (load-sharing) deployments
- Upstream/downstream switch or router topologies for hot standby
- Preemption behavior and failover verification

**🛠️ Hands-on Skills Gained**
- I can build a two-firewall active/standby pair with a heartbeat link
- I can verify config and session sync between peers
- I can trigger and observe a failover, then confirm that user sessions survive

**Tools/Technologies:** VRRP, VGMP, HRP, `display hrp state`, `display vrrp brief`

```bash
[USG-A] interface GigabitEthernet 1/0/1
[USG-A-GigabitEthernet1/0/1] vrrp vrid 1 virtual-ip 203.0.113.1 active
[USG-A] hrp interface GigabitEthernet 1/0/3 remote 10.10.10.2
[USG-A] hrp enable
[USG-A] hrp mirror session enable
[USG-A] display hrp state
```

---

### Module 7 — Intrusion Prevention & Content Security

I learned how the firewall inspects payloads (not just headers) to catch exploits, malware, and risky web traffic.

**🧠 Key Concepts**
- IDS vs. IPS: detection versus inline blocking
- Signature-based detection, protocol anomaly detection, and signature-database updates
- IPS profiles: signature actions (alert, block, reset), exceptions, and false-positive tuning
- Deploying IPS via security policy profiles
- Antivirus scanning and URL/category filtering
- Recognizing risks: vulnerability exploitation, botnet C&C traffic, web attacks
- Logging and reporting for incident analysis

**🛠️ Hands-on Skills Gained**
- I can create an IPS profile and attach it to a security policy
- I can update signature databases and check the version
- I can read threat logs to identify the attacker, target, and blocked signature

**Tools/Technologies:** USG IPS/AV/URL filtering profiles, threat logs, signature database updates

---

### Module 8 — User Management & Authentication

This module covered identity-aware security policies, so rules are based on *who* the user is, not just their IP address.

**🧠 Key Concepts**
- AAA: authentication, authorization, accounting
- RADIUS vs. HWTACACS: transport, encryption scope, and typical use cases
- Local, server-based, and directory (LDAP/AD) authentication
- Authentication methods: Portal, SSO (agent/AD), and password-based
- User, user group, and security group organization
- Authentication policies and integration with security policies
- Admin access hardening: SSH over Telnet, role-based administrator accounts

**🛠️ Hands-on Skills Gained**
- I can integrate a firewall with a RADIUS server for user authentication
- I can write identity-based security policies (e.g., "Finance group can reach the ERP server")
- I can troubleshoot failed logins using AAA debug and log output

**Tools/Technologies:** RADIUS, HWTACACS, LDAP/Active Directory, Portal auth, SSH

---

### Module 9 — Encryption, PKI & Secure Communications

The cryptography module: the algorithms, how they combine into protocols, and how trust is established with certificates.

**🧠 Key Concepts**
- Symmetric encryption: DES, 3DES, AES (block modes and key lengths)
- Asymmetric encryption: RSA, ECC, Diffie-Hellman key exchange
- Hash functions and integrity: MD5, SHA-1/SHA-2, SM3, HMAC
- Digital signatures and digital envelopes (combining symmetric and asymmetric)
- PKI components: CA, RA, certificate repository, CRL/OCSP
- X.509 certificate structure and the certificate lifecycle (request, issue, renew, revoke)
- IPsec: AH vs. ESP, transport vs. tunnel mode, IKE SA and IPsec SA negotiation
- SSL/TLS handshake and HTTPS

**🛠️ Hands-on Skills Gained**
- I can explain the TLS handshake step by step, including where certificates are validated
- I can generate keys and inspect certificate fields and chains
- I can configure a site-to-site IPsec VPN (IKE proposal/peer, IPsec proposal/policy) and verify the SAs
- I can troubleshoot "phase 1 up, phase 2 down" style failures by comparing proposals and ACLs

**Tools/Technologies:** OpenSSL, Huawei USG IPsec, IKE, X.509, PKI

```bash
[USG] display ike sa
[USG] display ipsec sa brief
```

---

## 🎯 Skills Acquired

### Technical Skills
**Firewall & Perimeter Security**
- [x] Configure security zones, interfaces, and ordered security policies
- [x] Read and interpret firewall session tables
- [x] Configure source NAT, NAT Server, and hairpin NAT
- [x] Build active/standby firewall high availability (VRRP/VGMP/HRP)

**Threat Prevention**
- [x] Identify and classify common network and application-layer attacks
- [x] Apply attack defense, IPS, antivirus, and URL filtering profiles
- [x] Analyze threat logs and tune false positives

**Identity & Cryptography**
- [x] Implement AAA with RADIUS/HWTACACS and identity-based policies
- [x] Explain symmetric, asymmetric, hashing, and digital signature mechanisms
- [x] Describe PKI and validate X.509 certificate chains
- [x] Configure and verify IPsec VPN tunnels

**Networking Foundations**
- [x] Subnetting, VLANs, static routing, and OSPF basics
- [x] Packet analysis with Wireshark
- [x] Huawei VRP CLI navigation and `display` command troubleshooting

### Soft Skills
- [x] Structured troubleshooting (layer-by-layer isolation)
- [x] Translating security risk into business language
- [x] Documenting network changes and policy intent
- [x] Working from vendor documentation and lab guides

---

## 🧪 Practical Applications

How I apply this on my IT Support → Cloud Networking path:

| Scenario | How HCIA-Security helps |
|----------|------------------------|
| **"I can't reach the server" tickets** | Check zones, policy hits, and sessions before blaming the app or DNS |
| **Cloud security groups & NACLs** | Firewall zones and policy logic map directly onto AWS/Azure/Huawei Cloud security groups and network ACLs |
| **Site-to-site VPN to a cloud VPC/VNet** | IKE/IPsec knowledge lets me match phase 1/2 parameters and debug tunnel failures |
| **Publishing a cloud-hosted service** | NAT Server and DMZ design translate to load balancers, NAT gateways, and public IP mappings |
| **Resilient architecture** | HA concepts (failover, session sync, heartbeats) inform multi-AZ and redundant gateway design |
| **Identity-based access** | AAA/RADIUS concepts carry over to SSO, IAM policies, and VPN authentication |
| **Incident triage** | Recognizing flood, scan, and spoofing patterns speeds up escalation with useful evidence |
| **Certificate expiry incidents** | PKI knowledge helps me diagnose expired or untrusted certificates quickly |

---

## 🔗 Related Certifications & Next Steps

**Prerequisites**
- No formal prerequisites. Basic TCP/IP knowledge is strongly recommended (HCIA-Datacom or CCNA-level fundamentals).

**Recommended Next Certifications**

| Priority | Certification | Why |
|----------|---------------|-----|
| 1 | **HCIA-Datacom V1.0** (H12-811) | Strengthens the routing/switching foundation behind every security design |
| 2 | **HCIA-Cloud Service** (Huawei) | Bridges into cloud platforms and virtual networking |
| 3 | **HCIP-Security V4.0** (H12-725) | Deeper firewall, VPN, and threat-defense skills at Professional level |
| 4 | **CompTIA Security+** | Vendor-neutral security credential that's widely recognized by employers |
| 5 | **AWS Advanced Networking – Specialty / Azure AZ-700 / Google Professional Cloud Network Engineer** | Cloud networking target certifications |

**How this connects to my goal:** Cloud networking is traditional networking with security controls expressed as software. Zones, policies, NAT, VPN, and HA all reappear as security groups, route tables, gateways, and multi-AZ designs. This certificate gives me the underlying model, so I can learn cloud tooling faster.

---

## 📖 Study Resources

- [Huawei Talent Platform](https://e.huawei.com/en/talent/) — official courses, exam outlines, and certification info
- Huawei ICT Academy HCIA-Security V4.0 course materials and lab guide
- [Huawei Enterprise Support](https://support.huawei.com/enterprise/en/) — USG product documentation and CLI references
- **eNSP** with USG6000V firewall images for lab practice
- **Wireshark** and **OpenSSL** for packet and certificate analysis

**Exam reference (for anyone continuing to H12-711 V4.0):** third-party prep sites report roughly 60 questions in 90 minutes with a 600/1000 pass mark. Confirm current details on Huawei Talent before booking. Exam topics reportedly span security concepts, network basics, threats, firewall security policies, NAT, hot standby, IPS, user management, and encryption/PKI.

---

<sub>📅 README generated: September 19, 2026 ·</sub
