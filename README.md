 TryHackMe: RootMe Machine Walkthrough 🛡️

**Date:** April 2026  
**Lab:** RootMe (Difficulty: Easy)  
**Objective:** Exploitation and Privilege Escalation

---

## 🛠️ Project Methodology

### 1. Reconnaissance & Enumeration
The first step involved scanning the target to identify open ports and hidden directories.
* **Findings:** Discovered an Apache web server with a hidden `/panel/` directory that allowed file uploads.
* **Evidence:** `reconnaissance.jpg`

### 2. Initial Access (Web Exploitation)
I exploited an insecure file upload vulnerability. Since `.php` files were blocked, I bypassed the filter using the `.phtml` extension to upload a reverse shell.
* **Payload:** PHP Reverse Shell
* **Access Level:** `www-data` (Low-privileged web user)

### 3. Privilege Escalation (SUID Bit Exploitation)
After gaining access, I searched for SUID binaries to find a way to escalate to root.
* **Vulnerability:** Found that **Python 2.7** had the SUID bit set (`-rwsr-xr-x`). This is a critical misconfiguration.
* **Exploit:** Executed a Python one-liner to spawn a root-level shell.
* **Evidence:** `suid discovery.jpg`

### 4. Final Victory (Root Flag)
Successfully escalated to root privileges and captured the final flag from the `/root` directory.
* **Command:** `cat /root/root.txt`
* **Root Flag:** `THM{pr1v1l3g3_3sc4l4t10n}`
* **Evidence:** `hero shot.jpg`

---

## 📸 Proof of Concept (PoC)
I have documented the process with screenshots:
1. **Initial Access:** Showing the bypass and shell connection.
2. **SUID Check:** Identifying the vulnerable Python binary.
3. **Root Proof:** Output of `whoami` as root and the final flag.

---

### 🚀 Skills Demonstrated
* **Vulnerability Assessment:** Identifying misconfigured permissions.
* **Web Security:** Bypassing upload filters.
* **Linux Security:** Exploiting SUID binaries.
* **Documentation:** Clear reporting of penetration testing steps.

