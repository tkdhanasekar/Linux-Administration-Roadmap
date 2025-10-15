
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
</details>

<details>
  <summary>Package Management</summary>

--- 
 
## ✅ **Package Management in Linux – Key Topics**

### 🔹 1. **Overview of Package Management**

* What is a package? (Binary, source, metadata)
* Difference between package formats (e.g., `.deb`, `.rpm`)
* Difference between package managers and repositories
* Local vs remote packages
* Signed packages and package verification

---

### 🔹 2. **Debian-Based Systems (APT – Ubuntu, Debian)**

* Installing packages: `apt install`, `dpkg -i`
* Removing packages: `apt remove`, `apt purge`
* Updating package lists: `apt update`
* Upgrading packages: `apt upgrade`, `apt full-upgrade`
* Searching for packages: `apt search`, `apt show`
* Managing repositories:

  * `/etc/apt/sources.list`
  * `/etc/apt/sources.list.d/`
* Cleaning cache: `apt clean`, `apt autoremove`
* Package info: `dpkg -l`, `dpkg -s`, `dpkg -L`, `dpkg -S`

---

### 🔹 3. **Red Hat-Based Systems (RPM/YUM/DNF – RHEL, CentOS, Fedora, AlmaLinux)**

* Installing packages: `dnf install`, `yum install`, `rpm -ivh`
* Removing packages: `dnf remove`, `yum erase`
* Updating packages: `dnf update`
* Listing packages: `rpm -qa`, `dnf list installed`
* Searching: `dnf search`, `dnf info`
* Querying package ownership: `rpm -qf /path/to/file`
* Working with repositories:

  * Adding/removing `.repo` files in `/etc/yum.repos.d/`
  * Using `dnf config-manager`
* Cleaning cache: `dnf clean all`
* Verifying packages: `rpm -V`, `rpm --checksig`

---

### 🔹 4. **Working with Repositories**

* Understanding official vs third-party repos
* Enabling/disabling repos (`yum-config-manager`, `add-apt-repository`)
* Setting priorities for repos
* Creating local repositories (using `createrepo`, `dpkg-scanpackages`)
* Offline package management

---

### 🔹 5. **Package Verification & Security**

* GPG keys and package signing
* Verifying package integrity and origin
* `apt-key`, `/etc/apt/trusted.gpg.d/`
* `rpm --checksig`, `dnf repoquery --requires`

---

### 🔹 6. **Advanced Package Management**

* Holding packages (preventing updates):

  * `apt-mark hold`
  * `dnf versionlock`
* Downgrading packages
* Managing dependencies and dependency resolution
* Debugging broken packages and dependency issues

---

### 🔹 7. **Building Packages**

* Basics of source packages (`.src.rpm`, `.dsc`)
* Compiling and installing from source (`make`, `make install`)
* Building `.deb` or `.rpm` packages (advanced)
* Understanding package spec files (RPM) or control files (DEB)

---

### 🔹 8. **Alternative Tools and Formats**

* Snap packages (`snap install`, `snap list`)
* Flatpak (`flatpak install`, `flatpak run`)
* AppImage (standalone apps)
* Comparisons and use cases

---

### 🔹 9. **Troubleshooting & Maintenance**

* Resolving broken installs (`apt --fix-broken`, `dnf check`)
* Reinstalling packages
* Logs and transaction history:

  * `/var/log/apt/`
  * `/var/log/dnf.log`
* Dependency resolution failures
* Manual dependency installation with `dpkg` or `rpm`

---

### 🔹 10. **Package Management Automation**

* Using Ansible, Puppet, or shell scripts for package tasks
* Preseed/kickstart for automated installs with pre-installed packages
* Maintaining system consistency across servers

---

Here's a **comprehensive study checklist** for **Package Management in Linux Administration** It covers both **Debian-based** and **Red Hat-based** systems

---

## ✅ **Linux Package Management – Study Checklist**

### 🔸 1. Fundamentals of Package Management

* [ ] Understand what packages are (binary vs source)
* [ ] Know the difference between package formats:

  * `.deb` (Debian/Ubuntu)
  * `.rpm` (Red Hat-based distros)
* [ ] Understand repositories and package dependencies
* [ ] Learn how Linux resolves package dependencies

---

### 🔸 2. Debian-Based Systems (APT, DPKG)

* [ ] Install a package using `apt install`
* [ ] Remove a package (`apt remove`, `apt purge`)
* [ ] Update package lists with `apt update`
* [ ] Upgrade packages:

  * Regular upgrade: `apt upgrade`
  * Full system upgrade: `apt full-upgrade`
