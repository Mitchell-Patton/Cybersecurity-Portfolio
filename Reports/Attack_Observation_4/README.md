# Attack Observation Report 4  
**PHPUnit CVE-2017-9841 probing and attempted web shell upload**

## Summary
An attacker from **62.171.135.11** sent over **1,081 requests in 16 seconds**, using a custom user-agent (`libredtail-http`) to probe for exposed `/vendor/phpunit` paths. This activity aligns with discovery attempts for **CVE-2017-9841**, which allows remote PHP code execution using improperly secured PHPUnit installations.

---

## Intended Exploitation
| Vulnerability | Details |
|---------------|---------|
| CVE-2017-9841 | Remote PHP Code Execution (PHPUnit eval-stdin.php) |
| Malware Association | Androxgh0st botnet deployment via PHP web shell |
| Goal | Web shell upload, C2 payload deployment, RCE |

---

## MITRE ATT&CK Mapping
| Tactic | Technique |
|--------|-----------|
| Initial Access | Exploit Public-Facing Application (T1190) |
| Execution | Server-Side Code Execution |
| Discovery | File/Dir Enumeration (T1083) |

---

## Indicators of Compromise
| Type | Value |
|------|-------|
| IP | 62.171.135.11 |
| Malicious Paths | `/vendor/phpunit/phpunit/src/Util/PHP/eval-stdin.php` |
| Suspicious Headers | Content-Length: 33 |
| Behavior | 903 HTTP 200 responses, repetitive scanning |

---

## Mitigation Strategies
- Block public access to `/vendor/` directories  
- Patch/remove PHPUnit from production servers  
- Enforce WAF rules for malicious PHP patterns  
- Use sandboxing and application isolation  
- Monitor for automated scanner fingerprints (CL=33, libredtail-http)

---

📎 Full PDF report available in `/Reports/Attack_Observation_4_final.pdf`
