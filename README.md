
Incident Summary

During analysis of a simulated environment, I identified a critical security misconfiguration that allowed unauthorized access via anonymous FTP, leading to credential exposure, password cracking, and full system compromise (root).

This exercise mirrors a real-world incident involving poor access controls, weak encryption practices, and credential reuse.

Initial Detection & Enumeration

As part of initial reconnaissance, I performed network enumeration to identify exposed services.

Findings:

FTP service exposed with anonymous authentication enabled

SSH service accessible externally

From a SOC perspective, anonymous FTP access represents a high-risk misconfiguration and should immediately trigger investigation due to its history of data leakage and abuse.

Evidence Collection & Analysis

While reviewing accessible directories on the FTP service, I identified sensitive user-related files located in a world-readable directory. These included encrypted backups and cryptographic material.

Security Impact:

Sensitive data stored in insecure locations

Lack of proper file permissions

No monitoring or alerting on unauthorized file access

Credential Exposure & Cryptographic Weakness

Further analysis revealed a private PGP key protected by a weak passphrase.

Using offline analysis techniques, the passphrase was cracked, allowing decryption of a backup file containing hashed credentials, including the root account.

From a SOC standpoint, this represents:

Weak encryption key management

Poor password hygiene

Inadequate separation of sensitive system files

Privilege Escalation & Impact

Cracked credentials were reused to authenticate via SSH as the root user, resulting in full system compromise.

Confirmed Impact:

Unauthorized root access

Total loss of confidentiality, integrity, and availability

Potential lateral movement risk if system were part of a larger network

Root Cause Analysis

The compromise was enabled by a combination of:

Anonymous FTP access enabled

Insecure file permissions

Weak cryptographic passphrases

Credential reuse

Lack of monitoring and alerting

Defensive & SOC Takeaways

This scenario highlights several key SOC lessons:

Service Hardening: Anonymous FTP should be disabled unless explicitly required.

Access Controls: Sensitive files must follow least privilege principles.

Credential Security: Strong passphrases and key rotation are critical.

Monitoring: File access and authentication attempts should be logged and monitored.

Detection Opportunities: Failed login attempts, unusual file access, and abnormal FTP usage should trigger alerts.

How This Applies to a SOC Role

This exercise strengthened my ability to:

Identify high-risk misconfigurations

Investigate exposed services and access patterns

Analyze credential exposure scenarios

Communicate technical findings clearly

Think in terms of impact, detection, and remediation, not just exploitation

Tools & Skills Demonstrated

Network enumeration and service analysis

Logically mapping attack paths

Understanding credential compromise scenarios

Security-focused documentation and reporting