* [ ] View package info: `apt show`, `dpkg -s`
* [ ] Search packages: `apt search`, `apt list`
* [ ] List all installed packages: `dpkg -l`
* [ ] List files in a package: `dpkg -L <pkg>`
* [ ] Find the package owning a file: `dpkg -S <file>`
* [ ] Install a `.deb` file with `dpkg -i`
* [ ] Fix broken installs: `apt --fix-broken install`
* [ ] Clean the package cache: `apt clean`, `apt autoremove`
* [ ] Configure or add a repository:

  * Edit `/etc/apt/sources.list`
  * Add repo via `add-apt-repository`
* [ ] Manage GPG keys for trusted packages (`apt-key`, signed repos)

---

### 🔸 3. Red Hat-Based Systems (RPM, YUM, DNF)

* [ ] Install a package with `dnf install`, `yum install`
* [ ] Remove a package: `dnf remove`, `yum erase`
* [ ] Update all packages: `dnf update`
* [ ] List installed packages: `rpm -qa`, `dnf list installed`
* [ ] Search for packages: `dnf search <term>`, `dnf info`
* [ ] Query a package file with `rpm -qpi <package.rpm>`
* [ ] Install local RPM files: `rpm -ivh`, `dnf install ./pkg.rpm`
* [ ] View package files: `rpm -ql <pkg>`
* [ ] Find which package owns a file: `rpm -qf /path/to/file`
* [ ] Clean metadata and cache: `dnf clean all`
* [ ] Verify package integrity: `rpm -V`, `rpm --checksig`
* [ ] Understand and use repo files in `/etc/yum.repos.d/`
* [ ] Enable/disable repos using `dnf config-manager`
* [ ] Configure GPG key trust and signed repos

---

### 🔸 4. Working with Repositories

* [ ] Manually add/edit APT and DNF repo configurations
* [ ] Create a local repository for `.deb` or `.rpm` packages
* [ ] Use tools like `createrepo`, `dpkg-scanpackages`
* [ ] Host a simple HTTP or NFS repo for local installs
* [ ] Understand offline package installation methods

---

### 🔸 5. Advanced Package Management

* [ ] Hold or lock package versions:

  * `apt-mark hold` (Debian)
  * `dnf versionlock` (Red Hat)
* [ ] Downgrade a package to a previous version
* [ ] Exclude packages from updates
* [ ] Configure auto-updates (e.g., `unattended-upgrades`, `dnf-automatic`)
* [ ] Understand and manage dependency chains
* [ ] Reinstall packages using `apt reinstall` or `dnf reinstall`

---

### 🔸 6. Alternative Package Formats

* [ ] Understand Snap packages:

  * Install: `snap install`
  * List: `snap list`
  * Remove: `snap remove`
* [ ] Understand Flatpak:

  * Install: `flatpak install`
  * Run: `flatpak run`
  * List: `flatpak list`
* [ ] Know what AppImage is and how to use it

---

### 🔸 7. Building & Installing from Source

* [ ] Compile software from source using `./configure`, `make`, `make install`
* [ ] Understand how to remove source-installed software
* [ ] Build a basic `.deb` or `.rpm` package (introductory level)
* [ ] Know the structure of spec files (RPM) or control files (DEB)

---

### 🔸 8. Troubleshooting & Maintenance

* [ ] Diagnose and fix broken or partially installed packages
* [ ] Check logs for package install issues:

  * APT logs: `/var/log/apt/`
  * DNF/YUM logs: `/var/log/dnf.log`, `/var/log/yum.log`
* [ ] Resolve dependency errors
* [ ] Understand transaction rollbacks (supported in `dnf`)
* [ ] Use tools like `aptitude` (Debian) or `yum-complete-transaction`

---

### 🔸 9. Package Management Automation

* [ ] Automate package installation in shell scripts
* [ ] Use configuration management tools:

  * Ansible: `apt`, `dnf`, `package` modules
  * Puppet, Chef, etc.
* [ ] Configure unattended installations with preseed or kickstart
* [ ] Maintain consistent package sets across servers

---

### 🔸 Bonus: Practice Exercises

* [ ] Install and remove 3 different packages using APT and DNF
* [ ] Create a list of all installed packages and save it to a file
* [ ] Set up a local repository and install from it
* [ ] Compile a simple program from source and install it
* [ ] Write a shell script to check for and install missing packages

---
</details>


<details>
  <summary>File and Directory Management</summary>
 Here's a **comprehensive list of topics** in **File and Directory Management** for **Linux system administration**. This area is essential for working with the filesystem, maintaining file security, automation, and managing storage efficiently.

