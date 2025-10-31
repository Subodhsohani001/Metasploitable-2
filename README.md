## Penetration Test: Metasploitable 2 (Educational Lab) — Oct 3, 2025 ⚡

### TL;DR
Completed an end-to-end lab penetration test against Metasploitable 2. Enumerated services, found multiple vulnerable services, and exploited the **vsftpd 2.3.4 backdoor** to obtain a root shell. Documented findings, impact, and practical remediation steps.

---

### Objectives 🎯
- Practice the full pentest lifecycle: discovery → vulnerability identification → exploit → post-exploitation verification → remediation recommendations.  
- Produce clear, reproducible documentation suitable for learning and defensive hardening.

---

### Environment 🧪
- **Target:** Metasploitable 2 VM 
- **Attacker:** Kali Linux VM  
- **Scope:** Isolated lab environment (permissioned)

---

### Tools & Techniques 🛠️
- **Nmap** — network discovery, full TCP scan, version detection  
- **Metasploit Framework** — `exploit/unix/ftp/vsftpd_234_backdoor`  
- Manual post-exploitation checks: `whoami`, `ifconfig`, `ls`

---

### Key Findings ⚠️
- **Critical:** vsftpd 2.3.4 backdoor — remote code execution leading to a root shell (confirmed via Metasploit).  
- Several other exposed services (ssh, telnet, mysql, http, vnc) present for additional enumeration and learning.

---

### Steps I performed 🧭
1. Performed subnet discovery and identified the Metasploitable host.  
2. Ran full TCP port scan and targeted version detection (`nmap -p-` + `-sV`).  
3. Identified vsftpd 2.3.4 and confirmed public advisory for a backdoor.  
4. Launched Metasploit module `exploit/unix/ftp/vsftpd_234_backdoor`, set `RHOSTS`, and executed.  
5. Verified compromise (`whoami` → `root`, `ifconfig`) and captured session output.  
6. Documented findings, impact, and remediation guidance in the final report. :contentReference[oaicite:2]{index=2}

---

### Impact 💥
- Full system compromise is achievable on an unpatched host — highlights the importance of timely patching, minimizing exposed services, and adopting secure alternatives (SFTP/FTPS).

---

### Recommendations ✅
- Remove or upgrade vulnerable vsftpd builds; use SFTP (OpenSSH) or properly configured FTPS instead.  
- Apply network segmentation and host-based monitoring.  
- Rebuild compromised hosts from trusted images and rotate all credentials.  
- Implement regular vulnerability scanning and automated patching where feasible.

---

### Artifacts included 📁
- `pentest_report_metasploitable2_v1.0_20251003.pdf` — full written report with command outputs and screenshots. :contentReference[oaicite:3]{index=3}  
- (Suggested) `evidence/` — redacted screenshots (`01-nmap.png`, `02-msf-run.png`, `03-whoami.png`)  
- (Suggested) `notes/commands.txt` — reproduction commands for lab environments

> Tip: keep raw logs and any sensitive artifacts out of the public repo. Add them to `.gitignore` if you keep them locally.

---

### Skills demonstrated 🧠
- Vulnerability discovery & validation  
- Exploit execution (Metasploit)  
- Post-exploitation verification and impact analysis  
- Technical reporting & remediation guidance

---

### Next steps ➕
- Build a hardened remediation playbook (Ansible/CIS benchmarks).  
- Create an automated verification script to detect vsftpd and similar risky versions.  
- Develop a simple dashboard to visualize scan/exploit timelines and evidence.

---

## License 🔒

MIT License — add this exact block to your `LICENSE` file (replace `[YEAR]` and `[FULL NAME OR ORGANIZATION]`):

```text
MIT License

Copyright (c) [YEAR] [FULL NAME OR ORGANIZATION]

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.

---

#⚔️ Hack Ethically & Responsibly — Learn, Protect, Repeat 🔁
