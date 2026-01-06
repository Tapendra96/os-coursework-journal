# Week 4: Initial System Configuration & Security Implementation

## SSH Key-Based Authentication
Generated keys on Kali and copied to server (192.168.56.105). Edited /etc/ssh/sshd_config to disable password auth. Successful connection without password.

![SSH Key Generation ](images/week4_ssh_keygen1.png)

![SSH Key Copy](images/week4_ssh_keygen2.png)

![SSH Connection](images/week4_ssh_connect.png)

## Firewall Configuration
Installed UFW, allowed SSH from Kali IP (192.168.56.107), enabled, and checked status (shows ruleset limiting access).

![Firewall Install and Rules](images/week4_firewall.png)

## Manage Users and Privileges
Created non-root user 'adminuser' with sudo privileges. Copied SSH key for secure access.

![User Creation and Privileges](images/week4_users.png)

## SSH Access Evidence
Successful SSH as adminuser from Kali.

![New SSH Connect](images/week4_new_connect.png)

## Configuration Files
Before/after for /etc/ssh/sshd_config (e.g., PasswordAuthentication no).

## Remote Administration Evidence
Ran sample commands (ls, whoami) via SSH on server from Kali, demonstrating remote CLI management.

![Remote Commands](images/week4_remote_commands.png)

**Reflection:** This implements LO3 security mechanisms (key auth, firewall) and LO4 CLI tasks. Trade-off: Enhanced security reduces usability (no password fallback). Challenge: Ensuring key copy without initial password exposure.