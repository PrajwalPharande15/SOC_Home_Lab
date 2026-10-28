# Home SOC Lab

A self-directed home lab where I practice SOC analyst fundamentals: log analysis, SIEM searches, and detecting suspicious activity, using my own virtual machines.

## Why I built this

I'm a BCA graduate building toward an entry-level SOC Analyst (L1) role. This lab is where I turn what I'm learning (Cisco Networking Academy, TryHackMe, self-study) into hands-on practice I can actually explain, not just read about.

## Lab setup

- **VirtualBox** running 3 VMs on an isolated Host-only network:
  - **Kali Linux** — attacker machine
  - **Ubuntu** — target machine, running SSH, logs ingested into Splunk
  - **Windows 10** — endpoint for future exercises
- **Splunk Enterprise (Trial)** installed on Ubuntu as the SIEM, ingesting `/var/log/auth.log`

## Exercises completed

### 1. Linux user account investigation
Created a Linux user account, then found the full creation event (adduser, group creation, password set) in the system logs using `journalctl` and `grep`.

### 2. Failed login detection
Triggered failed `su` logins on purpose, then located them in the logs with exact timestamps, the targeted account, and who attempted it.

### 3. Privilege escalation attempt
Logged in correctly, then tried a `sudo` command from a non-admin account. The logs recorded the refusal (`user NOT in sudoers`), the same pattern analysts look for when investigating unauthorized access attempts.

### 4. Cross-machine SSH monitoring
Connected Kali and Ubuntu over SSH on a private lab network, then found login activity (success and failure) in Splunk, including the source IP of the connecting machine.

### 5. Simulated SSH brute-force attack and detection
Used Hydra to run a password-guessing attack against a test SSH account, then identified the attack pattern in Splunk: a burst of failed logins from one source IP within seconds, followed by one successful login.

See [`incident-report.md`](./incident-report.md) for the full write-up of this exercise.

## Skills demonstrated

- Linux command line (user/permission management, log investigation)
- SIEM searching (Splunk Search Processing Language)
- Log analysis and evidence-based investigation
- Basic networking (VM-to-VM connectivity, SSH)
- Incident documentation

## Tools used

`VirtualBox` · `Kali Linux` · `Ubuntu` · `Splunk Enterprise` · `Hydra` · `journalctl` / `grep`

## What's next

- Wireshark packet capture analysis
- Nmap scanning and detection
- OWASP Top 10 fundamentals

---
*Each exercise was also documented step-by-step on [my LinkedIn](https://linkedin.com/in/prajwal-pharande-050283303) as I completed it.*