---

## ✅ **File and Directory Management in Linux – Topics Overview**

---

### 🔹 1. **Filesystem Hierarchy Standard (FHS)**

* Understanding Linux directory structure (/, /home, /etc, /var, etc.)
* Purpose of key system directories
* Temporary files and locations (`/tmp`, `/var/tmp`)

---

### 🔹 2. **Basic File and Directory Operations**

* Listing contents: `ls`, `ls -l`, `ls -a`, `ls -lh`
* Creating files: `touch`, `echo`, `cat >`, `>`, `printf`
* Creating directories: `mkdir`, `mkdir -p`
* Copying files and directories: `cp`, `cp -r`
* Moving/renaming files and directories: `mv`
* Deleting files and directories: `rm`, `rm -r`, `rmdir`
* Viewing file contents: `cat`, `more`, `less`, `head`, `tail`

---

### 🔹 3. **File and Directory Permissions**

* Understanding permissions: read, write, execute (rwx)
* Owner, group, others
* Changing permissions: `chmod` (symbolic and numeric)
* Changing ownership: `chown`, `chgrp`
* Viewing permissions: `ls -l`
* Understanding and using `umask`

---

### 🔹 4. **Special Permissions**

* SetUID (SUID)
* SetGID (SGID)
* Sticky bit (used in `/tmp` and shared directories)
* Finding files with special permissions: `find / -perm`

---

### 🔹 5. **File Types and Attributes**

* File types: regular, directory, symlink, block/character device, socket, FIFO
* Identifying file types: `ls -l`, `file`
* Creating symbolic and hard links: `ln -s`, `ln`
* Viewing and modifying file attributes: `lsattr`, `chattr`

---

### 🔹 6. **Finding Files and Directories**

* Using `find` to locate files by name, size, type, date, permission
* Using `locate`, `updatedb`
* Using `which`, `whereis`, `type` to find command binaries
* Grepping within files: `grep`, `egrep`, `zgrep`

---

### 🔹 7. **File Archiving and Compression**

* Archiving with `tar`, `cpio`
* Compressing files: `gzip`, `bzip2`, `xz`, `zip`
* Decompressing files: `gunzip`, `bunzip2`, `unzip`, `tar -x`
* Creating and extracting tarballs: `.tar`, `.tar.gz`, `.tar.bz2`

---

### 🔹 8. **File System Links**

* Hard vs symbolic (soft) links
* Creating and removing links
* When to use hard vs soft links
* Detecting broken symlinks

---

### 🔹 9. **Disk Usage and File Size**

* Checking file/directory size: `du`, `du -sh`, `du -a`
* Checking free disk space: `df -h`
* Analyzing disk usage with `ncdu`, `du -x`, `find -size`

---

### 🔹 10. **Text File Manipulation (for Admin Tasks)**

* Viewing and editing: `cat`, `nano`, `vim`, `less`, `head`, `tail`
* Concatenation and redirection: `>`, `>>`, `<`, `|`, `tee`
* Sorting, cutting, and filtering:

  * `sort`, `uniq`, `cut`, `tr`, `awk`, `sed`

---

### 🔹 11. **Managing Hidden Files and Dotfiles**

* Creating and viewing hidden files
* Dotfiles for configuration (`.bashrc`, `.profile`, etc.)
* Backing up and managing user config files

---

### 🔹 12. **Access Control Lists (ACLs) (Advanced)**

* Enabling and checking ACL support
* Setting ACLs with `setfacl`
* Viewing ACLs with `getfacl`
* Removing ACLs

---

### 🔹 13. **Timestamps and File Metadata**

* File timestamps: access (atime), modify (mtime), change (ctime)
* Viewing with `ls -l`, `stat`
* Changing timestamps: `touch`, `utime`

---

### 🔹 14. **Mount Points and Bind Mounts (Basic Filesystem Concepts)**

* Creating mount points (e.g., `/mnt`, `/media`)
* Mounting temporary filesystems or bind mounts (e.g., `mount --bind`)
* Understanding mount context for file access

---

Here’s a **comprehensive study checklist** for **File and Directory Management** in **Linux Administration**.

---

## ✅ **File and Directory Management in Linux – Study Checklist**

---

### 🔸 1. Filesystem Hierarchy & Navigation

* [ ] Understand the Linux Filesystem Hierarchy Standard (FHS)
* [ ] Know the purpose of key directories (`/`, `/home`, `/etc`, `/var`, `/usr`, `/tmp`, `/opt`)
* [ ] Navigate directories using `cd`, `pwd`, `ls`
* [ ] Use `tree` to view directory structure (if installed)

