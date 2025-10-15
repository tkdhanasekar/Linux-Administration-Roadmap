
## Linux Administration Roadmap

<details>
  <summary>User and Group Management</summary>
---

### 🔹 **1. User Account Management**

* Creating users (`useradd`, `adduser`)
* Modifying user accounts (`usermod`)
* Deleting user accounts (`userdel`)
* Managing user passwords (`passwd`, `chage`)
* Setting password aging policies
* Locking and unlocking user accounts
* Setting default user settings (`/etc/skel`, `/etc/default/useradd`)
* Managing user shell and home directories

---

### 🔹 **2. Group Management**

* Creating groups (`groupadd`)
* Modifying groups (`groupmod`)
* Deleting groups (`groupdel`)
* Adding users to groups (`usermod -aG`, `gpasswd`)
* Primary vs. secondary groups
* Viewing group membership (`groups`, `id`, `/etc/group`)

---

### 🔹 **3. System Files Related to Users & Groups**

* `/etc/passwd` – user account information
* `/etc/shadow` – encrypted passwords and aging info
* `/etc/group` – group information
* `/etc/gshadow` – secure group info (used by `gpasswd`)

---

### 🔹 **4. Permissions and Ownership**

* File and directory ownership (`chown`, `chgrp`)
* File permissions (read/write/execute)
* Special permissions:

  * SUID
  * SGID
  * Sticky bit
* Umask and default permissions

---

### 🔹 **5. User Environment Configuration**

* Login shells (`/etc/shells`)
* Environment files: `.bashrc`, `.bash_profile`, `.profile`
* Session configuration for shells

---

### 🔹 **6. User Session Management**

* Who is logged in (`who`, `w`, `users`, `last`)
* Managing user sessions (`pkill`, `kill`, `logout`)
* Session limits (`/etc/security/limits.conf`)

---

### 🔹 **7. Access Control**

* Using `sudo` and configuring `/etc/sudoers`
* `visudo` and best practices for sudo permissions
* Restricting access via PAM (Pluggable Authentication Modules)
* Account restrictions based on time, groups, or hosts

---

### 🔹 **8. Automation and Bulk Operations**

* Creating multiple users/groups via scripts
* Using `newusers` for bulk user creation
* Automating password assignment

---

### 🔹 **9. LDAP and Centralized Authentication (Advanced)**

* Integrating with LDAP/Active Directory
* Using `sssd`, `nslcd`, or `winbind`
* Central user/group management
* Kerberos for authentication

---

### 🔹 **10. Security Considerations**

* Auditing user activity
* Detecting inactive or locked accounts
* Monitoring sudo usage
* Handling compromised accounts

---

**comprehensive study checklist** for **User and Group Management in Linux Administration**

---

## ✅ **User & Group Management in Linux – Study Checklist**

### 🔸 1. Basic User Account Management

* [ ] Understand the purpose of users and user IDs (UIDs)
* [ ] Create new users with `useradd` or `adduser`
* [ ] Set or change user passwords with `passwd`
* [ ] Modify user properties with `usermod`
* [ ] Delete user accounts with `userdel`
* [ ] Assign users to specific home directories and default shells
* [ ] Use and configure `/etc/skel` for default user files

---

### 🔸 2. Group Management

* [ ] Understand primary vs secondary groups
* [ ] Create groups with `groupadd`
* [ ] Modify groups with `groupmod`
* [ ] Delete groups with `groupdel`
* [ ] Add users to groups with `usermod -aG` or `gpasswd`
* [ ] List user group memberships (`id`, `groups`, `getent group`)

---

### 🔸 3. User & Group Related System Files

* [ ] Understand the structure of `/etc/passwd`
* [ ] Understand the contents of `/etc/shadow`
* [ ] Review `/etc/group` and `/etc/gshadow`
* [ ] Know the fields in each file and what they represent
* [ ] Practice using `vipw` and `vigr` to safely edit these files

---

### 🔸 4. File Permissions and Ownership

* [ ] Understand read (r), write (w), execute (x) permissions
* [ ] Use `chmod`, `chown`, and `chgrp` to manage permissions
* [ ] Distinguish between user, group, and others
* [ ] Set default permissions using `umask`
* [ ] Apply and explain special permissions: SUID, SGID, Sticky Bit

---

### 🔸 5. Managing User Environments

* [ ] Configure default shells for users
* [ ] Understand and customize `.bashrc`, `.profile`, `.bash_profile`
* [ ] Use `/etc/profile` and `/etc/bash.bashrc` for system-wide settings

---

### 🔸 6. Session & User Management Tools

* [ ] Monitor logged-in users (`who`, `w`, `users`)
* [ ] Track login history with `last`, `lastlog`
* [ ] Terminate user sessions with `kill`, `pkill`
* [ ] Set user session limits in `/etc/security/limits.conf`

---

### 🔸 7. Sudo and Privilege Management

* [ ] Install and configure `sudo`
* [ ] Edit `/etc/sudoers` safely with `visudo`
* [ ] Grant limited root privileges to users and groups
* [ ] Use `sudo` logs for auditing

---

### 🔸 8. Password Policies & Account Security

