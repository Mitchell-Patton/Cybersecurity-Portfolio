# Attack Observation Report 3  
**High-volume web exploitation targeting CVE-2023-34133, CVE-2022-26134, and WordPress attacks**

## Summary
An attacker from **156.244.33.162** executed over **272,014 requests across 4 hours**, attempting multiple high-risk exploits including **SQL injection (CVE-2023-34133)** and **OGNL-based RCE in Confluence (CVE-2022-26134)**.

---

## Attack Goals
| Objective | Details |
|-----------|---------|
| Credential Extraction | SQLi targeting `password` and `users` tables |
| Remote Code Execution | OGNL exploit targeting Confluence |
| Web Shell Deployment | Malware targeting F5 BIG-IP, ColdFusion |
| CMS Attacks | WordPress brute-force and plugin fuzzing |

---

## MITRE ATT&CK Mapping
| Tactic | Technique |
|--------|-----------|
| Initial Access | Exploit Public-Facing Application (T1190) |
| Credential Access | Credentials from Database (T1552.002) |
| Execution | Command Injection (T1059) |
| Recon | Web Discovery and Enumeration (T1595) |

---

## Key IOCs
| Type | IOC |
|------|-----|
| IP Address | 156.244.33.162 |
| Confluence RCE Payload | `${@java.lang.Runtime@getRuntime()...}` |
| SQL Injection Identifier | `union select concat(id, ':', password)` |
| Endpoint Pattern | `/ws/msw/tenant/...` |

---

## Mitigation Strategies
- Patch vulnerable Confluence and SonicWall appliances  
- Enforce DMZ segmentation for public services  
- Use WAF with SQLi/OGNL detection signatures  
- Block automated scanners based on request frequency  
- Monitor outbound DNS lookup behavior (blind RCE detection)

---

📎 Complete PDF report is included in `/Reports/Attack_Observation_3.pdf`
