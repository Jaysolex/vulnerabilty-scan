# 🔐 Cybersecurity Vulnerability Assessment Report

**📌 Project Title:** Authenticated & Unauthenticated Vulnerability Scans on Windows 11 VM in Azure  
**👤 Name:** Solomon James  
**📅 Date:** May 20, 2025  
**🛠️ Tools Used:** Microsoft Azure, Tenable Nessus Essentials  
**🧪 Techniques:** Vulnerability Scanning, Risk Assessment, Hardening Planning

---

## 🧾 1. Project Overview

As part of a hands-on cybersecurity portfolio project using Josh Madakor’s lab framework, I created a Windows 11 virtual machine in Microsoft Azure and conducted both **unauthenticated** and **authenticated** scans using **Tenable Nessus**. The objective was to simulate external reconnaissance vs. internal visibility and prioritize the remediation of real-world risks.

---

## ☁️ 2. Lab Environment

- **Platform:** Microsoft Azure  
- **VM:** Windows 11 Pro Build 26100  
- **Scanner:** Tenable Nessus Essentials  
- **Network:** Default NSG allowing RDP  
- **Credentialed Access:** Enabled via `labuser` account

---

## 🔍 3. Scan Summary

| Scan Type        | Critical | High | Medium | Low | Info | Total |
|------------------|----------|------|--------|-----|------|-------|
| Unauthenticated  |    0     |  0   |   4    |  1  |  31  |  36    |
| Authenticated    |    0     |  2   |   4    |  1  | 133  | 140    |

---

## ⚠️ 4. Key Findings (Authenticated Scan)

### 🔴 High Severity

- **CVE-2024-20670 – Microsoft Outlook NTLM Hash Leak**  
  *Outlook allows spoofing that leaks NTLMv2 hashes to attacker-controlled servers.*  
  **Fix:** Apply [KB5002574](https://msrc.microsoft.com/update-guide/en-US/vulnerability/CVE-2024-20670)

- **Winlogon Cached Passwords**  
  *Cached credentials stored in the registry can be brute-forced.*  
  **Fix:** Set `CachedLogonsCount = 0` in the registry.

### 🟡 Medium Severity

- **Self-Signed SSL Certificate on RDP**  
  *May enable MITM attacks.*  
  **Fix:** Replace with a valid certificate.

- **TLS 1.1 Detected**  
  *Outdated and insecure encryption.*  
  **Fix:** Disable TLS 1.0/1.1 and enforce TLS 1.2 or 1.3.

- **SMB Shares Wide Access**  
  *Shares like `ADMIN$`, `C$`, and `D$` are accessible with full read/write permissions.*  
  **Fix:** Limit access to trusted users or remove external exposure.

---

## 🔐 5. Security Insights Gained

- Compared **external vs. internal attack surface**
- Leveraged **SMB/WMI/Registry** enumeration with credentials
- Identified:
  - Local group/user memberships
  - Installed packages
  - Security settings (e.g., Credential Guard)
- Simulated both **unauthenticated and authenticated threat models**

---

## 🧠 6. Skills Demonstrated

- ✅ Vulnerability Scanning (Tenable Nessus Essentials)  
- ✅ Windows Hardening Techniques  
- ✅ Azure VM Deployment & NSG Configuration  
- ✅ Registry & Group Policy Review  
- ✅ Report Writing and Analysis  
- ✅ Credentialed vs. Uncredentialed Threat Modeling

---

## ✅ 7. Remediation Plan

- [ ] Apply security updates (e.g., Outlook, .NET rollups)  
- [ ] Harden RDP access (restrict, use VPN/Bastion)  
- [ ] Replace self-signed SSL certs with trusted CAs  
- [ ] Limit or remove public SMB share access  
- [ ] Disable outdated TLS versions (1.0/1.1)  
- [ ] Clear cached credentials in registry

---

🔗 **📄[Download Full PDF Report](./Cybersecurity_Portfolio_Report_CyberSolex_Clean.pdf)**