* [ ] Enforce password aging with `chage`
* [ ] Set password complexity via PAM
* [ ] Lock and unlock accounts (`passwd -l`, `passwd -u`)
* [ ] Disable accounts after inactivity
* [ ] Audit users with weak or empty passwords

---

### 🔸 9. Bulk User/Group Operations (Intermediate)

* [ ] Create users in batch with scripts or `newusers`
* [ ] Use `cut`, `awk`, and `getent` to extract account info
* [ ] Automate password assignment (e.g., `chpasswd`)

---

### 🔸 10. Centralized Authentication (Advanced)

* [ ] Understand basics of LDAP/Active Directory integration
* [ ] Use `sssd`, `nsswitch.conf`, and PAM for auth configs
* [ ] Authenticate users via Kerberos (concept level)
* [ ] Centralize user home directories using NFS/automount

---

### 🔸 11. Security & Best Practices

* [ ] Regularly audit `/etc/passwd`, `/etc/shadow` for anomalies
* [ ] Check for unused or inactive accounts
* [ ] Use tools like `faillock` or `pam_tally2` to monitor failed logins
* [ ] Enforce least privilege using groups and sudo

---

### ✅ Bonus: Practice Tasks

* [ ] Create 5 users and assign different groups and shells
* [ ] Configure a user with a locked account and password expiration
* [ ] Set up a shared directory using SGID
* [ ] Use `sudo` to allow a user to run only specific commands
* [ ] Script bulk creation of users from a CSV file

---

Would you like this checklist as a **printable PDF** or in **Notion/Markdown format** for tracking?

</details>

<details>
  <summary>DNS</summary>
Here’s a comprehensive list of DNS administration topics specifically within the context of Linux system administration. These cover both foundational concepts and hands-on administration skills:

---

## 📘 DNS Administration Topics in Linux

### 1. **Introduction to DNS**

* What is DNS?
* DNS hierarchy: Root, TLD, authoritative servers
* DNS record types: A, AAAA, CNAME, MX, TXT, NS, PTR, SRV, SOA
* Recursive vs iterative queries

---

### 2. **Linux DNS Client Configuration**

* `/etc/resolv.conf`
* `nmcli` or NetworkManager for DNS configuration
* Setting up DNS in `/etc/systemd/resolved.conf`
* Testing DNS resolution using:

  * `dig`
  * `nslookup`
  * `host`

---

### 3. **BIND (Berkeley Internet Name Domain) – DNS Server**

* Installing BIND: `bind9` or `named`
* BIND configuration files:

  * `/etc/named.conf` or `/etc/bind/named.conf`
  * `/var/named/` or `/etc/bind/zones/`
* Creating and editing zone files
* Forward and reverse DNS zones
* Zone file syntax and TTLs

---

### 4. **DNS Records Management**

* A/AAAA (IPv4/IPv6 address)
* CNAME (alias)
* MX (mail exchanger)
* PTR (reverse lookup)
* TXT (SPF, DKIM)
* NS (name server delegation)
* SOA (start of authority)

---

### 5. **Zone Delegation and Subdomains**

* Creating subdomains
* Delegating authority to child zones
* Configuring NS records for subzones

---

### 6. **Reverse DNS Configuration**

* Understanding in-addr.arpa and ip6.arpa zones
* Creating PTR records for reverse lookups

---

### 7. **DNS Caching and Performance**

* Caching DNS responses with `dnsmasq` or `unbound`
* Configuring TTL and cache settings
* Flushing DNS cache (on client and server)
* Tools for testing: `dig +trace`, `drill`

---

### 8. **DNS Security**

* DNSSEC basics and configuration
* TSIG (Transaction SIGnature) for zone transfers
* Preventing DNS spoofing
* Using `named-checkconf` and `named-checkzone` for validation

---

### 9. **Logging and Troubleshooting**

* BIND log files: `/var/log/named/`, syslog
* Enabling query logging
* Debugging with `dig`, `tcpdump`, `journalctl`
* Common errors: SERVFAIL, NXDOMAIN, REFUSED

---

### 10. **Automation and Scripting**

* Scripting DNS updates with `nsupdate`
* Managing DNS with Ansible/Bash scripts
* Zone file templating

---

### 11. **High Availability and Redundancy**

* Setting up secondary (slave) DNS servers
* Zone transfers (AXFR, IXFR)
* Load balancing DNS servers

---

### 12. **DNS Forwarding and Conditional Forwarding**

* Setting up forwarders in BIND
* Split-horizon DNS (internal vs external views)
* Using `views` in BIND for conditional DNS serving

---

### 13. **Local DNS Servers for Development**

* Using `dnsmasq` for lightweight DNS
* Using `unbound` for validating recursive resolver
* Hosts file override (`/etc/hosts`)

---

### 14. **Monitoring and Auditing**

* Monitoring DNS queries
* Rate limiting DNS queries
* DNS analytics with tools like `dnstop`, `dnsstat`

---
</details>

<details>
  <summary>DHCP</summary>

  DHCP details

</details>

<details>
  <summary>Apache</summary>

  Apache details

</details>

<details>
  <summary>Nginx</summary>

  Nginx details

</details>
