---
title: "Linux Fundamentals Lab Challenges – Hack The Box"
date: 2026-02-19 14:00:00 +0000
categories: [Cybersecurity, Linux, Hack The Box]
tags: [linux, hackthebox, enumeration, bash, systemctl, networking, permissions, user-management, find-command, netstat, security]
---

# Linux Fundamentals Lab Challenges

## Overview
This post highlights key lab challenges completed during the **Linux Fundamentals** module on Hack The Box. These exercises provided hands-on experience with Linux structure, distributions, shell navigation, file management, permissions, user management, package management, services, process control, networking, and security concepts.

---

## Challenge 1: Machine Hardware Name

### Problem Statement
Find out the machine hardware name.

### Approach
1. Spawned the target machine and connected via SSH.
2. Ran the following command:

```bash
uname -m
```

### Key Lessons Learned
- The `uname -m` command prints the machine hardware name (e.g., `x86_64`).
- System information commands are fundamental for profiling a target.

---

## Challenge 2: Home Directory Path

### Problem Statement
Identify the path to the `htb-student`'s home directory.

### Approach

```bash
pwd
```

### Key Lessons Learned
- The system automatically places you in the home directory after login.
- `pwd` confirms your current working directory.

---

## Challenge 3: User Shell Identification

### Problem Statement
Identify which shell is specified for the `htb-student` user.

### Approach

```bash
env
```

The shell identified was:

```
/bin/bash
```

### Key Lessons Learned
- The `env` command displays environment variables, including the default shell.

---

## Challenge 4: Network Interface with MTU 1500

### Approach

```bash
ifconfig
```

Identified interface: `ens192`.

### Key Lessons Learned
- `ifconfig` displays network configuration details including MTU values.

---

## Challenge 5: Hidden History File

### Approach

```bash
ls -la
```

Identified hidden file: `.bash_history`.

### Key Lessons Learned
- Hidden files begin with a dot (`.`).
- `ls -a` reveals hidden files.

---

## Challenge 6: Last Modified File in /var/backups

### Approach

```bash
ls -la /var/backups
```

Identified: `apt.extended_states.0`.

---

## Challenge 7: Inode Number of shadow.bak

### Approach

```bash
ls -i /var/backups
```

Inode number: `265293`.

---

## Challenge 8: Finding Configuration File with find

### Approach

```bash
find / -type f -name "*.conf" -exec ls -al {} \; 2>/dev/null
```

Identified: `00-mesa-defaults.conf`.

---

## Challenge 9: Counting .bak Files

### Approach

```bash
find / -type f -name "*.bak" -exec ls -al {} \; 2>/dev/null | wc -l
```

Total: `4`.

---

## Challenge 10: Finding Full Path of xxd Binary

### Approach

```bash
which xxd
```

Path: `/usr/bin/xxd`.

---

## Challenge 11: Counting .log Files

### Approach

```bash
find / -type f -name "*.log" -exec ls -al {} \; 2>/dev/null | wc -l
```

---

## Challenge 12: Counting Listening Services

### Approach

```bash
netstat -lnp4 | grep LISTEN | grep -v "127" | awk '{print $4}' | wc -l
```

Listening services (excluding localhost): `7`.

---

## Challenge 13: Identifying ProFTPd User

### Approach

```bash
ps aux | grep proftpd
```

User: `proftpd`.

---

## Challenge 14: Creating Home Directory with useradd

### Approach

```bash
man useradd
```

Required option: `-m`.

---

## Challenge 15: Locking a User Account with usermod

### Approach

```bash
man usermod
```

Option: `--lock` or `-L`.

---

## Challenge 16: Identifying Snapd AppArmor Service

### Approach

```bash
systemctl list-units --type=service | grep "Load AppArmor"
```

Service: `snapd.apparmor.service`.

---

## Challenge 17: Identifying dconf.service Type

### Approach

```bash
cat /usr/lib/systemd/user/dconf.service
```

Type: `dbus`.

---

## Challenge 18: Starting HTTP Server with npm

### Approach

```bash
http-server -p 8080
```

---

## Challenge 19: Starting HTTP Server with PHP

### Approach

```bash
php -S 127.0.0.1:8080
```

---

## Challenge 20: Counting Partitions in Pwnbox

### Approach

```bash
sudo fdisk -l
```

Partitions: `3`.

---

## Conclusion

The Linux Fundamentals module provided hands-on experience with:

- System enumeration (`uname`, `ifconfig`, `ps`)
- File navigation and discovery (`ls`, `find`, `pwd`)
- User and permission management (`useradd`, `usermod`)
- Service management (`systemctl`)
- Network enumeration (`netstat`)
- Command-line filtering (`grep`, `awk`, `wc`)
- Lightweight web server deployment
- Disk and partition analysis

These exercises strengthened my understanding of Linux system administration, security assessment techniques, and command-line efficiency. Mastering these foundational skills is essential for penetration testing, DevOps, and cybersecurity operations.

*Completed as part of Hack The Box Linux Fundamentals module.*
