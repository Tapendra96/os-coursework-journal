# Week 7: Security Audit and System Evaluation

## Security Audit Tasks
- Lynis: `sudo lynis audit system` (before: details on system, boot, kernel, malware, security modules; suggestions for scanners).
- Fixes: Installed rkhunter (`sudo apt-get install rkhunter`, `--update`, `--check`) for rootkit scans.
- Alternative: chkrootkit (`sudo apt-get install chkrootkit`, `sudo chkrootkit`).
- Scheduled: `sudo crontab -e`, added `0 0 * * * /usr/bin/rkhunter --check --cronjob` for daily scans.

Lynis Audit Before
![Lynis Audit Before](images/week7_lynis.png)

Lynis Audit After
![Lynis Audit After](images/week7_lynisafter.png)


## Network Security with nmap
`nmap -sV 192.168.56.105`: Version detection, open ports (e.g., 22/tcp open ssh OpenSSH 9.2p1).

![Nmap Results](images/week7_nmap.png)

## Access Control Verification
`sudo aa-status`: Profiles loaded (29 total, 25 enforce mode, including system defaults).

![aa-status](images/week7_aa_status.png)

## Service Audit
`systemctl list-units --type=service`: Lists active services (e.g., sshd, apache2, fail2ban, cron). Justifications: Essential for admin (sshd), testing (apache2—disabled after), security (fail2ban). Minimized unneeded.

![Service List](images/week7_services.png)

## Security Audit Report
Overall: System secure in VM environment. Lynis improved post-fixes (e.g., added malware scans). Nmap confirms only SSH exposed. Risks: Kernel warnings mitigated by updates/cron. Score aim >80%.


**Reflection:** Audits fulfill LO3 with vulnerability assessments and fixes. LO5 trade-offs: Scanners add minor overhead (e.g., cron CPU) but bolster protection. Learned integrating Lynis with rkhunter for comprehensive checks.