---

### 🔸 2. Basic File and Directory Operations

* [ ] Create files with `touch`, `echo`, `cat >`, `printf`
* [ ] View file contents using `cat`, `less`, `more`, `head`, `tail`
* [ ] Create directories with `mkdir`, including nested directories (`mkdir -p`)
* [ ] Copy files and directories: `cp`, `cp -r`, `cp -p`
* [ ] Move or rename files: `mv`
* [ ] Delete files and directories: `rm`, `rm -r`, `rmdir`

---

### 🔸 3. File and Directory Permissions

* [ ] Understand file permission structure (`rwx`, owner/group/other)
* [ ] Change permissions with `chmod` (symbolic and numeric modes)
* [ ] Change file ownership using `chown`, `chgrp`
* [ ] Set and interpret default permissions using `umask`
* [ ] Recursively change permissions or ownership

---

### 🔸 4. Special File Permissions

* [ ] Understand and apply SUID (Set User ID)
* [ ] Understand and apply SGID (Set Group ID)
* [ ] Use the sticky bit in shared directories (e.g., `/tmp`)
* [ ] Find files with special permissions using `find -perm`

---

### 🔸 5. File Types and Attributes

* [ ] Identify file types using `ls -l`, `file`
* [ ] Understand symbolic link vs hard link
* [ ] Create symbolic (`ln -s`) and hard links (`ln`)
* [ ] List and modify file attributes with `lsattr`, `chattr` (e.g., `i`, `a` flags)

---

### 🔸 6. Finding Files and Directories

* [ ] Find files by name: `find / -name <pattern>`
* [ ] Find files by size, time, permissions, type: `find / -size`, `-mtime`, `-type`
* [ ] Use `locate` and `updatedb` for fast searching
* [ ] Use `which`, `type`, `whereis` to locate binaries and commands
* [ ] Search inside files with `grep`, `egrep`, `zgrep`

---

### 🔸 7. File Archiving and Compression

* [ ] Archive files with `tar`, `cpio`
* [ ] Compress files using `gzip`, `bzip2`, `xz`, `zip`
* [ ] Decompress using `gunzip`, `bunzip2`, `unzip`, `tar -x`
* [ ] Create/extract compressed tarballs: `.tar.gz`, `.tar.bz2`, `.tar.xz`

---

### 🔸 8. Disk Usage and File Size Management

* [ ] Check file/directory size using `du`, `du -sh`, `du -a`
* [ ] Check available disk space using `df -h`
* [ ] Use `ncdu` for interactive disk usage analysis
* [ ] Find large files using `find -size`, `du -a | sort -n`

---

### 🔸 9. Text File Manipulation

* [ ] Display and edit text with `cat`, `nano`, `vim`, `less`
* [ ] Use redirection: `>`, `>>`, `<`
* [ ] Use pipes (`|`) and `tee` to combine and capture output
* [ ] Filter and process text:

  * `sort`, `uniq`, `cut`, `awk`, `sed`, `tr`, `wc`

---

### 🔸 10. Hidden Files and Dotfiles

* [ ] Identify and list hidden files (`ls -a`)
* [ ] Understand dotfiles for shell configuration (`.bashrc`, `.bash_profile`, `.profile`)
* [ ] Safely edit and back up dotfiles

---

### 🔸 11. Access Control Lists (ACLs) – Advanced

* [ ] Check if filesystem supports ACLs
* [ ] View ACLs with `getfacl`
* [ ] Set ACLs with `setfacl` (e.g., set permissions for multiple users)
* [ ] Remove ACLs with `setfacl -x` or `setfacl -b`

---

### 🔸 12. Timestamps and File Metadata

* [ ] Understand file timestamps: atime (access), mtime (modify), ctime (change)
* [ ] View timestamps with `ls -l`, `ls -lt`, `stat`
* [ ] Change timestamps with `touch`

---

### 🔸 13. Mount Points and Bind Mounts (Basic Filesystem Management)

* [ ] Create mount points (`mkdir /mnt/xyz`)
* [ ] Use `mount` to bind a directory (`mount --bind`)
* [ ] View mounted filesystems: `mount`, `findmnt`, `df -h`
* [ ] Unmount with `umount`

---

### 🔸 Bonus: Practice Exercises

* [ ] Create a directory structure and populate it with files
* [ ] Set various permission levels and test access as different users
* [ ] Archive and compress a folder, then extract it
* [ ] Use `find` to locate files by type, age, and size
* [ ] Search for a string in multiple files and output results to a new file
* [ ] Set and test ACLs on a shared directory

---

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
