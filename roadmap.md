
## Linux Administration Roadmap

<details>
  <summary>User and Group Management</summary>
---
 
## ✅ **User and Group Management – Topics Overview**

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

### 🔸 12. Practice Tasks

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

---

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

## ✅ **Linux Package Management – Study Checklist**

---

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

### 🔸 10. Practice Exercises

* [ ] Install and remove 3 different packages using APT and DNF
* [ ] Create a list of all installed packages and save it to a file
* [ ] Set up a local repository and install from it
* [ ] Compile a simple program from source and install it
* [ ] Write a shell script to check for and install missing packages

---

</details>

<details>
  <summary>File and Directory Management</summary>

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
  <summary>Networking Management</summary>

---

## ✅ **Networking Management in Linux – Topics Overview**

---

### 🔹 1. **Networking Basics**

* OSI and TCP/IP models (basic understanding)
* IP addressing: IPv4 and IPv6
* Subnetting, CIDR notation
* Default gateway and routing concepts
* Public vs. private IP addresses
* DNS concepts and how name resolution works

---

### 🔹 2. **Interface Configuration**

* Network interfaces naming (`eth0`, `ens33`, `enp0s3`, etc.)
* Viewing interfaces: `ip a`, `ifconfig`, `nmcli device`
* Enabling/disabling interfaces
* Assigning static and dynamic IP addresses
* Configuring interface files:

  * `/etc/network/interfaces` (Debian/Ubuntu)
  * `/etc/sysconfig/network-scripts/ifcfg-*` (RHEL/CentOS)
  * `netplan` configuration files (Ubuntu 18.04+)

---

### 🔹 3. **Networking Tools & Commands**

* `ip` command suite: `ip a`, `ip r`, `ip link`, `ip addr add/del`
* Legacy: `ifconfig`, `route`, `netstat`
* `nmcli` and `nmtui` (NetworkManager tools)
* `hostname`, `hostnamectl`
* `ping`, `traceroute`, `mtr`
* `dig`, `nslookup`, `host`
* `arp`, `ip neigh`
* `ss`, `netstat` for socket and port monitoring
* `ethtool`, `mii-tool` for interface diagnostics

---

### 🔹 4. **Hostname and DNS Configuration**

* Set and persist hostname: `hostnamectl set-hostname`
* Configure DNS in:

  * `/etc/resolv.conf` (traditional)
  * `systemd-resolved` (`/etc/systemd/resolved.conf`)
  * `netplan`, NetworkManager, or interface config files
* Test DNS with `dig`, `host`, `nslookup`

---

### 🔹 5. **Routing and Gateways**

* View routing table: `ip route`, `route -n`
* Add/remove static routes
* Default gateway configuration
* Persistent static routes

---

### 🔹 6. **Firewall and Port Management**

* `iptables` (traditional firewall tool)
* `nftables` (modern replacement for iptables)
* `firewalld` and `firewall-cmd` (common on RHEL-based distros)
* Opening, closing, forwarding ports
* Managing services/zones with `firewalld`

---

### 🔹 7. **Network Services & Daemons**

* Enable and monitor key services:

  * `sshd`, `dhclient`, `NetworkManager`, `systemd-networkd`
* Service management with `systemctl`
* Logging network service activity (`journalctl`, `/var/log/`)

---

### 🔹 8. **Testing and Troubleshooting**

* Test connectivity: `ping`, `curl`, `wget`
* Check open ports: `ss -tuln`, `netstat -tulnp`, `nmap`
* Trace route to remote host: `traceroute`, `mtr`
* Debug DNS issues: `dig`, `host`, `nslookup`
* Use `tcpdump` and `wireshark` for packet capture and analysis

---

### 🔹 9. **DHCP and Static IP Configuration**

* Configure DHCP clients (`dhclient`, `dhcpcd`)
* Set static IP addresses via:

  * Interface files
  * `nmcli` or `nmtui`
  * `netplan`
* Restarting network services

---

### 🔹 10. **Advanced Network Features**

* Bridging interfaces: `brctl`, `ip link add type bridge`
* Bonding (link aggregation): `modprobe bonding`, `ifenslave`, `nmcli`
* VLANs: `ip link add link eth0 name eth0.100 type vlan id 100`
* Network namespaces and virtual interfaces
* Tunneling: GRE, IPIP, etc.

---

### 🔹 11. **SSH and Remote Access**

* Secure Shell basics: `ssh`, `scp`, `sftp`
* SSH key management
* SSH server config: `/etc/ssh/sshd_config`
* Port forwarding with SSH
* Restricting and securing SSH access

---

### 🔹 12. **Proxy, NAT, and Port Forwarding**

* Set up basic NAT with `iptables` or `nftables`
* Configure port forwarding
* Use of HTTP/HTTPS proxies (`http_proxy`, `https_proxy`)
* Configure transparent proxies (e.g., `squid`)

---

### 🔹 13. **Network Monitoring and Analysis**

* Monitor traffic with `iftop`, `iptraf`, `bmon`
* Capture packets with `tcpdump`, analyze with `wireshark`
* Identify bandwidth usage
* Detect open ports and services with `nmap`

---

### 🔹 14. **Network Configuration Systems**

* Traditional tools: `ifconfig`, `system-config-network`
* Modern tools:

  * `NetworkManager` (`nmcli`, `nmtui`)
  * `netplan` (Ubuntu 18.04+)
  * `systemd-networkd`
* Configure persistent settings for reboots

---

### 🔹 15. **Security Considerations**

* Disable unused network services
* Secure SSH access (disable root login, use keys)
* Block unused ports with firewalls
* Monitor for unauthorized open ports or connections
* Use intrusion detection tools (e.g., `fail2ban`, `snort`)

---

## ✅ **Linux Networking Management – Study Checklist**

---

### 🔸 1. Networking Fundamentals

* [ ] Understand TCP/IP and OSI models (layer functions)
* [ ] Identify IPv4 and IPv6 address types and structures
* [ ] Understand subnetting and CIDR notation
* [ ] Differentiate public vs. private IPs
* [ ] Know what DNS does and how name resolution works
* [ ] Understand default gateway and basic routing principles

---

### 🔸 2. Interface Management

* [ ] List and inspect network interfaces: `ip a`, `ifconfig`
* [ ] Bring interfaces up/down: `ip link set`, `ifdown/ifup`
* [ ] Assign static IPs using:

  * Interface config files (`/etc/sysconfig/`, `/etc/network/interfaces`)
  * `nmcli` or `nmtui`
  * `netplan` (Ubuntu)
* [ ] Configure dynamic IPs via DHCP
* [ ] View MAC addresses and link status: `ip link`, `ethtool`

---

### 🔸 3. Essential Networking Commands

* [ ] Use `ping` to test connectivity
* [ ] Trace route with `traceroute` or `mtr`
* [ ] Lookup DNS info: `dig`, `nslookup`, `host`
* [ ] View and manage routes: `ip route`, `route`, `ip r`
* [ ] Monitor connections and ports: `ss`, `netstat`, `lsof -i`
* [ ] View ARP cache: `ip neigh`, `arp`

---

### 🔸 4. Hostname and DNS Configuration

* [ ] Set the hostname using `hostnamectl`
* [ ] Configure DNS manually:

  * `/etc/resolv.conf`
  * Via interface or `netplan`
* [ ] Test name resolution using `ping`, `dig`, `host`

---

### 🔸 5. Routing and Gateways

* [ ] Display the routing table: `ip route`
* [ ] Add and delete static routes: `ip route add/del`
* [ ] Configure persistent routes (via config files)

---

### 🔸 6. Network Services and Daemons

* [ ] Enable and restart networking service (`systemctl restart NetworkManager`)
* [ ] Configure and check `sshd` (SSH daemon)
* [ ] View service logs with `journalctl`, `systemctl status`

---

### 🔸 7. SSH and Remote Access

* [ ] Connect to remote servers using `ssh`
* [ ] Copy files using `scp`, `rsync`, `sftp`
* [ ] Set up SSH key authentication
* [ ] Modify SSH server config (`/etc/ssh/sshd_config`)
* [ ] Restrict SSH access (users, ports, root login)
* [ ] Set up SSH port forwarding (local, remote, dynamic)

---

### 🔸 8. DHCP and Static IP Configuration

* [ ] Configure static IPs via:

  * NetworkManager (`nmcli`)
  * Netplan
  * Legacy interface files
* [ ] Start and stop `dhclient`
* [ ] Verify DHCP leases

---

### 🔸 9. Firewall and Port Control

* [ ] Use `iptables` or `nftables` to:

  * Allow/deny traffic by port/IP
  * Configure NAT/masquerading
* [ ] Manage firewalld zones with `firewall-cmd`
* [ ] Open and close ports
* [ ] Set default policies
* [ ] Save and restore firewall configurations

---

### 🔸 10. Advanced Networking Features

* [ ] Create and manage virtual network interfaces
* [ ] Set up VLANs using `ip link` or `vconfig`
* [ ] Configure network bonding (LACP, active-backup)
* [ ] Create bridges for virtual machines or containers
* [ ] Use `ip netns` for network namespaces

---

### 🔸 11. Proxy and NAT Configuration

* [ ] Configure outbound NAT/masquerading with `iptables/nftables`
* [ ] Set environment variables: `http_proxy`, `https_proxy`, `no_proxy`
* [ ] Use proxy-aware tools (`curl`, `apt`, `yum` with proxies)
* [ ] Configure port forwarding with `iptables`, `nftables`, or `sshd`

---

### 🔸 12. Network Monitoring and Diagnostics

* [ ] Monitor bandwidth and usage with `iftop`, `nload`, `bmon`
* [ ] Capture traffic with `tcpdump`
* [ ] Analyze packets with Wireshark (`.pcap` files)
* [ ] Scan open ports with `nmap`
* [ ] Check logs for networking issues (`/var/log/`, `journalctl`)

---

### 🔸 13. Network Configuration Systems

* [ ] Use legacy tools: `ifconfig`, `route`, `/etc/network/interfaces`
* [ ] Use `NetworkManager` tools: `nmcli`, `nmtui`, `nm-connection-editor`
* [ ] Use `netplan` for Ubuntu 18.04+
* [ ] Understand `systemd-networkd` basics

---

### 🔸 14. Security Best Practices

* [ ] Disable unused interfaces and ports
* [ ] Use firewall rules to limit access
* [ ] Use SSH key authentication (no passwords)
* [ ] Monitor for unauthorized open ports
* [ ] Install and configure `fail2ban` to prevent brute force attacks

---

### 🔸 Bonus: Practice Exercises

* [ ] Configure a static IP and test connectivity
* [ ] Create and test a VLAN or bridge interface
* [ ] Set up and test firewall rules to allow/block specific traffic
* [ ] Set up SSH key authentication and disable password login
* [ ] Capture network traffic with `tcpdump` and analyze it

---

</details>


<details>
  <summary>Filesystem and Disk Management</summary>

## ✅ **Filesystem and Disk Management – Topics Overview**

---

### 🔹 1. **Disk and Storage Device Basics**

* Device naming conventions (`/dev/sda`, `/dev/nvme0n1`, etc.)
* Understanding partitions vs. whole disks
* Viewing disk info: `lsblk`, `blkid`, `fdisk -l`

---

### 🔹 2. **Partitioning Disks**

* Partition types: primary, extended, logical
* Partition tables: MBR vs. GPT
* Tools for partitioning:

  * `fdisk`
  * `parted`
  * `gdisk`
  * `cfdisk`

---

### 🔹 3. **Filesystem Types**

* Common Linux filesystems:

  * `ext2`, `ext3`, `ext4`
  * `xfs`
  * `btrfs`
  * `vfat`, `ntfs`
* Journaling vs. non-journaling filesystems
* Choosing the right filesystem for a use case

---

### 🔹 4. **Creating and Managing Filesystems**

* Creating filesystems: `mkfs` (e.g., `mkfs.ext4`, `mkfs.xfs`)
* Formatting partitions
* Viewing filesystem info: `tune2fs`, `xfs_info`
* Labeling filesystems: `e2label`, `xfs_admin`

---

### 🔹 5. **Mounting and Unmounting Filesystems**

* Mounting manually: `mount`
* Unmounting: `umount`
* Persistent mounts using `/etc/fstab`
* Mounting by:

  * Device name
  * UUID
  * Label
* Mount options (e.g., `noatime`, `ro`, `defaults`)

---

### 🔹 6. **Filesystem Maintenance**

* Checking and repairing filesystems:

  * `fsck`
  * `xfs_repair`
* Resizing filesystems:

  * `resize2fs`, `xfs_growfs`
* Tuning filesystem parameters: `tune2fs`
* File attributes: `lsattr`, `chattr`

---

### 🔹 7. **Swap Space Management**

* What is swap and how it works
* Creating swap partitions/files
* Enabling/disabling swap: `swapon`, `swapoff`
* Viewing swap usage: `free`, `swapon --show`
* Configuring swap in `/etc/fstab`

---

### 🔹 8. **Logical Volume Management (LVM)**

* Concepts: PV, VG, LV
* Creating:

  * Physical volumes (`pvcreate`)
  * Volume groups (`vgcreate`)
  * Logical volumes (`lvcreate`)
* Resizing logical volumes:

  * `lvextend`, `lvreduce`
  * `resize2fs`, `xfs_growfs`
* Viewing LVM info: `pvs`, `vgs`, `lvs`
* Taking and restoring snapshots

---

### 🔹 9. **Disk and Filesystem Usage Monitoring**

* Checking disk space: `df -h`
* Checking directory/file sizes: `du`, `ncdu`
* Checking inode usage: `df -i`
* Finding large files: `find`, `du`, `ncdu`

---

### 🔹 10. **Automounting and Removable Media**

* Mounting USB drives, CDs manually
* Automatic mounting using:

  * `autofs`
  * `udev` rules
* Mounting ISO images: `mount -o loop`

---

### 🔹 11. **Filesystem Quotas**

* Enabling user/group quotas
* Tools:

  * `quota`
  * `edquota`
  * `repquota`
  * `quotacheck`
* Setting soft and hard limits

---

### 🔹 12. **RAID (Software RAID with mdadm)**

* RAID levels: 0, 1, 5, 6, 10
* Creating and managing arrays with `mdadm`
* Checking RAID status (`cat /proc/mdstat`)
* Rebuilding and monitoring arrays

---

### 🔹 13. **File and Disk Backup Tools**

* Archiving: `tar`, `cpio`
* Syncing: `rsync`
* Disk cloning: `dd`
* Backup best practices

---

### 🔹 14. **Encrypted Filesystems (LUKS)**

* Encrypting partitions: `cryptsetup`
* Mounting and unmounting encrypted volumes
* Managing passphrases and keys

---

### 🔹 15. **Network Filesystems**

* Mounting NFS shares: `mount -t nfs`
* Mounting CIFS/SMB shares: `mount -t cifs`
* Persistent network shares in `/etc/fstab`

---

## ✅ Filesystem & Disk Management in Linux – Study Checklist

---

### 🔸 1. Disk and Storage Fundamentals

* [ ] Understand Linux disk naming (e.g. `/dev/sda`, `/dev/nvme0n1`)
* [ ] Identify different storage devices (HDD, SSD, USB, virtual disks)
* [ ] Know the difference between disks and partitions
* [ ] Use `lsblk`, `blkid`, and `fdisk -l` to list disks and partitions

---

### 🔸 2. Partitioning Disks

* [ ] Understand partition types: primary, extended, logical
* [ ] Understand MBR vs GPT partition schemes
* [ ] Create partitions using:

  * [ ] `fdisk` (for MBR)
  * [ ] `gdisk` (for GPT)
  * [ ] `parted`
* [ ] Delete, resize, and label partitions

---

### 🔸 3. Filesystem Types and Concepts

* [ ] Understand journaling vs non-journaling filesystems
* [ ] Compare Linux filesystems:

  * [ ] `ext2`, `ext3`, `ext4`
  * [ ] `xfs`
  * [ ] `btrfs`
  * [ ] `vfat`, `ntfs`
* [ ] Choose an appropriate filesystem for different use cases

---

### 🔸 4. Creating and Managing Filesystems

* [ ] Format partitions using:

  * [ ] `mkfs.ext4`
  * [ ] `mkfs.xfs`
  * [ ] `mkfs.vfat`
* [ ] Label filesystems with `e2label` or `xfs_admin`
* [ ] View filesystem details using `tune2fs` or `xfs_info`

---

### 🔸 5. Mounting and Unmounting Filesystems

* [ ] Mount filesystems manually: `mount`
* [ ] Unmount filesystems: `umount`
* [ ] Use `mount -o` for custom options (e.g., `noatime`, `ro`)
* [ ] Configure persistent mounts in `/etc/fstab`
* [ ] Mount filesystems using UUID or label

---

### 🔸 6. Filesystem Maintenance

* [ ] Check and repair filesystems:

  * [ ] `fsck` (for ext-based FS)
  * [ ] `xfs_repair` (for XFS)
* [ ] Resize filesystems:

  * [ ] `resize2fs` (for ext)
  * [ ] `xfs_growfs`
* [ ] Set file attributes: `chattr`, `lsattr`
* [ ] Tune filesystem options with `tune2fs`

---

### 🔸 7. Swap Space Management

* [ ] Understand the purpose of swap
* [ ] Create swap partitions and swap files
* [ ] Enable/disable swap: `swapon`, `swapoff`
* [ ] View swap usage: `free`, `swapon --show`
* [ ] Add swap entries in `/etc/fstab`

---

### 🔸 8. Logical Volume Management (LVM)

* [ ] Understand LVM components: PV, VG, LV
* [ ] Create physical volumes: `pvcreate`
* [ ] Create volume groups: `vgcreate`
* [ ] Create logical volumes: `lvcreate`
* [ ] Resize LVs:

  * [ ] Extend: `lvextend` + grow filesystem
  * [ ] Reduce: `lvreduce` + shrink FS (carefully!)
* [ ] Display volume info: `pvs`, `vgs`, `lvs`
* [ ] Mount and use LVM volumes
* [ ] Create and use LVM snapshots

---

### 🔸 9. Disk and Filesystem Usage Monitoring

* [ ] Check overall disk space: `df -h`
* [ ] Check directory sizes: `du -sh`, `ncdu`
* [ ] Identify large files
* [ ] Check inode usage: `df -i`
* [ ] Monitor I/O performance: `iostat`, `iotop`

---

### 🔸 10. Filesystem Quotas

* [ ] Understand soft vs hard quotas
* [ ] Enable quota support in filesystem
* [ ] Use `edquota` to set limits
* [ ] Use `repquota` to report usage
* [ ] Use `quotacheck` to scan and update quota database

---

### 🔸 11. Automounting and Removable Media

* [ ] Manually mount USB drives, CDs/DVDs
* [ ] Use `autofs` for on-demand mounting
* [ ] Configure `udev` rules for device-based automounting
* [ ] Mount ISO images using `mount -o loop`

---

### 🔸 12. RAID (Software RAID with `mdadm`)

* [ ] Understand RAID levels (0, 1, 5, 6, 10)
* [ ] Create RAID arrays with `mdadm`
* [ ] Monitor RAID with `/proc/mdstat`
* [ ] Assemble or stop arrays
* [ ] Replace failed drives and rebuild RAID

---

### 🔸 13. Backup and Recovery Tools

* [ ] Create archives: `tar`, `cpio`
* [ ] Use `rsync` for incremental backups
* [ ] Clone disks with `dd`
* [ ] Mount `.iso` and image files

---

### 🔸 14. Encrypted Filesystems

* [ ] Understand LUKS and full-disk encryption
* [ ] Encrypt a partition or file container with `cryptsetup`
* [ ] Open and mount encrypted volumes
* [ ] Configure auto-mounting of encrypted volumes (optional)

---

### 🔸 15. Network Filesystem Support

* [ ] Mount NFS shares: `mount -t nfs`
* [ ] Mount SMB/CIFS shares: `mount -t cifs`
* [ ] Configure persistent mounts for network shares in `/etc/fstab`

---

### 🔸 Bonus Practice Tasks

* [ ] Partition and format a new disk with `ext4`
* [ ] Create and resize an LVM logical volume
* [ ] Set up and test disk quotas for a user
* [ ] Create and mount a swap file
* [ ] Mount a USB drive using UUID and `/etc/fstab`

---
</details>


<details>
  <summary>Process Management</summary>

## ✅ Process Management in Linux – Topics Overview

---

### 🔹 1. **Understanding Linux Processes**

* What is a process?
* Process lifecycle (start, run, wait, terminate)
* Foreground vs. background processes
* Parent and child processes
* PID (Process ID) and PPID (Parent Process ID)

---

### 🔹 2. **Viewing Running Processes**

* Listing processes:

  * `ps`
  * `top` / `htop`
  * `pgrep`, `pidof`
  * `pstree`
* Real-time monitoring with `top`, `htop`, `glances`
* Filtering processes by user, name, PID, TTY, etc.

---

### 🔹 3. **Controlling Processes**

* Start, pause, resume, and terminate processes:

  * `kill`, `killall`
  * `pkill`
  * `nice`, `renice`
  * `fg`, `bg`
  * `jobs`
  * `wait`, `disown`
* Sending signals to processes (e.g., `SIGTERM`, `SIGKILL`, `SIGHUP`)

---

### 🔹 4. **Background and Foreground Jobs**

* Run process in background using `&`
* List jobs with `jobs`
* Bring job to foreground: `fg`
* Send job to background: `bg`
* Use `nohup` and `disown` for persistent background jobs

---

### 🔹 5. **Process Priorities and Scheduling**

* Understanding nice values (range: -20 to 19)
* Set priority with `nice`
* Change priority of running processes with `renice`
* Real-time vs. normal scheduling
* Scheduling classes: `SCHED_OTHER`, `SCHED_FIFO`, `SCHED_RR`
* `chrt` command for real-time scheduling

---

### 🔹 6. **Monitoring Resource Usage**

* View CPU and memory usage:

  * `top`, `htop`
  * `ps aux --sort=-%mem`
  * `vmstat`, `iostat`
* Identify high resource-consuming processes

---

### 🔹 7. **Process Limits and Resource Control**

* View and set limits with `ulimit`
* Soft vs. hard limits
* Persistent limits in `/etc/security/limits.conf`
* Monitor per-process open files and limits:

  * `lsof`
  * `/proc/[pid]/limits`

---

### 🔹 8. **The `/proc` Filesystem**

* Process details in `/proc/[pid]/`
* Files of interest:

  * `status`
  * `cmdline`
  * `cwd`
  * `fd/`
* Use `/proc` to monitor system and process info

---

### 🔹 9. **Zombie and Orphan Processes**

* What is a zombie process?
* How to detect and handle zombies
* What is an orphan process?
* How init/systemd adopts orphaned processes

---

### 🔹 10. **Process Accounting (Optional/Advanced)**

* Enable process accounting with `acct` or `psacct`
* Use `sa`, `lastcomm`, and `accton` for tracking
* Use `auditd` for process-level auditing (security-focused)

---

### 🔹 11. **Systemd and Process Control**

* List and control system services: `systemctl`
* Start, stop, enable, disable background services
* Difference between a system process and a user process
* Understanding systemd unit files (`.service`)

---

### 🔹 12. **Creating and Managing Custom Processes**

* Write and run simple shell scripts as processes
* Run scripts with scheduling (`at`, `cron`, `systemd timers`)
* Create persistent processes using `tmux`, `screen`, or `nohup`

---

### 🔹 13. **Debugging and Tracing Processes (Advanced)**

* Use `strace` to trace system calls
* Use `lsof` to find open files by processes
* Use `gdb` to debug running processes
* Examine memory usage with `pmap`, `smem`

---

## ✅ **Linux Process Management – Study Checklist**

---

### 🔸 1. **Linux Process Fundamentals**

* [ ] Understand what a process is
* [ ] Understand PID (Process ID) and PPID (Parent Process ID)
* [ ] Know the difference between foreground and background processes
* [ ] Understand process states (Running, Sleeping, Zombie, etc.)
* [ ] Learn how Linux creates processes (`fork()`, `exec()`)

---

### 🔸 2. **Listing and Viewing Processes**

* [ ] List all running processes using:

  * [ ] `ps`, `ps aux`, `ps -ef`
  * [ ] `top`
  * [ ] `htop` (if installed)
* [ ] View process tree: `pstree`
* [ ] Find processes by name or user: `pgrep`, `pidof`

---

### 🔸 3. **Foreground & Background Jobs**

* [ ] Run a command in the background using `&`
* [ ] Bring jobs to foreground with `fg`
* [ ] Send jobs to background with `bg`
* [ ] List background jobs using `jobs`
* [ ] Detach jobs using `disown`
* [ ] Use `nohup` to run a job persistently in the background

---

### 🔸 4. **Managing and Controlling Processes**

* [ ] Send signals to processes using:

  * [ ] `kill` (by PID)
  * [ ] `killall` (by name)
  * [ ] `pkill` (by name or pattern)
* [ ] Understand common signals:

  * [ ] `SIGTERM` (15): terminate gracefully
  * [ ] `SIGKILL` (9): force kill
  * [ ] `SIGHUP` (1): reload configuration
* [ ] Pause/resume processes using `CTRL+Z`, `fg`, `bg`
* [ ] Wait for processes to complete using `wait`

---

### 🔸 5. **Process Prioritization**

* [ ] Understand nice values (-20 to 19)
* [ ] Launch a command with a specific priority using `nice`
* [ ] Change the priority of a running process using `renice`
* [ ] Know the impact of priority on CPU scheduling

---

### 🔸 6. **Monitoring CPU and Memory Usage**

* [ ] Monitor CPU usage of processes using:

  * [ ] `top`, `htop`, `ps`
  * [ ] `ps aux --sort=-%cpu`
* [ ] Monitor memory usage:

  * [ ] `ps aux --sort=-%mem`
  * [ ] `free`, `vmstat`, `smem`
* [ ] Use `iotop` or `iostat` to monitor disk I/O by process (if installed)

---

### 🔸 7. **Process Limits and Resource Control**

* [ ] View current limits using `ulimit -a`
* [ ] Set temporary limits using `ulimit`
* [ ] Configure persistent user limits:

  * [ ] `/etc/security/limits.conf`
* [ ] Understand soft vs. hard limits

---

### 🔸 8. **Understanding the `/proc` Filesystem**

* [ ] Navigate `/proc/[PID]/` to inspect:

  * [ ] `status`
  * [ ] `cmdline`
  * [ ] `cwd`
  * [ ] `fd/` (open file descriptors)
* [ ] Understand the role of `/proc` in process monitoring

---

### 🔸 9. **Zombie and Orphan Processes**

* [ ] Define what zombie processes are
* [ ] Detect zombies using `ps` or `top`
* [ ] Know how zombies are cleaned up by the init process
* [ ] Understand orphan processes and how `systemd`/`init` adopts them

---

### 🔸 10. **Systemd and Service-Based Processes**

* [ ] Start, stop, and manage services using `systemctl`
* [ ] Understand how services run as processes
* [ ] Check service status and logs: `systemctl status`, `journalctl`
* [ ] Understand service units and their relation to processes

---

### 🔸 11. **Custom Processes and Background Scripts**

* [ ] Run shell scripts in background
* [ ] Use `tmux` or `screen` to manage persistent sessions
* [ ] Automate process execution using:

  * [ ] `cron` for scheduled tasks
  * [ ] `at` for one-time jobs

---

### 🔸 12. **Debugging and Tracing Processes (Advanced)**

* [ ] Trace system calls with `strace`
* [ ] Monitor open files with `lsof`
* [ ] Debug running processes with `gdb` (basic)
* [ ] Analyze memory maps using `pmap`
* [ ] Monitor file access and activity with `inotify-tools` (optional)

---

### 🔸 13. **Process Accounting (Optional/Advanced)**

* [ ] Install and enable process accounting: `acct`, `psacct`
* [ ] Use tools:

  * [ ] `sa` to summarize command usage
  * [ ] `lastcomm` to view commands by user
  * [ ] `accton` to enable accounting

---

### 🔸 Bonus Practice Tasks

* [ ] Start a long-running job in the background and bring it to foreground
* [ ] Kill a process by name using `pkill` and by PID using `kill`
* [ ] Adjust a running process's priority using `renice`
* [ ] Monitor the top 5 CPU-consuming processes
* [ ] View the full environment of a running process using `/proc/[PID]/environ`

---
</details>

<details>
  <summary>Permission Management</summary>

## ✅ **Permission Management in Linux – Topics Overview**

---

### 🔹 1. **Understanding File Permissions**

* Linux file permission model: User, Group, Others
* Read (r), Write (w), Execute (x) permissions
* Default permissions for files and directories
* Permission notation:

  * Symbolic (`rwxr-xr--`)
  * Octal (`755`, `644`, etc.)

---

### 🔹 2. **Changing Permissions**

* Use of `chmod`:

  * Symbolic mode (`chmod u+x file`)
  * Numeric mode (`chmod 755 file`)
* Recursive permission changes (`chmod -R`)
* When and how to give execute permissions

---

### 🔹 3. **Understanding and Changing Ownership**

* Owners: User and Group
* View ownership with `ls -l`
* Change ownership with:

  * `chown` (change user and/or group)
  * `chgrp` (change group only)
* Recursive ownership changes (`chown -R`)

---

### 🔹 4. **Default Permissions and `umask`**

* What is `umask` and how it works
* Calculating default permissions using `umask`
* Set temporary `umask` value
* Configure persistent `umask` (e.g., in `~/.bashrc`, `/etc/profile`)

---

### 🔹 5. **Special Permission Bits**

* **Setuid (`s`)**:

  * Executable runs with the file owner's privileges
  * Used in commands like `passwd`
* **Setgid (`s`)**:

  * On files: run with group’s privileges
  * On directories: new files inherit group
* **Sticky bit (`t`)**:

  * Used on shared directories (e.g., `/tmp`)
  * Only file owner can delete

---

### 🔹 6. **Access Control Lists (ACLs)**

* Extended permissions beyond standard `ugo`
* Enable ACLs on filesystem (if not by default)
* Use `getfacl` to view ACLs
* Use `setfacl` to:

  * Set user or group-specific permissions
  * Set default ACLs on directories
* Remove ACLs with `setfacl -x` or `setfacl -b`

---

### 🔹 7. **File and Directory Permissions Behavior**

* Execute bit on directories (controls access to content)
* Read vs execute on directories
* Permissions required to:

  * Enter a directory
  * List files
  * Read or write files

---

### 🔹 8. **Symbolic and Hard Links and Permissions**

* How permissions work with symbolic (`ln -s`) and hard (`ln`) links
* Effects of changing permissions on the link vs the target

---

### 🔹 9. **Permission Management Tools**

* `ls -l`, `stat` – view detailed permissions
* `chmod`, `chown`, `chgrp` – change permissions
* `getfacl`, `setfacl` – ACL tools
* `find` – to locate files by permission (`-perm` flag)

---

### 🔹 10. **Security and Best Practices**

* Least privilege principle
* Securing sensitive files (e.g., `/etc/shadow`)
* Avoid giving write access to "others"
* Use group-based permission strategies
* Logging permission changes (auditd, `auditctl`)

---

### 🔹 11. **File Permission Defaults for New Files**

* How umask affects new files and directories
* Set directory default ACLs for collaborative environments
* Use skeleton files (`/etc/skel/`) for setting initial user configs

---

### 🔹 12. **Permissions in Multi-User Environments**

* Use of shared groups for team directories
* Setgid on directories for group file inheritance
* Sticky bit for shared temp folders
* Preventing unauthorized file deletion

---

## ✅ **Linux Permission Management – Study Checklist**

---

### 🔸 1. **Understanding File Permissions**

* [ ] Understand the Linux permission model: User, Group, Others
* [ ] Identify read (`r`), write (`w`), and execute (`x`) permissions
* [ ] Interpret symbolic permissions (e.g. `rwxr-xr--`)
* [ ] Interpret numeric/octal permissions (e.g. `755`, `644`)
* [ ] Use `ls -l` to view file permissions

---

### 🔸 2. **Modifying Permissions**

* [ ] Change file permissions using `chmod`

  * [ ] Symbolic mode (`u+x`, `g-w`, etc.)
  * [ ] Numeric mode (`chmod 755 filename`)
* [ ] Apply permissions recursively with `chmod -R`
* [ ] Understand how permissions apply differently to files vs. directories

---

### 🔸 3. **File and Directory Ownership**

* [ ] View file owner and group using `ls -l` or `stat`
* [ ] Change file owner using `chown`
* [ ] Change group ownership using `chgrp`
* [ ] Recursively change ownership with `chown -R`

---

### 🔸 4. **Default Permissions and `umask`**

* [ ] Understand how default permissions are determined
* [ ] Calculate final permissions using `umask`
* [ ] View current `umask` with `umask` command
* [ ] Set persistent `umask` in shell config files (e.g. `~/.bashrc`, `/etc/profile`)

---

### 🔸 5. **Special Permission Bits**

* [ ] Understand and set **Setuid** (`chmod u+s`)

  * [ ] Verify with `ls -l` (`s` in user field)
* [ ] Understand and set **Setgid** (`chmod g+s`)

  * [ ] Used in shared directories for group inheritance
* [ ] Understand and set **Sticky bit** (`chmod +t`)

  * [ ] Used to secure public directories like `/tmp`

---

### 🔸 6. **Access Control Lists (ACLs)**

* [ ] Understand the need for ACLs (fine-grained permissions)
* [ ] View current ACLs using `getfacl`
* [ ] Set ACLs using `setfacl` (e.g., `setfacl -m u:john:rw file.txt`)
* [ ] Set default ACLs for directories
* [ ] Remove ACLs with `setfacl -x` or clear all with `setfacl -b`
* [ ] Ensure filesystem is mounted with ACL support

---

### 🔸 7. **Working with Directory Permissions**

* [ ] Understand execute (`x`) permission on directories
* [ ] Know what’s required to:

  * [ ] List directory contents
  * [ ] Enter directory
  * [ ] Read/write files inside
* [ ] Practice secure directory setups (e.g., `chmod 700 ~/private`)

---

### 🔸 8. **Links and Permissions**

* [ ] Understand how permissions work with symbolic links
* [ ] Understand how permissions work with hard links
* [ ] Know that `chmod` on symlink affects the target (not the link itself)

---

### 🔸 9. **Permission Tools and Utilities**

* [ ] Use `ls`, `stat` to inspect permissions
* [ ] Use `chmod`, `chown`, `chgrp` to manage them
* [ ] Use `find` to locate files with specific permissions (`-perm`)
* [ ] Use `namei` to troubleshoot path permission issues
* [ ] Use `lsof` to check open files by process

---

### 🔸 10. **Multi-User Security Practices**

* [ ] Use shared groups for collaborative access
* [ ] Use Setgid on directories for consistent group ownership
* [ ] Use the sticky bit to prevent file deletion in shared dirs
* [ ] Avoid giving write permission to “others”
* [ ] Restrict file access with strict `umask` (e.g., `077`)

---

### 🔸 11. **System Files and Security**

* [ ] Understand critical file permissions (e.g., `/etc/passwd`, `/etc/shadow`)
* [ ] Secure configuration files with appropriate ownership and modes
* [ ] Prevent privilege escalation by locking down world-writable files
* [ ] Check system for misconfigured permissions with `find`

---

### 🔸 12. **Practice and Troubleshooting**

* [ ] Practice setting permissions and ownership on files/directories
* [ ] Create a shared group folder with ACLs or Setgid
* [ ] Debug "Permission denied" errors with `ls`, `stat`, `namei`, or `sudo`
* [ ] Set up sticky bit on `/tmp`-like directories and test deletion protection
* [ ] Practice interpreting permission modes under timed conditions
* [ ] Write commands to correct permission/ownership for given scenarios
* [ ] Use `find / -perm -4000` to detect SUID binaries (common exam topic)

</details>

<details>
  <summary>System Monitoring and Performance Tuning</summary>

---

### **1. System Monitoring Basics**

* Understanding system performance metrics (CPU, memory, disk, network)
* Real-time vs historical monitoring
* Logging vs monitoring

---

### **2. CPU Monitoring**

* Load average interpretation (`uptime`, `top`, `w`)
* CPU usage (`top`, `htop`, `mpstat`, `vmstat`, `sar`)
* Identifying CPU bottlenecks

---

### **3. Memory Monitoring**

* RAM and swap usage (`free`, `vmstat`, `top`, `smem`, `sar`)
* Page faults and memory leaks
* Buffer vs cache memory
* OOM (Out of Memory) killer analysis

---

### **4. Disk and I/O Monitoring**

* Disk usage (`df`, `du`)
* I/O performance (`iostat`, `iotop`, `dstat`, `blktrace`)
* Filesystem performance and tuning (`tune2fs`, journaling options)
* Disk latency and throughput analysis

---

### **5. Network Monitoring**

* Bandwidth usage (`iftop`, `nload`, `ip -s link`)
* Network connections (`netstat`, `ss`, `lsof`)
* Packet analysis and sniffing (`tcpdump`, `wireshark`)
* Latency and packet loss (`ping`, `mtr`, `traceroute`)
* Network congestion and tuning (TCP window size, buffers)

---

### **6. Process Monitoring and Management**

* Process resource usage (`ps`, `top`, `htop`, `nice`, `renice`)
* Zombie and orphan processes
* Service monitoring (`systemctl`, `service`)
* Cgroups for resource control

---

### **7. Logs and Event Monitoring**

* System logs (`/var/log/`, `journalctl`, `rsyslog`, `syslog-ng`)
* Log rotation and management (`logrotate`)
* Kernel logs and dmesg
* Audit logs (`auditd`, `ausearch`)

---

### **8. System Tuning Tools and Techniques**

* `sysctl` and `/etc/sysctl.conf` tuning
* Kernel parameters (e.g., for networking, memory management)
* `ulimit` and resource limits
* Tuning swappiness and cache pressure

---

### **9. Benchmarking Tools**

* `stress`, `stress-ng` for load testing
* `sysbench` for CPU, memory, I/O, MySQL
* `fio` for file I/O benchmarking
* `phoronix-test-suite`

---

### **10. Performance Profiling and Tracing**

* `perf` (Linux performance counters)
* `strace` (system call tracing)
* `ltrace` (library call tracing)
* `ftrace`, `bpftrace`, `eBPF`, `SystemTap`
* Flame graphs for visual profiling

---

### **11. System Resource Scheduling and Optimization**

* Nice values and CPU affinity
* I/O schedulers (CFQ, deadline, noop, BFQ)
* Tuning priority of services (cgroups, systemd slices)

---

### **12. Monitoring and Alerting Tools**

* **Command-line tools**: `top`, `htop`, `iotop`, `dstat`, `atop`
* **System monitoring suites**:

  * **Nagios**, **Zabbix**, **Icinga**
  * **Prometheus** + **Grafana**
  * **Netdata**
  * **Glances**
* **Logging and observability stacks**: ELK Stack (Elasticsearch, Logstash, Kibana), Graylog

---

### **13. Virtualization and Container Performance**

* Monitoring virtual machines (KVM, QEMU, libvirt tools)
* Container resource usage (`docker stats`, `cgroup` analysis)
* Kubernetes monitoring (Prometheus, cAdvisor, kube-state-metrics)

---

### **14. Automation and Scripting**

* Automating monitoring scripts (Bash, Python)
* Scheduled monitoring and alerts (cron jobs)
* Integration with alert systems (email, Slack, PagerDuty)

---

### **15. Security and Audit Performance**

* Audit system performance impacts
* Monitoring unauthorized access or system misuse
* Fail2ban, auditd performance considerations

---

## ✅ **Linux System Monitoring & Performance Tuning – Study Checklist**

---

###  **1. Fundamentals of System Monitoring**

* [ ] Understand what system monitoring entails
* [ ] Learn the difference between real-time and historical monitoring
* [ ] Familiarize yourself with key system resources (CPU, memory, disk, network)
* [ ] Learn the Linux system boot process (relevant for root cause analysis)

---

###  **2. CPU Monitoring**

* [ ] Understand load average (`uptime`, `top`, `w`)
* [ ] Monitor CPU usage with `top`, `htop`
* [ ] Use `mpstat`, `vmstat`, `sar` for deeper insights
* [ ] Identify CPU bottlenecks and high CPU-consuming processes
* [ ] Learn how to adjust process priority (`nice`, `renice`, `taskset`)

---

###  **3. Memory Monitoring**

* [ ] Check memory and swap usage (`free`, `vmstat`, `top`, `htop`)
* [ ] Understand buffer/cache memory
* [ ] Monitor swap behavior and usage patterns
* [ ] Analyze memory leaks using `smem`, `ps`, `valgrind`
* [ ] Understand and analyze the OOM Killer logs (`dmesg`, `/var/log/messages`)

---

###  **4. Disk & I/O Monitoring**

* [ ] Check disk usage (`df`, `du`)
* [ ] Monitor I/O with `iostat`, `iotop`, `dstat`, `blktrace`
* [ ] Understand disk latency and throughput
* [ ] Analyze filesystem performance (ext4, xfs tuning options)
* [ ] Learn about I/O schedulers (`noop`, `deadline`, `cfq`, `bfq`)
* [ ] Use `tune2fs` and `mount` options for filesystem tuning

---

###  **5. Network Monitoring**

* [ ] Monitor bandwidth usage (`iftop`, `nload`, `vnstat`)
* [ ] List open ports and connections (`netstat`, `ss`, `lsof`)
* [ ] Analyze traffic using `tcpdump`, `wireshark`
* [ ] Check network latency and packet loss (`ping`, `mtr`, `traceroute`)
* [ ] Tune network stack with `sysctl` parameters (e.g., TCP buffer sizes)

---

###  **6. Process Monitoring & Management**

* [ ] Monitor processes with `ps`, `top`, `htop`
* [ ] Identify zombie and orphan processes
* [ ] Manage background jobs and services (`systemctl`, `service`, `jobs`)
* [ ] Use `cgroups` to limit CPU and memory usage
* [ ] Create and apply custom service unit files in `systemd`

---

###  **7. Logging and Audit Monitoring**

* [ ] View and filter system logs (`journalctl`, `/var/log/`)
* [ ] Configure `rsyslog`, `syslog-ng`, or `journald`
* [ ] Set up log rotation with `logrotate`
* [ ] Enable and analyze logs with `auditd`, `ausearch`, `aureport`
* [ ] Track kernel messages using `dmesg`

---

###  **8. Kernel and System Tuning**

* [ ] Learn how to read and change kernel parameters with `sysctl`
* [ ] Configure `/etc/sysctl.conf`
* [ ] Understand and tune `vm.swappiness`, `dirty_ratio`, `cache_pressure`
* [ ] Set process resource limits with `ulimit` and `/etc/security/limits.conf`
* [ ] Explore CPU affinity and real-time tuning (`taskset`, `chrt`)

---

###  **9. Benchmarking Tools**

* [ ] Use `stress`, `stress-ng` for CPU and memory stress tests
* [ ] Benchmark disk I/O with `fio`
* [ ] Use `sysbench` for CPU, memory, file I/O, and MySQL
* [ ] Try `phoronix-test-suite` for comprehensive benchmarking
* [ ] Compare pre- and post-tuning performance

---

###  **10. Profiling & Tracing Tools**

* [ ] Monitor system calls with `strace`, `ltrace`
* [ ] Use `perf` for CPU profiling
* [ ] Learn basics of `ftrace`, `bpftrace`, and `SystemTap`
* [ ] Visualize performance with flame graphs
* [ ] Trace long-running system issues with eBPF tools

---

###  **11. Monitoring and Alerting Tools**

#### Command-line tools:

* [ ] `top`, `htop`, `iotop`, `nmon`, `atop`, `glances`

#### Monitoring stacks:

* [ ] Install and configure **Prometheus**
* [ ] Set up **Grafana** dashboards
* [ ] Use **node_exporter** or **collectd**
* [ ] Try **Netdata** for real-time monitoring
* [ ] Compare **Nagios**, **Zabbix**, **Icinga**

#### Alerting:

* [ ] Set up alert rules in Prometheus or Zabbix
* [ ] Send alerts via email, Slack, PagerDuty, etc.

---

###  **12. Virtualization and Containers**

* [ ] Monitor VMs with `virt-top`, `virsh`, `libvirt`
* [ ] Use `docker stats` for container performance
* [ ] Apply cgroups limits to Docker containers
* [ ] Set up Prometheus + cAdvisor for container metrics
* [ ] Monitor Kubernetes with `kube-state-metrics`, `metrics-server`

---

###  **13. Automation and Scripting**

* [ ] Write Bash scripts to automate monitoring tasks
* [ ] Schedule monitoring scripts with `cron`
* [ ] Parse logs and metrics with `awk`, `sed`, `grep`
* [ ] Integrate scripts with alerting systems (mail, webhook, Slack)

---

###  **14. Security and Audit Performance**

* [ ] Analyze audit logs without degrading performance
* [ ] Monitor failed login attempts (`faillog`, `lastb`)
* [ ] Use `fail2ban` to block brute-force attacks
* [ ] Check for rootkits with `chkrootkit`, `rkhunter`
* [ ] Understand how security tools impact system performance

---

###  **15. Projects to Practice**

* [ ] Create a resource dashboard using Prometheus + Grafana
* [ ] Simulate load and optimize performance using tuning parameters
* [ ] Build a container monitoring solution with Docker + cAdvisor
* [ ] Write a script to alert when CPU or memory usage exceeds a threshold
* [ ] Analyze a performance issue from a real or simulated Linux server

---
</details>

<details>
  <summary>Text Processing</summary>

---

### 1. File Viewing and Navigation

* `cat`, `tac` – Display contents of files (forward/reverse)
* `more`, `less` – Paginated viewing
* `head`, `tail` – Display the beginning or end of files
* `nl` – Number lines in a file

### 2. Searching and Filtering

* `grep`, `egrep`, `fgrep` – Pattern matching with regular expressions
* Recursive searches and context options (`-r`, `-A`, `-B`, `-C`)
* Combining `find` with `grep` for targeted searches

### 3. Cutting, Splitting, and Joining

* `cut` – Extract specific fields or columns
* `awk` – Pattern scanning and field-based processing
* `sed` – Stream editing (substitute, delete, insert, append)
* `tr` – Translate or delete characters
* `split`, `csplit` – Split files by size or pattern
* `paste` – Merge lines side by side
* `join` – Join files on a common field

### 4. Sorting and Uniqueness

* `sort` – Sort lines in files
* `uniq` – Remove or count duplicate lines
* `comm` – Compare two sorted files line by line
* `diff`, `sdiff` – Display differences between files

### 5. Counting and Statistics

* `wc` – Count lines, words, characters, bytes
* Using `awk` for aggregation and statistical summaries
* Frequency counts using `cut`, `sort`, and `uniq -c`

### 6. Text Substitution and Transformation

* `sed` – Pattern substitution and text transformations
* `awk` – Field editing and record reformatting
* `tr` – Character-level transformations (e.g. case conversion)

### 7. Formatting and Alignment

* `fmt` – Reformat text with line wrapping
* `pr` – Format text for printing (headers, pagination)
* `column` – Align tabular data in columns
* `expand`, `unexpand` – Convert tabs to spaces and vice versa
* `fold` – Wrap long lines to a specific width
* `nl` – Line numbering with formatting options

### 8. Regular Expressions

* Basic and extended regular expressions
* Used with `grep`, `sed`, `awk`, `perl`, `find`, etc.
* Anchors, quantifiers, character classes, groups

### 9. Text Archival and Compression Tools (Optional for Text Pipelines)

* `gzip`, `gunzip`, `zcat`
* `bzip2`, `xz`, `zip`, `tar`
* Searching within compressed files using `zgrep`, `zcat`, etc.

### 10. Pipelining and Tool Chaining

* Combining tools with pipes (`|`)
* Building processing chains like:
  `cat file | grep error | awk '{print $5}' | sort | uniq -c`

### 11. Advanced and Structured Data Tools

* `jq` – JSON parsing and formatting
* `yq` – YAML processing
* `xmlstarlet` – XML parsing and transformation
* `perl` – Advanced text and regex processing
* `python` (with `re`, `csv`, `json`, `pandas`) for complex tasks

### 12. Common Use Cases in System Administration

* Parsing and analyzing log files
* Extracting values from configuration files
* Bulk editing or formatting of text files
* Automating reports and summaries from text data
* Processing CSV/TSV or other delimited files

---

## ✅ Text Processing in Linux Administration – Study Checklist

---

### 1. **File Viewing and Navigation**

* [ ] Learn to use `cat` and `tac` to view files
* [ ] View files page-by-page using `more` and `less`
* [ ] Display the first and last N lines of files with `head` and `tail`
* [ ] Use `nl` to number lines of a file

---

### 2. **Text Searching and Filtering**

* [ ] Use `grep` for basic string matching
* [ ] Use `egrep`/`grep -E` for extended regular expressions
* [ ] Filter by inverted match, count occurrences, and show line numbers
* [ ] Use context options: `-A`, `-B`, `-C`
* [ ] Search recursively in directories with `grep -r`
* [ ] Combine `find` and `grep` for targeted search

---

### 3. **Text Cutting, Splitting, and Joining**

* [ ] Use `cut` to extract specific columns or fields
* [ ] Use `awk` to parse fields, filter rows, and generate formatted output
* [ ] Learn basic `awk` syntax: `BEGIN`, `END`, field access `$1`, `$2`, etc.
* [ ] Use `sed` for search and replace in streams/files
* [ ] Use `tr` to translate or delete characters
* [ ] Use `split` and `csplit` to divide files by size or pattern
* [ ] Combine lines using `paste`
* [ ] Join lines from two files using `join` based on common fields

---

### 4. **Sorting and Removing Duplicates**

* [ ] Sort files alphabetically and numerically using `sort`
* [ ] Sort by specific fields using `sort -k`
* [ ] Sort in reverse or stable order
* [ ] Remove duplicates using `uniq`
* [ ] Count duplicates using `uniq -c`
* [ ] Compare files line-by-line with `comm`, `diff`, and `sdiff`

---

### 5. **Text Counting and Statistics**

* [ ] Count lines, words, characters, and bytes with `wc`
* [ ] Use `awk` for calculating sums, averages, and other statistics
* [ ] Combine `cut`, `sort`, and `uniq -c` for frequency analysis

---

### 6. **Text Substitution and Transformation**

* [ ] Use `sed` to:

  * Substitute text (`s/old/new/`)
  * Delete or insert lines
  * Work with in-place editing (`-i`)
* [ ] Use `awk` to:

  * Replace and reformat fields
  * Perform conditional substitutions
* [ ] Use `tr` to:

  * Change case
  * Delete whitespace or specific characters

---

### 7. **Text Formatting and Alignment**

* [ ] Format long lines with `fmt`
* [ ] Format for printing with `pr` (headers, columns)
* [ ] Format tabular data using `column`
* [ ] Convert tabs to spaces using `expand`
* [ ] Convert spaces to tabs using `unexpand`
* [ ] Wrap long lines using `fold`
* [ ] Add or customize line numbers with `nl`

---

### 8. **Regular Expressions (Regex)**

* [ ] Understand basic regex syntax:

  * `^`, `$`, `.`, `*`, `+`, `?`, `[]`, `()`
* [ ] Learn extended regex (`grep -E`)
* [ ] Practice grouping and alternation (`(a|b)`, `a{2,3}`)
* [ ] Apply regex with `grep`, `sed`, `awk`, `perl`
* [ ] Test expressions with sample text files

---

### 9. **Working with Compressed Text Files**

* [ ] Use `gzip`, `bzip2`, `xz`, and `zip` for compression
* [ ] Use `zcat`, `zless`, `zgrep` for working with compressed logs
* [ ] Use `tar` with compression options (`-czf`, `-xzf`, etc.)

---

### 10. **Combining Tools in Pipelines**

* [ ] Practice using pipes (`|`) to combine commands
* [ ] Build common processing pipelines:

  * `cat file | grep pattern | awk '{print $2}' | sort | uniq -c`
* [ ] Redirect input/output using `<`, `>`, `>>`, `2>`, `&>`, etc.

---

### 11. **Advanced Structured Data Processing**

* [ ] Parse and format JSON using `jq`
* [ ] Parse YAML files using `yq`
* [ ] Process XML using `xmlstarlet`
* [ ] Use `perl` for advanced text and regex operations
* [ ] Write simple `python` scripts with `re`, `csv`, or `json` modules

---

### 12. **System Administration Use Cases**

* [ ] Extract information from system log files (`/var/log/`)
* [ ] Parse Apache/Nginx logs or system audit logs
* [ ] Edit or validate configuration files in bulk
* [ ] Generate simple text reports (e.g., top IP addresses from logs)
* [ ] Process CSV/TSV data for reporting or alerts
* [ ] Monitor real-time log data with `tail -f | grep`

---

### 13. **Project for Practice**

* [ ] Build a log parser that extracts IPs and counts them
* [ ] Create a script that summarizes disk usage per directory
* [ ] Develop a tool that watches a log file for errors in real time
* [ ] Write a report generator using `awk` for a CSV export
* [ ] Automate text substitution across multiple config files

---

</details>

<details>
  <summary>Archiving and Compression</summary>

---

## Archiving and Compression Topics in Linux Administration

---

### 1. **Concepts and Fundamentals**

* Differences between archiving and compression
* File extensions and format recognition (e.g. `.tar`, `.gz`, `.zip`, `.xz`)
* Compression ratios and performance trade-offs
* Lossless vs lossy compression (note: Linux admin uses are mostly lossless)

---

### 2. **Archiving with `tar`**

* Creating archives with `tar -cf`
* Extracting files with `tar -xf`
* Listing archive contents with `tar -tf`
* Archiving directories and preserving permissions
* Verbose mode (`-v`) to show file progress
* Absolute vs relative paths inside archives
* Excluding files (`--exclude`, `--exclude-from`)
* Using wildcards and patterns in `tar`

---

### 3. **Compression Tools and Formats**

#### gzip

* Compress files with `gzip`
* Decompress files with `gunzip`
* View contents without extracting using `zcat`, `zmore`, `zless`
* Set compression levels with `-1` to `-9`

#### bzip2

* Compress with `bzip2`
* Decompress with `bunzip2`
* Use `bzcat`, `bzmore`, `bzless` for reading

#### xz

* Compress with `xz`
* Decompress with `unxz`
* Use `xzcat` to view contents

#### zip and unzip

* Create ZIP archives with `zip`
* Extract files with `unzip`
* List contents of ZIP files
* Password protection options
* Recursive directory compression

---

### 4. **Combined Archiving and Compression**

* Create compressed archives:

  * `.tar.gz` using `tar -czf`
  * `.tar.bz2` using `tar -cjf`
  * `.tar.xz` using `tar -cJf`
* Extract compressed archives:

  * `tar -xzf` (for `.tar.gz`)
  * `tar -xjf` (for `.tar.bz2`)
  * `tar -xJf` (for `.tar.xz`)

---

### 5. **Multi-File and Split Compression**

* Splitting large files into parts with `split`
* Reassembling with `cat` or `tar --concatenate`
* Use of `zip` with split volumes (`zip -s`)
* Compressing each file individually in a directory

---

### 6. **Archiving Metadata and Permissions**

* Preserving symbolic links, owners, permissions (`tar -p`, `--preserve`)
* Working with `cpio` for backups and permission retention
* Archive file integrity with checksums

---

### 7. **Backup and Restore Use Cases**

* Creating full system backups with `tar`
* Automating scheduled backups with `cron`
* Compressing logs and rotating them (`logrotate`, with compression)
* Remote archive transfer using `ssh` + `tar`
* Incremental backups (e.g., `tar --listed-incremental`)

---

### 8. **Archive Inspection and Validation**

* Viewing contents without extraction
* Testing compressed files for corruption (`gzip -t`, `unzip -t`)
* Verifying checksums (`md5sum`, `sha256sum`, `shasum`)

---

### 9. **Graphical Compression Tools (Optional)**

* Use of GUI tools like:

  * `file-roller` (GNOME)
  * `ark` (KDE)
* Integrating GUI tools with desktop environments

---

### 10. **Advanced Compression Utilities (Optional/Advanced)**

* `7z` (p7zip): high compression ratio tool
* `lrzip`: large file compression
* `zstd`: fast compression with good ratio
* Comparison: gzip vs bzip2 vs xz vs zstd

---

## ✅ Archiving and Compression in Linux – Study Checklist

---

### 1. **Core Concepts**

* [ ] Understand the difference between archiving and compression
* [ ] Identify common archive and compression file extensions (`.tar`, `.gz`, `.bz2`, `.xz`, `.zip`)
* [ ] Know when to use compression vs just archiving
* [ ] Understand compression ratios and trade-offs in speed vs size

---

### 2. **Archiving with `tar`**

* [ ] Create archives using `tar -cf archive.tar file1 file2`
* [ ] Extract files from an archive using `tar -xf archive.tar`
* [ ] List archive contents with `tar -tf archive.tar`
* [ ] Archive entire directories recursively
* [ ] Use verbose output with `tar -v` to see included files
* [ ] Preserve file permissions and symbolic links (`-p`, `--preserve`)
* [ ] Exclude files or directories using `--exclude` or `--exclude-from=file`
* [ ] Use relative paths to avoid full path restoration

---

### 3. **Compressing and Decompressing Files**

#### gzip

* [ ] Compress files using `gzip file`
* [ ] Decompress `.gz` files using `gunzip file.gz`
* [ ] View contents with `zcat`, `zless`, `zmore`
* [ ] Set compression levels with `gzip -1` to `-9`

#### bzip2

* [ ] Compress files using `bzip2 file`
* [ ] Decompress using `bunzip2 file.bz2`
* [ ] View with `bzcat`, `bzless`, `bzmore`

#### xz

* [ ] Compress with `xz file`
* [ ] Decompress with `unxz file.xz`
* [ ] Use `xzcat` to view without extracting

#### zip/unzip

* [ ] Create zip archives using `zip archive.zip file1 file2`
* [ ] Extract with `unzip archive.zip`
* [ ] List contents using `unzip -l archive.zip`
* [ ] Use password protection with `zip -e`
* [ ] Compress directories recursively with `zip -r`

---

### 4. **Combining Archiving and Compression**

* [ ] Create `.tar.gz` using `tar -czf archive.tar.gz files`
* [ ] Create `.tar.bz2` using `tar -cjf archive.tar.bz2 files`
* [ ] Create `.tar.xz` using `tar -cJf archive.tar.xz files`
* [ ] Extract compressed archives:

  * `tar -xzf` for `.tar.gz`
  * `tar -xjf` for `.tar.bz2`
  * `tar -xJf` for `.tar.xz`

---

### 5. **Working with Split and Large Files**

* [ ] Split large files into chunks using `split -b 100M file part_`
* [ ] Recombine parts using `cat part_* > full_file`
* [ ] Create split ZIP archives using `zip -s 100m -r archive.zip folder/`
* [ ] Use `tar` with `--tape-length` for splitting (less common)

---

### 6. **Archiving Metadata and Special Files**

* [ ] Preserve ownership, permissions, timestamps with `tar --preserve`
* [ ] Handle symbolic and hard links in archives
* [ ] Include hidden files and directories
* [ ] Use `cpio` as an alternative archiving tool with permission support

---

### 7. **Backup and Restore Use Cases**

* [ ] Use `tar` to back up a directory and compress it (`tar -czf backup.tar.gz /etc`)
* [ ] Automate backups using `cron` and shell scripts
* [ ] Use `logrotate` for compressing rotated log files
* [ ] Perform full vs incremental backups (`tar --listed-incremental`)
* [ ] Transfer archives over SSH (`tar -czf - /dir | ssh user@host 'cat > backup.tar.gz'`)

---

### 8. **Archive Inspection and Integrity**

* [ ] View archive contents without extracting (`tar -tf`, `unzip -l`)
* [ ] Test `.gz` files with `gzip -t`
* [ ] Test `.zip` files with `unzip -t`
* [ ] Validate file integrity using checksums (`md5sum`, `sha256sum`)
* [ ] Compare extracted files with originals using `diff`, `cmp`

---

### 9. **Advanced Compression Tools (Optional)**

* [ ] Use `7z` (p7zip) for high-compression formats
* [ ] Install and use `zstd` for fast and efficient compression
* [ ] Compare performance and speed of gzip vs bzip2 vs xz vs zstd
* [ ] Use `lrzip` for compressing large files with redundancy

---

### 10. **Scripting and Automation**

* [ ] Write scripts to back up and compress files automatically
* [ ] Log each backup with a timestamp
* [ ] Automate archiving of rotated logs
* [ ] Schedule recurring tasks with `cron` or `systemd timers`

---

### 11. **Optional: Graphical Compression Tools**

* [ ] Use GUI tools like:

  * `file-roller` (GNOME)
  * `ark` (KDE)
* [ ] Compress/extract files from GUI file managers

---

### 12. **Project for Practice**

* [ ] Create a full backup script for `/etc` with timestamped archives
* [ ] Compress and archive logs older than 7 days using `find` and `tar`
* [ ] Create a multi-part ZIP archive and test extraction
* [ ] Write a script that verifies archive integrity after creation
* [ ] Schedule a daily cron job to back up and compress a directory

---
</details>

<details>
  <summary>System Hardware and Kernel Management</summary>

---

##  System Hardware and Kernel Management in Linux – Topics List

---

### 1. **System Hardware Overview**

* Identifying hardware components (CPU, RAM, disks, etc.)
* Understanding the role of firmware/BIOS/UEFI
* Motherboard components and chipset awareness
* Hardware abstraction in Linux

---

### 2. **Hardware Information and Diagnostics**

* Viewing CPU info: `lscpu`, `/proc/cpuinfo`
* Viewing memory info: `free`, `vmstat`, `/proc/meminfo`
* Viewing PCI devices: `lspci`
* Viewing USB devices: `lsusb`
* Viewing block devices: `lsblk`, `blkid`, `fdisk`, `parted`
* General hardware overview: `lshw`, `hwinfo`
* Monitoring sensors and temperatures: `lm-sensors`, `sensors`
* Power management and ACPI: `acpi`, `/proc/acpi/`

---

### 3. **Kernel Basics**

* Role of the Linux kernel
* Kernel architecture overview (monolithic, modular)
* Kernel versioning and naming conventions
* Viewing kernel version: `uname -r`, `uname -a`
* Checking active kernel modules: `lsmod`

---

### 4. **Kernel Modules Management**

* Listing loaded modules: `lsmod`
* Loading modules: `modprobe`, `insmod`
* Unloading modules: `rmmod`, `modprobe -r`
* Viewing module dependencies: `modinfo`
* Managing `/etc/modules-load.d/` and `/etc/modprobe.d/`
* Blacklisting modules

---

### 5. **Kernel Parameters and Tuning**

* Viewing runtime kernel parameters: `sysctl`, `/proc/sys/`
* Modifying parameters temporarily: `sysctl -w`
* Persisting changes: `/etc/sysctl.conf` or `/etc/sysctl.d/*.conf`
* Common tunables:

  * `vm.swappiness`
  * `fs.file-max`
  * `net.ipv4.*`
* Security-related kernel parameters (e.g., disabling IP forwarding)

---

### 6. **Custom Kernel Compilation (Advanced/Optional)**

* Downloading kernel source from kernel.org
* Kernel configuration tools: `make menuconfig`, `make xconfig`
* Compiling the kernel: `make`, `make modules`, `make install`
* Installing and updating GRUB for new kernel versions
* Building custom modules or patching kernel code

---

### 7. **Boot Process and Kernel Interaction**

* Linux boot sequence: BIOS/UEFI → bootloader → kernel → initramfs → systemd/init
* Role of `initramfs` and how it's generated
* Kernel boot parameters: how to view and modify via GRUB
* Temporary boot options using GRUB menu
* Editing `/etc/default/grub` and updating with `update-grub` or `grub2-mkconfig`

---

### 8. **Device and Driver Management**

* Understanding udev and dynamic device handling
* Viewing and managing device files in `/dev`
* udev rules customization (`/etc/udev/rules.d/`)
* Loading drivers (kernel modules) for hardware
* Troubleshooting driver issues

---

### 9. **Monitoring and Performance Tools**

* CPU and process monitoring: `top`, `htop`, `mpstat`
* Disk I/O monitoring: `iostat`, `iotop`, `dstat`
* Memory usage analysis: `free`, `vmstat`, `smem`
* Kernel profiling tools (advanced): `perf`, `ftrace`, `SystemTap`, `bpftrace`

---

### 10. **Kernel Updates and Upgrades**

* Identifying currently running and installed kernels
* Listing available kernel versions via package manager
* Installing new kernel packages (`apt`, `yum`, `dnf`, `zypper`)
* Removing old/unused kernels
* Ensuring correct bootloader configuration after updates

---

### 11. **Systemd and Kernel Integration**

* System targets and kernel handoff (`systemd` units like `default.target`)
* Kernel log access with `journalctl -k`
* Handling hardware-related systemd services

---

### 12. **Virtualization and Kernel Support**

* Checking for CPU virtualization support: `egrep '(vmx|svm)' /proc/cpuinfo`
* Kernel modules for virtualization: `kvm`, `kvm_intel`, `kvm_amd`
* Using `virt-what`, `dmesg`, and `lsmod` to verify virtualization features

---

### 13. **Security Features in the Kernel**

* Kernel-level security modules: AppArmor, SELinux
* Kernel hardening options: `grsecurity`, `PaX` (optional/advanced)
* Seccomp, capabilities, and namespaces (relevant to containers)
* Kernel lockdown mode (UEFI Secure Boot)

---

### 14. **Troubleshooting and Logs**

* Kernel messages: `dmesg`, `journalctl -k`
* Identifying hardware errors or failures
* Diagnosing driver or module load failures
* Troubleshooting boot and kernel panics

---

## ✅ System Hardware and Kernel Management in Linux – Study Checklist

---

### 1. **Fundamentals and Concepts**

* [ ] Understand the role of the Linux kernel in hardware management
* [ ] Know the differences between kernel space and user space
* [ ] Identify the types of hardware Linux supports (CPU, RAM, storage, peripherals)
* [ ] Learn how device files work in `/dev`
* [ ] Understand how the kernel interacts with hardware through drivers and modules

---

### 2. **Viewing System Hardware Information**

* [ ] View CPU details with `lscpu` and `/proc/cpuinfo`
* [ ] View memory info using `free`, `vmstat`, `/proc/meminfo`
* [ ] View block devices using `lsblk`, `blkid`, `fdisk`, `parted`
* [ ] List PCI devices with `lspci`
* [ ] List USB devices with `lsusb`
* [ ] Get a full hardware report with `lshw` or `hwinfo`
* [ ] Monitor hardware sensors with `lm-sensors`, `sensors`
* [ ] Check ACPI info with `acpi` and `/proc/acpi/`

---

### 3. **Kernel Basics**

* [ ] Check the current kernel version using `uname -r`, `uname -a`
* [ ] Understand kernel version numbering and naming conventions
* [ ] Know the difference between monolithic and modular kernels
* [ ] Understand what kernel modules are and how they extend functionality

---

### 4. **Kernel Module Management**

* [ ] List loaded kernel modules using `lsmod`
* [ ] Load modules dynamically using `modprobe`, `insmod`
* [ ] Unload modules using `rmmod`, `modprobe -r`
* [ ] View module information using `modinfo`
* [ ] Configure module loading with `/etc/modules-load.d/`
* [ ] Blacklist unwanted modules using `/etc/modprobe.d/`

---

### 5. **Kernel Parameters and Tuning**

* [ ] View kernel parameters with `sysctl` and `/proc/sys/`
* [ ] Modify kernel parameters at runtime using `sysctl -w`
* [ ] Make persistent changes via `/etc/sysctl.conf` or `/etc/sysctl.d/*.conf`
* [ ] Tune system performance using parameters like:

  * `vm.swappiness`
  * `fs.file-max`
  * `net.ipv4.ip_forward`
* [ ] Reload kernel parameters using `sysctl -p`

---

### 6. **Boot Process and Kernel Interaction**

* [ ] Understand the Linux boot process (BIOS/UEFI → GRUB → kernel → initramfs → systemd)
* [ ] Learn the role of `initramfs` and how it’s created
* [ ] View and edit kernel boot parameters via GRUB
* [ ] Modify `/etc/default/grub` and regenerate GRUB config (`update-grub` or `grub2-mkconfig`)
* [ ] Temporarily change boot parameters from the GRUB menu

---

### 7. **Device and Driver Management**

* [ ] Understand how Linux uses device drivers (modules)
* [ ] Learn how `udev` manages dynamic device nodes
* [ ] View and manage device files in `/dev`
* [ ] Write basic custom `udev` rules in `/etc/udev/rules.d/`
* [ ] Troubleshoot missing or incorrect drivers

---

### 8. **Monitoring and Diagnostics**

* [ ] Monitor CPU usage with `top`, `htop`, `mpstat`
* [ ] Monitor memory usage with `free`, `vmstat`, `smem`
* [ ] Monitor disk I/O with `iostat`, `iotop`, `dstat`
* [ ] View kernel logs with `dmesg` and `journalctl -k`
* [ ] Identify hardware or driver issues in logs
* [ ] Troubleshoot kernel panics and boot failures

---

### 9. **Kernel Updates and Upgrades**

* [ ] List installed kernels on the system
* [ ] Install a new kernel using package managers (`apt`, `yum`, `dnf`, `zypper`)
* [ ] Remove old/unused kernels safely
* [ ] Ensure GRUB is properly updated after kernel changes
* [ ] Set default boot kernel in GRUB configuration

---

### 10. **Custom Kernel Compilation (Optional/Advanced)**

* [ ] Download and extract kernel source from [kernel.org](https://www.kernel.org/)
* [ ] Configure the kernel using `make menuconfig`, `make xconfig`, or `make defconfig`
* [ ] Compile the kernel: `make`, `make modules`, `make install`
* [ ] Install modules and initramfs
* [ ] Add the new kernel to GRUB and test booting

---

### 11. **Security and Kernel Integration**

* [ ] Understand the role of AppArmor and SELinux as kernel-level security modules
* [ ] Explore kernel hardening options (e.g., `grsecurity`, `PaX`)
* [ ] Learn about kernel namespaces, cgroups, and seccomp
* [ ] Understand kernel lockdown mode and Secure Boot interactions

---

### 12. **Virtualization Support in the Kernel**

* [ ] Check for virtualization support: `egrep '(vmx|svm)' /proc/cpuinfo`
* [ ] Load necessary virtualization modules (`kvm`, `kvm_intel`, `kvm_amd`)
* [ ] Verify virtualization features using `virt-what`, `dmesg`, and `lsmod`
* [ ] Understand kernel dependencies for tools like KVM, QEMU, and containers

---

### 13. **Project for Practice**

* [ ] Write a script to monitor hardware info and generate reports
* [ ] Tune kernel parameters to optimize memory usage
* [ ] Load and unload kernel modules on demand
* [ ] Create a custom udev rule for USB device handling
* [ ] Compile and boot a custom kernel (optional advanced task)

---

</details>

<details>
  <summary>Daemon Services Management</summary>

---

## Topics in Daemon Services Management 

---

### 1. **Fundamentals of Daemons and Services**

* Definition of a daemon (background process)
* Difference between a service and a daemon
* Lifecycle of a daemon (start, stop, reload, restart)
* Typical locations for daemon binaries and configuration files (`/usr/sbin`, `/etc/`)

---

### 2. **Init Systems Overview**

* Evolution of init systems in Linux

  * **SysVinit**
  * **Upstart**
  * **Systemd** (modern standard)
* Role of the init system in starting and managing services

---

### 3. **Systemd – Service Management**

#### Basic Service Operations

* Starting a service: `systemctl start <service>`
* Stopping a service: `systemctl stop <service>`
* Restarting a service: `systemctl restart <service>`
* Reloading configuration: `systemctl reload <service>`
* Viewing service status: `systemctl status <service>`
* Enabling/disabling at boot: `systemctl enable/disable <service>`
* Checking if service is enabled: `systemctl is-enabled <service>`

#### Managing Unit Files

* Understanding unit types: `*.service`, `*.socket`, `*.target`, `*.mount`, etc.
* Unit file locations: `/etc/systemd/system/`, `/usr/lib/systemd/system/`
* Creating and editing custom service unit files
* Using `systemctl daemon-reload` after changes

#### Advanced Systemd Features

* Service dependencies: `After=`, `Requires=`, `Wants=`
* Configuring environment variables for services
* Restart policies (`Restart=always`, `on-failure`, etc.)
* Timeout settings and resource limits
* Overriding vendor unit files using `systemctl edit`
* Using `journalctl` to view service logs

---

### 4. **SysVinit (Legacy)**

* Managing services with `service` command
* Enabling/disabling services with `chkconfig` or `update-rc.d`
* Understanding `/etc/init.d/` scripts

---

### 5. **Upstart (Legacy Ubuntu Systems)**

* Managing services with `initctl` command
* Understanding `/etc/init/*.conf` configuration files

---

### 6. **Service Configuration and Customization**

* Editing service configuration files in `/etc/`
* Understanding the role of environment files (`/etc/default/`, `/etc/sysconfig/`)
* Reloading daemons after configuration changes

---

### 7. **Logging and Monitoring Daemons**

* Viewing logs with `journalctl`
* Filtering logs by unit: `journalctl -u <service>`
* Persistent logs vs runtime logs
* Using `logrotate` to manage daemon log files

---

### 8. **Socket-Activated Services (Systemd)**

* Understanding socket activation
* Using `.socket` unit files
* Creating socket-activated custom services

---

### 9. **Timers and Scheduled Daemon Tasks**

* Replacing cron with systemd timers
* Creating and managing `.timer` units
* Comparing cron vs systemd timer behavior

---

### 10. **Security and Resource Controls**

* Restricting daemons with `Systemd` security directives:

  * `ProtectSystem=`, `PrivateTmp=`, `NoNewPrivileges=`, `CapabilityBoundingSet=`
* Managing service privileges (user, group)
* Using `cgroups` and `systemd` directives to limit CPU, memory, I/O

---

### 11. **Troubleshooting and Debugging Services**

* Interpreting `systemctl status` and `journalctl` logs
* Diagnosing failed services with `systemctl list-units --failed`
* Running services in the foreground for debugging
* Checking service exit codes and causes of failure

---

### 12. **Custom and Third-Party Daemons**

* Creating your own systemd service for custom scripts or applications
* Installing and managing third-party services
* Securing and isolating third-party daemons

---

### 13. **Best Practices in Service Management**

* Minimal privilege principle (run as non-root when possible)
* Using `Type=notify`, `Type=forking`, `Type=simple` appropriately in services
* Implementing logging and monitoring for every daemon
* Documenting custom service setups and dependencies

---

## ✅ Daemon Services Management in Linux – Study Checklist

---

### 1. **Understanding Daemons and Services**

* [ ] Know what a daemon is and how it differs from a regular process
* [ ] Understand the lifecycle of a daemon (start, stop, reload, restart)
* [ ] Learn typical daemon file locations (`/usr/sbin/`, `/etc/`) and naming conventions

---

### 2. **Init Systems Overview**

* [ ] Understand the role and evolution of init systems: SysVinit, Upstart, and Systemd
* [ ] Identify which init system your Linux distribution uses

---

### 3. **Managing Services with Systemd**

* [ ] Start, stop, restart, and reload services using `systemctl`
* [ ] Check the status of a service (`systemctl status <service>`)
* [ ] Enable and disable services at boot (`systemctl enable/disable <service>`)
* [ ] Check if a service is enabled (`systemctl is-enabled <service>`)
* [ ] Reload systemd manager configuration (`systemctl daemon-reload`) after unit file changes

---

### 4. **Systemd Unit Files**

* [ ] Understand different unit types (`.service`, `.socket`, `.target`, `.mount`)
* [ ] Locate systemd unit files in `/etc/systemd/system/` and `/usr/lib/systemd/system/`
* [ ] Create and edit custom service unit files
* [ ] Use `systemctl edit` to override vendor unit files
* [ ] Configure service dependencies (`After=`, `Requires=`, `Wants=`)
* [ ] Set environment variables and resource limits in unit files
* [ ] Configure restart policies (`Restart=`, `RestartSec=`)
* [ ] Manage timeout and start-up behavior

---

### 5. **SysVinit Service Management (Legacy)**

* [ ] Use the `service` command to manage services
* [ ] Enable/disable services at startup with `chkconfig` or `update-rc.d`
* [ ] Understand and troubleshoot init scripts in `/etc/init.d/`

---

### 6. **Upstart Service Management (Legacy)**

* [ ] Manage services with `initctl`
* [ ] Understand Upstart job configuration in `/etc/init/*.conf`

---

### 7. **Service Configuration and Environment**

* [ ] Edit daemon configuration files in `/etc/` (e.g., `/etc/default/`, `/etc/sysconfig/`)
* [ ] Reload daemons after configuration changes
* [ ] Understand environment variable management for services

---

### 8. **Logging and Monitoring Services**

* [ ] Use `journalctl` to view logs (`journalctl -u <service>`)
* [ ] Filter logs by time and priority
* [ ] Understand persistent vs volatile journal logs
* [ ] Use and configure `logrotate` for service log management

---

### 9. **Socket-Activated Services (Systemd)**

* [ ] Understand socket activation concept
* [ ] Create and manage `.socket` unit files
* [ ] Link socket units with service units

---

### 10. **Timers and Scheduled Tasks**

* [ ] Understand and create systemd timer units (`.timer`)
* [ ] Compare timers with traditional cron jobs
* [ ] Manage timer units (`systemctl start/enable/disable <timer>`)

---

### 11. **Security and Resource Control**

* [ ] Configure service sandboxing options (`ProtectSystem=`, `PrivateTmp=`, `NoNewPrivileges=`)
* [ ] Set user and group privileges for daemons
* [ ] Use `CapabilityBoundingSet=` to limit service capabilities
* [ ] Control resource usage with cgroups (`CPUQuota=`, `MemoryLimit=`)

---

### 12. **Troubleshooting and Debugging**

* [ ] Analyze failed services with `systemctl list-units --failed`
* [ ] Check exit statuses and error messages in logs
* [ ] Run services in the foreground for debugging
* [ ] Use `strace` or `lsof` to troubleshoot service issues

---

### 13. **Managing Custom and Third-Party Daemons**

* [ ] Create custom service unit files for scripts or applications
* [ ] Secure and isolate third-party services
* [ ] Understand service dependencies and startup order for custom daemons

---

### 14. **Best Practices**

* [ ] Run daemons with the least required privileges
* [ ] Keep service configuration files well documented
* [ ] Regularly monitor service health and logs
* [ ] Automate service management tasks using scripts and cron/systemd timers

---

### 15. **Hands-On Practice**

* [ ] Start/stop/restart common services (e.g., `nginx`, `ssh`, `cron`)
* [ ] Enable and disable services on boot
* [ ] Write and deploy a custom systemd service for a shell script
* [ ] Configure a service to auto-restart on failure
* [ ] Set up a timer to run a maintenance script daily
* [ ] Analyze and resolve a failed service startup

---

</details>

<details>
  <summary>Bash builtin Commands</summary>

---

## Topics in Bash Built-in Commands 

---

### 1. **Shell Environment and Variables**

* `export` — set environment variables
* `unset` — remove variables or functions
* `readonly` — make variables/constants read-only
* `declare`/`typeset` — declare variables and attributes
* `env` — display environment variables
* `set` — set shell options and positional parameters
* `unset` — unset variables/functions

---

### 2. **Shell Control and Flow**

* `if`, `then`, `else`, `elif`, `fi` — conditional statements
* `case`, `esac` — multi-way branching
* `for`, `while`, `until`, `do`, `done` — loops
* `break`, `continue` — loop control
* `exit` — exit shell or script with status code
* `return` — return from a function
* `trap` — catch signals and execute commands on signals/events

---

### 3. **Command Execution and Job Control**

* `exec` — replace shell with another command
* `eval` — execute arguments as a shell command
* `command` — run a command bypassing shell functions
* `hash` — remember full pathnames of commands
* `type` — display information about commands
* `jobs` — list current jobs
* `fg`, `bg` — foreground/background jobs
* `disown` — remove jobs from shell job table

---

### 4. **Functions and Shell Scripts**

* `function` — define shell functions
* `local` — define local variables inside functions
* `source` or `.` — execute commands from a file in the current shell
* `alias`, `unalias` — create or remove command aliases

---

### 5. **Input and Output Control**

* `read` — read input from user or file
* `printf` — formatted output
* `echo` — print text to standard output
* `test` or `[` `]` — evaluate expressions

---

### 6. **Shell Options and Settings**

* `shopt` — shell options specific to Bash
* `set` — enable/disable shell options (`-e`, `-u`, `-x`, `-o` options)

---

### 7. **History and Command Line Editing**

* `history` — show command history
* `fc` — fix command (edit and re-execute commands from history)
* `bind` — manipulate readline key bindings

---

### 8. **Process Substitution and Expansion**

* Parameter expansion `${}`, including default values, substring, length, pattern replacement
* Command substitution `` `command` `` and `$(command)`
* Arithmetic expansion `$(( ))`
* Process substitution `<(command)`, `>(command)`

---

### 9. **Miscellaneous Built-ins**

* `wait` — wait for background jobs
* `let` — evaluate arithmetic expressions
* `times` — print user and system time for the shell and child processes
* `caller` — return information about the current subroutine call

---

## ✅ Bash Built-in Commands – Study Checklist

---

### 1. **Shell Environment and Variables**

* [ ] Use `export` to set and export environment variables
* [ ] Remove variables and functions with `unset`
* [ ] Make variables read-only with `readonly`
* [ ] Declare variables with attributes using `declare` or `typeset`
* [ ] Display environment variables using `env`
* [ ] Understand `set` for shell options and positional parameters
* [ ] Practice modifying shell options with `set -e`, `set -u`, `set -x`

---

### 2. **Shell Control and Flow**

* [ ] Write conditional statements using `if`, `then`, `else`, `elif`, and `fi`
* [ ] Implement multi-way branching with `case` and `esac`
* [ ] Create loops using `for`, `while`, `until`, `do`, and `done`
* [ ] Control loops with `break` and `continue`
* [ ] Use `exit` to terminate scripts with status codes
* [ ] Return from functions using `return`
* [ ] Use `trap` to handle signals and cleanup actions

---

### 3. **Command Execution and Job Control**

* [ ] Replace the shell with another command using `exec`
* [ ] Evaluate arguments as shell commands with `eval`
* [ ] Run commands bypassing functions using `command`
* [ ] Use `hash` to cache command locations
* [ ] Identify commands and functions using `type`
* [ ] List current background jobs with `jobs`
* [ ] Bring jobs to foreground with `fg` and background with `bg`
* [ ] Detach jobs from shell with `disown`

---

### 4. **Functions and Script Management**

* [ ] Define functions with `function` syntax
* [ ] Use `local` variables inside functions to limit scope
* [ ] Source scripts or files in the current shell using `source` or `.`
* [ ] Create and remove aliases with `alias` and `unalias`

---

### 5. **Input and Output Control**

* [ ] Read user input with `read` and handle input options
* [ ] Print formatted output using `printf`
* [ ] Output text with `echo` (understand differences and escape sequences)
* [ ] Evaluate conditional expressions using `test` or `[ ]`

---

### 6. **Shell Options and Settings**

* [ ] Use `shopt` to view and modify Bash shell options
* [ ] Toggle error checking and debugging options with `set -e`, `set -u`, `set -x`
* [ ] Understand the impact of options like `noclobber`, `nullglob`, `dotglob`

---

### 7. **History and Command Line Editing**

* [ ] Use `history` to view command history
* [ ] Edit and re-execute commands with `fc`
* [ ] Customize readline key bindings with `bind`

---

### 8. **Parameter and Command Substitution**

* [ ] Use parameter expansion `${var}`, including default values and substring extraction
* [ ] Perform command substitution with `` `command` `` and `$(command)`
* [ ] Use arithmetic expansion with `$((expression))`
* [ ] Use process substitution with `<(command)` and `>(command)`

---

### 9. **Miscellaneous Built-ins**

* [ ] Use `wait` to wait for background jobs to finish
* [ ] Perform arithmetic calculations with `let`
* [ ] Use `times` to check CPU time used by shell and child processes
* [ ] Use `caller` to debug function call stacks

---

### 10. **Hands-On Practice**

* [ ] Write scripts using conditionals and loops with built-in commands
* [ ] Create and manage environment variables in scripts
* [ ] Define and use shell functions with local variables
* [ ] Trap signals like `SIGINT` in scripts for graceful exits
* [ ] Use job control commands in multi-tasking shell environments
* [ ] Experiment with parameter expansion and substitution in practical scenarios

---

</details>

<details>
  <summary>Security Management</summary>
  
---

## Topics in Security Management

---

### 1. **User and Group Management**

* Secure user account creation and management
* Password policies and management (`passwd`, PAM)
* User and group permissions and ownership
* Managing sudo privileges (`/etc/sudoers`, `visudo`)
* Implementing account lockout policies

---

### 2. **File and Directory Permissions**

* Understanding Linux file permissions (rwx for user/group/others)
* Using `chmod`, `chown`, `chgrp` commands
* Special permissions: SUID, SGID, Sticky bit
* Access Control Lists (ACLs) with `setfacl` and `getfacl`
* Secure management of sensitive files

---

### 3. **Authentication and Authorization**

* Pluggable Authentication Modules (PAM) configuration and management
* Implementing multi-factor authentication (MFA)
* SSH key-based authentication and management
* Kerberos and LDAP integration
* Managing authentication logs and monitoring

---

### 4. **SELinux and AppArmor**

* Basics of Mandatory Access Control (MAC)
* Configuring and enforcing SELinux policies
* Troubleshooting SELinux denials
* Understanding AppArmor profiles and enforcement
* Comparing SELinux vs AppArmor

---

### 5. **Firewall and Network Security**

* Configuring firewalls with `iptables`, `nftables`
* Using `firewalld` for dynamic firewall management
* Managing TCP wrappers (`/etc/hosts.allow`, `/etc/hosts.deny`)
* Securing network services and ports
* VPN setup and management

---

### 6. **Intrusion Detection and Prevention**

* Using tools like `fail2ban` for automated banning
* Setting up Intrusion Detection Systems (IDS) such as `Snort`, `OSSEC`
* Log monitoring and analysis (`logwatch`, `rsyslog`)
* File integrity monitoring (`AIDE`, `Tripwire`)

---

### 7. **Encryption**

* Using `gpg` for file encryption and signing
* Disk encryption with LUKS and dm-crypt
* Securing data with SSL/TLS certificates
* Encrypting network traffic (e.g., SSH, OpenVPN)

---

### 8. **Security Updates and Patch Management**

* Configuring automatic security updates
* Managing package repositories securely
* Auditing and vulnerability scanning (`Lynis`, `OpenVAS`)

---

### 9. **System Auditing and Logging**

* Configuring and managing auditd (`auditd.conf`, rules)
* Centralized logging with `syslog`, `rsyslog`, or `journald`
* Analyzing logs for security events
* Setting up alerts for suspicious activities

---

### 10. **Process and Service Hardening**

* Minimizing running services (principle of least privilege)
* Securing daemons and services (chroot, capabilities)
* Using Linux namespaces and containers for isolation
* Configuring secure system boot (UEFI Secure Boot)

---

### 11. **Backup and Recovery Security**

* Securing backup data
* Implementing secure backup strategies
* Recovery procedures and testing

---

### 12. **Security Policies and Compliance**

* Creating and enforcing security policies
* Compliance standards (e.g., PCI-DSS, HIPAA)
* Using tools to check compliance

---

## ✅ Linux Security Management – Comprehensive Study Checklist

---

### 1. **User and Group Management**

* [ ] Create and manage user accounts securely
* [ ] Implement strong password policies and expiration rules
* [ ] Configure and manage sudo privileges safely using `visudo`
* [ ] Set up account lockout policies to prevent brute force attacks
* [ ] Manage group memberships and permissions appropriately

---

### 2. **File and Directory Permissions**

* [ ] Understand standard Linux permissions and ownership (rwx)
* [ ] Apply permissions using `chmod`, `chown`, and `chgrp`
* [ ] Use special permissions: SUID, SGID, and sticky bit correctly
* [ ] Manage Access Control Lists (ACLs) with `setfacl` and `getfacl`
* [ ] Secure critical files and directories (e.g., `/etc/shadow`, `/root`)

---

### 3. **Authentication and Authorization**

* [ ] Configure and customize Pluggable Authentication Modules (PAM)
* [ ] Implement and test multi-factor authentication (MFA)
* [ ] Set up SSH key-based authentication and disable password login
* [ ] Integrate centralized authentication systems like LDAP or Kerberos
* [ ] Monitor authentication logs for suspicious activity

---

### 4. **SELinux and AppArmor**

* [ ] Understand Mandatory Access Control (MAC) principles
* [ ] Configure SELinux modes: enforcing, permissive, and disabled
* [ ] Write and troubleshoot SELinux policy modules and contexts
* [ ] Manage AppArmor profiles and enforce restrictions
* [ ] Analyze and resolve denials using audit logs and tools

---

### 5. **Firewall and Network Security**

* [ ] Configure firewall rules using `iptables` or `nftables`
* [ ] Manage dynamic firewall with `firewalld` and zones
* [ ] Use TCP wrappers (`/etc/hosts.allow` and `/etc/hosts.deny`)
* [ ] Harden network services by closing unused ports and restricting access
* [ ] Set up and secure VPNs for remote access

---

### 6. **Intrusion Detection and Prevention**

* [ ] Install and configure `fail2ban` to block suspicious IPs
* [ ] Deploy Intrusion Detection Systems (IDS) like `Snort` or `OSSEC`
* [ ] Set up file integrity monitoring tools (`AIDE`, `Tripwire`)
* [ ] Monitor system and security logs regularly (`logwatch`, `rsyslog`)
* [ ] Establish alerting mechanisms for security events

---

### 7. **Encryption**

* [ ] Use `gpg` for encrypting files and verifying signatures
* [ ] Implement full disk encryption with LUKS/dm-crypt
* [ ] Configure SSL/TLS certificates for secure communications
* [ ] Secure network traffic with protocols like SSH and OpenVPN
* [ ] Understand and use encrypted backups

---

### 8. **Security Updates and Patch Management**

* [ ] Configure and automate security updates
* [ ] Use secure package repositories and verify package signatures
* [ ] Conduct vulnerability assessments using tools like `Lynis` and `OpenVAS`
* [ ] Keep track of security advisories and CVEs relevant to your distro

---

### 9. **System Auditing and Logging**

* [ ] Set up and configure `auditd` with appropriate rules
* [ ] Centralize logs with `rsyslog` or `journald` for easier analysis
* [ ] Regularly review audit logs for unauthorized access or anomalies
* [ ] Implement log rotation and archival policies
* [ ] Set up real-time log alerting for critical security events

---

### 10. **Process and Service Hardening**

* [ ] Apply the principle of least privilege to running services
* [ ] Use chroot jails or containers to isolate services
* [ ] Restrict capabilities and resource usage with Linux namespaces and cgroups
* [ ] Secure boot processes (UEFI Secure Boot, BIOS passwords)
* [ ] Disable or remove unnecessary services and daemons

---

### 11. **Backup and Recovery Security**

* [ ] Secure backup data with encryption and access controls
* [ ] Create and test reliable backup and recovery procedures
* [ ] Implement off-site or cloud backups for disaster recovery
* [ ] Regularly verify the integrity of backups

---

### 12. **Security Policies and Compliance**

* [ ] Develop and document security policies and best practices
* [ ] Understand relevant compliance frameworks (PCI-DSS, HIPAA, GDPR)
* [ ] Use compliance auditing tools to verify adherence
* [ ] Train users and administrators on security awareness

---

### 13. **Hands-On Practice**

* [ ] Set up a secure user environment with strong passwords and sudo rules
* [ ] Configure and test SELinux or AppArmor enforcement on a service
* [ ] Write firewall rules to restrict network access to essential ports
* [ ] Deploy and configure an IDS or fail2ban on a test system
* [ ] Perform system auditing and analyze logs for suspicious activity

---

</details>

<details>
  <summary>Debug Management</summary>

---

## Topics in Debug Management 

---

### 1. **System Logs and Log Management**

* Understanding Linux logging system (syslog, rsyslog, journald)
* Configuring and managing system logs
* Using `journalctl` to query and filter logs
* Log rotation and archival with `logrotate`

---

### 2. **Kernel Debugging**

* Using `dmesg` to read kernel ring buffer messages
* Kernel crash dumps and kdump configuration
* Using `kgdb` for kernel debugging
* Analyzing kernel panic and oops messages

---

### 3. **Process Debugging**

* Using `strace` to trace system calls and signals
* Using `ltrace` to trace library calls
* Debugging processes with `gdb` (GNU Debugger)
* Attaching to running processes with `gdb`
* Using `pstack` or `pmap` for stack traces and memory maps

---

### 4. **Performance Analysis Tools**

* Using `top`, `htop` for real-time process monitoring
* CPU profiling with `perf`
* Using `vmstat`, `iostat`, `sar` for system resource usage
* Memory leak detection with `valgrind`
* Analyzing I/O bottlenecks with `iotop`

---

### 5. **Network Debugging**

* Debugging network issues with `tcpdump` and `wireshark`
* Using `netstat`, `ss` to view network sockets and connections
* Analyzing firewall rules and traffic flow
* Using `traceroute` and `ping` for connectivity diagnosis

---

### 6. **Debugging Shell Scripts**

* Using `bash -x` or `set -x` for script tracing
* Debugging functions and loops in scripts
* Redirecting error output and debug logs
* Using `trap` for signal handling in scripts

---

### 7. **Debugging Services and Daemons**

* Checking service status and logs (`systemctl status`, `journalctl -u`)
* Restarting and reloading services safely
* Analyzing failed unit files and dependencies
* Using strace on daemon processes

---

### 8. **Core Dumps and Crash Analysis**

* Enabling core dumps and configuring limits (`ulimit -c`)
* Analyzing core dumps with `gdb`
* Using `systemd-coredump` for core dump management

---

### 9. **Debugging Hardware Issues**

* Using `dmesg` for hardware-related messages
* Checking hardware status with `lshw`, `lsblk`, `lspci`, `lsusb`
* Monitoring hardware logs and sensors (`lm-sensors`)
* Firmware and driver debugging

---

### 10. **Advanced Debugging Tools**

* Using `systemtap` for dynamic tracing
* Using `ebpf` (extended Berkeley Packet Filter) for kernel tracing
* Using `perf` tools for in-depth performance analysis
* Debugging with `Valgrind` and sanitizers for memory and threading issues

---

## ✅ Debug Management – Comprehensive Study Checklist

---

### 1. **System Logs and Log Management**

* [ ] Understand Linux logging systems: `syslog`, `rsyslog`, `journald`
* [ ] Configure and manage system log files
* [ ] Use `journalctl` to filter and query systemd journal logs
* [ ] Set up and manage log rotation with `logrotate`
* [ ] Analyze logs for error messages and warnings

---

### 2. **Kernel Debugging**

* [ ] Use `dmesg` to read and interpret kernel messages
* [ ] Configure and use `kdump` for kernel crash dumps
* [ ] Understand kernel panic and oops messages
* [ ] Explore `kgdb` for interactive kernel debugging
* [ ] Analyze kernel logs after system crashes

---

### 3. **Process Debugging**

* [ ] Use `strace` to trace system calls and signals of a process
* [ ] Use `ltrace` to trace library calls used by a process
* [ ] Debug applications using `gdb` (attach to running or new processes)
* [ ] Generate and analyze stack traces with `pstack` or `gdb`
* [ ] Use `pmap` to inspect process memory layout

---

### 4. **Performance Analysis Tools**

* [ ] Monitor processes in real-time with `top` and `htop`
* [ ] Use `perf` for CPU profiling and performance counters
* [ ] Check system resource usage with `vmstat`, `iostat`, and `sar`
* [ ] Detect memory leaks and errors with `valgrind`
* [ ] Monitor disk I/O using `iotop`

---

### 5. **Network Debugging**

* [ ] Capture and analyze network traffic with `tcpdump` and `wireshark`
* [ ] View active network connections and sockets with `netstat` and `ss`
* [ ] Test connectivity with `ping` and trace routing with `traceroute`
* [ ] Analyze firewall rules and troubleshoot network blocking issues

---

### 6. **Debugging Shell Scripts**

* [ ] Use `bash -x` or `set -x` to trace shell script execution
* [ ] Redirect standard error and debug output to files for analysis
* [ ] Debug functions and loops within scripts
* [ ] Use `trap` to handle signals and debug abnormal script termination

---

### 7. **Debugging Services and Daemons**

* [ ] Check service status and logs with `systemctl` and `journalctl -u`
* [ ] Restart and reload services during troubleshooting
* [ ] Analyze failed service units and dependency problems
* [ ] Attach `strace` to daemon processes for system call tracing

---

### 8. **Core Dumps and Crash Analysis**

* [ ] Enable core dumps (`ulimit -c`) and configure storage paths
* [ ] Analyze core dump files using `gdb`
* [ ] Use `systemd-coredump` to manage core dumps on systemd systems
* [ ] Interpret crash information to identify fault causes

---

### 9. **Debugging Hardware Issues**

* [ ] Use `dmesg` to monitor hardware-related kernel messages
* [ ] Inspect hardware info with `lshw`, `lsblk`, `lspci`, and `lsusb`
* [ ] Monitor hardware health with `lm-sensors` and related tools
* [ ] Troubleshoot firmware and driver-related problems

---

### 10. **Advanced Debugging Tools**

* [ ] Use `systemtap` for dynamic kernel and system tracing
* [ ] Learn and apply `ebpf` tools for advanced tracing and profiling
* [ ] Use sanitizers and `valgrind` for memory and threading debugging
* [ ] Integrate multiple debugging tools for comprehensive analysis

---

### 11. **Hands-On Practice**

* [ ] Practice tracing a faulty process with `strace` and `gdb`
* [ ] Debug a crashing service using systemd logs and core dumps
* [ ] Analyze kernel messages after a simulated kernel panic
* [ ] Capture and analyze network traffic to find connectivity issues
* [ ] Write and debug simple shell scripts using tracing options

---

</details>

<details>
  <summary>Log Management</summary>
  
---

## Topics in Log Management

---

### 1. **Introduction to Logging in Linux**

* Purpose and importance of system logs
* Types of logs (system logs, application logs, security logs)

---

### 2. **Linux Logging Systems**

* Syslog and syslogd basics
* `rsyslog` – advanced syslog daemon
* `syslog-ng` – alternative syslog implementation
* `journald` and the systemd journal

---

### 3. **Log Files and Their Locations**

* Common log file locations (e.g., `/var/log/`)
* Important log files: `/var/log/messages`, `/var/log/syslog`, `/var/log/auth.log`, `/var/log/kern.log`, `/var/log/secure`

---

### 4. **Configuring Logging Services**

* Configuring `rsyslog.conf` and rules
* Setting up `journald` configurations (`/etc/systemd/journald.conf`)
* Forwarding logs to remote servers (centralized logging)
* Customizing log formats and filters

---

### 5. **Log Rotation and Management**

* Purpose of log rotation
* Using `logrotate` for automated log rotation
* Configuring `logrotate.conf` and custom rules
* Compression and archival of old logs

---

### 6. **Log Analysis and Monitoring**

* Using `journalctl` to query and filter systemd logs
* Using `tail`, `less`, `grep`, `awk`, and `sed` for log analysis
* Real-time monitoring with `tail -f` and `multitail`
* Using log analyzers like `Logwatch` and `GoAccess`

---

### 7. **Security and Audit Logs**

* Understanding `/var/log/auth.log` or `/var/log/secure`
* Configuring and analyzing `auditd` logs
* Managing SELinux audit logs
* Detecting intrusion attempts through log analysis

---

### 8. **Centralized Logging**

* Benefits of centralized logging
* Setting up centralized log servers with `rsyslog` or `syslog-ng`
* Using ELK stack (Elasticsearch, Logstash, Kibana) for advanced log management
* Configuring remote log forwarding and secure transmission

---

### 9. **Troubleshooting Using Logs**

* Identifying hardware issues via logs
* Debugging service failures using logs
* Kernel and boot logs for system startup issues
* Application-specific log troubleshooting

---

### 10. **Log Security and Compliance**

* Securing log files (permissions, integrity checks)
* Configuring log retention policies
* Ensuring compliance with regulations (PCI-DSS, HIPAA)
* Audit trails and forensic readiness

---

## ✅ Linux Log Management – Comprehensive Study Checklist

---

### 1. **Introduction to Logging in Linux**

* [ ] Understand the purpose and importance of system logs
* [ ] Differentiate between system logs, application logs, and security logs

---

### 2. **Linux Logging Systems**

* [ ] Learn about traditional syslog and its functionality
* [ ] Explore `rsyslog` and its advanced features
* [ ] Understand `syslog-ng` as an alternative logging daemon
* [ ] Study `journald` and systemd’s logging mechanism

---

### 3. **Log Files and Their Locations**

* [ ] Identify common log file locations (`/var/log/`)
* [ ] Know key log files: `/var/log/messages`, `/var/log/syslog`, `/var/log/auth.log`, `/var/log/kern.log`, `/var/log/secure`
* [ ] Understand the purpose of each log file type

---

### 4. **Configuring Logging Services**

* [ ] Configure `rsyslog` through `/etc/rsyslog.conf` and custom rules
* [ ] Customize `journald` behavior via `/etc/systemd/journald.conf`
* [ ] Set up log forwarding to remote servers
* [ ] Modify log formats and apply filters

---

### 5. **Log Rotation and Management**

* [ ] Understand why log rotation is necessary
* [ ] Configure `logrotate` for automatic log rotation
* [ ] Create and manage custom `logrotate` rules
* [ ] Set up compression and archival for rotated logs

---

### 6. **Log Analysis and Monitoring**

* [ ] Use `journalctl` for querying and filtering systemd logs
* [ ] Apply command-line tools (`tail`, `less`, `grep`, `awk`, `sed`) for log inspection
* [ ] Perform real-time monitoring with `tail -f` and `multitail`
* [ ] Use tools like `Logwatch` for automated log summaries

---

### 7. **Security and Audit Logs**

* [ ] Review and analyze authentication logs (`/var/log/auth.log` or `/var/log/secure`)
* [ ] Configure and use `auditd` for detailed auditing
* [ ] Understand SELinux audit logs and troubleshoot denials
* [ ] Identify intrusion attempts and anomalies through logs

---

### 8. **Centralized Logging**

* [ ] Understand the benefits of centralized log management
* [ ] Set up centralized logging servers using `rsyslog` or `syslog-ng`
* [ ] Learn basics of the ELK stack (Elasticsearch, Logstash, Kibana)
* [ ] Configure secure log forwarding and encryption

---

### 9. **Troubleshooting Using Logs**

* [ ] Analyze logs to diagnose hardware issues
* [ ] Use logs to debug service and application failures
* [ ] Investigate kernel and boot issues through logs
* [ ] Apply logs to resolve network and connectivity problems

---

### 10. **Log Security and Compliance**

* [ ] Secure log files with proper permissions and ownership
* [ ] Implement log integrity verification techniques
* [ ] Establish log retention and archival policies
* [ ] Ensure compliance with industry regulations (PCI-DSS, HIPAA)
* [ ] Maintain audit trails for forensic investigations

---

### 11. **Hands-On Practice**

* [ ] Configure `rsyslog` with custom rules and filters
* [ ] Query and analyze logs using `journalctl`
* [ ] Set up `logrotate` for various log files
* [ ] Simulate intrusion attempts and analyze related logs
* [ ] Configure centralized logging and forward logs to a remote server

---

</details>

<details>
  <summary>Backup Management</summary>
  
---

## Topics in Backup Management 

---

### 1. **Introduction to Backup Concepts**

* Importance of backups and data protection
* Types of backups: full, incremental, differential
* Backup retention policies and scheduling

---

### 2. **Backup Tools and Utilities**

* Using `tar` for archiving backups
* `rsync` for efficient file synchronization and backups
* `dump` and `restore` for filesystem-level backups
* `dd` for block-level backups and cloning
* Advanced tools: `Bacula`, `Amanda`, `Duplicity`, `Restic`, `BorgBackup`

---

### 3. **Backup Storage Options**

* Local storage backups (external drives, NAS)
* Network backups (NFS, Samba shares)
* Remote backups over SSH/SFTP
* Cloud backup solutions integration

---

### 4. **Automating Backups**

* Writing backup scripts using bash or cron jobs
* Scheduling backups with `cron` and `systemd` timers
* Managing backup logs and notifications

---

### 5. **Backup Verification and Testing**

* Verifying backup integrity and consistency
* Testing restore procedures to ensure data recovery
* Monitoring backup success/failure

---

### 6. **Disaster Recovery Planning**

* Creating a disaster recovery strategy
* Off-site and off-line backups for redundancy
* Recovery point objectives (RPO) and recovery time objectives (RTO)

---

### 7. **Backup Security**

* Encrypting backups to protect sensitive data
* Access control for backup files and storage
* Secure transfer of backups over the network

---

### 8. **Backup Best Practices**

* Regular backup schedules and policy enforcement
* Keeping multiple backup copies
* Documentation of backup and recovery processes

---

### 9. **Troubleshooting Backup Issues**

* Diagnosing failed backup jobs
* Resolving permission and disk space issues
* Handling corrupted or incomplete backups

---

## ✅ Linux Backup Management – Comprehensive Study Checklist

---

### 1. **Introduction to Backup Concepts**

* [ ] Understand the importance of backups and data protection
* [ ] Learn different backup types: full, incremental, differential
* [ ] Define and apply backup retention policies
* [ ] Understand scheduling and frequency of backups

---

### 2. **Backup Tools and Utilities**

* [ ] Use `tar` for creating archives and backups
* [ ] Utilize `rsync` for incremental and remote backups
* [ ] Work with `dump` and `restore` for filesystem backups
* [ ] Use `dd` for disk cloning and block-level backups
* [ ] Explore advanced backup tools: `Bacula`, `Amanda`, `Duplicity`, `Restic`, `BorgBackup`

---

### 3. **Backup Storage Options**

* [ ] Set up local storage backups (external HDDs, NAS)
* [ ] Configure network-based backups via NFS or Samba shares
* [ ] Implement remote backups using SSH/SFTP
* [ ] Integrate cloud backup solutions and understand their use cases

---

### 4. **Automating Backups**

* [ ] Write bash scripts to automate backup tasks
* [ ] Schedule backups using `cron` jobs and `systemd` timers
* [ ] Manage logging and alerting for backup processes

---

### 5. **Backup Verification and Testing**

* [ ] Verify backup integrity (checksums, file comparisons)
* [ ] Regularly test restore processes to validate backups
* [ ] Monitor and report backup success or failure status

---

### 6. **Disaster Recovery Planning**

* [ ] Develop a comprehensive disaster recovery plan
* [ ] Implement off-site and off-line backup strategies
* [ ] Understand and define Recovery Point Objectives (RPO) and Recovery Time Objectives (RTO)

---

### 7. **Backup Security**

* [ ] Encrypt backup files to protect sensitive data
* [ ] Implement strict access control on backup files and devices
* [ ] Secure backup data transfers over the network with encryption

---

### 8. **Backup Best Practices**

* [ ] Maintain regular backup schedules and enforce policies
* [ ] Keep multiple copies of backups, including off-site copies
* [ ] Document backup and recovery procedures clearly

---

### 9. **Troubleshooting Backup Issues**

* [ ] Diagnose common backup failures and error messages
* [ ] Resolve permission, disk space, and hardware-related problems
* [ ] Handle and recover from corrupted or incomplete backups

---

### 10. **Hands-On Practice**

* [ ] Create full and incremental backups with `tar` and `rsync`
* [ ] Automate backup jobs using `cron` and test their execution
* [ ] Simulate disaster recovery using restore procedures
* [ ] Encrypt backup files and verify decryption during restore

---

</details>

<details>
  <summary>Logical Volume Management</summary>
  
---

## Topics in Logical Volume Management (LVM)

---

### 1. **Introduction to LVM**

* What is Logical Volume Management?
* Benefits of using LVM over traditional partitioning
* Basic LVM concepts: Physical Volumes (PV), Volume Groups (VG), Logical Volumes (LV)

---

### 2. **LVM Components**

* Physical Volume (PV) creation and management
* Volume Group (VG) creation, extension, and reduction
* Logical Volume (LV) creation, resizing, and removal

---

### 3. **LVM Setup and Configuration**

* Initializing disks as physical volumes (`pvcreate`)
* Creating volume groups (`vgcreate`)
* Creating logical volumes (`lvcreate`)
* Formatting logical volumes with filesystems

---

### 4. **Managing Logical Volumes**

* Extending logical volumes (`lvextend`)
* Reducing logical volumes (`lvreduce`)
* Resizing filesystems on logical volumes
* Removing logical volumes (`lvremove`)

---

### 5. **Managing Volume Groups**

* Adding physical volumes to a volume group (`vgextend`)
* Removing physical volumes from a volume group (`vgreduce`)
* Displaying volume group information (`vgdisplay`, `vgs`)

---

### 6. **Managing Physical Volumes**

* Displaying physical volume information (`pvdisplay`, `pvs`)
* Moving data between physical volumes (`pvmove`)
* Removing physical volumes from volume groups

---

### 7. **Snapshots and Backup**

* Creating snapshots of logical volumes (`lvcreate --snapshot`)
* Using snapshots for backup and recovery
* Removing snapshots (`lvremove`)

---

### 8. **LVM Metadata and Recovery**

* Understanding LVM metadata
* Backing up and restoring LVM metadata (`vgcfgbackup`, `vgcfgrestore`)
* Recovering from metadata corruption

---

### 9. **LVM Monitoring and Troubleshooting**

* Monitoring LVM status and health
* Common LVM errors and troubleshooting techniques
* Using `lvscan`, `vgscan`, `pvscan` commands

---

### 10. **Advanced LVM Features**

* Thin provisioning with LVM
* LVM caching for performance improvement
* Using LVM in combination with RAID

---

## ✅ Logical Volume Management (LVM) – Comprehensive Study Checklist

---

### 1. **Introduction to LVM**

* [ ] Understand what LVM is and its advantages over traditional partitioning
* [ ] Learn key concepts: Physical Volumes (PV), Volume Groups (VG), Logical Volumes (LV)

---

### 2. **LVM Components**

* [ ] Create and manage Physical Volumes with `pvcreate`, `pvdisplay`
* [ ] Create and manage Volume Groups with `vgcreate`, `vgextend`, `vgreduce`, `vgdisplay`
* [ ] Create and manage Logical Volumes with `lvcreate`, `lvextend`, `lvreduce`, `lvremove`

---

### 3. **LVM Setup and Configuration**

* [ ] Initialize physical disks as PVs using `pvcreate`
* [ ] Create Volume Groups by combining PVs with `vgcreate`
* [ ] Create Logical Volumes within VGs using `lvcreate`
* [ ] Format logical volumes with appropriate filesystems (e.g., ext4, xfs)

---

### 4. **Managing Logical Volumes**

* [ ] Extend logical volumes with `lvextend`
* [ ] Reduce logical volumes carefully using `lvreduce` (after resizing filesystem)
* [ ] Resize filesystems on LVs after volume resizing
* [ ] Remove logical volumes with `lvremove`

---

### 5. **Managing Volume Groups**

* [ ] Add physical volumes to volume groups (`vgextend`)
* [ ] Remove physical volumes from volume groups (`vgreduce`)
* [ ] Display VG information with `vgdisplay` and summary with `vgs`

---

### 6. **Managing Physical Volumes**

* [ ] Display PV details using `pvdisplay` and `pvs`
* [ ] Move data between physical volumes using `pvmove`
* [ ] Remove physical volumes from VGs (`vgreduce`)

---

### 7. **Snapshots and Backup**

* [ ] Create snapshots of logical volumes (`lvcreate --snapshot`)
* [ ] Use snapshots for backups or testing purposes
* [ ] Remove snapshots safely (`lvremove`)

---

### 8. **LVM Metadata and Recovery**

* [ ] Understand LVM metadata and where it is stored
* [ ] Backup LVM metadata using `vgcfgbackup`
* [ ] Restore metadata with `vgcfgrestore`
* [ ] Troubleshoot and recover from metadata corruption

---

### 9. **LVM Monitoring and Troubleshooting**

* [ ] Use `lvscan`, `vgscan`, `pvscan` to discover LVM components
* [ ] Monitor free space in VGs and PVs
* [ ] Identify and resolve common LVM issues (e.g., missing PVs, inactive VG)
* [ ] Read logs for LVM errors

---

### 10. **Advanced LVM Features**

* [ ] Learn about thin provisioning and how to create thin volumes
* [ ] Explore LVM caching for performance improvement
* [ ] Understand how to combine LVM with RAID for redundancy and performance

---

### 11. **Hands-On Practice**

* [ ] Initialize disks as PVs and create VGs and LVs on a test system
* [ ] Resize logical volumes and filesystems safely
* [ ] Create and remove snapshots; test restoring from snapshots
* [ ] Backup and restore LVM metadata
* [ ] Troubleshoot simulated LVM errors and recover the system

---

</details>

<details>
  <summary>RAID</summary>

---

## Topics in RAID Management

---

### 1. **Introduction to RAID**

* What is RAID and why it’s used
* Difference between hardware RAID and software RAID
* Advantages and disadvantages of RAID

---

### 2. **RAID Levels and Their Use Cases**

* RAID 0 – Striping (performance, no redundancy)
* RAID 1 – Mirroring (redundancy)
* RAID 5 – Striping with parity (balance of performance and redundancy)
* RAID 6 – Double parity (redundancy with more fault tolerance)
* RAID 10 (1+0) – Nested RAID (mirroring + striping)
* RAID 01 (0+1) – Nested RAID (striping + mirroring)

---

### 3. **Software RAID in Linux (mdadm)**

* Introduction to `mdadm` – Linux software RAID tool
* Installing and configuring `mdadm`
* Creating different RAID levels using `mdadm`
* Understanding RAID metadata and superblocks

---

### 4. **Creating and Managing RAID Arrays**

* Preparing disks for RAID (partitioning or using whole disks)
* Creating a RAID array with `mdadm --create`
* Checking RAID status with `cat /proc/mdstat` and `mdadm --detail`
* Saving RAID configuration to `mdadm.conf`
* Setting RAID arrays to start automatically at boot

---

### 5. **Monitoring and Maintaining RAID Arrays**

* Monitoring RAID health and status
* Replacing failed disks in a RAID array
* Rebuilding and resyncing RAID arrays
* Adding or removing devices from an array
* Growing or reshaping RAID arrays

---

### 6. **RAID Troubleshooting and Recovery**

* Detecting and identifying degraded or failed RAID arrays
* Assembling arrays with `mdadm --assemble`
* Replacing and re-syncing failed disks
* Recovering RAID arrays after disk or power failures
* Reading data from a degraded or partially failed array

---

### 7. **Filesystem and Mounting with RAID**

* Formatting RAID devices with filesystems (e.g., ext4, xfs)
* Mounting RAID devices and configuring `/etc/fstab`
* Ensuring proper UUID and device mapping for boot

---

### 8. **RAID Performance and Benchmarking**

* Measuring RAID performance with tools like `dd`, `fio`, or `hdparm`
* Comparing performance across different RAID levels
* Tuning RAID parameters (e.g., chunk size) for performance

---

### 9. **Hot Spares and Fault Tolerance**

* Adding hot spare disks to RAID arrays
* Auto-replacement using hot spares
* Understanding hot swap vs hot spare

---

### 10. **Integration with LVM and Other Tools**

* Using RAID arrays as physical volumes for LVM
* Creating encrypted volumes on top of RAID arrays
* Using RAID in virtualized or cloud environments

---

## ✅ RAID Management – Comprehensive Study Checklist

---

### 1. **RAID Fundamentals**

* [ ] Understand what RAID is and why it is used
* [ ] Distinguish between hardware RAID and software RAID
* [ ] Learn advantages and limitations of RAID solutions
* [ ] Know when to use RAID vs. other redundancy techniques

---

### 2. **RAID Levels and Their Characteristics**

* [ ] Study the features, performance, and fault tolerance of:

  * [ ] RAID 0 (Striping)
  * [ ] RAID 1 (Mirroring)
  * [ ] RAID 5 (Striping + Parity)
  * [ ] RAID 6 (Double Parity)
  * [ ] RAID 10 (1+0)
  * [ ] RAID 01 (0+1)
* [ ] Understand use cases and trade-offs for each RAID level

---

### 3. **Introduction to Software RAID with `mdadm`**

* [ ] Install and configure `mdadm` on a Linux system
* [ ] Understand RAID metadata and superblocks
* [ ] Learn about persistent RAID configurations with `/etc/mdadm/mdadm.conf`

---

### 4. **Creating and Managing RAID Arrays**

* [ ] Prepare disks for use (partitioning or whole disks)
* [ ] Create arrays using `mdadm --create` with appropriate RAID level
* [ ] Format the RAID device with a filesystem (e.g., `mkfs.ext4`)
* [ ] Mount RAID arrays and add them to `/etc/fstab`
* [ ] Configure automatic assembly of RAID arrays at boot

---

### 5. **Monitoring RAID Arrays**

* [ ] Monitor array status with:

  * [ ] `cat /proc/mdstat`
  * [ ] `mdadm --detail`
  * [ ] `mdadm --examine`
* [ ] Configure email alerts or logging for RAID health
* [ ] Use smart tools (`smartctl`) for disk health monitoring

---

### 6. **Maintaining RAID Arrays**

* [ ] Add and remove disks from RAID arrays
* [ ] Replace failed drives and rebuild the array (`mdadm --replace`)
* [ ] Reshape or grow a RAID array
* [ ] Add hot spares to arrays (`mdadm --add`)

---

### 7. **RAID Troubleshooting and Recovery**

* [ ] Assemble broken or degraded arrays with `mdadm --assemble`
* [ ] Detect and replace failed or missing disks
* [ ] Read from degraded arrays when a drive is missing
* [ ] Rebuild arrays safely and monitor sync progress
* [ ] Backup and restore `mdadm` configuration

---

### 8. **Filesystem Integration**

* [ ] Format and mount RAID devices
* [ ] Set correct mount options and test persistence with `/etc/fstab`
* [ ] Use UUIDs to ensure proper device mounting at boot

---

### 9. **Performance Testing and Tuning**

* [ ] Benchmark RAID performance using `dd`, `fio`, or `hdparm`
* [ ] Compare RAID performance across different levels
* [ ] Optimize chunk size and read/write policies for performance
* [ ] Test RAID performance under load and during rebuild

---

### 10. **Advanced Topics**

* [ ] Configure hot spare and auto-rebuild options
* [ ] Integrate LVM on top of RAID arrays
* [ ] Encrypt RAID volumes with `LUKS`
* [ ] Use RAID arrays in cloud/VM environments (e.g., KVM, AWS EBS)

---

### 11. **Hands-On Practice**

* [ ] Build and manage multiple RAID levels in a test environment
* [ ] Simulate disk failures and perform replacements
* [ ] Resize and reshape an existing RAID array
* [ ] Assemble arrays manually without config files
* [ ] Practice recovery scenarios with degraded or failed arrays

---

</details>

### **Services Management**

<details>
  <summary>Apache</summary>

---

## Topics in Apache Web Server

---

### 1. **Introduction to Apache**

* Overview of Apache HTTP Server (httpd)
* Apache vs. other web servers (Nginx, Lighttpd)
* Understanding Apache's role in the LAMP stack (Linux, Apache, MySQL, PHP)

---

### 2. **Installing Apache**

* Installing Apache on major Linux distributions (Debian/Ubuntu: `apache2`, RHEL/CentOS: `httpd`)
* Managing Apache service (`systemctl start|stop|restart httpd/apache2`)
* Checking Apache version and modules

---

### 3. **Apache Directory Structure and Files**

* Key configuration files:

  * `/etc/httpd/` (RedHat-based)
  * `/etc/apache2/` (Debian-based)
* Main config file: `httpd.conf` or `apache2.conf`
* Site configuration files: `sites-available/` and `sites-enabled/`
* Log files: `access.log`, `error.log`

---

### 4. **Basic Apache Configuration**

* Setting the server name and admin email
* Configuring the document root (`DocumentRoot`)
* Creating and serving a basic HTML page
* Customizing directory index and error documents

---

### 5. **Virtual Hosts (Name-Based and IP-Based)**

* Creating virtual hosts for multiple websites on the same server
* Name-based vs. IP-based virtual hosting
* Enabling and disabling virtual sites (`a2ensite`, `a2dissite`)
* Testing and troubleshooting virtual host configuration

---

### 6. **Modules and Extensions**

* Understanding Apache’s modular architecture
* Enabling and disabling modules (`a2enmod`, `a2dismod`)
* Common modules: `mod_ssl`, `mod_rewrite`, `mod_proxy`, `mod_headers`, `mod_security`

---

### 7. **Security Configuration**

* Restricting directory access (`Allow`, `Deny`, `Require`)
* Using `.htaccess` files and `AllowOverride`
* Configuring HTTPS with SSL/TLS (`mod_ssl`)
* Creating and using self-signed or Let's Encrypt SSL certificates
* Setting up basic authentication (`htpasswd`)

---

### 8. **Performance Tuning**

* Managing MaxClients, KeepAlive, Timeout settings
* Caching configuration (`mod_cache`, `mod_expires`)
* Compression with `mod_deflate`
* Load balancing with `mod_proxy_balancer`

---

### 9. **Logging and Monitoring**

* Access and error logs (`access.log`, `error.log`)
* LogFormat and CustomLog directives
* Using tools like `goaccess`, `awk`, `grep`, `webalizer` for log analysis

---

### 10. **URL Rewriting and Redirection**

* Using `mod_rewrite` for clean URLs and redirects
* Creating rewrite rules with `.htaccess` or main config
* Implementing 301/302 redirects

---

### 11. **Hosting Dynamic Content**

* Running PHP with Apache (`mod_php`, FastCGI)
* Integrating Apache with other languages (Python via WSGI, Perl, etc.)
* CGI configuration basics

---

### 12. **Access Control and Security Hardening**

* Directory protection with `.htaccess`
* Hiding Apache version and OS info
* Disabling unnecessary modules
* Preventing directory listing
* Rate limiting with `mod_evasive` or `mod_security`

---

### 13. **Backup and Restore**

* Backing up Apache config files
* Restoring and testing configuration
* Version control with Git or manual backups

---

### 14. **Troubleshooting Apache**

* Diagnosing config errors and failed starts
* Interpreting Apache logs
* Testing configuration with `apachectl configtest`
* Common misconfigurations (permissions, file paths, module issues)

---


## ✅ Apache Web Server – Comprehensive Study Checklist

---

### 1. **Apache Basics**

* [ ] Understand what Apache is and how it fits into the LAMP stack
* [ ] Know the difference between Apache and other web servers (e.g., Nginx)
* [ ] Identify Apache package names (`httpd`, `apache2`) on different distros

---

### 2. **Installation & Service Management**

* [ ] Install Apache on:

  * [ ] Debian/Ubuntu (`sudo apt install apache2`)
  * [ ] RHEL/CentOS/Fedora (`sudo dnf/yum install httpd`)
* [ ] Start, stop, restart, and enable Apache with `systemctl`
* [ ] Check Apache version and running status

---

### 3. **Apache Directory and Config Files**

* [ ] Locate main config files (`httpd.conf`, `apache2.conf`)
* [ ] Understand role of:

  * [ ] `/etc/httpd/` (RHEL)
  * [ ] `/etc/apache2/` (Debian)
* [ ] Identify:

  * [ ] `sites-available/`, `sites-enabled/`
  * [ ] `mods-available/`, `mods-enabled/`
* [ ] Locate and understand `access.log`, `error.log`

---

### 4. **Basic Web Server Setup**

* [ ] Set `ServerName`, `DocumentRoot`, and `DirectoryIndex`
* [ ] Serve a simple static HTML page
* [ ] Customize error messages with `ErrorDocument`

---

### 5. **Virtual Host Configuration**

* [ ] Create Name-based virtual hosts
* [ ] Configure multiple websites on one server
* [ ] Enable/disable sites with `a2ensite`, `a2dissite`
* [ ] Test virtual host setup with `curl` or browser

---

### 6. **Apache Modules**

* [ ] List loaded modules (`apachectl -M`)
* [ ] Enable/disable modules (`a2enmod`, `a2dismod`)
* [ ] Understand functions of key modules:

  * [ ] `mod_ssl`
  * [ ] `mod_rewrite`
  * [ ] `mod_proxy`
  * [ ] `mod_headers`
  * [ ] `mod_security`

---

### 7. **Security Configuration**

* [ ] Configure access control using `Require`, `Allow`, `Deny`
* [ ] Use `.htaccess` for per-directory rules
* [ ] Disable directory listing (`Options -Indexes`)
* [ ] Hide Apache version info (`ServerSignature`, `ServerTokens`)
* [ ] Implement basic authentication with `htpasswd`

---

### 8. **SSL/TLS (HTTPS)**

* [ ] Install and enable `mod_ssl`
* [ ] Create and use self-signed certificates
* [ ] Use Let’s Encrypt with `certbot` for free SSL
* [ ] Redirect HTTP to HTTPS

---

### 9. **Hosting Dynamic Content**

* [ ] Install PHP and configure it with Apache (`libapache2-mod-php`)
* [ ] Run dynamic content (e.g., PHP scripts)
* [ ] Configure CGI or WSGI for other languages (Python, Perl)

---

### 10. **URL Rewriting and Redirection**

* [ ] Enable `mod_rewrite`
* [ ] Write basic rewrite rules in `.htaccess` or main config
* [ ] Implement 301/302 redirects

---

### 11. **Performance Tuning**

* [ ] Tune `KeepAlive`, `MaxRequestWorkers`, `Timeout`
* [ ] Enable gzip compression with `mod_deflate`
* [ ] Configure caching with `mod_expires`, `mod_cache`
* [ ] Monitor with tools like `ab` (ApacheBench), `htop`, or `top`

---

### 12. **Monitoring and Logging**

* [ ] Analyze `access.log` and `error.log`
* [ ] Customize `LogFormat` and `CustomLog`
* [ ] Monitor traffic with tools: `goaccess`, `webalizer`, `awstats`

---

### 13. **Backup and Restore**

* [ ] Backup config files (`/etc/httpd/` or `/etc/apache2/`)
* [ ] Use version control for config management
* [ ] Test restoring Apache from a backup

---

### 14. **Troubleshooting**

* [ ] Use `apachectl configtest` to validate config
* [ ] Read error logs for troubleshooting clues
* [ ] Diagnose:

  * [ ] Failed service starts
  * [ ] 403/404 errors
  * [ ] Permission issues
  * [ ] Port conflicts

---

### 15. **Hands-On Practice**

* [ ] Set up a real-world virtual host configuration
* [ ] Enable SSL and force HTTPS
* [ ] Restrict access to certain directories
* [ ] Deploy a simple PHP application
* [ ] Use `.htaccess` to apply rewrite rules

---

**Apache Web Server – Hands-On Exercises**

**Basic Setup & Configuration**

1. Install Apache (`httpd` or `apache2`) on a Linux system
2. Start, stop, restart, and enable Apache using `systemctl`
3. Verify Apache is running using `curl` or a web browser
4. Replace the default `index.html` with a custom webpage
5. Set appropriate file permissions and ownership for web content

**Virtual Hosts**

6. Create name-based virtual hosts with separate `DocumentRoot` directories
7. Configure custom domain names using the `/etc/hosts` file
8. Enable and disable sites using `a2ensite` and `a2dissite` (Debian-based systems)
9. Test multiple websites on a single server using `curl` or browser
10. Set up IP-based virtual hosting (optional advanced task)

**Security and Access Control**

11. Create a `.htaccess` file and use it to restrict access to a directory
12. Generate a `.htpasswd` file to implement basic HTTP authentication
13. Disable directory listing by adjusting the `Options` directive
14. Hide Apache version and OS signature in HTTP response headers
15. Create and configure a self-signed SSL certificate
16. Install and configure a free SSL certificate using Let’s Encrypt (`certbot`)

**Rewriting and Redirection**

17. Enable `mod_rewrite` and create `.htaccess` rules for URL rewriting
18. Set up permanent (301) and temporary (302) redirects using `Redirect` and `RewriteRule`
19. Test redirect behavior using `curl -I` or a browser

**Performance Tuning and Optimization**

20. Enable Gzip compression using `mod_deflate`
21. Configure browser caching using `mod_expires` or `mod_headers`
22. Tune Apache settings such as `KeepAlive`, `Timeout`, and `MaxRequestWorkers`
23. Benchmark site performance using `ab` (Apache Benchmark)

**Logging and Monitoring**

24. Monitor `access.log` and `error.log` for real-time activity
25. Customize log formats using `LogFormat` and `CustomLog` directives
26. Install and use a log analysis tool such as `goaccess` or `awstats`

**Dynamic Content and Scripting**

27. Install PHP and integrate it with Apache (`libapache2-mod-php`)
28. Deploy a basic PHP script (e.g., `phpinfo()`) to test functionality
29. Install and host a PHP-based web application (e.g., WordPress)

**Troubleshooting**

30. Introduce a syntax error in the Apache config file and fix it using `apachectl configtest`
31. Simulate a port conflict and resolve it by identifying the conflicting service
32. Diagnose and fix a misconfigured virtual host (e.g., incorrect path or permissions)
33. Use Apache logs to troubleshoot access and configuration issues

---

</details>

<details>
  <summary>Nginx</summary>
  
---

**Nginx Web Server Administration**

1. Introduction to Nginx
2. Comparison of Nginx vs Apache
3. Installing Nginx on various Linux distributions
4. Managing the Nginx service with systemctl
5. Understanding the Nginx configuration structure
6. Working with nginx.conf and include directives
7. Setting up a basic static web server
8. Configuring server_name and root directives
9. Managing virtual hosts (server blocks)
10. Serving multiple websites on a single server
11. Using sites-available and sites-enabled (Debian-based systems)
12. Serving custom error pages
13. Understanding and configuring location blocks
14. Using Nginx as a reverse proxy
15. Proxying traffic to Apache, Node.js, Python (Flask/Django), or other backends
16. Configuring load balancing with upstream blocks
17. Load balancing algorithms: round-robin, least connections, IP hash
18. Implementing basic access control by IP
19. Setting up HTTP basic authentication using auth_basic
20. Enabling HTTPS with a self-signed certificate
21. Using Let's Encrypt with Certbot for free SSL certificates
22. Redirecting HTTP to HTTPS
23. Tuning SSL settings for security (TLS versions, ciphers)
24. Enabling Gzip compression
25. Configuring browser caching and static file expiration headers
26. Optimizing worker_processes, worker_connections, and other performance settings
27. Customizing access logs and error logs
28. Creating and using custom log formats
29. Real-time log monitoring with tail and grep
30. Integrating Nginx logs with log analysis tools (e.g., goaccess)
31. Handling FastCGI with PHP-FPM for dynamic content
32. Running PHP applications like WordPress with Nginx
33. Writing rewrite rules with rewrite and return directives
34. Implementing permanent and temporary redirects (301 and 302)
35. Removing or enforcing trailing slashes
36. Redirecting non-www to www and vice versa
37. Organizing configurations using modular includes
38. Defining and using Nginx variables
39. Using conditional logic inside configuration blocks
40. Implementing connection limiting with limit_conn and limit_req
41. Configuring request rate limiting and burst settings
42. Setting security headers (CSP, X-Frame-Options, X-Content-Type-Options)
43. Disabling unwanted HTTP methods
44. Hiding Nginx version and server signature
45. Detecting and mitigating DDoS attempts
46. Setting up high availability with tools like keepalived (optional)
47. Using DNS-based failover and backup servers
48. Checking configuration syntax with nginx -t
49. Reloading configuration without downtime
50. Troubleshooting common issues (403, 404, 502, 504 errors)
51. Analyzing error logs for debugging
52. Automating SSL renewal with cron or systemd timers
53. Maintaining configuration backups and version control
54. Using Nginx in containerized environments (Docker)
55. Creating reusable config templates for deployment

---

## Nginx Web Server Administration – Study Checklist

---

### 1. **Foundations of Nginx**

* [ ] Understand what Nginx is and its core architecture
* [ ] Know how Nginx differs from Apache (event-driven vs process-driven)
* [ ] Identify common Nginx use cases (static server, reverse proxy, load balancer)

---

### 2. **Installation and Service Management**

* [ ] Install Nginx using package managers (APT, YUM, DNF)
* [ ] Start, stop, restart, and reload Nginx using `systemctl`
* [ ] Enable Nginx to start on boot
* [ ] Check service status and logs
* [ ] Test Nginx configuration syntax with `nginx -t`

---

### 3. **Nginx Configuration Structure**

* [ ] Understand the main config file (`/etc/nginx/nginx.conf`)
* [ ] Learn the purpose of each main block: `events`, `http`, `server`, `location`
* [ ] Use `include` statements to modularize configuration
* [ ] Understand the difference between `sites-available/` and `sites-enabled/`

---

### 4. **Basic Web Server Setup**

* [ ] Configure a server block to serve static files
* [ ] Set `server_name`, `listen`, and `root` directives
* [ ] Create custom error pages using `error_page`
* [ ] Manage file permissions and ownership

---

### 5. **Virtual Hosting**

* [ ] Set up name-based virtual hosts (multiple domains on one IP)
* [ ] Configure domain resolution using `/etc/hosts` or DNS
* [ ] Use symbolic links in `sites-enabled/` (Debian-based systems)
* [ ] Test virtual host configurations with `curl` or a browser

---

### 6. **Reverse Proxy Setup**

* [ ] Understand the concept of reverse proxying
* [ ] Configure Nginx to proxy requests to backend servers (e.g., Apache, Node.js, Flask)
* [ ] Set headers correctly with `proxy_set_header`
* [ ] Handle WebSocket or long-lived connections

---

### 7. **Load Balancing**

* [ ] Create an `upstream` block to define backend servers
* [ ] Configure load balancing using round-robin, least connections, or IP hash
* [ ] Test failover behavior by shutting down backends
* [ ] Optionally explore third-party health check modules

---

### 8. **Security and Access Control**

* [ ] Restrict access by IP using `allow` and `deny`
* [ ] Set up basic authentication using `auth_basic` and `.htpasswd`
* [ ] Disable directory listing using `autoindex off`
* [ ] Hide Nginx version and server tokens
* [ ] Disable unused HTTP methods (`DELETE`, `TRACE`, etc.)

---

### 9. **SSL/TLS Configuration**

* [ ] Enable HTTPS using a self-signed certificate
* [ ] Install and configure Let’s Encrypt SSL using `certbot`
* [ ] Redirect HTTP traffic to HTTPS using `return` or `rewrite`
* [ ] Configure SSL ciphers and TLS protocols securely
* [ ] Implement HSTS (HTTP Strict Transport Security)

---

### 10. **Performance Optimization**

* [ ] Enable Gzip compression with `gzip` directives
* [ ] Set up browser caching with `expires` or `cache-control` headers
* [ ] Tune `worker_processes`, `worker_connections`, and `keepalive_timeout`
* [ ] Configure client buffer sizes
* [ ] Optimize serving of static content

---

### 11. **Logging and Monitoring**

* [ ] Understand and locate `access.log` and `error.log`
* [ ] Customize log formats using `log_format`
* [ ] Monitor logs in real-time using `tail -f`
* [ ] Analyze logs with tools like `goaccess` or `awk`
* [ ] Track request/response status codes

---

### 12. **Serving Dynamic Content**

* [ ] Set up PHP processing via `fastcgi_pass` and PHP-FPM
* [ ] Deploy a PHP-based application (e.g., WordPress)
* [ ] Proxy to backend app servers (Node.js, Python, Ruby)
* [ ] Manage cache headers and buffering behavior

---

### 13. **URL Rewriting and Redirection**

* [ ] Create simple and complex rewrites using `rewrite`
* [ ] Implement 301 and 302 redirects with `return` and `rewrite`
* [ ] Force HTTPS or www/non-www redirects
* [ ] Handle trailing slash redirects

---

### 14. **Modular and Advanced Configuration**

* [ ] Use variables and conditional blocks (`if`, `map`)
* [ ] Apply reusable configuration snippets with `include`
* [ ] Use nested `location` blocks for fine-grained control
* [ ] Organize complex deployments with multiple config files

---

### 15. **Rate Limiting and Connection Control**

* [ ] Configure request rate limiting using `limit_req`
* [ ] Set up concurrent connection limits with `limit_conn`
* [ ] Use burst and delay options to smooth traffic spikes
* [ ] Block bots or scrapers based on user agent or request patterns

---

### 16. **Security Hardening**

* [ ] Implement common security headers (CSP, X-Frame-Options, X-Content-Type-Options)
* [ ] Prevent host header injection and open redirect vulnerabilities
* [ ] Protect against slowloris and HTTP flood attacks
* [ ] Implement DDoS mitigation basics

---

### 17. **Troubleshooting and Maintenance**

* [ ] Check configuration syntax (`nginx -t`)
* [ ] Reload and restart Nginx without downtime
* [ ] Debug common issues (403, 404, 502, 504 errors)
* [ ] Analyze `error.log` to trace backend or config issues
* [ ] Use `curl -I` or `curl -v` for response inspection

---

### 18. **Automation and Best Practices**

* [ ] Automate SSL renewal with cron or systemd timers
* [ ] Use version control (e.g., Git) for Nginx configurations
* [ ] Backup and restore Nginx configs
* [ ] Use containers (Docker) for isolated Nginx environments (optional)
* [ ] Maintain staging vs production environments

---

## **Nginx Web Server Hands-On Exercises**

1. Install Nginx on a Linux system using the package manager.
2. Start, stop, restart, and reload the Nginx service using systemctl.
3. Verify Nginx is running by accessing the default web page via browser or curl.
4. Locate and examine the main configuration file `/etc/nginx/nginx.conf`.
5. Test the Nginx configuration syntax using `nginx -t`.
6. Create a simple static website by replacing the default index page.
7. Set appropriate permissions for the web root directory and files.
8. Configure a basic server block (virtual host) for a custom domain or IP.
9. Configure multiple server blocks to host multiple websites on one server.
10. Edit the `/etc/hosts` file to map test domain names to localhost for testing.
11. Create custom error pages (e.g., 404, 500) and configure them in server blocks.
12. Configure a reverse proxy to forward requests to a backend server (Apache, Node.js, etc.).
13. Set up load balancing across multiple backend servers using upstream blocks.
14. Implement HTTP basic authentication to restrict access to a directory.
15. Disable directory listing in the server configuration.
16. Hide Nginx version information from HTTP response headers.
17. Create and apply a self-signed SSL certificate to enable HTTPS.
18. Install and configure Let’s Encrypt SSL certificates using Certbot.
19. Configure HTTP to HTTPS redirection.
20. Enable gzip compression for served content.
21. Set browser caching headers for static files.
22. Customize access and error log formats and locations.
23. Monitor access and error logs in real-time using `tail -f`.
24. Configure Nginx to serve PHP applications via PHP-FPM.
25. Write rewrite rules for URL redirection and modification.
26. Test permanent and temporary redirects using curl or browser.
27. Limit client request rates using `limit_req` directives.
28. Limit number of simultaneous connections using `limit_conn`.
29. Use conditional statements and variables in configuration files.
30. Reload Nginx configuration without downtime.
31. Introduce a syntax error in configuration and fix it after troubleshooting with `nginx -t`.
32. Troubleshoot common HTTP errors (403 Forbidden, 404 Not Found, 502 Bad Gateway, 504 Gateway Timeout).
33. Automate SSL certificate renewal with cron or systemd timers.
34. Backup and restore Nginx configuration files.
35. Deploy Nginx inside a Docker container for isolated testing environments.

---

</details>

<details>
  <summary>DNS</summary>

---

**DNS Management Topics in Linux Administration**

1. Introduction to DNS and its role in networking
2. Understanding DNS record types (A, AAAA, CNAME, MX, NS, PTR, TXT, SRV)
3. Installing and configuring DNS servers (BIND, dnsmasq, Unbound)
4. DNS server architecture and components (zones, zone files, resolvers)
5. Forward and reverse DNS lookups
6. Creating and managing DNS zones (primary/master and secondary/slave zones)
7. Configuring zone files: syntax and structure
8. Managing DNS records in zone files
9. Setting up and configuring caching DNS servers
10. Configuring DNS forwarding and recursion
11. Understanding and configuring TTL (Time To Live) values
12. Configuring and managing DNSSEC (DNS Security Extensions)
13. Using tools for DNS diagnostics and troubleshooting (dig, nslookup, host)
14. Configuring and securing BIND server (access control lists, logging, chroot)
15. Implementing dynamic DNS updates (DDNS)
16. Configuring split-horizon (views) DNS
17. Managing DNS zones with DNS management software or web interfaces
18. Integrating DNS with DHCP for dynamic IP address assignment
19. Monitoring and logging DNS server activity
20. Troubleshooting common DNS issues (e.g., resolution failures, propagation delays)

---

## DNS Management – Comprehensive Study Checklist

---

### 1. **Fundamentals of DNS**

* [ ] Understand the purpose and function of DNS in networking
* [ ] Learn about DNS hierarchy and the domain name space
* [ ] Differentiate between DNS record types: A, AAAA, CNAME, MX, NS, PTR, TXT, SRV

---

### 2. **DNS Server Software**

* [ ] Install and configure BIND DNS server
* [ ] Understand alternatives: dnsmasq, Unbound, PowerDNS
* [ ] Know the components of DNS server architecture (zones, resolvers, caching)

---

### 3. **DNS Zones and Zone Files**

* [ ] Create and manage forward DNS zones (primary/master and secondary/slave)
* [ ] Create and manage reverse DNS zones for PTR records
* [ ] Understand and edit zone file syntax and structure
* [ ] Add and update DNS resource records in zone files
* [ ] Increment and manage the zone serial number correctly for updates

---

### 4. **DNS Server Configuration**

* [ ] Configure named.conf (BIND) with proper zone declarations
* [ ] Implement access control lists (ACLs) for security
* [ ] Enable logging for DNS queries and errors
* [ ] Configure chroot jail for BIND server security (optional advanced)

---

### 5. **DNS Query Types and Resolution**

* [ ] Understand recursive vs iterative queries
* [ ] Configure DNS recursion and forwarding
* [ ] Set up caching DNS servers to improve performance

---

### 6. **DNS Security**

* [ ] Implement DNSSEC for zone signing and validation
* [ ] Manage DNSSEC keys and signatures
* [ ] Understand and configure TSIG keys for secure zone transfers
* [ ] Secure zone transfers between primary and secondary servers

---

### 7. **Dynamic DNS (DDNS)**

* [ ] Configure Dynamic DNS updates using `nsupdate` or DHCP integration
* [ ] Manage permissions for dynamic updates
* [ ] Integrate DHCP with DNS for automatic updates of DNS records

---

### 8. **Advanced DNS Configurations**

* [ ] Configure split-horizon (views) DNS for internal/external clients
* [ ] Manage multiple views in named.conf for different network zones
* [ ] Use forwarders and stub zones for complex DNS setups

---

### 9. **DNS Troubleshooting and Diagnostics**

* [ ] Use `dig` to query specific DNS records and diagnose issues
* [ ] Use `nslookup` and `host` for DNS lookups
* [ ] Check zone file syntax with `named-checkzone`
* [ ] Verify BIND configuration syntax with `named-checkconf`
* [ ] Troubleshoot common DNS issues: resolution failures, propagation delays, stale records

---

### 10. **Monitoring and Maintenance**

* [ ] Monitor DNS server logs for abnormal activities
* [ ] Plan and perform regular DNS zone backups
* [ ] Automate DNS server and zone file maintenance tasks
* [ ] Keep DNS server software up to date for security and performance

---

### 11. **Practical Skills**

* [ ] Configure a fully functional authoritative DNS server (primary and secondary)
* [ ] Set up a caching and forwarding DNS server for internal use
* [ ] Perform zone transfers securely between DNS servers
* [ ] Implement DNSSEC and test validation
* [ ] Set up dynamic DNS with DHCP integration
* [ ] Troubleshoot DNS resolution issues using diagnostic tools

---

**Hands-on Exercises in DNS Management**

1. Install BIND DNS server on a Linux machine.
2. Start, stop, and enable the BIND service to run on boot.
3. Configure a basic forward DNS zone for a sample domain (e.g., example.com).
4. Create and edit the zone file with A, CNAME, and MX records.
5. Configure and verify reverse DNS zone for the corresponding IP range.
6. Test DNS resolution using tools like `dig`, `nslookup`, and `host`.
7. Configure and enable DNS recursion and forwarding to an external DNS server.
8. Set up a secondary (slave) DNS server and configure zone transfers securely.
9. Implement access control lists (ACLs) to restrict DNS queries and zone transfers.
10. Configure logging of DNS queries and errors, and analyze the logs.
11. Set up DNSSEC on a zone: generate keys, sign the zone, and verify signatures.
12. Configure Dynamic DNS (DDNS) updates for the zone and update records dynamically.
13. Integrate DHCP with BIND to automatically update DNS records upon lease assignments.
14. Configure split-horizon DNS (views) to serve different DNS responses to internal and external clients.
15. Use `named-checkconf` and `named-checkzone` to validate DNS configuration and zone files.
16. Simulate common DNS issues and troubleshoot them using diagnostic tools.
17. Backup and restore DNS zone files and configuration files.
18. Configure caching DNS server using BIND or dnsmasq for internal network use.
19. Implement and test TSIG keys for securing zone transfers between master and slave servers.
20. Use tools like `tcpdump` or `wireshark` to monitor DNS traffic for troubleshooting.

---

</details>


<details>
  <summary>DHCP</summary>

---

### **DHCP Management Topics**

1. **Introduction to DHCP**

   * Role of DHCP in network management
   * Static vs dynamic IP addressing
   * DHCP lease process (DORA: Discover, Offer, Request, Acknowledgement)

2. **DHCP Protocol Basics**

   * DHCP message types
   * Lease time, renewal, and rebinding
   * DHCP options (e.g., DNS server, default gateway, domain name)
   * DHCP relay agent concept

3. **Installing DHCP Server**

   * Installing `isc-dhcp-server` (Debian/Ubuntu)
   * Installing `dhcpd` on RHEL/CentOS/Fedora
   * Verifying installation and required directories

4. **DHCP Server Configuration**

   * Editing the main configuration file (`/etc/dhcp/dhcpd.conf`)
   * Defining subnet declarations and IP address ranges
   * Setting lease times (default and max lease)
   * Configuring options: router, DNS, NTP, domain-name

5. **Static IP Assignment (DHCP Reservation)**

   * Assigning fixed IPs to clients using MAC addresses
   * Testing reservations with multiple devices

6. **DHCP Lease Management**

   * Viewing active leases (`/var/lib/dhcp/dhcpd.leases`)
   * Releasing and renewing IP leases on clients
   * Clearing or expiring leases manually

7. **Running and Managing DHCP Server**

   * Starting, stopping, and enabling the DHCP service
   * Configuring DHCP to start at boot
   * Checking service status and logs

8. **Logging and Monitoring**

   * Location and interpretation of DHCP logs
   * Monitoring DHCP server activity and failures
   * Troubleshooting client IP assignment issues

9. **DHCP Relay Agent Configuration**

   * Configuring `dhcrelay` on a router or intermediate host
   * Understanding how DHCP relay works across networks

10. **Security in DHCP**

    * Limiting DHCP access to specific MAC or IP ranges
    * Isolating DHCP traffic using VLANs or firewalls
    * Preventing rogue DHCP servers (DHCP snooping concepts)

11. **DHCP Client Configuration**

    * Using `dhclient` to request or release an IP address
    * Manually configuring DHCP on a Linux client
    * Checking client lease files and interface settings

12. **Advanced DHCP Topics**

    * Multiple subnet declarations
    * Failover and load balancing between two DHCP servers
    * Integrating DHCP with DNS (Dynamic DNS updates)
    * IPv6 DHCP (DHCPv6) overview and configuration basics

13. **Alternative DHCP Servers**

    * Overview of `dnsmasq` for lightweight DHCP/DNS
    * Using `systemd-networkd`'s built-in DHCP server (minimal setups)
    * Comparison of ISC DHCP vs Kea DHCP (next-gen ISC server)

14. **Backup and Recovery**

    * Backing up DHCP configuration and lease files
    * Restoring DHCP settings on a new or reinstalled server

---

## DHCP Management in Linux – Comprehensive Study Checklist

---

### 1. **Fundamentals of DHCP**

* [ ] Understand the purpose and function of DHCP
* [ ] Learn the DHCP lease acquisition process (DORA: Discover, Offer, Request, Acknowledge)
* [ ] Identify key DHCP terms: scopes, leases, reservations, options
* [ ] Distinguish between dynamic, automatic, and static (manual) IP assignment

---

### 2. **DHCP Protocol and Options**

* [ ] Understand DHCP message types (Discover, Offer, etc.)
* [ ] Learn about DHCP lease durations and renewal times
* [ ] Study common DHCP options (routers, DNS servers, domain-name, NTP servers)
* [ ] Explore advanced options and custom option definitions

---

### 3. **Installing and Enabling DHCP Server**

* [ ] Install ISC DHCP server (`isc-dhcp-server` or `dhcpd`)
* [ ] Create and verify configuration directories and files
* [ ] Enable and start the DHCP service with `systemctl`
* [ ] Configure the correct network interface for DHCP to listen on

---

### 4. **Basic DHCP Server Configuration**

* [ ] Edit `/etc/dhcp/dhcpd.conf` for global settings
* [ ] Define subnet and IP range declarations
* [ ] Set default and maximum lease times
* [ ] Configure basic DHCP options (gateway, DNS, domain name)

---

### 5. **DHCP Reservation (Static IP Assignment)**

* [ ] Assign a static IP to a client using its MAC address
* [ ] Test the reservation from the client side
* [ ] Use different reservation formats based on OS or DHCP implementation

---

### 6. **Managing DHCP Leases**

* [ ] Understand lease file location (`/var/lib/dhcp/dhcpd.leases`)
* [ ] View and interpret active lease entries
* [ ] Manually release and renew IP leases from clients
* [ ] Clear or expire leases on the server

---

### 7. **Client-Side DHCP Configuration**

* [ ] Use `dhclient` to request or renew IP address
* [ ] Check IP configuration using `ip a` or `ifconfig`
* [ ] View lease details on the client
* [ ] Manually configure or disable DHCP on Linux clients

---

### 8. **Logging and Troubleshooting**

* [ ] Locate and monitor DHCP server logs (e.g., `/var/log/syslog` or `/var/log/messages`)
* [ ] Enable detailed logging in DHCP configuration
* [ ] Troubleshoot issues with leases, reservations, or incorrect options
* [ ] Use tools like `tcpdump` or `wireshark` to inspect DHCP traffic

---

### 9. **DHCP Relay (dhcrelay)**

* [ ] Understand the purpose and function of DHCP relay agents
* [ ] Install and configure `dhcrelay` on an intermediate host
* [ ] Test and verify relay behavior between networks

---

### 10. **Security in DHCP**

* [ ] Restrict access to DHCP based on MAC address or interface
* [ ] Understand and mitigate risks from rogue DHCP servers
* [ ] Explore DHCP snooping (switch-level configuration)
* [ ] Use firewall rules to contain or limit DHCP traffic

---

### 11. **Advanced DHCP Features**

* [ ] Configure multiple subnets and multiple ranges in one config
* [ ] Set up failover/load balancing between two DHCP servers
* [ ] Configure DDNS (Dynamic DNS updates) integration with DHCP
* [ ] Understand DHCPv6 basics and configuration differences

---

### 12. **Alternative DHCP Implementations**

* [ ] Install and configure `dnsmasq` for small-scale DHCP needs
* [ ] Explore `systemd-networkd`'s built-in DHCP server (for minimal systems)
* [ ] Compare ISC DHCP vs Kea DHCP (modern alternative by ISC)

---

### 13. **Maintenance and Backup**

* [ ] Backup DHCP configuration files and lease databases
* [ ] Restore DHCP server from a backup
* [ ] Automate lease cleanup or archiving
* [ ] Keep server software updated and secure

---

## DHCP Management – Hands-On Exercises

1. **Install the DHCP Server**

   * Install `isc-dhcp-server` (Debian/Ubuntu) or `dhcpd` (RHEL/CentOS/Fedora).
   * Verify the installation and locate key configuration files.

2. **Start and Enable the DHCP Service**

   * Start the DHCP service using `systemctl`.
   * Enable the service to start on boot.
   * Check the status and logs for service confirmation.

3. **Configure a Basic DHCP Server**

   * Edit `/etc/dhcp/dhcpd.conf` to define a subnet with:

     * IP address range
     * Default gateway
     * DNS servers
     * Lease time values

4. **Assign Static IPs via DHCP Reservation**

   * Assign a fixed IP to a client using its MAC address.
   * Verify the reservation from both server and client sides.

5. **Configure Multiple Subnets**

   * Define two or more subnet declarations for different networks.
   * Assign each to the correct interface or relay setup.

6. **Start and Use a DHCP Client**

   * Use `dhclient` on a Linux machine to request an IP.
   * Release and renew the IP lease manually.

7. **View and Manage Lease Information**

   * Explore the lease file at `/var/lib/dhcp/dhcpd.leases`.
   * Identify active leases and expired entries.

8. **Enable and Test Logging**

   * Enable detailed DHCP logging in the config.
   * Monitor logs in `/var/log/syslog` or `/var/log/messages`.

9. **Test DHCP Failures and Recovery**

   * Deliberately misconfigure the DHCP server and troubleshoot.
   * Correct the configuration and restore proper lease delivery.

10. **Configure a DHCP Relay**

    * Set up `dhcrelay` to forward requests from a different subnet.
    * Verify relayed requests are handled by the central DHCP server.

11. **Simulate Multiple Clients**

    * Use virtual machines or containers to simulate multiple DHCP clients.
    * Observe how the server handles concurrent requests.

12. **Configure a Secondary DHCP Server (Failover)**

    * Create a second DHCP server in failover mode (if supported).
    * Test load balancing or redundancy behavior.

13. **Integrate DHCP with DNS (Optional Advanced)**

    * Configure Dynamic DNS (DDNS) updates from the DHCP server.
    * Use `nsupdate` to update DNS records based on DHCP events.

14. **Set Up DHCP with dnsmasq (Lightweight Alternative)**

    * Install and configure `dnsmasq` to provide DHCP and DNS services.
    * Test leases and compare behavior with ISC DHCP.

15. **Secure the DHCP Server**

    * Limit access by interface or subnet.
    * Set up firewall rules to restrict DHCP traffic.
    * Identify rogue DHCP servers using `tcpdump` or `nmap`.

16. **Back Up and Restore DHCP Configurations**

    * Create a backup of DHCP config and lease files.
    * Simulate recovery from backup on a new system.

17. **Monitor DHCP Traffic**

    * Use `tcpdump` to capture DHCP packets.
    * Analyze DHCPDISCOVER, DHCPOFFER, DHCPREQUEST, DHCPACK messages.

18. **Experiment with DHCP Options**

    * Add options for domain name, NTP server, WINS server, etc.
    * Verify they are received by the client.

19. **Set Lease Durations**

    * Configure short and long lease times.
    * Observe renewal behavior and logs.

20. **Troubleshoot Common DHCP Issues**

    * Handle scenarios like:

      * IP exhaustion
      * Invalid option delivery
      * Conflicting static/manual IPs

---

</details>

<details>
  <summary>NIS</summary>

---

## **NIS Management Topics in Linux Administration**

---

### 1. **Introduction to NIS**

* What is NIS and its role in centralized authentication
* NIS vs LDAP vs other directory services
* Components of NIS: master server, slave server, clients

---

### 2. **NIS Architecture and Concepts**

* Domain name vs hostname in NIS
* NIS maps: passwd, group, hosts, services, etc.
* ypserv, ypbind, ypxfr, yppush, and their functions
* NIS master-slave replication model

---

### 3. **Installing NIS Services**

* Installing NIS packages: `ypserv`, `ypbind`, `yp-tools`
* Setting up NIS master server
* Configuring slave servers for redundancy
* Installing and configuring NIS client packages

---

### 4. **Configuring NIS Server (Master)**

* Setting the NIS domain name
* Editing and initializing `/etc/yp.conf`, `/var/yp/Makefile`
* Managing source files in `/etc` (passwd, group, hosts, etc.)
* Creating NIS maps using `ypinit -m`
* Starting and enabling NIS services (`ypserv`, `ypxfrd`)

---

### 5. **Configuring NIS Clients**

* Setting the NIS domain name with `domainname` or `/etc/defaultdomain`
* Configuring `/etc/yp.conf` and `/etc/nsswitch.conf`
* Binding the client to the correct NIS domain and server
* Starting and enabling `ypbind` service
* Verifying user and group information from NIS

---

### 6. **Creating and Managing NIS Maps**

* Adding new users and groups to NIS
* Rebuilding and pushing maps using `make` and `yppush`
* Listing available maps using `ypcat`, `ypwhich`, `yppoll`
* Transferring maps to slave servers using `ypxfr`

---

### 7. **NIS Slave Server Configuration**

* Setting up a slave using `ypinit -s`
* Automating map transfer with `cron` or `ypxfrd`
* Testing redundancy and failover

---

### 8. **User Authentication with NIS**

* NIS-based login for users across client machines
* Password management and shadow password support
* Integrating NIS with PAM (Pluggable Authentication Modules)

---

### 9. **Security in NIS**

* Limiting access to NIS servers using TCP wrappers or firewalls
* Restricting map access and controlling which maps are shared
* Using `securenets` file to restrict client access by IP
* Understanding security weaknesses in NIS (e.g., clear-text transmission)

---

### 10. **Troubleshooting NIS**

* Common NIS errors: domain not bound, map not found, authentication failure
* Using diagnostic tools: `ypwhich`, `ypcat`, `yptest`, `rpcinfo`
* Checking and interpreting logs for NIS services
* Restarting services and reinitializing maps

---

### 11. **Maintenance and Backup**

* Backing up NIS source files and map databases
* Updating maps safely without downtime
* Migrating from NIS to LDAP (for long-term maintainability)

---

### 12. **Alternatives and Deprecation**

* Understanding NIS limitations and aging status
* Comparing NIS with LDAP, Kerberos, and SSSD
* Planning transition strategies from NIS to modern authentication systems

---

## ✅ NIS Management in Linux – Comprehensive Study Checklist

---

### 1. **Understanding NIS Basics**

* [ ] Understand the role and purpose of NIS in Linux environments
* [ ] Compare NIS with LDAP and other directory services
* [ ] Learn the client-server architecture of NIS (master, slave, clients)
* [ ] Understand NIS terminology: domain name, maps, bindings, ypbroadcast

---

### 2. **NIS Installation**

* [ ] Install necessary NIS packages (`ypserv`, `ypbind`, `yp-tools`) on server and clients
* [ ] Verify NIS services are installed and accessible

---

### 3. **NIS Server Configuration (Master)**

* [ ] Set the NIS domain name using `domainname` and persist it
* [ ] Configure `/etc/yp.conf` on the server
* [ ] Edit `/var/yp/Makefile` to define which files are mapped
* [ ] Initialize NIS master server with `ypinit -m`
* [ ] Start and enable NIS services: `ypserv`, `ypxfrd`

---

### 4. **Configuring NIS Maps**

* [ ] Understand the function of NIS maps (passwd, group, hosts, etc.)
* [ ] Add users/groups to `/etc/passwd` and `/etc/group` for inclusion in NIS
* [ ] Rebuild maps using `make` and push changes using `yppush`
* [ ] List maps with `ypcat`, `yppoll`, `ypwhich`

---

### 5. **Setting Up NIS Clients**

* [ ] Set and persist the NIS domain name
* [ ] Configure `/etc/yp.conf` and `/etc/nsswitch.conf` on clients
* [ ] Start and enable `ypbind` service
* [ ] Verify successful NIS binding using `ypwhich` and `ypcat`
* [ ] Test login using NIS user accounts

---

### 6. **NIS Slave Server Configuration**

* [ ] Configure a slave server using `ypinit -s`
* [ ] Enable and test map transfers from master using `ypxfr`
* [ ] Ensure the slave takes over if master fails
* [ ] Automate map sync via `cron` or `ypxfrd`

---

### 7. **User Authentication via NIS**

* [ ] Understand how NIS handles login credentials
* [ ] Configure NIS-based authentication using `/etc/nsswitch.conf`
* [ ] Integrate NIS with PAM for login and password management
* [ ] Handle shadow password support in NIS securely

---

### 8. **Securing NIS**

* [ ] Restrict map access using `/var/yp/securenets`
* [ ] Configure firewall or TCP wrappers to limit NIS access
* [ ] Understand the risks of NIS (unencrypted communication)
* [ ] Disable unused or insecure maps

---

### 9. **Troubleshooting NIS**

* [ ] Diagnose domain binding issues with `ypwhich` and `rpcinfo`
* [ ] Resolve common errors: map not found, domain not bound, failed authentication
* [ ] Check logs for `ypserv`, `ypbind`, and other services
* [ ] Restart services and rebuild maps when needed

---

### 10. **Maintenance and Best Practices**

* [ ] Backup NIS source files and map data regularly
* [ ] Safely edit and update maps without interrupting clients
* [ ] Monitor system logs for NIS activity or anomalies
* [ ] Apply updates and patch NIS services when needed

---

### 11. **Migrating from NIS**

* [ ] Understand limitations of NIS and deprecation trends
* [ ] Compare with LDAP, Kerberos, SSSD
* [ ] Plan and test a migration path from NIS to modern alternatives

---

## Hands-On Exercises in NIS Management 

---

### 1. **Install NIS Components**

* Install the required NIS packages:

  * `ypserv`, `ypbind`, `yp-tools` (server and client)
* Verify installation and service availability.

---

### 2. **Set NIS Domain Name**

* Use `domainname` to set the NIS domain temporarily.
* Make the domain name persistent across reboots.

---

### 3. **Configure the NIS Master Server**

* Edit `/etc/yp.conf` to define NIS domain and server.
* Modify `/var/yp/Makefile` to include necessary maps.
* Initialize the master server with `ypinit -m`.
* Start and enable `ypserv` and `ypxfrd`.

---

### 4. **Create and Push NIS Maps**

* Populate `/etc/passwd`, `/etc/group`, and other files.
* Run `make` in `/var/yp` to create maps.
* Use `yppush` to distribute maps to clients or slaves.

---

### 5. **Configure an NIS Client**

* Set the NIS domain name on the client.
* Edit `/etc/yp.conf` to point to the NIS server.
* Modify `/etc/nsswitch.conf` to use NIS for passwd, group, etc.
* Start and enable `ypbind`.

---

### 6. **Verify NIS Client Functionality**

* Run `ypwhich` to check the bound NIS server.
* Use `ypcat passwd` to retrieve map entries.
* Attempt login using an NIS user account.

---

### 7. **Set Up an NIS Slave Server**

* Install NIS packages on the slave.
* Run `ypinit -s` to initialize from the master.
* Schedule map transfers with `ypxfr` or enable `ypxfrd`.

---

### 8. **Add and Manage NIS Users**

* Create a new user in `/etc/passwd` and `/etc/shadow`.
* Rebuild the maps with `make`.
* Test login with the new user from the client.

---

### 9. **Use NIS Diagnostic Tools**

* Use `ypwhich`, `ypcat`, `yppoll`, and `rpcinfo` for diagnostics.
* View and interpret map entries using `ypmatch`.

---

### 10. **Secure the NIS Server**

* Configure `/var/yp/securenets` to restrict access by IP/subnet.
* Apply firewall rules to block unwanted access to NIS ports.
* Disable unused maps or restrict sensitive ones.

---

### 11. **Test NIS Failover with Slave Server**

* Shut down the master server.
* Check if the client binds to the slave server.
* Test NIS services via the slave.

---

### 12. **Automate NIS Map Backups**

* Create a cron job to back up `/etc/passwd`, `/etc/group`, and `/var/yp`.

---

### 13. **Rebuild and Troubleshoot Broken Maps**

* Corrupt or remove a map file, then rebuild it.
* Use logs and `make` to identify and fix the issue.

---

### 14. **Integrate NIS with PAM**

* Modify PAM configuration files to allow NIS authentication.
* Test password changes and login behavior.

---

### 15. **Remove NIS and Revert to Local Authentication**

* Stop and disable NIS services.
* Restore `/etc/nsswitch.conf` to local-only.
* Verify local user login after NIS removal.

---

</details>

<details>
  <summary>NFS</summary>

---

## **NFS Management Topics**

---

### 1. **Introduction to NFS**

* Purpose and use cases of NFS in networked environments
* NFS vs other file sharing protocols (e.g., SMB, FTP, SSHFS)
* NFS architecture: server-client model

---

### 2. **NFS Versions**

* Overview of NFS versions: NFSv2, NFSv3, NFSv4
* Key differences and improvements in NFSv4
* Compatibility considerations between versions

---

### 3. **Installing NFS Services**

* Installing NFS server and client packages (`nfs-utils`, `nfs-common`)
* Verifying required services: `nfs-server`, `rpcbind`, `nfslock`

---

### 4. **Configuring the NFS Server**

* Editing the `/etc/exports` file
* Exporting directories with specific options (ro, rw, no_root_squash, etc.)
* Setting export access control (IP address, subnet, hostname)
* Applying changes with `exportfs`

---

### 5. **Starting and Managing NFS Services**

* Starting, stopping, and enabling NFS-related services
* Managing services: `nfs-server`, `rpcbind`, `nfs-idmapd`
* Checking service status and troubleshooting startup

---

### 6. **NFS Client Configuration**

* Mounting NFS shares manually using `mount` command
* Editing `/etc/fstab` for persistent NFS mounts
* Understanding mount options (`soft`, `hard`, `intr`, `nolock`, etc.)

---

### 7. **NFSv4 Specific Configuration**

* Configuring NFSv4 domain name and `/etc/idmapd.conf`
* Using NFSv4 pseudo root
* Exporting and mounting NFSv4 without `/etc/exports` path dependencies
* Handling user and group name mapping

---

### 8. **User and Permission Management**

* Understanding how NFS handles file ownership and permissions
* Role of UID and GID matching between server and client
* Using `no_root_squash` and `root_squash` options
* Syncing user/group IDs with NIS/LDAP (optional)

---

### 9. **Firewall and Network Configuration**

* Opening required NFS ports (2049, rpcbind, mountd, etc.)
* Configuring firewalls (firewalld, iptables, nftables) for NFS
* Using static ports for NFS and mountd for easier firewall setup

---

### 10. **Security in NFS**

* Restricting access by IP, subnet, or hostname
* Using `root_squash` to limit root access from clients
* Implementing Kerberos authentication with NFSv4 (optional/advanced)
* Using `sec=sys`, `sec=krb5`, `krb5i`, `krb5p` options

---

### 11. **Monitoring and Troubleshooting**

* Viewing active NFS mounts with `showmount` or `nfsstat`
* Checking logs (`/var/log/messages`, `journalctl`) for NFS errors
* Diagnosing stale NFS mounts and lock issues
* Using `rpcinfo` and `netstat` to debug connectivity problems

---

### 12. **NFS Performance Tuning**

* Tuning NFS performance with mount options
* Adjusting read/write buffer sizes
* Using async/sync options
* Monitoring performance with tools like `iotop`, `nfsstat`, `nmon`, `dstat`

---

### 13. **Advanced NFS Configurations**

* Setting up NFS behind NAT or firewalls with fixed ports
* NFS over TCP vs UDP
* Using automount (`autofs`) for on-demand mounting
* Exporting read-only or read-write with user-specific permissions

---

### 14. **NFS Backup and Recovery**

* Backup strategies for NFS shares
* Restoring shared directories
* Snapshot integration (with LVM or Btrfs/ZFS) for shared data

---

### 15. **Alternative and Related Technologies**

* Comparison with SMB/CIFS (Samba)
* When to use NFS vs SSHFS or rsync
* Combining NFS with high availability solutions (e.g., DRBD, Pacemaker)

---

## ✅ NFS Management in Linux – Comprehensive Study Checklist

---

### 1. **Understanding NFS Basics**

* [ ] Understand the purpose and use cases of NFS
* [ ] Learn NFS client-server architecture
* [ ] Identify when to use NFS vs SMB, SSHFS, or rsync
* [ ] Know the differences between NFSv2, v3, and v4

---

### 2. **Installing NFS Services**

* [ ] Install NFS server (`nfs-utils`, `nfs-kernel-server`, etc.)
* [ ] Install NFS client tools (`nfs-common`)
* [ ] Install and configure `rpcbind` and other required services

---

### 3. **Configuring the NFS Server**

* [ ] Edit and manage the `/etc/exports` file
* [ ] Set correct export options (`rw`, `ro`, `sync`, `async`, etc.)
* [ ] Restrict exports to specific IPs or hostnames
* [ ] Use `exportfs -a` and `exportfs -r` to apply changes
* [ ] Test exported directories with `showmount -e`

---

### 4. **Starting and Managing NFS Services**

* [ ] Start and enable `nfs-server` and related services
* [ ] Use `systemctl` to manage `nfs-server`, `rpcbind`, `nfs-idmapd`
* [ ] Verify active exports using `exportfs`
* [ ] Check the status of NFS services and troubleshoot failures

---

### 5. **Configuring NFS Clients**

* [ ] Mount NFS shares manually using the `mount` command
* [ ] Add entries to `/etc/fstab` for persistent mounts
* [ ] Use appropriate mount options (`soft`, `hard`, `intr`, `nolock`, etc.)
* [ ] Use `showmount` and `mount` to verify client access

---

### 6. **NFSv4 Specific Configuration**

* [ ] Configure NFSv4 pseudo root and `/etc/idmapd.conf`
* [ ] Understand NFSv4 mount points and unified namespace
* [ ] Use NFSv4 with or without `/etc/exports` full paths
* [ ] Resolve identity mapping issues between server and client

---

### 7. **User Permissions and UID/GID Mapping**

* [ ] Understand how file ownership is handled in NFS
* [ ] Sync user and group IDs between server and clients
* [ ] Use `root_squash`, `no_root_squash`, `all_squash` options appropriately

---

### 8. **Firewall and Network Access**

* [ ] Open required NFS and RPC ports in `firewalld` or `iptables`
* [ ] Configure static ports for `mountd`, `statd`, and `lockd`
* [ ] Verify connectivity using `rpcinfo`, `netstat`, or `ss`

---

### 9. **Security Practices**

* [ ] Restrict NFS access to trusted hosts/networks
* [ ] Use `root_squash` to limit root privileges from clients
* [ ] Understand and (optionally) configure NFSv4 with Kerberos:

  * `sec=sys`, `krb5`, `krb5i`, `krb5p`
* [ ] Monitor access and prevent unauthorized sharing

---

### 10. **Monitoring and Troubleshooting**

* [ ] Use `nfsstat` and `showmount` for monitoring
* [ ] Check logs (`/var/log/messages`, `journalctl`, etc.) for errors
* [ ] Detect and fix stale mounts
* [ ] Use `rpcinfo`, `dmesg`, and client-side logs for debugging

---

### 11. **Performance Tuning**

* [ ] Optimize NFS performance with mount options (`rsize`, `wsize`)
* [ ] Use `async` or `sync` options wisely
* [ ] Monitor network and disk I/O to identify bottlenecks
* [ ] Consider using `autofs` for dynamic mounting

---

### 12. **Using Automount (autofs)**

* [ ] Install and configure `autofs`
* [ ] Set up `/etc/auto.master` and map files
* [ ] Verify on-demand mounting and unmounting behavior

---

### 13. **Backup and Recovery**

* [ ] Implement backup strategies for exported directories
* [ ] Use snapshot tools (LVM, Btrfs, etc.) with NFS shares
* [ ] Test backup and restore scenarios for shared data

---

### 14. **Advanced Configurations**

* [ ] Export NFS shares with fine-grained permissions
* [ ] Combine NFS with HA tools (e.g., Pacemaker, DRBD)
* [ ] Configure cross-platform NFS usage (Linux <-> BSD, macOS)
* [ ] Enable and test NFS over TCP vs UDP

---

### 15. **Decommissioning and Cleanup**

* [ ] Unmount NFS shares cleanly
* [ ] Remove entries from `/etc/fstab` and `/etc/exports`
* [ ] Disable and stop NFS services when no longer needed

---

## Hands-On Exercises in NFS Management

---

### 1. **Install NFS Server and Client Packages**

* Install `nfs-utils` (RHEL/CentOS) or `nfs-kernel-server` (Debian/Ubuntu) on the server.
* Install `nfs-common` on the client system.
* Verify installations with `rpm -qa`, `dpkg -l`, or `which`.

---

### 2. **Enable and Start NFS Services**

* Enable and start the following services:

  * `nfs-server`
  * `rpcbind`
  * `nfs-idmapd`
* Use `systemctl` to verify service status.

---

### 3. **Create and Export a Shared Directory**

* Create a directory (e.g., `/srv/nfs/shared`) on the NFS server.
* Set permissions and ownership appropriately.
* Edit `/etc/exports` to export the directory with options like:

  * `rw`, `sync`, `no_subtree_check`
* Run `exportfs -a` to apply exports.

---

### 4. **Verify Exported File Systems**

* Use `exportfs -v` to verify active exports.
* Use `showmount -e <nfs-server-ip>` from a client to list available exports.

---

### 5. **Mount NFS Share on Client (Temporary Mount)**

* Use the `mount` command to manually mount the NFS share:

  ```
  mount -t nfs <nfs-server-ip>:/srv/nfs/shared /mnt/nfs
  ```
* Verify the mount with `df -h` or `mount`.

---

### 6. **Configure Persistent Mounts (fstab)**

* Edit `/etc/fstab` on the client to auto-mount the NFS share at boot:

  ```
  <nfs-server-ip>:/srv/nfs/shared  /mnt/nfs  nfs  defaults  0  0
  ```
* Reboot or run `mount -a` to test.

---

### 7. **Test File Sharing Between Client and Server**

* On the client, create a file inside the mounted NFS directory.
* On the server, verify the file was created.
* Test read/write behavior from multiple clients.

---

### 8. **Experiment with Export Options**

* Modify `/etc/exports` to test options like:

  * `ro`, `rw`, `no_root_squash`, `all_squash`
* Re-export with `exportfs -ra`.
* Observe behavior changes from the client side.

---

### 9. **Set Up NFSv4 with Pseudo-Root**

* Configure NFSv4 with a pseudo-root directory (e.g., `/export`).
* Bind export directories under `/export` using `mount --bind`.
* Ensure `/etc/exports` contains NFSv4-style paths.
* Test NFSv4 mount from client:

  ```
  mount -t nfs4 <nfs-server-ip>:/ /mnt/nfs
  ```

---

### 10. **Configure and Test `idmapd` for NFSv4**

* Edit `/etc/idmapd.conf` on both server and client.
* Set the correct `Domain` and `Local-Realms`.
* Restart `nfs-idmapd` service.
* Test if usernames (not just UIDs) show up correctly.

---

### 11. **Set Up Firewall Rules for NFS**

* Open required ports for NFS, `rpcbind`, and `mountd`.
* For example, on firewalld:

  ```
  firewall-cmd --permanent --add-service=nfs
  firewall-cmd --reload
  ```
* Test connectivity from the client.

---

### 12. **Configure Static NFS Ports (Advanced)**

* Configure fixed ports for `mountd`, `statd`, and `lockd` in `/etc/sysconfig/nfs` or `/etc/nfs.conf`.
* Update firewall rules accordingly.
* Restart NFS services and test from client.

---

### 13. **Test Automounting with autofs**

* Install `autofs`.
* Configure `/etc/auto.master` and `/etc/auto.nfs` map files.
* Restart `autofs` and test on-demand mounting by accessing mount point.

---

### 14. **Simulate Network Failure or Server Unavailability**

* Unplug or stop the NFS server.
* Observe behavior on the client (e.g., hanging processes).
* Use `soft` and `hard` mount options to test differences.

---

### 15. **Monitor NFS Activity and Status**

* Use `nfsstat`, `rpcinfo`, and `ss` to monitor connections.
* Check `/proc/mounts` and `/proc/fs/nfsfs/volumes`.

---

### 16. **Troubleshoot NFS Issues**

* Test invalid mounts or missing exports.
* Check logs with `journalctl`, `/var/log/messages`, or `/var/log/syslog`.
* Use `rpcinfo -p` to list RPC services and ports.

---

### 17. **Backup and Restore Exported Data**

* Use `rsync`, `tar`, or `cp` to back up exported directories.
* Test restoring data while preserving permissions and timestamps.

---

</details>

<details>
  <summary>FTP</summary>
  
---

## ✅ Topics in FTP Management

---

### 1. **Introduction to FTP**

* What is FTP and how it works (control/data channels)
* Active vs Passive FTP modes
* FTP vs SFTP vs FTPS vs SCP
* Use cases for FTP in enterprise and legacy systems

---

### 2. **FTP Server Software Options**

* Overview of common Linux FTP servers:

  * `vsftpd` (Very Secure FTP Daemon)
  * `ProFTPD`
  * `Pure-FTPd`
* Choosing the right FTP server for your use case

---

### 3. **Installing an FTP Server**

* Installing vsftpd on RHEL/CentOS, Debian/Ubuntu
* Installing ProFTPD or Pure-FTPd as alternatives
* Verifying installation and locating configuration files

---

### 4. **Basic FTP Server Configuration**

* Main configuration file locations:

  * `/etc/vsftpd/vsftpd.conf`
  * `/etc/proftpd/proftpd.conf`
* Setting FTP root directories (`chroot`)
* Defining default ports and passive port ranges
* Allowing or denying anonymous logins
* Configuring banner messages and logging

---

### 5. **User Management for FTP**

* Configuring local Linux users for FTP access
* Creating FTP-only users (nologin/shell-less)
* Configuring chroot jails for individual users
* Managing upload/download permissions

---

### 6. **Anonymous FTP Configuration**

* Enabling anonymous access securely
* Restricting permissions (read-only or upload-only)
* Disabling write access for anonymous users

---

### 7. **Securing FTP Connections**

* Disabling plain FTP; enforcing encryption (FTPS)
* Configuring vsftpd with TLS/SSL (using OpenSSL certificates)
* Using passive mode securely with firewalls
* Hardening user permissions and disabling shell access
* Logging and auditing access attempts

---

### 8. **Firewall and SELinux Configuration**

* Opening standard FTP and passive port ranges
* Adjusting `firewalld` or `iptables` for FTP
* Configuring SELinux policies for vsftpd
* Using `setsebool` and `semanage` for FTP SELinux rules

---

### 9. **Virtual Users for FTP**

* Setting up virtual FTP users with:

  * PAM
  * DB-based backends (Berkeley DB, MySQL, etc.)
* Mapping virtual users to system users or restricted chroot environments

---

### 10. **Logging and Monitoring**

* Location and analysis of FTP logs:

  * `/var/log/vsftpd.log`
  * `/var/log/xferlog`
* Monitoring with tools like `logwatch`, `journalctl`, `fail2ban`

---

### 11. **Troubleshooting FTP Issues**

* Diagnosing common issues:

  * Connection timeouts
  * Login failures
  * Permission denied errors
* Using tools like `ftp`, `lftp`, `telnet`, `netstat`, `ss`, `tcpdump`
* Checking passive/active mode behavior

---

### 12. **FTP Client Configuration**

* Using command-line FTP clients (`ftp`, `lftp`, `ncftp`)
* Using GUI clients (FileZilla, WinSCP)
* Automating FTP transfers with scripts

---

### 13. **Performance and Resource Tuning**

* Limiting connections per IP/user
* Bandwidth throttling (upload/download rates)
* Timeouts and idle session control
* Maximum client sessions and queued connections

---

### 14. **Advanced Configuration Topics**

* Configuring virtual hosts in ProFTPD
* Using MySQL/LDAP authentication with Pure-FTPd
* Integration with chrooted environments and jail directories
* Setting per-user or per-IP policies

---

### 15. **Migrating and Replacing FTP**

* Migrating users and data from older FTP servers
* Planning transition from FTP to SFTP/SCP
* Decommissioning insecure FTP setups

---

## ✅ FTP Management – Comprehensive Study Checklist

---

### 1. **Understand FTP Basics**

* [ ] Learn FTP protocol fundamentals: control and data connections
* [ ] Differentiate Active vs Passive FTP modes
* [ ] Understand FTP vs SFTP vs FTPS vs SCP use cases

---

### 2. **FTP Server Software and Installation**

* [ ] Know popular FTP servers: vsftpd, ProFTPD, Pure-FTPd
* [ ] Install FTP server packages on major Linux distros
* [ ] Locate and understand main FTP configuration files

---

### 3. **Basic FTP Server Configuration**

* [ ] Configure FTP root directories and chroot jails
* [ ] Set default ports and passive port ranges
* [ ] Enable or disable anonymous FTP access securely
* [ ] Configure welcome/banner messages and logging

---

### 4. **User Management**

* [ ] Create and configure local users for FTP access
* [ ] Create FTP-only users without shell access
* [ ] Configure permissions and chroot environment for users
* [ ] Manage upload/download rights per user

---

### 5. **Anonymous FTP Setup**

* [ ] Enable anonymous FTP if required
* [ ] Restrict permissions (read-only or upload-only)
* [ ] Secure anonymous access to prevent misuse

---

### 6. **Securing FTP**

* [ ] Configure FTPS (FTP over SSL/TLS) with certificates
* [ ] Disable plain-text FTP where possible
* [ ] Manage firewall rules for FTP and passive ports
* [ ] Harden user permissions and disable shell access for FTP users
* [ ] Set up logging and monitoring for security auditing

---

### 7. **Firewall and SELinux Configuration**

* [ ] Open FTP control and data ports in firewalls (`firewalld`, `iptables`)
* [ ] Configure SELinux policies for FTP servers
* [ ] Use `setsebool` and `semanage` commands for FTP-related SELinux booleans

---

### 8. **Virtual User Management**

* [ ] Set up virtual FTP users via PAM or database backends
* [ ] Map virtual users to system users or restricted directories
* [ ] Configure authentication mechanisms for virtual users

---

### 9. **Logging and Monitoring**

* [ ] Locate and analyze FTP logs (`vsftpd.log`, `xferlog`)
* [ ] Use log monitoring tools (`logwatch`, `fail2ban`)
* [ ] Monitor FTP sessions and active connections

---

### 10. **Troubleshooting FTP Issues**

* [ ] Diagnose common FTP errors: connection refused, permission denied
* [ ] Troubleshoot passive/active mode connection issues
* [ ] Use command-line tools (`ftp`, `lftp`, `telnet`, `tcpdump`) for debugging
* [ ] Review logs and SELinux denials

---

### 11. **FTP Client Usage**

* [ ] Use command-line FTP clients for manual transfers
* [ ] Understand GUI FTP clients (FileZilla, WinSCP)
* [ ] Automate FTP transfers using scripts and cron jobs

---

### 12. **Performance Tuning**

* [ ] Limit number of simultaneous connections per user/IP
* [ ] Set bandwidth limits (upload/download speed throttling)
* [ ] Configure session timeouts and idle disconnects
* [ ] Adjust max clients and queued connection parameters

---

### 13. **Advanced FTP Server Configuration**

* [ ] Configure virtual hosts (ProFTPD) for multiple FTP sites
* [ ] Integrate FTP servers with databases (MySQL, LDAP) for user authentication
* [ ] Implement per-user or per-group restrictions and quotas
* [ ] Use jail/chroot environments for enhanced security

---

### 14. **Migration and Alternatives**

* [ ] Plan migration from legacy FTP to SFTP or FTPS
* [ ] Backup and restore FTP user data and configurations
* [ ] Understand benefits of SFTP and SCP as secure alternatives to FTP

---

## Hands-On Exercises for FTP Management

---

### 1. **Install FTP Server Software**

* Install vsftpd (or ProFTPD/Pure-FTPd) on your Linux server.
* Verify installation and locate configuration files.

---

### 2. **Start and Enable FTP Service**

* Start the FTP service (`vsftpd`).
* Enable it to start automatically on boot.
* Check service status with `systemctl`.

---

### 3. **Configure Basic FTP Server Settings**

* Edit `/etc/vsftpd/vsftpd.conf` to:

  * Enable/disable anonymous FTP.
  * Set the FTP root directory.
  * Enable logging.
* Restart the service to apply changes.

---

### 4. **Create FTP Users and Set Permissions**

* Create a system user for FTP access.
* Set appropriate directory ownership and permissions.
* Restrict users to their home directories (chroot jail).

---

### 5. **Configure Anonymous FTP Access**

* Enable anonymous login securely.
* Set upload/download permissions for anonymous users.
* Test anonymous FTP access from a client.

---

### 6. **Configure Passive Mode and Firewall**

* Configure passive port range in FTP server config.
* Open FTP and passive ports in firewall (`firewalld` or `iptables`).
* Test FTP connection in passive mode from client.

---

### 7. **Enable and Configure FTPS (FTP over SSL/TLS)**

* Generate or install SSL certificates.
* Configure vsftpd for SSL/TLS encrypted FTP.
* Test secure FTP connection using FTPS client.

---

### 8. **Set Up FTP-Only Users (No Shell Access)**

* Create users with `/sbin/nologin` shell.
* Configure FTP server to allow these users.
* Test login and file transfer.

---

### 9. **Configure Virtual FTP Users (Optional)**

* Create a virtual user database (e.g., using PAM).
* Map virtual users to directories.
* Test login with virtual FTP users.

---

### 10. **Automate FTP File Transfers**

* Use command-line FTP or `lftp` to upload/download files.
* Create simple FTP scripts for automated transfers.
* Schedule FTP transfers using `cron`.

---

### 11. **Monitor FTP Logs and Sessions**

* Locate and analyze FTP logs.
* Use tools like `tail`, `grep` to filter log entries.
* Monitor active FTP sessions and connections.

---

### 12. **Troubleshoot Common FTP Issues**

* Simulate and fix permission errors.
* Diagnose connection failures (firewall, SELinux).
* Resolve passive vs active mode connection issues.

---

### 13. **Limit FTP Connections and Bandwidth**

* Configure max clients and connections per IP.
* Set upload/download bandwidth limits.
* Test connection limits from multiple clients.
* Quota limits - user , group , project

---

### 14. **Backup and Restore FTP Configuration and Data**

* Backup FTP server config files and user directories.
* Restore from backup and verify service functionality.

---

</details>

<details>
  <summary>SAMBA</summary>

---

## Topics in Samba Management

---

### 1. **Introduction to Samba**

* Overview of Samba and SMB/CIFS protocol
* Samba use cases in Linux and Windows interoperability
* Differences between Samba and NFS

---

### 2. **Installing Samba**

* Installing Samba packages on various Linux distributions
* Understanding Samba server components (`smbd`, `nmbd`, `winbindd`)
* Verifying installation and service status

---

### 3. **Samba Configuration Basics**

* Samba configuration file: `/etc/samba/smb.conf`
* Global section configuration parameters
* Defining shares and share-specific parameters
* Configuring workgroups and server role (standalone, domain member, AD DC)

---

### 4. **User and Authentication Management**

* Samba users vs Linux users
* Adding and managing Samba users with `smbpasswd`
* Configuring passdb backends (tdbsam, smbpasswd, ldapsam)
* Integrating Samba with system authentication (PAM, NSS)

---

### 5. **File Sharing Configuration**

* Creating and configuring share definitions
* Setting permissions and access control (read-only, read-write)
* Configuring guest access and anonymous shares
* Setting valid users, write list, and other access restrictions

---

### 6. **Print Sharing**

* Configuring Samba as a print server
* Sharing printers over SMB
* Managing printer permissions and options

---

### 7. **Integration with Windows Networks**

* Joining Samba to an Active Directory domain
* Using `winbind` for user and group mapping
* Configuring Kerberos for authentication
* Managing Samba as a Domain Controller (NT4 style or Active Directory DC)

---

### 8. **Security and Hardening**

* Securing Samba with proper permissions
* Encrypting SMB communication
* Using firewalls and SELinux with Samba
* Restricting access with hosts allow/deny and `smb.conf` settings

---

### 9. **Samba Services and Daemons**

* Understanding roles of `smbd`, `nmbd`, and `winbindd`
* Starting, stopping, enabling Samba services
* Troubleshooting Samba daemons

---

### 10. **Monitoring and Logging**

* Samba log files location and configuration
* Using `testparm` to check configuration syntax
* Monitoring Samba connections and shares
* Analyzing logs for troubleshooting

---

### 11. **Performance Tuning**

* Optimizing Samba parameters for performance
* Managing concurrent connections
* Adjusting socket options and cache settings

---

### 12. **Backup and Recovery**

* Backing up Samba configuration and data
* Restoring shares and user databases

---

### 13. **Advanced Samba Configuration**

* VFS modules and custom extensions
* Samba clustering and replication options
* Configuring DFS (Distributed File System) shares

---

### 14. **Troubleshooting Samba**

* Common Samba errors and fixes
* Diagnosing connectivity and permission issues
* Using tools like `smbclient`, `smbstatus`, `rpcclient`

---

## ✅ Samba Management – Comprehensive Study Checklist

---

### 1. **Understand Samba Basics**

* [ ] Learn Samba architecture and SMB/CIFS protocol fundamentals
* [ ] Understand Samba’s role in Linux-Windows interoperability
* [ ] Differentiate Samba from other file sharing protocols like NFS

---

### 2. **Install Samba**

* [ ] Install Samba packages on major Linux distributions
* [ ] Understand the roles of `smbd`, `nmbd`, and `winbindd` daemons
* [ ] Verify installation and service status

---

### 3. **Configure Samba**

* [ ] Locate and understand the `/etc/samba/smb.conf` configuration file
* [ ] Configure global settings (workgroup, server role, netbios name)
* [ ] Define and configure file and printer shares
* [ ] Set appropriate permissions and access controls for shares

---

### 4. **Manage Users and Authentication**

* [ ] Add and manage Samba users with `smbpasswd`
* [ ] Understand Samba user vs Linux system user concepts
* [ ] Configure passdb backends (tdbsam, smbpasswd, ldapsam)
* [ ] Integrate Samba with system authentication services (PAM, NSS)

---

### 5. **Configure File Sharing**

* [ ] Set up read-only and read-write shares
* [ ] Configure guest and anonymous access securely
* [ ] Manage valid users, write lists, and deny lists for shares

---

### 6. **Set Up Print Sharing**

* [ ] Configure Samba as a print server
* [ ] Share printers over SMB protocol
* [ ] Manage printer permissions and options

---

### 7. **Integrate Samba with Windows Networks**

* [ ] Join Samba to an Active Directory domain
* [ ] Configure and use `winbind` for user and group mapping
* [ ] Set up Kerberos authentication for Samba
* [ ] Configure Samba as an NT4-style domain controller or Active Directory DC

---

### 8. **Secure Samba**

* [ ] Harden Samba configuration for security
* [ ] Enable encryption for SMB communication
* [ ] Configure firewall rules for Samba ports
* [ ] Manage SELinux policies related to Samba
* [ ] Use hosts allow/deny and other access restrictions in `smb.conf`

---

### 9. **Manage Samba Services**

* [ ] Understand the functions of `smbd`, `nmbd`, and `winbindd`
* [ ] Start, stop, restart, and enable Samba services at boot
* [ ] Troubleshoot common daemon issues

---

### 10. **Monitor and Log Samba Activity**

* [ ] Configure Samba logging levels and log file locations
* [ ] Use `testparm` to validate Samba configuration
* [ ] Monitor active Samba sessions and shares (`smbstatus`)
* [ ] Analyze logs for troubleshooting connection and permission problems

---

### 11. **Tune Samba Performance**

* [ ] Optimize Samba socket options and cache settings
* [ ] Adjust limits on concurrent connections
* [ ] Fine-tune Samba parameters for workload demands

---

### 12. **Backup and Restore Samba Configuration**

* [ ] Backup `/etc/samba/smb.conf` and Samba user databases
* [ ] Plan and test restoration of Samba configuration and data

---

### 13. **Advanced Samba Features**

* [ ] Explore VFS modules for extended functionality
* [ ] Understand Samba clustering and replication options
* [ ] Configure DFS (Distributed File System) shares for enterprise setups

---

### 14. **Troubleshoot Samba**

* [ ] Diagnose and resolve common Samba errors
* [ ] Use diagnostic tools: `smbclient`, `smbstatus`, `rpcclient`, `wbinfo`
* [ ] Troubleshoot connectivity, permission, and authentication issues

---

## Hands-On Exercises in Samba Management

---

### 1. **Install Samba Server**

* Install Samba packages on your Linux system (`yum`, `apt`, or `dnf`).
* Verify the installation and check Samba service status.

---

### 2. **Start and Enable Samba Services**

* Start `smbd` and `nmbd` services.
* Enable Samba services to start on boot.
* Verify service status using `systemctl`.

---

### 3. **Configure Basic Samba Settings**

* Edit `/etc/samba/smb.conf` to set:

  * Workgroup name
  * Server description
  * NetBIOS name
* Restart Samba and test configuration with `testparm`.

---

### 4. **Create and Share a Directory**

* Create a directory to be shared.
* Configure a basic Samba share in `smb.conf`.
* Set appropriate filesystem permissions.
* Restart Samba and access the share from a Linux or Windows client.

---

### 5. **Add Samba Users**

* Add system users to the Linux server.
* Add corresponding Samba users with `smbpasswd`.
* Test authentication using `smbclient` from the command line.

---

### 6. **Configure Share Permissions**

* Set read-only and read-write permissions for different users.
* Configure `valid users`, `write list`, and `browseable` options in `smb.conf`.
* Test access restrictions from clients.

---

### 7. **Enable Guest and Anonymous Access**

* Configure a guest-accessible share.
* Test anonymous access from client machines.
* Secure guest shares by limiting permissions.

---

### 8. **Set Up Samba Print Server**

* Configure Samba to share a local printer.
* Share the printer via Samba.
* Test printing from a Windows or Linux client.

---

### 9. **Join Samba Server to Active Directory Domain**

* Configure Kerberos client on the Linux server.
* Join Samba to an AD domain using `net ads join`.
* Verify domain membership and access domain resources.

---

### 10. **Configure Winbind for Authentication**

* Install and configure `winbind`.
* Test user and group lookup with `wbinfo` and `getent`.
* Configure PAM for winbind authentication.

---

### 11. **Configure and Use Samba as a Domain Controller**

* Set Samba server as an NT4-style domain controller.
* Add users and groups to Samba domain.
* Join Windows clients to the Samba domain.

---

### 12. **Secure Samba Configuration**

* Configure firewall rules to allow SMB ports.
* Set SELinux booleans for Samba if enabled.
* Restrict access with `hosts allow/deny` directives.
* Enable SMB encryption if supported.

---

### 13. **Monitor Samba Logs and Sessions**

* Locate Samba log files and increase logging verbosity if needed.
* Use `smbstatus` to monitor active connections and locks.
* Analyze logs to troubleshoot issues.

---

### 14. **Troubleshoot Samba Issues**

* Diagnose permission issues and fix them.
* Troubleshoot connectivity problems with `ping`, `telnet`, and `rpcclient`.
* Use `testparm` to validate Samba configuration.

---

### 15. **Backup and Restore Samba Configuration**

* Backup Samba configuration files and user databases.
* Restore configuration from backup and verify functionality.

---

</details>

<details>
  <summary>Squid Proxy</summary>
  
---

## Topics in Squid Proxy Management

---

### 1. **Introduction to Squid Proxy**

* Overview of Squid and proxy server concepts
* Types of proxy servers: forward, reverse, transparent
* Benefits of using Squid (caching, filtering, access control)
* Squid architecture and data flow

---

### 2. **Installing Squid**

* Installing Squid on major Linux distributions (`apt`, `dnf`, `yum`)
* Verifying installation and version
* Understanding Squid’s default file structure

---

### 3. **Squid Configuration Basics**

* Main configuration file: `/etc/squid/squid.conf`
* Key directives: `http_port`, `cache_dir`, `access_log`, etc.
* Understanding ACLs (Access Control Lists) and rules
* Testing configuration with `squid -k parse`

---

### 4. **Access Control and ACL Management**

* Creating ACLs for IP addresses, domains, users, methods
* Applying rules with `http_access`
* Blocking or allowing specific websites or content types
* Restricting access by time or user group

---

### 5. **Authentication Integration**

* Configuring user authentication (Basic, Digest, NTLM, Kerberos)
* Integrating Squid with LDAP or Active Directory
* Managing credentials and security of authentication

---

### 6. **Caching Management**

* How Squid caching works
* Configuring `cache_mem`, `maximum_object_size`, `cache_dir`, etc.
* Managing and cleaning cache (`squid -z`, `squid -k shutdown`)
* Cache hierarchy and parent-child proxy setup

---

### 7. **Logging and Monitoring**

* Understanding and configuring Squid log files:

  * `access.log`, `cache.log`, `store.log`
* Using log analysis tools like `sarg`, `squidAnalyzer`
* Monitoring real-time traffic and cache hits/misses

---

### 8. **Bandwidth Management and Delay Pools**

* Limiting bandwidth per user or group
* Configuring delay pools to shape traffic
* Prioritizing access or limiting download speed

---

### 9. **Transparent Proxy Configuration**

* Setting up Squid as a transparent proxy
* Redirecting traffic with `iptables` or firewall rules
* Configuring routers/gateways to forward traffic to Squid

---

### 10. **Reverse Proxy and Web Acceleration**

* Configuring Squid as a reverse proxy for web servers
* Content acceleration and reducing backend server load
* SSL termination with reverse proxy setup

---

### 11. **HTTPS and SSL Interception**

* Handling HTTPS traffic with SSL Bump
* Generating and managing certificates
* Legal/ethical implications and best practices of SSL interception

---

### 12. **High Availability and Load Balancing**

* Running multiple Squid servers
* Using CARP or load balancers for distribution
* Failover strategies and redundancy planning

---

### 13. **Performance Tuning**

* Optimizing memory and disk usage
* Tuning cache performance and access latency
* Reducing DNS resolution time and optimizing refresh patterns

---

### 14. **Troubleshooting Squid**

* Diagnosing common errors in `cache.log`
* Checking network connectivity and firewall issues
* Fixing access denials and ACL misconfigurations
* Restarting and reloading Squid correctly

---

### 15. **Security and Hardening**

* Restricting unauthorized access to the proxy
* Enabling firewalls and securing proxy ports
* Keeping Squid updated and patching vulnerabilities
* Limiting exposure of Squid management interfaces

---

## ✅ Squid Proxy Management – Comprehensive Study Checklist

---

### 1. **Understand Squid Proxy Basics**

* [ ] Learn the purpose and functions of a proxy server
* [ ] Understand types of proxies: forward, reverse, transparent
* [ ] Study Squid’s architecture and data flow model
* [ ] Identify common use cases: caching, filtering, access control, acceleration

---

### 2. **Install Squid**

* [ ] Install Squid on Debian/Ubuntu (`apt`) and RHEL/CentOS/Fedora (`yum`/`dnf`)
* [ ] Locate and understand default Squid configuration directories and files
* [ ] Start, stop, enable Squid service using `systemctl`
* [ ] Test Squid installation using default settings

---

### 3. **Basic Squid Configuration**

* [ ] Edit and understand the main config file: `/etc/squid/squid.conf`
* [ ] Configure `http_port`, `visible_hostname`, `cache_mem`, and `cache_dir`
* [ ] Reload and test configuration changes (`squid -k reconfigure`)
* [ ] Validate configuration syntax using `squid -k parse`

---

### 4. **Access Control and ACL Management**

* [ ] Create ACLs for IPs, domains, time-based access, methods
* [ ] Allow or deny access using `http_access` rules
* [ ] Block specific websites or file types
* [ ] Test ACLs with client browsers and logs

---

### 5. **User Authentication**

* [ ] Configure basic authentication (username/password)
* [ ] Set up Squid to use external authentication helpers (PAM, LDAP)
* [ ] Integrate Squid with Active Directory
* [ ] Test authentication from a client and monitor login attempts

---

### 6. **Caching and Storage Management**

* [ ] Configure memory and disk cache settings (`cache_mem`, `maximum_object_size`)
* [ ] Initialize and manage cache directories (`squid -z`)
* [ ] Set refresh patterns and cache rules
* [ ] Monitor cache hits and misses

---

### 7. **Logging and Monitoring**

* [ ] Understand Squid log files: `access.log`, `cache.log`, `store.log`
* [ ] Enable custom log formats if needed
* [ ] Use tools like `sarg`, `squidAnalyzer`, or `goaccess` for log analysis
* [ ] Monitor real-time connections and traffic

---

### 8. **Bandwidth Control and Delay Pools**

* [ ] Configure delay pools for traffic shaping
* [ ] Limit download speeds per user, IP, or time window
* [ ] Set class 1/2/3 delay pool configurations
* [ ] Test performance impact with large downloads

---

### 9. **Transparent Proxy Setup**

* [ ] Configure Squid as a transparent proxy
* [ ] Redirect HTTP traffic to Squid using `iptables` or `firewalld`
* [ ] Ensure no authentication is required in transparent mode
* [ ] Test with client browsers without manual proxy settings

---

### 10. **Reverse Proxy (Web Acceleration)**

* [ ] Set up Squid as a reverse proxy for a web server
* [ ] Configure cache settings for dynamic/static content
* [ ] Use `cache_peer` and `accelerate` options
* [ ] Test content delivery improvements

---

### 11. **HTTPS and SSL Interception (Optional/Advanced)**

* [ ] Understand SSL Bumping and HTTPS proxying
* [ ] Generate and install CA certificates for SSL interception
* [ ] Configure `ssl_bump`, `tls_outgoing_options`, and relevant ACLs
* [ ] Be aware of legal and privacy considerations

---

### 12. **High Availability and Load Balancing**

* [ ] Deploy multiple Squid instances for load balancing
* [ ] Use CARP (Cache Array Routing Protocol) or external tools for HA
* [ ] Configure `cache_peer` and sibling relationships
* [ ] Monitor health and failover functionality

---

### 13. **Security and Hardening**

* [ ] Restrict access to Squid ports and management interfaces
* [ ] Enable firewall rules to limit access
* [ ] Harden ACLs to prevent unauthorized use
* [ ] Keep Squid updated with security patches

---

### 14. **Performance Tuning**

* [ ] Tune memory and disk cache for performance
* [ ] Enable advanced caching options for large traffic environments
* [ ] Optimize DNS lookups, connection limits, and thread usage
* [ ] Benchmark before and after changes

---

### 15. **Troubleshooting**

* [ ] Identify errors in `cache.log` and `access.log`
* [ ] Diagnose ACL misconfigurations and blocked access
* [ ] Resolve DNS or network issues
* [ ] Use tools like `curl`, `dig`, `telnet`, `tcpdump` for debugging

---

## Hands-On Exercises – Squid Proxy Management in Linux

---

### 1. **Install Squid Proxy Server**

* Install Squid on Ubuntu/Debian (`apt install squid`) or RHEL/CentOS (`dnf/yum install squid`)
* Enable and start the Squid service using `systemctl`
* Verify installation with `squid -v` and `systemctl status squid`

---

### 2. **Configure Basic Squid Settings**

* Edit `/etc/squid/squid.conf` to configure:

  * `http_port`
  * `visible_hostname`
* Reload Squid and test the configuration using `squid -k reconfigure`
* Validate syntax with `squid -k parse`

---

### 3. **Set Up a Basic Forward Proxy**

* Configure a browser or system to use Squid as a proxy
* Test internet access through the proxy
* Analyze the traffic using `access.log`

---

### 4. **Create and Apply ACLs (Access Control Lists)**

* Create ACLs to:

  * Allow/deny specific IP addresses or subnets
  * Restrict access by time of day
  * Block specific domains or file types
* Test by attempting access from allowed and denied clients

---

### 5. **Block Specific Websites**

* Create a blacklist of domains (e.g., `facebook.com`, `youtube.com`)
* Configure Squid to block these using `dstdomain` ACL
* Verify access denial and log entries

---

### 6. **Enable User Authentication**

* Configure basic authentication using `auth_param basic`
* Create user credentials using `htpasswd`
* Require users to authenticate before browsing
* Test with browser prompt or `curl`

---

### 7. **Integrate with LDAP or Active Directory (Advanced)**

* Configure Squid to authenticate users via LDAP
* Test AD/LDAP authentication with domain credentials

---

### 8. **Configure Caching Parameters**

* Adjust `cache_mem`, `maximum_object_size`, and `cache_dir`
* Clear and reinitialize cache using `squid -z`
* Observe caching behavior in logs

---

### 9. **View and Analyze Logs**

* Monitor real-time activity in:

  * `/var/log/squid/access.log`
  * `/var/log/squid/cache.log`
* Use tools like `tail`, `grep`, or `sarg` to analyze traffic patterns

---

### 10. **Implement Delay Pools for Bandwidth Control**

* Configure delay pools to limit bandwidth per user/IP
* Apply class 2 or class 3 delay pools
* Test download speeds before and after applying limits

---

### 11. **Set Up Transparent Proxy (Optional)**

* Configure Squid to run as a transparent proxy
* Use `iptables` to redirect HTTP traffic to Squid’s port
* Test automatic proxying without configuring client browsers

---

### 12. **Configure Squid as a Reverse Proxy**

* Point Squid to a backend web server using `cache_peer`
* Enable `accelerate` and test caching of static content
* Measure response time before and after using Squid

---

### 13. **Enable SSL Bumping (Advanced & Optional)**

* Generate a CA certificate and import it into client browsers
* Configure `ssl_bump` and intercept HTTPS traffic
* Test secure browsing and verify decrypted logs
* Be aware of legal and privacy considerations

---

### 14. **Secure Squid with Firewalls and SELinux**

* Configure firewall rules to allow only specific IPs to connect to Squid
* Set SELinux booleans for Squid if enabled
* Test access from allowed and blocked clients

---

### 15. **Backup and Restore Squid Configuration**

* Backup `/etc/squid/squid.conf` and custom ACL files
* Restore from backup and restart Squid
* Confirm that settings are correctly applied

---

### 16. **Troubleshoot Common Issues**

* Simulate and resolve:

  * "Access Denied" errors
  * Configuration syntax issues
  * Service not starting
* Use `squid -k parse`, `systemctl status`, and logs for troubleshooting

---

</details>


<details>
  <summary>SSH</summary>
  
---

## Topics in SSH Management

---

### 1. **Introduction to SSH**

* Purpose and features of SSH
* SSH protocol overview (SSH-1 vs SSH-2)
* Components: `ssh`, `sshd`, `scp`, `sftp`, `ssh-agent`

---

### 2. **Installing and Enabling SSH**

* Installing `openssh-server` and `openssh-client`
* Enabling and starting the `sshd` service
* Checking SSH version and verifying installation

---

### 3. **SSH Client Usage**

* Connecting to remote systems with `ssh user@host`
* Specifying port, identity file, or custom configuration
* Using `scp` and `sftp` for file transfers
* Common SSH options (`-v`, `-X`, `-L`, `-i`, etc.)

---

### 4. **SSH Server Configuration**

* Main configuration file: `/etc/ssh/sshd_config`
* Configuring port, protocol, and address binding
* Allowing or denying root login
* Limiting user access with `AllowUsers` and `DenyUsers`
* Reloading or restarting the SSH service

---

### 5. **SSH Key-Based Authentication**

* Generating key pairs with `ssh-keygen`
* Deploying public keys to remote servers (`~/.ssh/authorized_keys`)
* Disabling password authentication for enhanced security
* Managing key permissions and formats

---

### 6. **SSH Agent and Key Management**

* Using `ssh-agent` to cache private keys
* Adding keys to the agent with `ssh-add`
* Forwarding keys to remote sessions (`ForwardAgent yes`)
* Managing multiple keys and identities

---

### 7. **SSH Hardening and Security**

* Changing default port (e.g., from 22 to 2222)
* Disabling root login (`PermitRootLogin no`)
* Enforcing key-only authentication
* Limiting login attempts and rate-limiting with `MaxAuthTries`
* Using `Fail2Ban` or similar tools for SSH protection
* Enabling `UseDNS` and `LoginGraceTime` configuration

---

### 8. **SSH Tunneling and Port Forwarding**

* Local port forwarding (`ssh -L`)
* Remote port forwarding (`ssh -R`)
* Dynamic port forwarding (SOCKS proxy) with `ssh -D`
* Use cases: securing insecure protocols, accessing internal resources

---

### 9. **SSH X11 Forwarding**

* Enabling GUI application forwarding (`ssh -X`, `ssh -Y`)
* Configuring X11Forwarding in `sshd_config`
* Security considerations of X11 forwarding

---

### 10. **SSH Connection Multiplexing**

* Reusing SSH sessions with `ControlMaster`, `ControlPath`, and `ControlPersist`
* Faster repeated SSH connections
* Custom SSH client configuration in `~/.ssh/config`

---

### 11. **SSH Logging and Monitoring**

* Log file locations: `/var/log/auth.log`, `/var/log/secure`
* Identifying failed login attempts and brute force attacks
* Enabling verbose logging for debugging
* Tracking user logins and session activity

---

### 12. **Troubleshooting SSH Issues**

* Diagnosing connection timeouts and refused connections
* Dealing with permission denied errors
* Using verbose/debug mode (`ssh -v`, `-vvv`)
* Fixing key or config file permission issues

---

### 13. **SSH Configuration Management**

* Managing global and per-user configuration files (`/etc/ssh/ssh_config`, `~/.ssh/config`)
* Creating host aliases and options
* Managing different identities and key pairs per host

---

### 14. **SSH with Two-Factor Authentication (2FA)**

* Enabling OTP (One-Time Password) with Google Authenticator or Authy
* Configuring PAM for SSH 2FA
* Testing SSH login with password + token

---

### 15. **Advanced SSH Use Cases**

* SSH jump hosts and bastion servers
* ProxyCommand and `ProxyJump` configuration
* Automated tasks and scripts over SSH
* Running remote commands (`ssh user@host command`)

---

## ✅ SSH Management – Comprehensive Study Checklist

---

### 1. **Basics of SSH**

* [ ] Understand what SSH is and how it works (protocols, ports, encryption)
* [ ] Learn the differences between SSH-1 and SSH-2
* [ ] Identify components: `ssh`, `sshd`, `scp`, `sftp`, `ssh-agent`

---

### 2. **Install and Enable SSH**

* [ ] Install OpenSSH server and client packages
* [ ] Enable and start the `sshd` service
* [ ] Verify SSH is listening (check ports using `ss -tnlp` or `netstat`)
* [ ] Confirm connectivity from local and remote machines

---

### 3. **Use SSH as a Client**

* [ ] Connect to a remote server using `ssh user@host`
* [ ] Use custom port with `ssh -p`
* [ ] Transfer files using `scp` and `sftp`
* [ ] Use SSH with verbose/debug mode (`-v`, `-vv`, `-vvv`)

---

### 4. **Configure SSH Server**

* [ ] Locate and edit `/etc/ssh/sshd_config`
* [ ] Configure `Port`, `Protocol`, `PermitRootLogin`, `PasswordAuthentication`, `AllowUsers`
* [ ] Reload the SSH service after changes (`systemctl restart sshd`)
* [ ] Test changes from a remote machine

---

### 5. **Set Up Key-Based Authentication**

* [ ] Generate an SSH key pair using `ssh-keygen`
* [ ] Copy public key to remote server (`ssh-copy-id` or manually)
* [ ] Ensure correct permissions on `~/.ssh` and `authorized_keys`
* [ ] Disable password-based authentication on the server

---

### 6. **Manage SSH Agent and Keys**

* [ ] Use `ssh-agent` and `ssh-add` to manage keys
* [ ] Enable key forwarding with `ForwardAgent`
* [ ] Manage multiple identities using `~/.ssh/config`

---

### 7. **Secure SSH Access**

* [ ] Change the default SSH port (optional, for obfuscation)
* [ ] Disable root login (`PermitRootLogin no`)
* [ ] Limit user logins with `AllowUsers` or `DenyUsers`
* [ ] Set `MaxAuthTries`, `LoginGraceTime`, and `UseDNS` options
* [ ] Set up `Fail2Ban` or similar to block brute-force attempts

---

### 8. **Configure SSH Tunneling**

* [ ] Set up **local port forwarding** (`ssh -L`)
* [ ] Set up **remote port forwarding** (`ssh -R`)
* [ ] Set up **dynamic port forwarding** (`ssh -D`)
* [ ] Test tunneling for secure access to internal services

---

### 9. **Enable X11 Forwarding**

* [ ] Enable `X11Forwarding` in `sshd_config`
* [ ] Connect using `ssh -X` or `-Y`
* [ ] Run GUI applications remotely over SSH
* [ ] Understand security implications of X11 forwarding

---

### 10. **Connection Multiplexing**

* [ ] Configure `ControlMaster`, `ControlPath`, and `ControlPersist` in `~/.ssh/config`
* [ ] Reuse SSH connections to reduce login time
* [ ] Test multiple sessions using a single connection

---

### 11. **Logging and Monitoring**

* [ ] Monitor SSH activity using:

  * `/var/log/auth.log` (Debian/Ubuntu)
  * `/var/log/secure` (RHEL/CentOS)
* [ ] Detect unauthorized login attempts
* [ ] Enable logging levels (`LogLevel` in `sshd_config`)

---

### 12. **Troubleshoot SSH Issues**

* [ ] Use `ssh -v` to debug connection issues
* [ ] Resolve common errors: permission denied, connection refused, key mismatch
* [ ] Fix configuration file errors and reload service
* [ ] Check firewall and SELinux settings

---

### 13. **Use SSH Configuration Files**

* [ ] Customize `~/.ssh/config` for:

  * Host aliases
  * Default usernames
  * Ports and keys
* [ ] Manage multiple connections with different keys

---

### 14. **Set Up SSH Two-Factor Authentication (2FA)**

* [ ] Install and configure `google-authenticator` or `libpam-google-authenticator`
* [ ] Integrate PAM for OTP-based login
* [ ] Test SSH login with password + OTP

---

### 15. **Advanced SSH Use Cases**

* [ ] Set up a **jump host** (`ProxyJump` or `ProxyCommand`)
* [ ] Run remote commands via SSH (`ssh user@host "command"`)
* [ ] Automate SSH commands using scripts
* [ ] Use SSH in cron jobs or scripts with key-based auth

---

## Hands-On Exercises – SSH Management in Linux

---

### 1. **Install and Enable SSH Server**

* Install `openssh-server` on your Linux machine
* Enable and start the `sshd` service using `systemctl`
* Verify that SSH is listening on the default port (22)

---

### 2. **Connect to a Remote System Using SSH**

* Use `ssh user@remote_ip` to initiate a connection
* Try different options:

  * Custom port (`-p`)
  * Verbose mode (`-v`)
  * Execute a remote command (`ssh user@host "uptime"`)

---

### 3. **Configure SSH Server Settings**

* Edit `/etc/ssh/sshd_config` to:

  * Change SSH port
  * Disable root login
  * Disable password authentication (for key-only login)
* Restart SSH and test each change

---

### 4. **Generate and Use SSH Key-Based Authentication**

* Create a key pair with `ssh-keygen`
* Copy the public key to the remote server using `ssh-copy-id`
* Disable password login and verify key-only access

---

### 5. **Set Up and Use `ssh-agent`**

* Add your private key to `ssh-agent` using `ssh-add`
* Use `ssh` without typing the passphrase each time
* Enable agent forwarding and test it on a remote host

---

### 6. **Configure and Use `~/.ssh/config`**

* Create entries to simplify SSH connections:

  ```ini
  Host webserver
      HostName 192.168.1.10
      User admin
      Port 2222
  ```
* Test connecting with `ssh webserver`

---

### 7. **Transfer Files with `scp` and `sftp`**

* Use `scp` to copy files to/from remote systems
* Use `sftp` to navigate and transfer files interactively
* Test downloading/uploading large files and verify permissions

---

### 8. **Set Up SSH Tunneling**

* Create a **local port forwarding** tunnel with `ssh -L`
* Create a **remote port forwarding** tunnel with `ssh -R`
* Use **dynamic port forwarding** with `ssh -D` and configure a SOCKS proxy in your browser

---

### 9. **Enable and Use X11 Forwarding**

* Enable `X11Forwarding` in `sshd_config`
* Connect using `ssh -X` or `ssh -Y`
* Run a graphical application like `xclock` or `gedit` over SSH

---

### 10. **Limit Access Using `AllowUsers` and `DenyUsers`**

* Restrict SSH access to specific users or groups
* Test login attempts with allowed and denied users

---

### 11. **Set Up Two-Factor Authentication for SSH**

* Install and configure Google Authenticator or TOTP
* Enable PAM support in SSH
* Test SSH login with OTP codes

---

### 12. **Monitor SSH Access Logs**

* View logs in `/var/log/auth.log` or `/var/log/secure`
* Identify successful logins and failed attempts
* Use `grep`, `awk`, or `fail2ban` to detect brute-force attempts

---

### 13. **Simulate and Resolve SSH Connection Errors**

* Change permissions on `~/.ssh` or keys to trigger errors
* Try logging in with wrong keys or wrong usernames
* Use `ssh -vvv` to debug and fix the issues

---

### 14. **Use a Jump Host (SSH Bastion)**

* Set up an intermediate server to connect to internal systems
* Configure `ProxyJump` or `ProxyCommand` in SSH config
* Test access via the jump host

---

### 15. **Automate Remote Commands via SSH**

* Write a shell script that logs in and runs commands remotely
* Use `ssh` in a `for` loop to run updates on multiple servers
* Test script execution with key-based auth

---

</details>

<details>
  <summary>NTP</summary>
  
---

## Topics in NTP Management

---

### 1. **Introduction to Time Synchronization**

* Importance of accurate timekeeping in Linux systems
* Overview of time synchronization protocols: NTP vs Chrony vs systemd-timesyncd
* Stratum levels and NTP server hierarchy

---

### 2. **NTP Concepts and Architecture**

* How NTP works (polling, drift, offsets, jitter)
* Understanding NTP server and client roles
* Public NTP pools and private time servers

---

### 3. **Installing NTP Services**

* Installing traditional NTP daemon (`ntpd`)
* Installing Chrony (`chronyd`) – modern alternative
* Installing `systemd-timesyncd` for lightweight setups

---

### 4. **Configuring NTP Client**

* Editing `/etc/ntp.conf` or `/etc/chrony/chrony.conf`
* Adding NTP servers (public or internal)
* Configuring drift files and polling intervals
* Restricting or allowing access to NTP services

---

### 5. **Configuring NTP Server**

* Setting up a Linux machine as an NTP server
* Allowing client access via `restrict` (NTP) or `allow` (Chrony)
* Configuring firewall for NTP (UDP port 123)
* Synchronizing time from an upstream source and serving it to clients

---

### 6. **Using `chrony` (Chronyd)**

* Differences between `ntpd` and `chronyd`
* Basic chrony configuration (`chronyc sources`, `tracking`, `sourcestats`)
* Enabling Chrony as a time server
* Monitoring Chrony with `chronyc` commands

---

### 7. **Using `systemd-timesyncd`**

* Understanding its lightweight nature
* Enabling/disabling with `timedatectl` and `systemctl`
* Configuring `/etc/systemd/timesyncd.conf`
* Verifying synchronization status

---

### 8. **Verifying Time Synchronization**

* Commands:

  * `ntpq -p` (for NTP)
  * `chronyc sources` and `chronyc tracking` (for Chrony)
  * `timedatectl`
* Checking offset, delay, jitter, and stratum
* Monitoring sync status and last successful sync

---

### 9. **Managing the Time and Date**

* Using `timedatectl` to view/set system time and timezone
* Setting hardware clock with `hwclock`
* Syncing system and hardware clocks manually

---

### 10. **Troubleshooting NTP Issues**

* Diagnosing unsynchronized clocks
* Checking firewall and port 123 accessibility
* Verifying config files and log messages
* Resolving stratum and drift issues

---

### 11. **Security and Best Practices**

* Securing NTP servers (restrict commands, interface binding)
* Using internal time servers for enterprise environments
* Avoiding abuse of public NTP servers
* Monitoring and logging NTP activities

---

## ✅ NTP Management – Comprehensive Study Checklist

---

### 1. **Fundamentals of Time Synchronization**

* [ ] Understand why time synchronization is important in Linux systems
* [ ] Learn the difference between system time and hardware clock
* [ ] Understand the role of time sync in logs, authentication, and clusters

---

### 2. **Overview of Time Sync Protocols**

* [ ] Understand NTP (Network Time Protocol) fundamentals
* [ ] Learn the difference between NTP, Chrony, and systemd-timesyncd
* [ ] Know what a stratum level is and how NTP hierarchy works

---

### 3. **Install Time Synchronization Tools**

* [ ] Install `ntpd` on Debian/Ubuntu and RHEL/CentOS
* [ ] Install `chronyd` (recommended for newer systems)
* [ ] Enable `systemd-timesyncd` on systems using `systemd`

---

### 4. **Basic NTP Client Configuration**

* [ ] Edit `/etc/ntp.conf` to add or remove NTP servers
* [ ] Configure the drift file and logging options
* [ ] Test configuration using `ntpq -p`
* [ ] Enable and restart the `ntpd` service

---

### 5. **Basic Chrony Client Configuration**

* [ ] Edit `/etc/chrony/chrony.conf` to specify NTP sources
* [ ] Start and enable the `chronyd` service
* [ ] Verify synchronization using `chronyc sources`, `tracking`
* [ ] Understand chrony's drift and offset metrics

---

### 6. **Configure systemd-timesyncd (lightweight option)**

* [ ] Edit `/etc/systemd/timesyncd.conf` to specify NTP servers
* [ ] Enable and start `systemd-timesyncd`
* [ ] Use `timedatectl` to view time sync status

---

### 7. **Set Up a Linux Machine as an NTP Server**

* [ ] Configure a system to serve time to clients
* [ ] Add local or upstream NTP sources
* [ ] Configure `restrict` (NTP) or `allow` (Chrony) for client access
* [ ] Open UDP port 123 in the firewall

---

### 8. **Verify Time Sync Status**

* [ ] Use `ntpq -p`, `chronyc sources`, and `timedatectl status`
* [ ] Check for offset, delay, and jitter
* [ ] Use `watch` or `grep` to monitor logs in `/var/log/`

---

### 9. **Manage System Time and Hardware Clock**

* [ ] View and change system time using `timedatectl`
* [ ] Set or sync the hardware clock with `hwclock`
* [ ] Sync system time with hardware clock and vice versa

---

### 10. **Troubleshoot Time Sync Issues**

* [ ] Diagnose why time is not syncing properly
* [ ] Check service status: `systemctl status ntpd`, `chronyd`, or `timesyncd`
* [ ] Inspect log files for errors (`/var/log/syslog`, `/var/log/messages`)
* [ ] Verify access to remote time servers
* [ ] Check for firewall blocking UDP port 123

---

### 11. **Security Best Practices**

* [ ] Restrict NTP access to specific networks or clients
* [ ] Disable control queries if not needed
* [ ] Use internal time servers for enterprise environments
* [ ] Avoid overloading public NTP pools with unnecessary queries

---

### 12. **Advanced NTP Topics (Optional)**

* [ ] Configure NTP authentication with symmetric keys
* [ ] Monitor NTP performance with `ntpstat` and `ntpq`
* [ ] Understand leap seconds and how NTP handles them

---

## Hands-On Exercises – NTP Management in Linux

---

### 1. **Install NTP Tools**

* Install the NTP daemon:

  * `sudo apt install ntp` (Debian/Ubuntu)
  * `sudo dnf install ntp` (RHEL/CentOS)
* Install Chrony:

  * `sudo apt install chrony` or `sudo dnf install chrony`
* Enable and start the services:

  * `systemctl enable --now ntpd` or `chronyd`

---

### 2. **Configure an NTP Client**

* Edit the NTP configuration file (`/etc/ntp.conf` or `/etc/chrony/chrony.conf`)
* Add NTP pool servers or internal NTP servers
* Restart the service and verify synchronization

---

### 3. **Verify Time Synchronization**

* Use `ntpq -p` to view NTP peers (for NTP daemon)
* Use `chronyc tracking` and `chronyc sources` (for Chrony)
* Use `timedatectl status` (for systemd-timesyncd)
* Observe offset, delay, jitter, and stratum

---

### 4. **Configure Time Server on Linux**

* Set up a machine to act as an NTP or Chrony server
* Add `restrict` or `allow` directives to permit specific clients
* Open port `123/UDP` in the firewall
* Sync clients to this local server and test connectivity

---

### 5. **Set the Time Manually**

* Set the system time manually using `timedatectl set-time`
* Set the hardware clock using `hwclock --set --date`
* Sync the system clock to the hardware clock and vice versa

---

### 6. **Configure `systemd-timesyncd`**

* Enable the service: `systemctl enable --now systemd-timesyncd`
* Edit `/etc/systemd/timesyncd.conf` to add NTP servers
* Use `timedatectl` to view and verify sync status

---

### 7. **Test NTP with Local Clock (Fallback)**

* Enable the local hardware clock as a fallback in `/etc/ntp.conf`
* Simulate upstream failure and test fallback behavior
* Monitor logs for failover events

---

### 8. **Test Drift File Accuracy**

* Locate and review the NTP drift file (usually `/var/lib/ntp/ntp.drift`)
* Observe how it updates over time
* Force a time change and watch how drift compensates

---

### 9. **Simulate a Time Desync and Re-Sync**

* Set the system time manually to a wrong value
* Restart the NTP service and observe how the system re-synchronizes
* Check logs and sync status during correction

---

### 10. **Monitor and Log NTP Activity**

* View `/var/log/syslog` or `/var/log/messages` for NTP logs
* Use `journalctl -u ntp` or `-u chronyd` for systemd logs
* Track time sync success/failure

---

### 11. **Secure NTP Server**

* Restrict access using `restrict` (NTP) or `allow` (Chrony)
* Disable unnecessary control commands
* Test access from unauthorized IPs and observe rejections

---

### 12. **Troubleshoot Time Sync Issues**

* Diagnose problems when time is not syncing:

  * Use `ntpq -pn`, `chronyc sources`, or `timedatectl`
  * Check for port 123 being blocked
  * Analyze logs for errors or misconfiguration

---

</details>

<details>
  <summary>SSL</summary>

---

## Topics in SSL/TLS Management 

---

### 1. **Introduction to SSL/TLS**

* What is SSL/TLS?
* Differences between SSL and TLS
* Why SSL/TLS is important in Linux environments
* How SSL works: certificates, keys, and the handshake process

---

### 2. **Understanding Digital Certificates**

* Components of an SSL certificate: CN, SAN, validity, issuer
* Types of certificates:

  * Self-signed certificates
  * CA-signed certificates
  * Wildcard and SAN certificates
* Certificate file formats: `.crt`, `.pem`, `.cer`, `.key`, `.p12`, `.csr`

---

### 3. **Generating SSL Certificates**

* Creating private keys and Certificate Signing Requests (CSRs) using OpenSSL
* Generating self-signed certificates
* Creating SAN certificates
* Setting certificate validity and extensions

---

### 4. **Working with Certificate Authorities (CAs)**

* Submitting a CSR to a public CA (Let’s Encrypt, DigiCert, etc.)
* Installing a CA-signed certificate
* Using internal/private CA for enterprise environments

---

### 5. **OpenSSL Basics and Usage**

* OpenSSL commands for:

  * Generating keys and CSRs
  * Converting between certificate formats
  * Viewing certificate details
  * Validating certificate chains
* Creating test certificates for internal services

---

### 6. **Deploying SSL Certificates in Common Services**

* **Apache HTTP Server**:

  * Enabling HTTPS with `SSLEngine` and `SSLCertificateFile`
  * Configuring virtual hosts for SSL
* **Nginx**:

  * Configuring SSL/TLS blocks in `server` sections
  * Using strong ciphers and disabling weak protocols
* **Postfix/Dovecot**, **MySQL/MariaDB**, **FTP**, etc.:

  * Configuring SSL in various services

---

### 7. **Let's Encrypt and Certbot**

* Installing and using Certbot to obtain free certificates
* Automating certificate renewal with systemd timers or cron
* Using DNS or HTTP challenge for validation
* Troubleshooting common Certbot errors

---

### 8. **SSL Configuration Best Practices**

* Enforcing HTTPS redirection
* Using modern ciphers and disabling SSLv2/SSLv3/TLSv1.0
* Configuring HSTS (HTTP Strict Transport Security)
* Setting up Diffie-Hellman parameters
* Testing with SSL Labs and `testssl.sh`

---

### 9. **Certificate Management**

* Renewing SSL certificates manually or automatically
* Replacing expired or compromised certificates
* Managing multiple certificates for multi-domain or wildcard use
* Certificate chain management (intermediate and root certs)

---

### 10. **SSL Verification and Debugging**

* Testing SSL connections with:

  * `openssl s_client`
  * `curl -v https://yourdomain.com`
  * `ssllabs.com` or `testssl.sh`
* Verifying certificate chain and expiry dates
* Diagnosing handshake failures or mismatched keys

---

### 11. **Security and Compliance**

* PCI-DSS, HIPAA, and other compliance requirements
* Logging and monitoring SSL traffic
* Handling revoked or compromised certificates (CRL/OCSP)
* Ensuring forward secrecy and perfect forward secrecy (PFS)

---

## Topics in Let’s Encrypt SSL 

---

### 12. **Introduction to Let’s Encrypt**

* What is Let’s Encrypt and how it works
* Benefits of using Let’s Encrypt (free, automated, trusted CA)
* Understanding ACME protocol (Automatic Certificate Management Environment)

---

### 13. **Prerequisites for Using Let’s Encrypt**

* Domain ownership and DNS configuration
* Web server (Apache, Nginx) configuration basics
* Firewall and port 80/443 accessibility

---

### 14. **Installing Certbot (Let’s Encrypt Client)**

* Installing Certbot on different Linux distros (Debian, Ubuntu, RHEL, CentOS, Fedora)
* Certbot plugins for Apache, Nginx, and standalone mode
* Updating Certbot and managing dependencies

---

### 15. **Obtaining SSL Certificates**

* Using Certbot to request a certificate:

  * Webroot method
  * Standalone method
  * Apache and Nginx plugins (automatic configuration)
* Understanding HTTP-01 and DNS-01 challenges
* Specifying domains and SAN (Subject Alternative Names)

---

### 16. **Automatic Certificate Renewal**

* How Let’s Encrypt certificates expire every 90 days
* Configuring automatic renewal using:

  * Cron jobs
  * systemd timers
* Testing renewal process with `certbot renew --dry-run`

---

### 17. **Configuring Web Servers with Let’s Encrypt Certificates**

* Integrating certificates into Apache:

  * Using Certbot’s Apache plugin to automate config
  * Manual configuration of SSL virtual hosts
* Integrating certificates into Nginx:

  * Using Certbot’s Nginx plugin
  * Manual configuration of SSL blocks

---

### 18. **Managing Certificates**

* Viewing certificate details with `certbot certificates`
* Revoking certificates with Certbot
* Deleting certificates and cleaning up old configs

---

### 19. **Handling Multiple Domains and Wildcards**

* Issuing certificates for multiple domains and subdomains
* Using DNS-01 challenge for wildcard certificates
* Configuring DNS provider API access for automation

---

### 20. **Troubleshooting Common Issues**

* Challenges failing due to port or firewall restrictions
* DNS validation problems
* Rate limits imposed by Let’s Encrypt
* Debugging Certbot logs and error messages

---

### 21. **Security Best Practices**

* Enforcing HTTPS and HSTS
* Configuring strong TLS versions and ciphers
* Keeping Certbot and server software updated
* Backing up certificates and keys securely

---

## SSL/TLS Comprehensive Study Checklist

---

### 1. **Fundamentals of SSL/TLS**

* [ ] Understand what SSL and TLS protocols are
* [ ] Know the differences between SSL and TLS versions
* [ ] Learn the purpose of SSL/TLS (encryption, authentication, data integrity)
* [ ] Understand the SSL/TLS handshake and key exchange process
* [ ] Know key SSL/TLS components: certificates, private keys, Certificate Authorities (CAs)

---

### 2. **Digital Certificates**

* [ ] Understand certificate structure (Subject, Issuer, Validity, Public Key)
* [ ] Differentiate certificate types:

  * Self-signed certificates
  * CA-signed certificates
  * Wildcard certificates
  * SAN (Subject Alternative Name) certificates
* [ ] Learn about certificate formats: PEM, DER, CRT, CER, KEY, PFX/P12

---

### 3. **Generating SSL Certificates**

* [ ] Generate private keys using OpenSSL
* [ ] Create Certificate Signing Requests (CSRs)
* [ ] Generate self-signed certificates for testing
* [ ] Understand certificate extensions and attributes

---

### 4. **Managing Certificates**

* [ ] Submit CSR to a public CA
* [ ] Install CA-signed certificates on servers
* [ ] Manage certificate renewal and replacement
* [ ] Understand certificate chain and intermediate certificates
* [ ] Securely store private keys and certificate files

---

### 5. **Configuring SSL in Linux Services**

* [ ] Configure SSL for Apache HTTP Server
* [ ] Configure SSL for Nginx Web Server
* [ ] Enable SSL in other services (FTP, SMTP, IMAP, MySQL)
* [ ] Redirect HTTP traffic to HTTPS (301 redirects)

---

### 6. **OpenSSL Tools and Usage**

* [ ] Use OpenSSL commands to generate keys, CSRs, and certificates
* [ ] Convert between certificate formats (PEM to DER, PFX, etc.)
* [ ] Inspect certificate details (`openssl x509 -in cert.pem -text -noout`)
* [ ] Verify certificate chains and validity
* [ ] Test SSL/TLS connections with `openssl s_client`

---

### 7. **Security Best Practices**

* [ ] Disable deprecated protocols (SSLv2, SSLv3, TLS 1.0, TLS 1.1)
* [ ] Use strong and modern cipher suites
* [ ] Implement Perfect Forward Secrecy (PFS)
* [ ] Configure HTTP Strict Transport Security (HSTS)
* [ ] Generate strong Diffie-Hellman parameters for key exchange
* [ ] Use security scanning tools like SSL Labs and testssl.sh

---

### 8. **Troubleshooting SSL Issues**

* [ ] Diagnose certificate errors (expired, mismatched CN, untrusted CA)
* [ ] Debug handshake failures and protocol errors
* [ ] Check and fix certificate chain issues
* [ ] Monitor SSL logs and error messages in web servers

---

### 9. **Compliance and Monitoring**

* [ ] Understand SSL requirements for compliance standards (PCI-DSS, HIPAA)
* [ ] Monitor SSL certificate expiration and renew proactively
* [ ] Audit SSL configurations regularly for security vulnerabilities

---

## Let’s Encrypt Comprehensive Study Checklist

---

### 1. **Introduction to Let’s Encrypt**

* [ ] Understand what Let’s Encrypt is and its benefits (free, automated, trusted CA)
* [ ] Learn about the ACME protocol and how it automates certificate issuance
* [ ] Know the types of challenges: HTTP-01, DNS-01, TLS-ALPN-01

---

### 2. **Prerequisites for Let’s Encrypt**

* [ ] Ensure domain ownership and DNS records are correctly set
* [ ] Verify web server is installed and accessible (Apache, Nginx, etc.)
* [ ] Confirm that ports 80 (HTTP) and 443 (HTTPS) are open and reachable

---

### 3. **Installing Certbot**

* [ ] Install Certbot on popular Linux distributions (Ubuntu, Debian, CentOS, RHEL, Fedora)
* [ ] Understand Certbot plugins: Apache, Nginx, standalone, webroot

---

### 4. **Obtaining SSL Certificates**

* [ ] Use Certbot to request certificates with:

  * Webroot method
  * Standalone method
  * Apache and Nginx plugins (auto-configure)
* [ ] Obtain certificates for multiple domains and SANs
* [ ] Request wildcard certificates using DNS-01 challenge

---

### 5. **Configuring Web Servers with Let’s Encrypt Certificates**

* [ ] Automate SSL configuration with Certbot Apache plugin
* [ ] Automate SSL configuration with Certbot Nginx plugin
* [ ] Manually configure SSL certificates in web server config files
* [ ] Test HTTPS access and verify certificate deployment

---

### 6. **Automatic Renewal of Certificates**

* [ ] Understand Let’s Encrypt’s 90-day certificate validity
* [ ] Configure automatic certificate renewal with:

  * Cron jobs
  * systemd timers
* [ ] Test renewal process with `certbot renew --dry-run`

---

### 7. **Managing Certificates**

* [ ] List current certificates with `certbot certificates`
* [ ] Revoke certificates when necessary
* [ ] Delete unused or expired certificates
* [ ] Backup certificates and private keys securely

---

### 8. **Advanced Topics**

* [ ] Use DNS provider APIs for automated DNS-01 challenge (wildcards)
* [ ] Handle Let’s Encrypt rate limits and best practices to avoid them
* [ ] Integrate Let’s Encrypt certificates with other services (mail servers, proxies)

---

### 9. **Troubleshooting Let’s Encrypt Issues**

* [ ] Diagnose common errors related to HTTP-01 and DNS-01 challenges
* [ ] Fix firewall or port blocking problems
* [ ] Resolve DNS misconfiguration issues
* [ ] Interpret Certbot logs for debugging

---

### 10. **Security Best Practices**

* [ ] Enforce HTTPS and HTTP to HTTPS redirection
* [ ] Configure strong TLS versions and cipher suites
* [ ] Enable HSTS (HTTP Strict Transport Security)
* [ ] Keep Certbot and server software updated

---

## Hands-on Exercises in SSL Management

---

1. **Generate a Private Key and CSR**

   * Use `openssl` to generate a 2048-bit RSA private key
   * Create a Certificate Signing Request (CSR) with proper domain details

2. **Create a Self-Signed Certificate**

   * Generate a self-signed SSL certificate valid for 365 days using OpenSSL
   * Inspect the certificate details

3. **Install SSL Certificate on Apache Web Server**

   * Configure Apache to use your SSL certificate and private key
   * Enable SSL module and set up a secure virtual host for HTTPS
   * Restart Apache and verify HTTPS access

4. **Install SSL Certificate on Nginx Web Server**

   * Configure Nginx to use SSL certificate and private key
   * Set up SSL parameters (protocols, ciphers) in the config
   * Reload Nginx and verify HTTPS connectivity

5. **Convert Certificate Formats**

   * Convert PEM to DER, PFX, or PKCS#12 formats using OpenSSL
   * Understand when each format is used

6. **Verify SSL Certificate Chain**

   * Use `openssl s_client` to verify server certificate chain and expiration
   * Troubleshoot chain errors

7. **Enable HTTP to HTTPS Redirection**

   * Configure Apache or Nginx to redirect all HTTP traffic to HTTPS
   * Test the redirection in the browser

8. **Configure Strong SSL Security Settings**

   * Disable SSLv2, SSLv3, and TLS 1.0, 1.1 protocols
   * Enable only TLS 1.2 and above
   * Configure strong cipher suites and Perfect Forward Secrecy (PFS)

9. **Generate and Configure Diffie-Hellman Parameters**

   * Generate a DH parameters file with OpenSSL
   * Configure Apache or Nginx to use the DH params

10. **Check SSL Certificate Expiry and Renew**

    * Use `openssl` or tools to check expiry dates of certificates
    * Practice renewing certificates and replacing old ones

11. **Test SSL Configuration with Online Tools**

    * Use SSL Labs server test or `testssl.sh` to scan your server
    * Analyze results and improve configuration

12. **Debug SSL/TLS Issues**

    * Use `openssl s_client` to simulate SSL connections and debug handshake failures
    * Review Apache/Nginx logs for SSL errors

---

## Hands-on Exercises for Let’s Encrypt

---

1. **Install Certbot on Your Linux Distribution**

   * Install Certbot using your distro’s package manager (apt, yum, dnf, etc.)
   * Verify Certbot installation

2. **Obtain a Let’s Encrypt SSL Certificate Using the Webroot Plugin**

   * Set up a basic website with a document root
   * Use Certbot with the webroot plugin to request a certificate for your domain
   * Verify the certificate files generated

3. **Obtain a Certificate Using the Standalone Plugin**

   * Stop your web server temporarily
   * Use Certbot standalone mode to obtain a certificate
   * Restart your web server and verify SSL

4. **Automatically Configure Apache with Certbot**

   * Use Certbot’s Apache plugin to request and install a certificate
   * Verify Apache SSL virtual host configuration and HTTPS access

5. **Automatically Configure Nginx with Certbot**

   * Use Certbot’s Nginx plugin to request and install a certificate
   * Check Nginx SSL settings and test HTTPS connectivity

6. **Obtain a Wildcard Certificate Using DNS-01 Challenge**

   * Configure your DNS provider’s API or manual TXT record
   * Request a wildcard certificate (`*.yourdomain.com`) using Certbot with DNS challenge
   * Verify the wildcard certificate installation

7. **Set Up Automatic Certificate Renewal**

   * Configure a cron job or systemd timer for `certbot renew`
   * Test renewal with `certbot renew --dry-run`
   * Monitor logs to confirm renewal success

8. **Manually Renew a Let’s Encrypt Certificate**

   * Perform manual renewal of an existing certificate using Certbot
   * Replace certificates in the web server configuration if needed

9. **Revoke a Let’s Encrypt Certificate**

   * Use Certbot to revoke a certificate
   * Confirm the certificate is no longer valid

10. **Backup and Restore Let’s Encrypt Certificates and Keys**

    * Locate and back up `/etc/letsencrypt` directory
    * Restore certificates and reconfigure your server after backup

11. **Troubleshoot Common Let’s Encrypt Errors**

    * Simulate challenge failures (e.g., block port 80, misconfigure DNS)
    * Diagnose errors using Certbot logs and fix issues

12. **Force HTTPS Redirect After Installing Let’s Encrypt Certificate**

    * Configure Apache or Nginx to redirect all HTTP traffic to HTTPS
    * Test redirection from HTTP to HTTPS in a browser

---

</details>

<details>
  <summary>LDAP</summary>

---

## Topics in LDAP Management

1. **Introduction to LDAP**

   * What is LDAP (Lightweight Directory Access Protocol)
   * LDAP architecture and components (servers, clients, directories)
   * Common LDAP use cases

2. **LDAP Server Installation and Configuration**

   * Installing OpenLDAP server on Linux
   * Understanding LDAP directory structure (DN, RDN, entries)
   * Configuring `slapd` (LDAP daemon)
   * Managing LDAP schemas

3. **LDAP Data Management**

   * Adding, modifying, and deleting LDAP entries
   * Using LDIF (LDAP Data Interchange Format) files
   * Importing and exporting LDAP data
   * Understanding object classes and attributes

4. **LDAP Authentication and Access Control**

   * Configuring LDAP authentication for Linux users
   * Setting up PAM and NSS with LDAP
   * Managing Access Control Lists (ACLs) in LDAP
   * Implementing secure LDAP (LDAPS and StartTLS)

5. **LDAP Client Configuration**

   * Installing and configuring LDAP client tools (`ldapsearch`, `ldapmodify`)
   * Configuring `nslcd` or `sssd` for system authentication
   * Testing LDAP client-server connectivity

6. **LDAP Replication and Backup**

   * Configuring LDAP replication (master-slave, multi-master)
   * Performing LDAP backups and restores
   * Monitoring LDAP server health and logs

7. **Advanced LDAP Topics**

   * Implementing password policies and account locking
   * Using LDAP overlays and modules
   * Integrating LDAP with other services (Kerberos, Samba)
   * LDAP troubleshooting and performance tuning

---

##  LDAP Management Comprehensive Study Checklist

---

### 1. **Understanding LDAP Basics**

* [ ] Learn what LDAP is and its primary purpose
* [ ] Understand LDAP directory structure: DN, RDN, entries, attributes
* [ ] Know LDAP data model: object classes, schemas, and attributes
* [ ] Understand LDAP operations: bind, search, modify, add, delete

---

### 2. **Installing and Configuring LDAP Server**

* [ ] Install OpenLDAP server (`slapd`) on your Linux distribution
* [ ] Understand and configure LDAP directory information tree (DIT)
* [ ] Configure LDAP schemas and extend them if necessary
* [ ] Set up slapd configuration files (`slapd.conf` or cn=config backend)

---

### 3. **Managing LDAP Data**

* [ ] Add, modify, delete LDAP entries using LDAP tools (`ldapadd`, `ldapmodify`)
* [ ] Create and apply LDIF files for batch operations
* [ ] Import/export LDAP data effectively
* [ ] Manage users, groups, and organizational units (OUs) in LDAP

---

### 4. **LDAP Authentication and Integration**

* [ ] Configure Linux PAM (Pluggable Authentication Modules) to use LDAP for authentication
* [ ] Configure NSS (Name Service Switch) for LDAP-based user/group information
* [ ] Secure LDAP connections using SSL/TLS (LDAPS and StartTLS)
* [ ] Configure LDAP client utilities (`ldapsearch`, `ldapwhoami`)

---

### 5. **Access Control and Security**

* [ ] Implement LDAP Access Control Lists (ACLs) for fine-grained permissions
* [ ] Manage user and group access policies
* [ ] Set password policies and account lockout mechanisms
* [ ] Secure LDAP server with firewalls and encryption

---

### 6. **LDAP Replication and High Availability**

* [ ] Understand LDAP replication types: master-slave, multi-master
* [ ] Configure replication between LDAP servers
* [ ] Monitor replication status and troubleshoot synchronization issues

---

### 7. **Backup and Recovery**

* [ ] Plan and execute regular LDAP backups
* [ ] Restore LDAP data from backups
* [ ] Use tools like `slapcat` and `slapadd` for data export/import

---

### 8. **Advanced LDAP Features**

* [ ] Use overlays and modules to extend LDAP functionality
* [ ] Configure referral and chaining in LDAP
* [ ] Integrate LDAP with Kerberos for Single Sign-On (SSO)
* [ ] Integrate LDAP with Samba for Windows interoperability

---

### 9. **Monitoring and Troubleshooting**

* [ ] Monitor LDAP server logs and performance metrics
* [ ] Diagnose connection and authentication failures
* [ ] Use tools like `ldapsearch` for testing queries
* [ ] Tune LDAP server performance and cache settings

---

### 10. **Compliance and Best Practices**

* [ ] Understand compliance requirements affecting LDAP (e.g., GDPR, HIPAA)
* [ ] Apply best security practices for directory services
* [ ] Document LDAP configurations and policies

---

## Hands-on Exercises in LDAP Management

---

1. **Install OpenLDAP Server**

   * Install `slapd` and related packages on your Linux system
   * Verify that the LDAP service is running

2. **Configure Basic LDAP Directory Structure**

   * Set up your LDAP directory base DN (e.g., `dc=example,dc=com`)
   * Define organizational units (OUs) such as `Users`, `Groups`, `Departments`

3. **Add LDAP Entries Using LDIF Files**

   * Create LDIF files to add users, groups, and OUs
   * Use `ldapadd` to import LDIF data into the directory
   * Verify entries using `ldapsearch`

4. **Modify LDAP Entries**

   * Use `ldapmodify` to update attributes of existing LDAP entries
   * Change user details like email, phone, or group membership

5. **Delete LDAP Entries**

   * Use `ldapdelete` or `ldapmodify` to remove users or groups from LDAP

6. **Set Up LDAP Authentication on a Linux Client**

   * Configure PAM and NSS to authenticate users against LDAP
   * Test user login using LDAP credentials

7. **Enable and Configure Secure LDAP (LDAPS)**

   * Generate or install SSL/TLS certificates for LDAP
   * Configure `slapd` to support LDAPS on port 636
   * Test secure connections using `ldapsearch -ZZ` or `ldapsearch -H ldaps://`

8. **Implement Access Control Lists (ACLs)**

   * Configure ACLs to restrict read/write access based on user roles
   * Test access restrictions for different LDAP clients/users

9. **Configure LDAP Replication**

   * Set up master-slave replication between two LDAP servers
   * Verify data synchronization across servers

10. **Backup and Restore LDAP Data**

    * Export LDAP directory data using `slapcat`
    * Restore data using `slapadd` after stopping the LDAP server

11. **Manage Password Policies**

    * Create and apply password policy overlays
    * Enforce password complexity, expiration, and lockout policies

12. **Integrate LDAP with Samba for File Sharing**

    * Configure Samba to use LDAP for user and group authentication
    * Test access control on shared directories using LDAP credentials

13. **Monitor LDAP Server Logs and Performance**

    * Locate and analyze LDAP logs (`/var/log/ldap/`, `/var/log/syslog`)
    * Use monitoring tools to check LDAP server health

14. **Troubleshoot LDAP Issues**

    * Diagnose common errors like bind failures, access denied, schema conflicts
    * Use verbose logging and debugging tools

---

</details>


<details>
  <summary>Kerberos</summary>

---

## Topics in Kerberos

---

### 1. **Introduction to Kerberos**

* Overview of Kerberos authentication protocol
* Components of Kerberos: KDC, TGT, service tickets
* Key terms: realm, principals, keytabs, tickets

---

### 2. **Kerberos Architecture and Workflow**

* How Kerberos authentication works
* Ticket Granting Ticket (TGT) and Service Ticket (TGS)
* Understanding mutual authentication
* Role of time synchronization in Kerberos

---

### 3. **Installing Kerberos**

* Installing Kerberos server (`krb5-kdc`, `krb5-admin-server`)
* Installing Kerberos client (`krb5-user`, `libkrb5`)
* Required configuration files: `krb5.conf`, `kdc.conf`, and `kadm5.acl`

---

### 4. **Kerberos Realm Configuration**

* Setting up a new Kerberos realm
* Defining default realms and domain-to-realm mappings
* Creating and configuring the Kerberos database
* Initializing the KDC

---

### 5. **User and Service Principal Management**

* Creating and managing user principals using `kadmin`
* Creating service principals for applications (e.g., HTTP, SSH)
* Using `ktadd` to generate and export keytab files
* Listing, deleting, and modifying principals

---

### 6. **Keytab File Management**

* Understanding keytab file purpose and format
* Creating keytabs for automated service authentication
* Securely storing and using keytab files

---

### 7. **Kerberos Client Configuration**

* Configuring Linux systems as Kerberos clients
* Authenticating users via Kerberos using `kinit`, `klist`, `kdestroy`
* Testing Kerberos login and ticket issuance

---

### 8. **Integrating Kerberos with Linux Services**

* Integrating Kerberos authentication with:

  * SSH
  * Apache HTTPD
  * NFSv4 with Kerberos
  * LDAP and PAM
* Configuring GSSAPI and SPNEGO for single sign-on (SSO)

---

### 9. **Time Synchronization and DNS Requirements**

* Configuring NTP for Kerberos time sensitivity
* Proper DNS setup for reverse and forward lookups
* Using FQDNs for host and service principal names

---

### 10. **Securing Kerberos Infrastructure**

* Using strong encryption types and disabling weak ones
* Restricting administrative access (`kadm5.acl`)
* Backing up the Kerberos database securely

---

### 11. **Kerberos Ticket Management**

* Understanding ticket lifetime and renewal policies
* Modifying default ticket and renewal durations
* Using `klist` to inspect ticket caches

---

### 12. **Troubleshooting Kerberos**

* Analyzing logs: `/var/log/krb5kdc.log`, `/var/log/auth.log`
* Common errors: clock skew, ticket expired, service not found
* Debugging with verbose `kinit`, `klist`, `kvno`, etc.
* Validating principal and keytab issues

---

## **Kerberos Management – Comprehensive Study Checklist**

---

### 1. **Kerberos Fundamentals**

* [ ] Understand what Kerberos is and why it's used
* [ ] Learn the key Kerberos components: KDC, TGS, TGT, principal, realm, keytab
* [ ] Study the Kerberos authentication flow
* [ ] Understand the importance of synchronized time in Kerberos

---

### 2. **Install and Configure Kerberos Server**

* [ ] Install `krb5-kdc` and `krb5-admin-server`
* [ ] Configure `/etc/krb5.conf`, `/etc/krb5kdc/kdc.conf`, and `kadm5.acl`
* [ ] Initialize the Kerberos database with `kdb5_util`
* [ ] Start and enable the KDC and admin services

---

### 3. **Configure a Kerberos Realm**

* [ ] Define a realm and domain-to-realm mappings in `krb5.conf`
* [ ] Set up a fully qualified domain name (FQDN) for the server
* [ ] Configure proper reverse and forward DNS resolution
* [ ] Ensure NTP (time synchronization) is enabled and working

---

### 4. **Create and Manage Principals**

* [ ] Use `kadmin.local` or `kadmin` to create user and host principals
* [ ] Understand principal naming conventions (e.g., `user@REALM`, `host/server.domain@REALM`)
* [ ] Modify or delete principals as needed
* [ ] Set and manage principal passwords and policies

---

### 5. **Generate and Use Keytab Files**

* [ ] Create keytab files for service principals using `ktadd`
* [ ] Securely store and manage keytab files
* [ ] Use `ktutil` for editing keytabs manually
* [ ] Use `klist -k` to verify keytab contents

---

### 6. **Configure Kerberos Clients**

* [ ] Install Kerberos client tools (`krb5-user`, `libkrb5`)
* [ ] Configure `/etc/krb5.conf` on client systems
* [ ] Authenticate using `kinit`, verify tickets with `klist`
* [ ] Use `kdestroy` to clear tickets

---

### 7. **Integrate Kerberos with Linux Services**

* [ ] Configure SSH to support GSSAPI-based Kerberos authentication
* [ ] Integrate Apache HTTPD or Nginx with Kerberos (via `mod_auth_kerb`)
* [ ] Set up NFSv4 with Kerberos security (`sec=krb5`, `krb5p`)
* [ ] Configure PAM and NSS for system-wide Kerberos login
* [ ] Integrate Kerberos with LDAP (e.g., FreeIPA or 389 Directory Server)

---

### 8. **Security and Policies**

* [ ] Enforce strong encryption types (AES over DES/RC4)
* [ ] Set ticket lifetime and renewal policies
* [ ] Restrict administrative access via `kadm5.acl`
* [ ] Enable logging and auditing for security events

---

### 9. **Backup and Disaster Recovery**

* [ ] Backup the Kerberos database regularly (`kdb5_util dump`)
* [ ] Securely store backup keytab and configuration files
* [ ] Test restore using `kdb5_util load`

---

### 10. **Monitoring and Troubleshooting**

* [ ] Monitor logs: `/var/log/krb5kdc.log`, `/var/log/auth.log`, `/var/log/secure`
* [ ] Troubleshoot common issues: clock skew, principal not found, expired tickets
* [ ] Use debugging flags with `kinit`, `klist`, `kvno`, and `kadmin`
* [ ] Use `tcpdump` or `Wireshark` to inspect Kerberos traffic if needed

---

## Hands-On Exercises in Kerberos 

---

### 1. **Install and Set Up a Kerberos Server (KDC)**

* Install the required Kerberos packages (`krb5-kdc`, `krb5-admin-server`)
* Configure `/etc/krb5.conf`, `/etc/krb5kdc/kdc.conf`, and `/etc/krb5kdc/kadm5.acl`
* Initialize the Kerberos database using `kdb5_util`
* Start and enable the KDC and Kerberos admin server services

---

### 2. **Create a Kerberos Realm**

* Define a new Kerberos realm (e.g., `EXAMPLE.COM`)
* Set up domain-to-realm mapping in `/etc/krb5.conf`
* Verify hostname and DNS settings match your Kerberos realm requirements

---

### 3. **Create User and Host Principals**

* Use `kadmin.local` or `kadmin` to:

  * Create user principals (e.g., `user1@EXAMPLE.COM`)
  * Create host principals (e.g., `host/server.example.com@EXAMPLE.COM`)
* Set passwords and test `kinit` for ticket acquisition

---

### 4. **Generate and Use Keytab Files**

* Generate a keytab file for a host or service using `ktadd`
* Use `klist -k` to verify the contents of the keytab
* Authenticate a service using the keytab instead of password

---

### 5. **Set Up a Kerberos Client**

* Install Kerberos client tools (`krb5-user`, `libkrb5`)
* Configure `/etc/krb5.conf` on the client
* Test authentication with `kinit`, check tickets with `klist`, clear with `kdestroy`

---

### 6. **Configure SSH with Kerberos (GSSAPI)**

* Enable `GSSAPIAuthentication yes` in `sshd_config`
* Ensure the host principal and keytab are present on the server
* Test SSH login using Kerberos authentication from a client

---

### 7. **Configure Kerberos Authentication for Linux Login**

* Set up PAM to authenticate Linux users using Kerberos
* Use `authconfig`, `pam_krb5`, or `sssd` for integration
* Test login from a local terminal or remote SSH session

---

### 8. **Secure Kerberos with TLS/Strong Encryption**

* Configure supported encryption types in `kdc.conf` and `krb5.conf`
* Remove deprecated types (like DES, RC4)
* Restart services and validate encryption during ticket requests

---

### 9. **Set Ticket Lifetime and Policies**

* Set default ticket and renewal lifetimes
* Create a password policy in `kadmin` and apply it to a user principal
* Test password expiration and account lockout

---

### 10. **Backup and Restore the Kerberos Database**

* Backup the KDC database using `kdb5_util dump`
* Stop the KDC, wipe the database, and restore using `kdb5_util load`
* Restart and verify data integrity

---

### 11. **Monitor and Troubleshoot Kerberos**

* Check Kerberos logs (`/var/log/krb5kdc.log`, `/var/log/auth.log`)
* Simulate common issues: wrong time, incorrect realm, missing keytab
* Use verbose output with `kinit`, `kvno`, `klist`, `kadmin` for debugging

---

### 12. **Integrate Kerberos with NFS or Apache**

* Configure NFSv4 with `sec=krb5` or `krb5p` for secure shares
* Configure Apache HTTP server with Kerberos (using `mod_auth_kerb` or `mod_auth_gssapi`)
* Test Kerberos SSO access to web or file services

---

</details>

<details>
  <summary>PAM</summary>
  
---

## Topics in PAM (Pluggable Authentication Modules)

---

### 1. **Introduction to PAM**

* What is PAM and why it is used
* PAM architecture and role in Linux authentication
* PAM-enabled services and applications

---

### 2. **PAM Configuration Files and Structure**

* `/etc/pam.d/` directory and individual service files
* The structure of PAM configuration lines: module-type, control-flag, module-path, arguments
* Reading and understanding `/etc/pam.d/common-auth`, `common-account`, `common-password`, `common-session` (Debian-based systems)

---

### 3. **PAM Module Types**

* `auth` – Authentication of users
* `account` – Authorization and account validity
* `password` – Password updating and checking
* `session` – Session setup and cleanup

---

### 4. **PAM Control Flags**

* `required`
* `requisite`
* `sufficient`
* `optional`
* The meaning and effects of each control flag in decision making

---

### 5. **Commonly Used PAM Modules**

* `pam_unix.so` – Standard UNIX authentication
* `pam_env.so` – Set user environment variables
* `pam_tally2.so` / `pam_faillock.so` – Account lockout policies
* `pam_securetty.so` – Restrict root login to secure terminals
* `pam_limits.so` – Enforce resource limits
* `pam_listfile.so` – Allow or deny access based on a list
* `pam_exec.so` – Execute custom scripts
* `pam_ldap.so` / `pam_sss.so` – LDAP or SSSD integration
* `pam_mkhomedir.so` – Automatically create home directories
* `pam_shells.so` – Validate login shells

---

### 6. **PAM Authentication Flow**

* How PAM processes module stacks
* Interaction of control flags and return codes
* Stack evaluation and decision flow

---

### 7. **Configuring and Testing PAM for Services**

* Modifying PAM policies for `sshd`, `login`, `sudo`, `su`, `passwd`, etc.
* Enabling/disabling modules for specific services
* Testing PAM authentication and access behavior

---

### 8. **Security Policies with PAM**

* Enforcing strong password policies with `pam_cracklib` or `pam_pwquality`
* Setting login failure limits and lockout mechanisms
* Restricting shell access using `pam_shells`
* Restricting logins by user/group with `pam_listfile`

---

### 9. **Integrating PAM with Central Authentication Systems**

* Using PAM with LDAP
* Using PAM with Kerberos
* Using PAM with Active Directory via SSSD

---

### 10. **Troubleshooting PAM**

* Understanding PAM log messages in `/var/log/auth.log` or `/var/log/secure`
* Diagnosing access denials or login issues
* Safe recovery from misconfigured PAM (e.g., regaining root access via single-user mode)

---

## PAM (Pluggable Authentication Modules) – Comprehensive Study Checklist

---

### 1. **PAM Fundamentals**

* [ ] Understand what PAM is and its role in Linux authentication
* [ ] Learn the modular structure of PAM (stacked processing)
* [ ] Identify PAM-aware services on your system (e.g., SSH, login, sudo)

---

### 2. **PAM Configuration Structure**

* [ ] Explore the `/etc/pam.d/` directory and identify individual service files
* [ ] Understand how PAM reads configuration files (per-service vs common files)
* [ ] Learn the format of PAM lines:
  `module-type  control-flag  module-path  [arguments]`

---

### 3. **PAM Module Types**

* [ ] `auth` – Authentication (passwords, biometrics, etc.)
* [ ] `account` – Authorization and account limitations
* [ ] `password` – Password updating and complexity
* [ ] `session` – Session initialization and cleanup

---

### 4. **PAM Control Flags**

* [ ] Understand how these flags affect authentication outcomes:

  * `required`
  * `requisite`
  * `sufficient`
  * `optional`
* [ ] Test combinations of flags to understand evaluation logic

---

### 5. **Common PAM Modules and Use Cases**

* [ ] `pam_unix.so` – Standard Linux authentication
* [ ] `pam_env.so` – Load user environment variables
* [ ] `pam_limits.so` – Enforce user resource limits
* [ ] `pam_listfile.so` – Allow/deny users based on lists
* [ ] `pam_tally2.so` / `pam_faillock.so` – Limit failed login attempts
* [ ] `pam_pwquality.so` or `pam_cracklib.so` – Password strength
* [ ] `pam_mkhomedir.so` – Auto-create home directories on login
* [ ] `pam_exec.so` – Run custom scripts during auth/session

---

### 6. **Service-Level PAM Configuration**

* [ ] Customize PAM settings for:

  * `sshd`
  * `login`
  * `sudo`
  * `passwd`
  * `su`
* [ ] Disable or restrict access to specific services using PAM
* [ ] Use `pam.d/other` to define default behavior for unknown services (with caution)

---

### 7. **Security Hardening with PAM**

* [ ] Configure account lockout after failed login attempts
* [ ] Restrict root login to secure terminals (`pam_securetty`)
* [ ] Enforce strong password policies
* [ ] Restrict logins to certain users/groups (`pam_listfile`, `pam_access`)

---

### 8. **Integration with External Authentication**

* [ ] Integrate PAM with **LDAP** using `pam_ldap.so`
* [ ] Integrate PAM with **Kerberos** using `pam_krb5.so`
* [ ] Configure **SSSD** (`pam_sss.so`) for central authentication
* [ ] Use `pam_mkhomedir.so` with LDAP or SSSD to create home directories

---

### 9. **Troubleshooting and Logging**

* [ ] Monitor PAM-related messages in `/var/log/auth.log` or `/var/log/secure`
* [ ] Use `pam_debug.so` for verbose logging during testing
* [ ] Safely test changes on non-critical services or in a VM
* [ ] Learn how to recover from misconfiguration (e.g., boot into rescue mode)

---

### 10. **Best Practices**

* [ ] Always backup PAM config files before changes
* [ ] Use comments (`#`) to document changes in PAM files
* [ ] Test changes with a second terminal open in case of lockout
* [ ] Avoid changing core files like `pam_unix.so` directly unless necessary

---

## Hands-On Exercises in PAM

---

### 1. **Explore PAM Configuration Files**

* Open and review contents of `/etc/pam.d/`
* Identify PAM configurations for services like `login`, `sshd`, `sudo`, `passwd`, `su`
* Locate and review `common-auth`, `common-account`, etc. (on Debian-based systems)

---

### 2. **Test `pam_unix.so` Authentication**

* Modify the `auth` section in a PAM-enabled service (e.g., `sudo`)
* Observe authentication flow using `pam_unix.so`
* Test successful and failed logins

---

### 3. **Implement Login Access Control with `pam_listfile.so`**

* Create a user deny list file
* Configure `pam_listfile.so` to block users from accessing a service (e.g., `su` or `ssh`)
* Test login attempts for denied and allowed users

---

### 4. **Enforce Password Complexity with `pam_pwquality.so`**

* Configure `/etc/security/pwquality.conf`
* Modify `common-password` (Debian) or relevant PAM stack to include `pam_pwquality.so`
* Test password changes and confirm enforcement

---

### 5. **Set Up Login Attempt Lockouts Using `pam_tally2.so` or `pam_faillock.so`**

* Configure login failure lockout policies
* Trigger failed login attempts to simulate account lockout
* Reset tally count using `pam_tally2 --reset` or `faillock --reset`

---

### 6. **Auto-Create Home Directories Using `pam_mkhomedir.so`**

* Add `pam_mkhomedir.so` to the `session` section of the PAM stack
* Authenticate with a user whose home directory doesn’t exist
* Verify automatic creation of the home directory on login

---

### 7. **Restrict Root Login Using `pam_securetty.so`**

* Modify `pam_securetty.so` to limit root access to specific TTYs
* Attempt root login from allowed and disallowed terminals

---

### 8. **Set Per-User Resource Limits Using `pam_limits.so`**

* Edit `/etc/security/limits.conf` to define resource limits
* Configure `pam_limits.so` in the `session` section
* Test limits by switching to the user and running commands that hit the limits

---

### 9. **Integrate PAM with LDAP (Optional)**

* Install and configure `libpam-ldap` or `pam_ldap.so`
* Bind to an existing LDAP directory
* Test user authentication via LDAP

---

### 10. **Integrate PAM with Kerberos (Optional)**

* Install Kerberos packages
* Configure `pam_krb5.so` in the appropriate PAM service stack
* Authenticate users using Kerberos credentials

---

### 11. **Use `pam_exec.so` to Run Scripts on Login**

* Write a simple shell script (e.g., log login times to a file)
* Use `pam_exec.so` in the `session` section to call the script
* Log in and verify that the script executes

---

### 12. **Configure and Test `pam_access.so` Rules**

* Edit `/etc/security/access.conf` to allow/deny user access
* Configure `pam_access.so` in the `account` section of a service
* Test access rules based on user and origin

---

### 13. **Simulate and Recover from PAM Misconfiguration**

* Break a PAM configuration (e.g., by misspelling a module)
* Get locked out and recover using a live CD, rescue mode, or another TTY
* Restore correct configuration from backup

---

### 14. **Enable Verbose Logging for Troubleshooting**

* Enable `pam_debug.so` in the stack for a test service
* Authenticate and review logs in `/var/log/auth.log` or `/var/log/secure`
* Understand success/failure flow of module stack

---

### 15. **Experiment with Custom PAM Stack for a Dummy Service**

* Create a custom service file under `/etc/pam.d/mytest`
* Use `login -f <username> --service mytest` (or a custom app) to trigger it
* Try different modules and control flags to observe behavior

---

</details>

<details>
  <summary>Load Balancers</summary>

**topics in Linux load balancers**

Introduction to Load Balancing in Linux
Load Balancing Concepts and Terminology
Types of Load Balancers (Hardware vs Software)
Layer 4 (Transport Layer) Load Balancing
Layer 7 (Application Layer) Load Balancing
Linux Networking Basics for Load Balancing
IPVS (IP Virtual Server) Overview
LVS (Linux Virtual Server) Architecture and Components
Direct Routing (DR) Mode
Network Address Translation (NAT) Mode
Tunneling (TUN) Mode
Keepalived Overview and Configuration
Keepalived for High Availability
VRRP (Virtual Router Redundancy Protocol) Concepts
Load Balancing Algorithms (Round Robin, Least Connections, Weighted, etc.)
Health Checking and Monitoring Backends
Session Persistence and Sticky Sessions
Failover and Redundancy Configuration
HAProxy Introduction and Architecture
HAProxy Installation and Configuration
HAProxy Frontend and Backend Setup
SSL/TLS Termination in HAProxy
Load Balancing HTTP and HTTPS Traffic
Load Balancing TCP/UDP Services
NGINX as a Load Balancer
NGINX Load Balancing Methods and Configuration
Advanced NGINX Load Balancing (Least Time, IP Hash, etc.)
Reverse Proxy vs Load Balancer Differences
Monitoring Load Balancers (logs, metrics, statistics)
Performance Tuning and Optimization
Security Considerations in Load Balancers
Firewall and iptables Integration
Load Balancing DNS and Multiple Data Centers
Dynamic Scaling and Auto-Scaling Concepts
Troubleshooting and Debugging Load Balancer Issues
Testing Load Balancer Configurations (ab, wrk, curl, etc.)
Case Studies: HAProxy + Keepalived for HA
Comparison of HAProxy, NGINX, and LVS
Automation of Load Balancer Deployment (Ansible, Bash)
Best Practices in Linux Load Balancer Administration

**comprehensive study checklist** for mastering **Linux Load Balancers**

---

### **1. Fundamentals of Load Balancing**

Understand what load balancing is and why it’s used
Learn key concepts: scalability, redundancy, failover, and fault tolerance
Study types of load balancers: hardware vs software
Differentiate between Layer 4 and Layer 7 load balancing
Understand traffic distribution algorithms (round robin, least connections, weighted, etc.)
Learn the difference between a reverse proxy and a load balancer

---

### **2. Networking Basics for Load Balancing**

Review Linux networking essentials (interfaces, routing, ARP, IP forwarding)
Understand TCP/UDP behavior and ports
Practice configuring static and dynamic IPs
Learn about NAT, routing tables, and packet flow in Linux
Explore iptables and nftables basics for packet control
Test connectivity and latency (ping, traceroute, netstat, ss)

---

### **3. Linux Virtual Server (LVS) and IPVS**

Understand the role of IPVS (IP Virtual Server) in Linux load balancing
Study LVS architecture and packet flow
Learn different LVS forwarding methods: NAT, DR, and TUN
Install and configure IPVS tools (ipvsadm)
Create basic LVS load balancing setups
Test and verify load distribution among real servers
Learn persistence options (source hashing, sticky sessions)
Explore LVS scheduler algorithms (rr, wlc, sh, dh, lblc, lblcr)

---

### **4. Keepalived and High Availability**

Understand Keepalived architecture and use cases
Study VRRP (Virtual Router Redundancy Protocol) and its function
Install and configure Keepalived for LVS management
Set up Keepalived for HAProxy or NGINX failover
Test master-backup failover with VRRP
Configure health checks and backend monitoring
Learn advanced Keepalived configurations (track scripts, notifications)

---

### **5. HAProxy Load Balancer**

Understand HAProxy architecture (frontend, backend, listener)
Install and configure HAProxy on Linux
Set up basic HTTP and TCP load balancing
Explore load balancing algorithms in HAProxy
Implement health checks for backend servers
Configure session persistence and sticky sessions
Set up SSL/TLS termination in HAProxy
Monitor HAProxy statistics and logs
Learn about ACLs (Access Control Lists) and conditional routing
Optimize HAProxy for performance and reliability

---

### **6. NGINX as Load Balancer**

Understand NGINX architecture and worker model
Install and configure NGINX as a reverse proxy and load balancer
Set up Layer 7 (HTTP) load balancing
Configure various balancing methods (round robin, least_conn, ip_hash)
Add health checks and failover mechanisms
Implement SSL termination and proxy buffering
Use caching and compression for optimization
Enable logging and monitoring for troubleshooting

---

### **7. Advanced Load Balancing Topics**

Compare HAProxy, NGINX, and LVS use cases and performance
Implement multi-layer load balancing (L4 + L7 combined)
Study global load balancing and geo-DNS concepts
Learn about dynamic scaling and auto-scaling with cloud integration
Integrate load balancers with Docker and Kubernetes
Explore automation with Ansible or shell scripts
Secure load balancer configurations with firewalls and ACLs
Implement DDoS mitigation strategies
Tune kernel parameters for high-performance networking

---

### **8. Monitoring and Troubleshooting**

Learn tools for load balancer diagnostics (tcpdump, ss, netstat, curl, ab, wrk)
Monitor system metrics (CPU, memory, network) with tools like top, htop, nload, iftop
Set up HAProxy or NGINX dashboards for live stats
Log analysis and alerting with syslog and Prometheus/Grafana
Troubleshoot packet flow and connection issues
Simulate failure scenarios to test resilience

---

### **9. Practical Projects and Case Studies**

Set up an LVS + Keepalived cluster for high availability
Configure HAProxy with HTTPS and sticky sessions for a web farm
Deploy NGINX load balancing for backend APIs
Build a hybrid HAProxy + Keepalived HA setup
Automate load balancer deployment using Ansible
Test performance under load with stress tools
Document configurations and results

---

### **10. Maintenance and Best Practices**

Apply configuration management and version control (Git)
Regularly update and patch load balancer software
Backup and restore configurations
Document load balancer topology and policies
Implement monitoring and alerting systems
Review logs and performance metrics periodically
Perform failover testing routinely

---

**comprehensive list of hands-on exercises** for learning **Linux Load Balancers**

---

### **1. Load Balancing Fundamentals**

Set up two Linux web servers using Apache or NGINX
Deploy a simple static website on each backend server
Use `curl` or `ab` to simulate client traffic
Observe how responses differ between servers
Measure latency and throughput before load balancing

---

### **2. Network Configuration Exercises**

Enable IP forwarding on a Linux machine
Configure static IPs and routing tables manually
Use `iptables` or `nftables` to perform basic NAT
Capture network packets with `tcpdump` to analyze traffic flow
Use `ss` or `netstat` to verify listening ports and connections

---

### **3. IPVS (LVS) Load Balancing**

Install `ipvsadm` on a Linux system
Create a basic IPVS load balancer for HTTP traffic
Add and remove real servers dynamically using `ipvsadm`
Test different scheduling algorithms: rr, wlc, sh, lblc
Use LVS NAT mode for backend servers on a private network
Configure LVS Direct Routing (DR) mode with multiple web nodes
Set up LVS Tunneling (TUN) mode between virtual networks
Check load distribution using repeated `curl` requests
Implement session persistence (sticky sessions)
Monitor IPVS statistics in real time

---

### **4. Keepalived and High Availability**

Install and configure Keepalived on two Linux nodes
Create a basic Keepalived VRRP configuration for failover
Assign a virtual IP shared between two nodes
Simulate master node failure and verify automatic failover
Integrate Keepalived with LVS for HA load balancing
Use Keepalived health checks to remove failed backends
Write custom health-check scripts for application-level monitoring
View VRRP state changes in system logs

---

### **5. HAProxy Load Balancing**

Install and start HAProxy on a Linux server
Set up HAProxy for HTTP load balancing between two backends
Test round robin and least connection algorithms
Implement backend health checks using `check` options
Add sticky sessions and observe cookie-based persistence
Configure HTTPS load balancing with SSL termination
Use ACLs to route traffic based on URL or hostname
Set up TCP load balancing for non-HTTP services (e.g., SSH or database)
Enable the HAProxy stats dashboard and monitor live connections
Benchmark HAProxy with `ab` or `wrk` load-testing tools
Tune HAProxy configuration parameters for performance

---

### **6. NGINX Load Balancing**

Install NGINX and configure it as a reverse proxy
Add multiple upstream backend servers
Test load balancing algorithms: round robin, least_conn, ip_hash
Set up passive health checks with `max_fails` and `fail_timeout`
Enable SSL termination for HTTPS traffic
Implement caching and compression for optimization
Simulate a failed backend and observe failover behavior
Use NGINX access logs to analyze traffic patterns

---

### **7. Advanced Load Balancing and Integration**

Set up a combined HAProxy + Keepalived high-availability cluster
Integrate load balancer with DNS for name-based traffic distribution
Deploy a multi-layer load balancer: LVS for L4, HAProxy for L7
Containerize backends using Docker and balance across containers
Use Ansible to automate HAProxy or NGINX setup
Deploy Prometheus + Grafana for load balancer monitoring
Stress test your setup with 10k+ concurrent connections
Simulate backend node crashes and recovery scenarios
Implement firewall rules to secure load balancer access
Measure and compare performance between LVS, HAProxy, and NGINX

---

### **8. Troubleshooting and Optimization**

Use `tcpdump` to capture and inspect packets through the load balancer
Diagnose connection resets and timeouts using logs
Check kernel parameters related to connection tracking (`sysctl net.ipv4.*`)
Analyze and tune keepalive and timeout values
Monitor CPU and memory usage under load
Use `iftop`, `nload`, or `dstat` for network monitoring
Document findings and performance metrics

---

### **9. Real-World Project Exercises**

Build a production-like web cluster with:
– 2 backend web servers
– 1 load balancer using HAProxy or NGINX
– 1 standby load balancer using Keepalived
Implement SSL, sticky sessions, and monitoring
Test HA failover and load redistribution
Measure performance and log analysis
Automate deployment with a shell or Ansible script

---

</details>

<details>
  <summary>Firewalld</summary>
  
**comprehensive list of topics in Firewalld administration**

---

### **1. Introduction to Firewalld**

Overview and purpose of Firewalld
Difference between Firewalld and iptables/nftables
Understanding Firewalld architecture
D-Bus interface and background daemon
Default behavior and integration with NetworkManager

---

### **2. Firewalld Concepts and Components**

Zones and their significance
Zone trust levels and default zones
Services and predefined service definitions
Ports and port ranges
Interfaces and source bindings
Rich rules and direct rules
Targets, chains, and tables (relation to nftables/iptables)

---

### **3. Firewalld Configuration Basics**

Installing and enabling Firewalld
Starting, stopping, and reloading the Firewalld service
Checking Firewalld status and active zones
Viewing and listing active configurations
Understanding runtime vs permanent configurations
Setting and changing the default zone
Assigning network interfaces to zones

---

### **4. Managing Zones**

Listing available zones
Exploring default zone configuration files
Adding and removing interfaces from zones
Changing a zone’s target policy (default behavior)
Creating and deleting custom zones
Configuring sources (IP/subnet) within zones
Viewing effective zone settings

---

### **5. Managing Services and Ports**

Listing predefined services
Adding and removing services from zones
Opening and closing specific ports manually
Allowing and blocking specific protocols
Configuring multiport rules
Reloading and verifying changes
Editing custom service definition XML files

---

### **6. Rich Rules and Advanced Filtering**

Understanding the purpose of rich rules
Syntax and structure of rich rules
Creating complex allow/deny rules (with logging, limit, or audit options)
Restricting access by source address or interface
Combining rich rules with services and ports
Testing and troubleshooting rich rule configurations

---

### **7. Direct Interface and Legacy Compatibility**

Understanding Firewalld direct interface
Adding, listing, and removing direct rules
Using direct rules for compatibility with raw iptables/nftables syntax
Interaction between Firewalld and direct rules
Testing rule precedence and rule conflict handling

---

### **8. Firewalld and IPv6**

Enabling and managing IPv6 rules
Allowing and blocking IPv6 traffic in zones
Testing IPv6 connectivity and filtering behavior

---

### **9. Firewalld and NetworkManager Integration**

Dynamic zone assignment via NetworkManager
Reloading Firewalld without disconnecting interfaces
Persisting network interface-zone mappings

---

### **10. Firewalld with SELinux and System Security**

Relationship between Firewalld and SELinux
Security boundaries and application contexts
Handling SELinux denials related to Firewalld

---

### **11. Firewalld Logging and Monitoring**

Enabling logging for dropped packets
Configuring log level and target (journal/syslog)
Using `journalctl` to monitor Firewalld events
Analyzing logs for denied connections
Integrating Firewalld logs with monitoring tools

---

### **12. Firewalld with NAT and Masquerading**

Understanding NAT concepts in Firewalld
Enabling and disabling masquerading
Forwarding ports between interfaces
Configuring source NAT (SNAT) and destination NAT (DNAT)
Testing NAT configurations with ping and curl

---

### **13. Custom Services and XML Configuration**

Creating custom service XML files in `/etc/firewalld/services/`
Defining custom ports, protocols, and modules
Validating and reloading custom service definitions
Sharing and reusing service configuration files

---

### **14. Firewalld Command-Line Mastery**

Using `firewall-cmd` effectively
Common commands for runtime and permanent settings
Listing, adding, and removing elements in one command
Testing configuration with `--check-config`
Combining commands in scripts for automation

---

### **15. Firewalld Backup, Restore, and Troubleshooting**

Exporting and importing Firewalld configurations
Resetting Firewalld to factory defaults
Debugging Firewalld issues
Using `firewall-offline-cmd` for offline configuration
Recovering from misconfigurations
Testing rule effectiveness with `nmap` or `curl`

---

### **16. Automation and Scripting**

Automating Firewalld setup using shell scripts
Integrating Firewalld rules with Ansible or Puppet
Dynamic configuration changes via D-Bus or Python API

---

### **17. Performance and Best Practices**

Minimizing reload downtime
Efficient zone and service organization
Regular audits of open ports and rules
Balancing security and accessibility
Combining Firewalld with intrusion detection tools

---

**comprehensive study checklist for Firewalld administration in Linux**

---

### **1. Firewalld Fundamentals**

Understand what Firewalld is and its purpose in Linux
Learn the difference between Firewalld and legacy iptables
Study the Firewalld architecture, components, and daemon process
Explore how Firewalld interacts with nftables underneath
Check if Firewalld is installed and running on your system
Practice enabling, starting, stopping, and reloading Firewalld
Understand runtime versus permanent configurations

---

### **2. Firewalld Zones**

Understand the concept of zones and their trust levels
List available default zones and their purposes
Check the currently active and default zone
Assign network interfaces to specific zones
Add source IP addresses or subnets to zones
Change the default zone for new interfaces
Create custom zones for specific applications or environments
Delete unnecessary or unused zones
Verify zone configuration using `firewall-cmd --list-all`

---

### **3. Managing Services and Ports**

List all predefined services in Firewalld
Inspect XML service definitions in `/usr/lib/firewalld/services/`
Add and remove predefined services from zones
Open and close specific TCP and UDP ports
Allow port ranges for specific applications
Block unwanted ports and verify the effect
Reload the firewall to apply permanent changes
Test open and closed ports using `nmap` or `ss -tuln`

---

### **4. Working with Rich Rules**

Understand the purpose of rich rules and how they differ from basic rules
Learn the syntax and components of a rich rule
Add a rich rule to allow or deny traffic from a specific source
Create a rich rule with logging or rate limiting
Combine multiple match conditions (source, destination, protocol, port)
View, verify, and remove existing rich rules
Test the effectiveness of rich rules using simulated connections

---

### **5. Managing Direct Rules**

Understand Firewalld’s direct interface and its purpose
Add direct rules using raw iptables/nftables syntax
List and remove direct rules when no longer needed
Test interaction and precedence between direct and rich rules
Use direct rules for complex legacy firewall scenarios

---

### **6. Masquerading and NAT Configuration**

Learn what NAT and masquerading mean in networking
Enable and verify masquerading for outbound traffic
Configure source NAT (SNAT) and destination NAT (DNAT)
Set up port forwarding between internal and external interfaces
Test NAT functionality using ping and curl between subnets
Disable masquerading safely and verify restoration

---

### **7. IPv6 Management**

Understand how Firewalld manages IPv6 traffic separately
Enable or disable IPv6 filtering
Add IPv6-specific rules and test their behavior
Check for dual-stack zone configurations

---

### **8. Logging and Monitoring**

Enable logging for dropped and accepted packets
Set log level (low, medium, high) and verify log behavior
View logs using `journalctl -xe` or system logs in `/var/log/`
Integrate Firewalld logs with centralized monitoring tools
Audit current rules and open ports regularly

---

### **9. Custom Services and Configuration Files**

Create a custom service definition file in `/etc/firewalld/services/`
Define custom ports, protocols, and descriptions
Validate XML configuration for syntax correctness
Reload Firewalld to register the new service
Use the custom service in a zone configuration
Share or migrate service files to other systems

---

### **10. Integration with System Components**

Study Firewalld’s relationship with NetworkManager
Learn how dynamic interface assignments are handled
Understand Firewalld interaction with SELinux policies
Resolve conflicts between SELinux port contexts and Firewalld rules

---

### **11. Automation and Scripting**

Practice using `firewall-cmd` for one-line and scripted operations
Write a Bash script to automate Firewalld configuration
Use `firewall-offline-cmd` for modifying configurations offline
Explore Firewalld’s D-Bus interface and Python bindings
Integrate Firewalld setup into an Ansible playbook

---

### **12. Troubleshooting and Recovery**

Identify the active configuration and conflicting rules
Reset Firewalld to its factory defaults
Recover from misconfigurations using offline commands
Test connectivity and rule behavior using `nmap`, `ping`, and `curl`
Debug startup or reload issues from logs
Use verbose mode to trace rule creation and deletion

---

### **13. Security Hardening and Best Practices**

Restrict unnecessary services and open ports
Use zones appropriately for public, internal, and trusted networks
Regularly audit configurations and rule sets
Implement logging and alerts for dropped packets
Test failover and recovery procedures regularly
Keep Firewalld and system packages up to date
Balance security policies with application accessibility

---

### **14. Performance and Optimization**

Review rule count and complexity for efficiency
Benchmark connection performance before and after Firewalld
Fine-tune timeouts and connection tracking parameters
Monitor CPU and memory usage under high traffic load

---

### **15. Real-World Scenarios and Case Studies**

Configure a public-facing web server with HTTP/HTTPS only
Set up internal DNS, NTP, and SSH access within trusted zones
Build a NAT gateway with masquerading for private subnets
Secure a mail server with specific inbound and outbound rules
Implement a logging-rich rule set for auditing in production
Simulate multi-zone configurations across multiple interfaces

---

**list of hands-on exercises Firewalld**

---

### **1. Getting Started with Firewalld**

Check if Firewalld is installed and running on your system
Enable and start the Firewalld service
View the default zone and list all available zones
Display the active configuration and current interfaces
Switch between runtime and permanent configurations
Stop and restart the Firewalld service safely

---

### **2. Working with Zones**

Identify which zone each network interface belongs to
Change the default zone and verify the update
Add a network interface to a specific zone
Remove an interface from a zone
Add a source IP or subnet to a zone and test access
Create a custom zone for a dedicated network segment
Delete a custom zone and restore default configuration
Use `firewall-cmd --get-active-zones` and `--list-all` for verification

---

### **3. Managing Services**

List all predefined services available in Firewalld
Add an existing service (for example, http, ssh) to a zone
Remove a service from a zone and confirm the change
Add a service permanently and reload Firewalld
Test connectivity before and after allowing a service
Inspect the XML definition of a predefined service in `/usr/lib/firewalld/services/`
Create a custom service XML for a custom port and protocol
Add and enable your custom service, then test access

---

### **4. Managing Ports and Protocols**

Add a single TCP port to a zone and verify it’s open
Add multiple ports or port ranges for a service
Remove a specific port from a zone
Allow a UDP port and test with `nc` or `nmap`
Block a specific port temporarily
Combine multiple port rules and verify effective configuration
Check open ports using `ss -tuln` or `netstat`

---

### **5. Rich Rules Practice**

Write a rich rule to allow access from a specific IP address
Add a rich rule to block traffic from a specific IP or network
Create a rule to log dropped packets with a prefix
Add a rich rule to limit connections per source
Use a rich rule to restrict access to a service by interface name
List and remove specific rich rules after testing
Test rule effectiveness with `ping`, `curl`, or `nc`

---

### **6. Direct Rules and Advanced Filtering**

Add a direct rule using iptables-like syntax through Firewalld
List all current direct rules
Create a direct rule to drop ICMP echo requests
Remove a specific direct rule
Check how direct rules interact with rich rules
Test both rule types with packet captures

---

### **7. Masquerading and NAT Configuration**

Enable masquerading on an external zone
Verify masquerading is active using `firewall-cmd --query-masquerade`
Configure simple port forwarding from one interface to another
Set up SNAT (Source NAT) for outbound connections
Set up DNAT (Destination NAT) for inbound redirection
Test NAT functionality using two virtual machines or containers
Disable masquerading and verify return to default behavior

---

### **8. IPv6 and Dual Stack Configuration**

Enable IPv6 support in Firewalld
Add and test an IPv6 rule to allow traffic from a specific IPv6 address
Test IPv6 connections using `ping6` and `curl`
Compare IPv4 and IPv6 behavior under the same zone configuration

---

### **9. Logging and Auditing**

Enable logging for dropped packets using rich rules
Adjust log level from low to high and observe differences
View logs in real time using `journalctl -f`
Filter logs related to Firewalld in `/var/log/messages` or `/var/log/firewalld`
Add a rich rule with both log and accept actions
Analyze logs for blocked ports or denied IPs

---

### **10. Custom Service Definitions**

Create a new XML service definition in `/etc/firewalld/services/`
Define custom ports and protocols in the XML file
Validate the XML syntax using `xmllint`
Reload Firewalld to apply new service definitions
Add the custom service to a zone and test access
Share or back up your custom service file

---

### **11. NetworkManager and SELinux Integration**

Change zone assignments dynamically with NetworkManager
Verify zone persistence after network restarts
Test how SELinux interacts with Firewalld rules
Allow an SELinux-protected service by adjusting port contexts
Troubleshoot SELinux denials related to blocked ports

---

### **12. Automation and Offline Configuration**

Use `firewall-offline-cmd` to configure Firewalld without starting the service
Write a shell script to automate common configuration steps
Add multiple services and ports in a single command sequence
Backup your entire Firewalld configuration using `firewall-cmd --runtime-to-permanent`
Use `firewall-cmd --permanent --export` and import it on another system

---

### **13. Troubleshooting Exercises**

Reset Firewalld to its default configuration and verify recovery
Simulate a connectivity problem and resolve it by opening the correct port
Trace dropped packets using logs and packet captures
Debug Firewalld startup or reload errors
Compare Firewalld rules with equivalent nftables rules
Verify effective firewall rules using `firewall-cmd --list-all` and `nft list ruleset`

---

### **14. Security Hardening Scenarios**

Close all unnecessary ports and services
Create separate zones for public, internal, and trusted networks
Allow only SSH access from a specific IP
Limit SSH connection attempts with rate limiting
Enable rich rule logging for security auditing
Simulate and test unauthorized connection attempts

---

### **15. Real-World Project Labs**

Set up a multi-zone environment: internal, public, and dmz
Allow web traffic on the public zone while restricting SSH to internal
Implement port forwarding from public zone to a backend web server
Enable masquerading for private subnets accessing the internet
Test failover and persistence of Firewalld rules after reboot
Document and verify configuration using command outputs

---

</details>

<details>
  <summary>IPTables</summary>
  
**list of topics in iptables**

---

### **1. Introduction to iptables**

Overview and purpose of iptables in Linux
Difference between iptables, nftables, and Firewalld
Understanding the Linux kernel Netfilter framework
iptables architecture and components
Understanding how packets flow through the Linux network stack

---

### **2. iptables Tables and Chains**

Overview of tables: filter, nat, mangle, raw, and security
Purpose and use cases of each table
Understanding built-in chains: INPUT, OUTPUT, FORWARD, PREROUTING, POSTROUTING
Chain policies and default actions (ACCEPT, DROP, REJECT)
Creating custom user-defined chains

---

### **3. Basic iptables Commands**

Installing iptables and verifying the package
Viewing existing rules and chains
Flushing, resetting, and saving rules
Listing rules in verbose and numeric formats
Setting default policies for chains
Inserting, appending, and deleting rules
Reordering and numbering rules for management

---

### **4. Packet Matching and Rule Syntax**

Understanding rule structure: match conditions and targets
Matching packets by protocol (TCP, UDP, ICMP)
Matching by source and destination IP addresses
Matching by source and destination ports
Using multiple match conditions in a single rule
Understanding negation (!) and logical combinations

---

### **5. Connection Tracking**

Overview of connection states: NEW, ESTABLISHED, RELATED, INVALID
Using `-m state` or `-m conntrack` modules
Allowing only established and related traffic
Blocking invalid packets
Connection tracking behavior in NAT and forwarding

---

### **6. Filtering Rules**

Building a basic inbound and outbound filtering policy
Creating input rules to allow or deny SSH, HTTP, HTTPS
Filtering traffic based on interface (e.g., eth0, ens33)
Blocking or allowing specific IP addresses or subnets
Implementing default DROP policy and whitelisting specific services
Logging dropped packets for auditing

---

### **7. NAT (Network Address Translation)**

Understanding NAT concepts: SNAT, DNAT, and masquerading
Using the nat table for address translation
Configuring SNAT for outbound connections
Configuring DNAT and port forwarding for inbound connections
Using MASQUERADE target for dynamic IP environments
Testing NAT configurations with multiple network interfaces

---

### **8. Port Forwarding**

Forwarding traffic from one port to another
Redirecting local and remote connections
Forwarding external traffic to internal servers
Testing port forwarding with curl or telnet

---

### **9. Advanced Match Modules**

Using `-m limit` to rate-limit connections
Using `-m mac` to match MAC addresses
Matching packets by string or content using `-m string`
Using `-m time` for time-based rules
Filtering based on packet length, TTL, or TCP flags
Combining multiple match modules for advanced filtering

---

### **10. Logging and Auditing**

Using the LOG target to record packet activity
Configuring log prefixes and log levels
Analyzing firewall logs using syslog and journalctl
Creating separate log chains for monitoring specific traffic
Rate-limiting log entries to prevent flooding

---

### **11. Custom Chains and Rule Management**

Creating user-defined chains for better rule organization
Linking custom chains within built-in chains
Deleting and renaming chains safely
Structuring rules for scalability and readability

---

### **12. mangle Table and Packet Alteration**

Understanding the purpose of the mangle table
Changing packet headers (TTL, TOS, MARK)
Marking packets for QoS or routing decisions
Using MARK and CONNMARK targets
Integrating with iproute2 for policy-based routing

---

### **13. iptables and IPv6 (ip6tables)**

Understanding differences between iptables and ip6tables
Creating basic IPv6 rules
Allowing and blocking IPv6 services
Testing IPv6 filtering with ping6 and curl
Integrating IPv6 rules with existing IPv4 policies

---

### **14. Persisting and Managing Rules**

Saving and restoring iptables configurations across reboots
Using iptables-save and iptables-restore
Managing configurations with systemd units or scripts
Understanding distribution-specific persistence tools (Debian, RHEL, CentOS, Ubuntu)

---

### **15. Troubleshooting and Debugging**

Viewing packet counters and statistics
Flushing and testing rules incrementally
Using `iptables -vL` and `iptables -S` for detailed analysis
Capturing packets with tcpdump for rule verification
Testing rules step by step using simulated traffic
Restoring default settings safely

---

### **16. Security and Best Practices**

Implementing least privilege principle with default DROP policy
Allowing only necessary services explicitly
Preventing IP spoofing and SYN flood attacks
Enabling logging for suspicious or dropped packets
Regularly auditing and updating rules
Combining iptables with intrusion detection tools like fail2ban

---

### **17. Automation and Integration**

Automating rule creation using shell scripts
Integrating iptables management with configuration tools (Ansible, Puppet)
Using iptables with Docker and Kubernetes networking
Combining iptables with Firewalld or nftables transitions

---

### **18. Performance and Optimization**

Optimizing rule order and structure for performance
Reducing rule count through custom chains and grouping
Analyzing packet drop rates and connection delays
Monitoring CPU utilization caused by large rule sets

---

### **19. Migration to nftables**

Understanding the relationship between iptables and nftables
Comparing syntax and concepts
Using iptables-nft compatibility mode
Migrating rules to nftables for modern systems

---

### **20. Real-World Scenarios and Case Studies**

Creating a secure web server firewall policy
Building a NAT gateway for private subnets
Implementing port forwarding for internal services
Configuring iptables on a multi-interface router
Logging and blocking suspicious traffic in production environments

---

**comprehensive study checklist for iptables**

---

### **1. Introduction to iptables**

Understand the purpose of iptables in Linux
Learn the difference between iptables, nftables, and Firewalld
Understand the Netfilter framework in the Linux kernel
Study packet flow through the Linux network stack
Familiarize with iptables architecture and components

---

### **2. iptables Tables and Chains**

Learn about the main tables: filter, nat, mangle, raw, security
Understand the purpose of each table
Study built-in chains: INPUT, OUTPUT, FORWARD, PREROUTING, POSTROUTING
Learn about default policies (ACCEPT, DROP, REJECT)
Create and manage user-defined chains

---

### **3. Basic iptables Commands**

Install and verify iptables package
List rules and chains in verbose and numeric formats
Flush and reset existing rules
Set default chain policies
Append, insert, and delete rules
Reorder rules and understand rule numbering
Save and restore iptables configurations

---

### **4. Packet Matching and Rule Syntax**

Understand the structure of an iptables rule
Match by protocol (TCP, UDP, ICMP)
Match by source and destination IP addresses
Match by source and destination ports
Use logical operators and negation
Combine multiple match conditions in a single rule

---

### **5. Connection Tracking**

Understand connection states: NEW, ESTABLISHED, RELATED, INVALID
Use `-m state` and `-m conntrack` modules
Allow only established and related traffic
Block invalid packets
Understand how NAT and forwarding interact with connection tracking

---

### **6. Filtering Rules**

Create input, output, and forward filtering policies
Allow and block common services (SSH, HTTP, HTTPS)
Filter traffic by interface
Block or allow specific IPs or subnets
Implement default DROP policies with whitelist exceptions
Log dropped or rejected packets for auditing

---

### **7. NAT (Network Address Translation)**

Understand SNAT, DNAT, and masquerading
Configure outbound NAT for internal networks
Configure inbound NAT and port forwarding
Use MASQUERADE for dynamic IP scenarios
Test NAT setups with multiple network interfaces

---

### **8. Port Forwarding**

Forward traffic from one port to another locally or remotely
Redirect external traffic to internal servers
Test port forwarding rules with `telnet`, `curl`, or `nc`

---

### **9. Advanced Match Modules**

Use `-m limit` to rate-limit connections
Match by MAC address using `-m mac`
Filter by content or strings using `-m string`
Use time-based rules with `-m time`
Filter packets by length, TTL, or TCP flags
Combine multiple modules for complex filtering

---

### **10. Logging and Auditing**

Log traffic with LOG target
Configure log prefixes and log levels
Analyze logs with `journalctl` or `/var/log/messages`
Rate-limit logging to prevent flooding
Create separate chains for monitored traffic

---

### **11. Custom Chains and Rule Management**

Create user-defined chains for organization
Link custom chains to built-in chains
Delete and rename chains safely
Design scalable rule sets for large environments

---

### **12. mangle Table and Packet Alteration**

Understand mangle table use cases
Alter packet headers (TTL, TOS, MARK)
Mark packets for QoS or routing
Integrate MARK with iproute2 policy routing

---

### **13. IPv6 Management (ip6tables)**

Learn differences between iptables and ip6tables
Create basic IPv6 filtering rules
Allow and block IPv6 services
Test IPv6 connectivity with `ping6` and `curl`
Integrate IPv6 rules with existing IPv4 policies

---

### **14. Persisting Rules**

Save and restore rules using iptables-save and iptables-restore
Make rules persistent across reboots
Use systemd units or distribution-specific tools (Debian, Ubuntu, RHEL, CentOS)

---

### **15. Troubleshooting and Debugging**

View packet counters and chain statistics
Flush and test rules incrementally
Capture packets with tcpdump for verification
Debug startup or reload issues
Verify effective rules with `iptables -S` and `iptables -vL`

---

### **16. Security and Best Practices**

Implement least privilege with default DROP policies
Allow only necessary services explicitly
Prevent IP spoofing and SYN flood attacks
Enable logging for auditing
Regularly review and update rules
Combine iptables with intrusion detection systems like fail2ban

---

### **17. Automation and Integration**

Automate rule creation using shell scripts
Integrate iptables with configuration management tools (Ansible, Puppet)
Use iptables with Docker or Kubernetes networking
Combine iptables with Firewalld or nftables transitions

---

### **18. Performance Optimization**

Order rules efficiently for faster processing
Reduce rule count with custom chains and grouping
Monitor CPU usage caused by large rule sets
Optimize connection tracking and timeouts

---

### **19. Migration to nftables**

Understand iptables-to-nftables compatibility
Compare syntax and capabilities
Migrate existing iptables rules to nftables for modern systems

---

### **20. Real-World Scenarios**

Secure a web server with input filtering rules
Set up NAT gateway for internal subnets
Implement port forwarding for internal services
Create multi-interface firewall policies
Log and block suspicious traffic in production environments

---

**list of hands-on exercises for iptables**

---

### **1. Getting Started with iptables**

Check if iptables is installed and running
View existing rules using `iptables -L -v -n`
Flush all rules and reset chains
Set default policies for INPUT, OUTPUT, and FORWARD chains
Save and restore a basic configuration

---

### **2. Basic Packet Filtering**

Allow SSH (port 22) access and test connectivity
Allow HTTP (port 80) and HTTPS (port 443) traffic
Block ICMP ping requests from a specific IP
Drop traffic from a specific subnet
Verify rules using `iptables -L -v -n` and `ping`

---

### **3. Managing Chains**

Create a custom chain named `LOGDROP`
Send specific traffic (e.g., SSH from a banned IP) to the custom chain
Log dropped packets with a prefix
Return packets from custom chain to main chain
Delete custom chains safely after testing

---

### **4. Connection Tracking**

Allow only established and related connections
Block invalid packets
Test connection tracking by starting new SSH sessions
Observe packet counters increment using `iptables -L -v`

---

### **5. Port and Protocol Filtering**

Allow traffic for specific TCP and UDP ports
Block unwanted TCP or UDP ports
Allow a range of ports for an application
Test access using `telnet`, `nc`, or `curl`
Verify filtering using `ss -tuln`

---

### **6. NAT (Network Address Translation)**

Set up SNAT for internal network access to the internet
Set up DNAT for port forwarding to a web server
Enable MASQUERADE for dynamic IP environments
Test NAT configuration using ping, curl, or accessing forwarded ports

---

### **7. Port Forwarding**

Forward external port 8080 to internal port 80
Redirect traffic from one port to another locally
Test port forwarding using a browser or `curl`
Remove and modify port forwarding rules

---

### **8. Advanced Match Modules**

Use `-m limit` to limit connection rate for SSH
Use `-m mac` to allow or block traffic by MAC address
Use `-m time` to allow traffic during specific hours
Combine multiple match modules in a single rule
Test rules by generating traffic that matches conditions

---

### **9. Logging and Monitoring**

Add LOG rules for dropped packets
View logs using `journalctl -f` or `/var/log/messages`
Rate-limit logging to avoid flooding
Analyze packet logs for auditing purposes
Create a separate logging chain for specific traffic

---

### **10. IPv6 Filtering (ip6tables)**

Allow specific IPv6 traffic (e.g., SSH, HTTP)
Block specific IPv6 addresses or subnets
Test IPv6 connectivity using `ping6` or `curl`
Integrate IPv6 rules alongside IPv4 rules for dual-stack setups

---

### **11. Troubleshooting**

Simulate connectivity issues and fix them using iptables
Use packet counters to verify rules are working
Capture packets with tcpdump to trace packet flow
Incrementally test complex rules for effectiveness
Debug startup or reload issues and restore defaults

---

### **12. Automation and Scripting**

Write a shell script to add multiple rules at once
Save and restore configuration using `iptables-save` and `iptables-restore`
Automate repetitive firewall setup for new servers
Test the script on a staging environment

---

### **13. Security Hardening Exercises**

Implement a default DROP policy and whitelist necessary services
Limit SSH access to specific IP addresses
Enable logging for suspicious traffic
Block IP spoofing attempts
Simulate attack traffic and verify firewall response

---

### **14. Real-World Project Labs**

Configure a web server with input filtering rules
Set up a NAT gateway for a private network
Implement port forwarding for internal services
Create firewall rules for a multi-interface router
Combine logging, NAT, and connection tracking in a single configuration
Document and verify rules with `iptables -L -v` and network tests

---

</details>


<details>
  <summary>NFTables</summary>
  
**list of topics in nftables**

---

### **1. Introduction to nftables**

Overview and purpose of nftables
Difference between iptables, nftables, and Firewalld
Architecture of nftables and its integration with Netfilter
Advantages over iptables: performance, simplicity, and flexibility
Understanding the nftables daemon and kernel interaction

---

### **2. nftables Concepts**

Tables, chains, and rules
Base families: `inet`, `ip`, `ip6`, `arp`, `bridge`
Types of chains: `input`, `output`, `forward`, `prerouting`, `postrouting`
Understanding chain hooks and priorities
Sets and maps for grouping addresses, ports, or protocols
Expressions, matches, and verdicts (accept, drop, reject, return)

---

### **3. Installation and Configuration Basics**

Installing nftables on Linux distributions
Starting, enabling, and checking the nftables service
Viewing active rulesets (`nft list ruleset`)
Adding, modifying, and deleting tables and chains
Saving and restoring nftables rules

---

### **4. Tables and Chains**

Creating tables for IPv4, IPv6, and inet families
Creating base and user-defined chains
Assigning hooks and priorities to chains
Understanding built-in chains versus custom chains
Flushing, deleting, and renaming tables and chains

---

### **5. Rules and Matching**

Basic rule syntax
Matching by protocol, source/destination IP
Matching by source/destination ports
Matching multiple conditions using logical operators
Negation and compound expressions
Packet classification using meta fields (`iif`, `oif`, `tcp flags`)

---

### **6. Sets and Maps**

Creating and managing sets for IP addresses, ports, or subnets
Using sets in rules for efficient filtering
Dynamic sets (adding/removing elements at runtime)
Maps for key-value matching in rules
Combining sets and maps with rules for scalable configuration

---

### **7. Connection Tracking**

Understanding connection states: `new`, `established`, `related`, `invalid`
Using the `ct` module for connection tracking
Filtering based on connection state
Integrating connection tracking with NAT rules
Logging connection states for auditing

---

### **8. NAT and Masquerading**

Configuring Source NAT (SNAT) for outgoing connections
Configuring Destination NAT (DNAT) and port forwarding
Enabling masquerading for dynamic IP addresses
Using `dnat` and `snat` in the `nat` table
Testing NAT and forwarding functionality

---

### **9. Logging and Monitoring**

Using `log` statements in rules
Configuring log prefixes and levels
Analyzing nftables logs using `journalctl` or syslog
Monitoring counters for rules, chains, and tables
Using `nft monitor` for real-time packet event monitoring

---

### **10. IPv6 Support**

Creating IPv6 tables, chains, and rules
Filtering IPv6 traffic alongside IPv4 using `inet` family
Allowing or blocking IPv6 services
Testing IPv6 connectivity and rule enforcement

---

### **11. Advanced Filtering**

Using concatenations and payload matching
Filtering by TCP flags, ICMP types, and packet metadata
Rate limiting and traffic policing with `limit` expression
Time-based rules using `time` expressions
Marking packets for policy routing or QoS using `mark`

---

### **12. Scripting and Automation**

Writing nftables configuration scripts
Loading rulesets at boot or via systemd
Backing up and restoring rulesets
Automating rule updates with shell or Python scripts
Using dynamic rules with `nft add element`

---

### **13. Troubleshooting and Debugging**

Checking ruleset counters and packet matches
Flushing and testing rules incrementally
Capturing packets with tcpdump or Wireshark for verification
Debugging NAT, forwarding, or filter issues
Resetting nftables to defaults safely

---

### **14. Performance and Optimization**

Optimizing rules using sets and maps
Ordering rules for faster packet processing
Minimizing redundant matches
Monitoring CPU and memory usage with large rule sets

---

### **15. Security and Best Practices**

Implementing default DROP policies
Allowing only required services and ports
Logging suspicious or dropped traffic
Regular auditing of rulesets
Combining nftables with intrusion detection systems

---

### **16. Integration with System Components**

Using nftables with Firewalld
Integration with NetworkManager for dynamic interfaces
Working with Docker or container networking
Combining nftables with SELinux or AppArmor policies

---

### **17. Real-World Scenarios**

Setting up a secure web server firewall
Configuring NAT gateway for internal network
Port forwarding for internal services
Multi-interface firewall configuration
Logging and monitoring suspicious traffic
Creating scalable, maintainable, and automated nftables rulesets

---

**comprehensive study checklist for nftables**

---

### **1. Introduction to nftables**

Understand the purpose of nftables in Linux
Learn the differences between nftables, iptables, and Firewalld
Study the Netfilter framework and kernel integration
Understand the advantages of nftables: performance, simplicity, and flexibility
Learn about the nftables daemon and its operation

---

### **2. nftables Concepts**

Understand tables, chains, and rules
Learn base families: `inet`, `ip`, `ip6`, `arp`, `bridge`
Understand built-in chains: `input`, `output`, `forward`, `prerouting`, `postrouting`
Learn about user-defined chains
Understand hooks, priorities, and rule evaluation order
Study sets, maps, and expressions for efficient rule management
Understand verdicts: `accept`, `drop`, `reject`, `return`

---

### **3. Installation and Service Management**

Install nftables on different Linux distributions
Start, enable, and check the nftables service
Verify active rulesets using `nft list ruleset`
Reload nftables rules without downtime

---

### **4. Tables and Chains**

Create tables for IPv4, IPv6, or inet family
Create base and custom chains
Assign hooks and priorities to chains
Flush and delete tables or chains safely
Understand chain types: `base` vs `user-defined`

---

### **5. Rules and Matching**

Understand rule syntax and components
Match by protocol (TCP, UDP, ICMP)
Match by source and destination IP addresses
Match by source and destination ports
Use logical operators and negation
Filter packets using metadata (`iif`, `oif`, `tcp flags`)

---

### **6. Sets and Maps**

Create and manage sets for IPs, ports, or subnets
Use sets in rules for efficient filtering
Add and remove elements dynamically
Create maps for key-value matching in rules
Combine sets and maps with rules for scalability

---

### **7. Connection Tracking**

Understand connection states: `new`, `established`, `related`, `invalid`
Use `ct` module for connection tracking
Filter based on connection state
Integrate connection tracking with NAT
Log connection states for auditing

---

### **8. NAT and Masquerading**

Configure Source NAT (SNAT)
Configure Destination NAT (DNAT) and port forwarding
Enable masquerading for dynamic IPs
Test NAT rules for outgoing and incoming traffic
Understand NAT in the `nat` table and relevant hooks

---

### **9. Logging and Monitoring**

Use `log` statements in rules
Configure log prefixes and severity
Monitor rule and chain counters
Use `nft monitor` for real-time packet events
Analyze logs using `journalctl` or syslog

---

### **10. IPv6 Filtering**

Create IPv6 tables, chains, and rules
Allow or block IPv6 services
Use `inet` family for dual-stack IPv4 and IPv6 rules
Test IPv6 connectivity using `ping6` or `curl`

---

### **11. Advanced Filtering**

Filter based on TCP flags, ICMP types, and metadata
Rate-limit traffic using `limit` expression
Create time-based rules using `time` expressions
Mark packets for QoS or policy routing using `mark`
Combine multiple match conditions for complex rules

---

### **12. Scripting and Automation**

Write nftables configuration scripts
Load rulesets automatically at boot
Backup and restore rulesets
Update rules dynamically using `nft add element`
Automate nftables setup using shell or Python scripts

---

### **13. Troubleshooting**

Check counters and packet matches for rules
Flush and test rules incrementally
Use tcpdump or Wireshark to verify traffic flow
Debug NAT, forwarding, and filter issues
Reset nftables rules safely for testing

---

### **14. Performance and Optimization**

Optimize rules using sets and maps
Order rules efficiently for faster processing
Minimize redundant matches
Monitor CPU and memory usage with large rulesets

---

### **15. Security and Best Practices**

Implement default DROP policies
Allow only necessary services and ports
Enable logging for auditing suspicious traffic
Regularly review and update rules
Integrate with intrusion detection systems

---

### **16. Integration with System Components**

Use nftables with Firewalld
Integrate with NetworkManager for dynamic interfaces
Use with Docker or containerized networking
Combine with SELinux or AppArmor for enhanced security

---

### **17. Real-World Scenarios**

Secure a public-facing web server
Build a NAT gateway for internal networks
Implement port forwarding to internal services
Create multi-interface firewall policies
Set up logging and monitoring for production environments
Design scalable, maintainable, and automated rulesets

---

**hands-on exercises for nftables**

---

### **1. Getting Started with nftables**

Check if nftables is installed and the service is running
List current rulesets with `nft list ruleset`
Start, enable, and reload the nftables service
Flush existing rules and reset tables
Create a simple table and chain, then add a basic accept rule

---

### **2. Tables and Chains**

Create IPv4 (`ip`), IPv6 (`ip6`), and `inet` tables
Add base chains for input, output, and forward with appropriate hooks
Create user-defined chains for logging or custom traffic handling
Assign priorities to chains and test the effect on packet flow
Delete chains and tables safely after testing

---

### **3. Basic Rules and Packet Filtering**

Add rules to allow SSH, HTTP, and HTTPS traffic
Block ICMP ping requests from a specific IP
Allow traffic from specific subnets
Drop all other traffic with a default DROP rule
Test rules using `ping`, `curl`, or `telnet`

---

### **4. Using Sets and Maps**

Create a set of allowed IP addresses
Use the set in rules to allow traffic only from those IPs
Dynamically add and remove IPs from the set
Create a map to match ports to specific actions
Test multiple IPs and ports with the sets and maps

---

### **5. Connection Tracking**

Filter traffic based on connection states: `new`, `established`, `related`, `invalid`
Allow only established and related connections while dropping new ones
Block invalid packets
Monitor connection counters using `nft list ruleset`

---

### **6. NAT and Masquerading**

Create a `nat` table with PREROUTING and POSTROUTING chains
Set up SNAT for outbound connections from a private network
Set up DNAT and port forwarding to an internal web server
Enable MASQUERADE for dynamic IP addresses
Test NAT functionality using ping, curl, or access to forwarded services

---

### **7. Logging and Monitoring**

Add log statements to specific rules with a custom prefix
Rate-limit logging to prevent flooding
Use `nft monitor` to observe packets in real time
Analyze logs using `journalctl` or `/var/log/messages`

---

### **8. IPv6 Filtering**

Create IPv6-specific tables and chains
Allow or block SSH, HTTP, and ICMPv6 traffic
Test IPv6 connectivity with `ping6` and `curl`
Combine IPv4 and IPv6 rules in a single `inet` table

---

### **9. Advanced Filtering**

Match packets based on TCP flags, ICMP types, or interface
Create time-based rules using `time` expressions
Mark packets for policy routing or QoS using `mark`
Rate-limit connections using the `limit` expression
Combine multiple match conditions for complex filtering scenarios

---

### **10. Custom Chains for Logging and Security**

Create custom chains for logging dropped packets
Send traffic from main chains to custom chains for logging or auditing
Return packets from custom chains after processing
Test and remove custom chains safely

---

### **11. Scripting and Automation**

Write an nftables configuration script to create tables, chains, and rules
Load the script automatically at boot
Backup and restore rulesets using `nft list ruleset > rules.nft` and `nft -f rules.nft`
Dynamically add or remove elements from sets in a script

---

### **12. Troubleshooting**

Use `nft list ruleset` to verify counters and packet hits
Flush rules incrementally to isolate issues
Use `tcpdump` or `wireshark` to verify packet flow
Test NAT, forwarding, and filter rules step-by-step
Reset rules safely to test different scenarios

---

### **13. Security Hardening**

Implement a default DROP policy for all chains
Allow only required services and ports
Enable logging for suspicious or dropped packets
Simulate unwanted traffic and verify rule enforcement
Test and refine firewall rules to harden the system

---

### **14. Real-World Project Labs**

Build a secure web server firewall with input filtering
Configure a NAT gateway for internal subnets
Set up port forwarding to internal application servers
Implement logging and monitoring for production traffic
Combine IPv4 and IPv6 rules in an `inet` table
Automate the configuration and maintain a backup of the ruleset

---

</details>

<details>
  <summary>UFW</summary>
  
**list of topics in UFW (Uncomplicated Firewall) administration**

---

### **1. Introduction to UFW**

Overview and purpose of UFW in Linux
Difference between UFW and iptables/nftables
Understanding UFW as a front-end for iptables
Advantages of UFW: simplicity and ease of use
Use cases in desktop and server environments

---

### **2. Installation and Service Management**

Installing UFW on different Linux distributions
Starting, enabling, disabling, and restarting the UFW service
Checking the status of UFW (`ufw status`)
Understanding runtime vs persistent configurations

---

### **3. Basic UFW Commands**

Enable and disable UFW
Check status in verbose and numbered formats
Reset UFW to default settings
Reload UFW to apply changes
View default policies and configured rules

---

### **4. Default Policies**

Set default incoming, outgoing, and forwarded policies
Understanding the difference between ACCEPT, DENY, and REJECT
Apply default policies for security hardening
Verify effective default rules

---

### **5. Managing Rules**

Allow or deny specific ports or services
Allow or deny traffic from specific IP addresses or subnets
Allow or deny TCP/UDP traffic specifically
Delete or modify existing rules
Use numbered rules for management

---

### **6. Application and Service Profiles**

Understanding UFW application profiles
Listing available application profiles
Allow or deny services by application name
Create custom application profiles
Test application profile rules

---

### **7. Advanced Rule Management**

Allow or deny connections from a range of IP addresses
Allow or deny traffic on specific network interfaces
Limit connections per IP using rate limiting
Allow or deny traffic from specific ports with TCP/UDP protocol specification
Combine multiple criteria in a single rule

---

### **8. Logging and Monitoring**

Enable UFW logging and configure log levels (low, medium, high, full)
View logs in `/var/log/ufw.log` or via `journalctl`
Analyze logged events for allowed and denied traffic
Use logging to troubleshoot connectivity issues

---

### **9. IPv6 Support**

Enable or disable IPv6 in UFW configuration
Allow or deny IPv6 traffic using rules
Test IPv6 connectivity and rule enforcement
Combine IPv4 and IPv6 rules for dual-stack systems

---

### **10. Integration with Network Services**

Configure UFW for SSH, HTTP, HTTPS, and other common services
Test service accessibility after rule changes
Use UFW with VPNs and internal network segments
Ensure UFW does not block essential network management services

---

### **11. Resetting and Recovery**

Reset UFW rules to default state
Disable UFW temporarily for troubleshooting
Recover previous configurations from backups
Test recovery and reload procedures

---

### **12. Automation and Scripting**

Automate UFW rule setup via shell scripts
Integrate UFW configuration in server provisioning scripts
Use custom scripts to apply rules across multiple servers

---

### **13. Security and Best Practices**

Use default deny policy for incoming traffic
Allow only required services and ports
Enable logging to monitor suspicious activity
Regularly audit UFW rules
Integrate UFW with intrusion detection tools

---

### **14. Real-World Scenarios**

Configure a web server firewall allowing HTTP, HTTPS, and SSH only
Limit SSH access to specific IPs and rate-limit connections
Set up rules for internal networks and VPNs
Enable logging and monitoring for production servers
Create reusable UFW configurations for multiple servers

---

**comprehensive study checklist for UFW**

---

### **1. Introduction to UFW**

Understand the purpose of UFW in Linux
Learn differences between UFW, iptables, and nftables
Understand UFW as a front-end to iptables
Study the advantages of UFW: simplicity and ease of use
Identify use cases for desktops, servers, and small networks

---

### **2. Installation and Service Management**

Install UFW on different Linux distributions
Start, enable, disable, and restart the UFW service
Check UFW status using `ufw status` and `ufw status verbose`
Understand the difference between runtime and persistent configurations

---

### **3. Basic Commands**

Enable and disable UFW
Check current status and active rules
Reset UFW to default settings
Reload UFW to apply new rules
View default policies and configured rules

---

### **4. Default Policies**

Set default incoming, outgoing, and forwarding policies
Understand ACCEPT, DENY, and REJECT policies
Apply default policies for security hardening
Verify effective default policies using `ufw status verbose`

---

### **5. Managing Rules**

Allow or deny specific ports or services
Allow or deny connections from specific IP addresses or subnets
Allow or deny TCP and UDP traffic
Delete, modify, and reorder rules
Use numbered rules for easier management

---

### **6. Application and Service Profiles**

Understand UFW application profiles
List available profiles using `ufw app list`
Allow or deny services by application name
Create custom application profiles in `/etc/ufw/applications.d/`
Test application profile rules for effectiveness

---

### **7. Advanced Rule Management**

Allow or deny traffic from IP ranges
Allow or deny traffic on specific network interfaces
Rate-limit connections per IP to prevent brute-force attacks
Combine multiple criteria in a single rule (port, protocol, IP, interface)
Verify complex rules using `ufw status numbered`

---

### **8. Logging and Monitoring**

Enable UFW logging and configure log levels (low, medium, high, full)
View logs in `/var/log/ufw.log` or via `journalctl`
Analyze allowed and denied traffic
Use logging to troubleshoot connectivity issues

---

### **9. IPv6 Support**

Enable or disable IPv6 in UFW configuration
Allow or deny IPv6 traffic using UFW rules
Test IPv6 connectivity and rule enforcement
Combine IPv4 and IPv6 rules in dual-stack environments

---

### **10. Integration with Network Services**

Configure UFW for SSH, HTTP, HTTPS, FTP, and other common services
Test service accessibility after rule changes
Use UFW with VPNs and internal networks
Ensure UFW does not block essential management or monitoring services

---

### **11. Resetting and Recovery**

Reset UFW rules to default state safely
Disable UFW temporarily for troubleshooting
Recover previous configurations from backups
Test recovery and reload procedures

---

### **12. Automation and Scripting**

Automate UFW setup using shell scripts
Integrate UFW rule configuration in server provisioning scripts
Create reusable scripts to deploy UFW rules across multiple servers

---

### **13. Security and Best Practices**

Implement default deny policy for incoming traffic
Allow only required services and ports
Enable logging for suspicious activity
Regularly audit and review UFW rules
Integrate UFW with intrusion detection or brute-force prevention tools

---

### **14. Real-World Scenarios**

Configure a web server firewall allowing HTTP, HTTPS, and SSH only
Limit SSH access to specific IPs and implement rate limiting
Set up rules for internal networks and VPN access
Enable logging and monitoring for production environments
Create reusable UFW configurations for multiple servers
Test firewall rules under simulated attack scenarios for validation

---

**list of hands-on exercises for UFW**

---

### **1. Getting Started with UFW**

Check if UFW is installed and the service is running
Enable UFW and verify its status (`ufw enable`, `ufw status`)
Disable UFW and reset rules to default (`ufw disable`, `ufw reset`)
View UFW version and configuration files

---

### **2. Basic Rules and Policies**

Set default policies for incoming and outgoing traffic (`ufw default deny incoming`, `ufw default allow outgoing`)
Allow SSH connections on port 22 and test connectivity
Allow HTTP (port 80) and HTTPS (port 443) traffic
Deny a specific port and verify using `telnet` or `nc`
Check the status of rules in verbose mode (`ufw status verbose`)

---

### **3. Managing IP Addresses and Subnets**

Allow traffic from a specific IP address and test access
Deny traffic from a specific IP or subnet
Allow traffic from a range of IPs using CIDR notation
Remove or modify rules for specific IPs
Verify applied rules and counters

---

### **4. Using Application Profiles**

List available application profiles (`ufw app list`)
Allow a service by application name (e.g., `ufw allow OpenSSH`)
Deny a service by application name
Create a custom application profile in `/etc/ufw/applications.d/`
Test custom profile rules for connectivity

---

### **5. Advanced Rule Management**

Allow or deny traffic on a specific network interface (`ufw allow in on eth0 to any port 80`)
Rate-limit SSH to prevent brute-force attacks (`ufw limit ssh`)
Combine multiple criteria in a single rule (IP + port + interface)
Use numbered rules for easier management (`ufw status numbered`)
Delete or modify numbered rules

---

### **6. Logging and Monitoring**

Enable UFW logging (`ufw logging on`)
Configure log levels (low, medium, high, full)
View logs in `/var/log/ufw.log` or with `journalctl -f`
Analyze allowed and denied traffic
Test logging by generating allowed and blocked traffic

---

### **7. IPv6 Configuration**

Enable or disable IPv6 in UFW configuration (`/etc/default/ufw`)
Allow or deny IPv6 traffic for specific services
Test IPv6 connectivity with `ping6` or `curl -6`
Combine IPv4 and IPv6 rules for dual-stack systems

---

### **8. Resetting and Recovery**

Reset all UFW rules to default and test connectivity
Temporarily disable UFW for troubleshooting
Restore rules from a backup file
Reload UFW after changes to ensure correct application

---

### **9. Automation and Scripting**

Write a shell script to apply multiple rules automatically
Automate UFW configuration during server provisioning
Test script across multiple servers or virtual machines
Add dynamic rule updates using scripts

---

### **10. Security Hardening**

Implement a default deny policy for incoming traffic
Allow only required services and ports
Enable logging for suspicious activity
Simulate unauthorized connection attempts and verify rules
Audit UFW rules regularly for compliance

---

### **11. Real-World Scenario Labs**

Set up a secure web server allowing only SSH, HTTP, and HTTPS
Limit SSH access to specific IP addresses
Enable rate-limiting for SSH to prevent brute-force attacks
Configure UFW for VPN traffic and internal network access
Enable logging and verify allowed and denied traffic
Document firewall rules and simulate rule changes for testing

---

</details>

<details>
  <summary>Monitoring & Performance Tuning</summary>

**list of topics in system monitoring and performance tuning**

---

### **1. Introduction to System Monitoring**

Purpose and importance of system monitoring
Overview of Linux performance metrics
Monitoring CPU, memory, disk, and network resources
Understanding system bottlenecks and performance issues
Differences between real-time monitoring and historical analysis

---

### **2. CPU Monitoring and Tuning**

Understanding CPU utilization and load averages
Using `top`, `htop`, `mpstat`, `vmstat`, and `sar` for CPU monitoring
Identifying CPU-bound processes
Processor affinity and CPU pinning
Tuning CPU scheduler parameters
Using `nice`, `renice`, and `taskset` for process priority and affinity

---

### **3. Memory Monitoring and Optimization**

Monitoring memory usage with `free`, `vmstat`, `smem`, and `top`
Understanding RAM, swap, cache, and buffers
Detecting memory leaks and high memory consumption
Tuning `swappiness` and other kernel memory parameters
Using `ulimit` to control resource limits per process
Optimizing application memory usage

---

### **4. Disk and Storage Monitoring**

Monitoring disk usage with `df`, `du`, and `lsblk`
Monitoring I/O performance using `iostat`, `iotop`, and `dstat`
Identifying I/O bottlenecks and heavy processes
Tuning I/O scheduler and block device parameters
Filesystem tuning and optimization (ext4, XFS, Btrfs)
Monitoring RAID and storage arrays

---

### **5. Network Monitoring and Tuning**

Monitoring network interfaces and traffic with `ifconfig`, `ip`, `netstat`, `ss`, and `nload`
Advanced network monitoring using `tcpdump`, `iftop`, `iperf`, `bmon`
Identifying network bottlenecks and latency issues
Tuning TCP/IP parameters (e.g., `sysctl` network settings)
Optimizing network buffers and socket settings
Monitoring firewall and packet filtering performance

---

### **6. Process and System Load Monitoring**

Monitoring processes using `ps`, `top`, `htop`, and `pgrep`
Tracking process resource usage (CPU, memory, I/O)
Analyzing load averages and system performance trends
Detecting zombie and defunct processes
Using `systemd-cgtop` for cgroup-based resource monitoring

---

### **7. Logging and Auditing**

Monitoring system logs using `journalctl`, `dmesg`, and `/var/log/`
Centralized logging with `rsyslog` or `syslog-ng`
Auditing performance events with `auditd`
Analyzing logs to detect performance degradation or failures

---

### **8. Performance Analysis Tools**

Using `perf`, `strace`, `ltrace`, and `blktrace` for detailed analysis
Using `sar` and `sysstat` utilities for historical performance data
Profiling applications for CPU, memory, and I/O usage
Using `vmstat`, `dstat`, and `iostat` for system-wide metrics

---

### **9. Resource Management and Limits**

Configuring `ulimit` and shell resource limits
Using `cgroups` for process resource control
Container-based resource management (Docker, LXC)
Controlling CPU, memory, I/O, and network resources per service

---

### **10. Kernel Tuning**

Tuning kernel parameters via `/proc` and `sysctl`
Adjusting network, I/O, and memory settings for performance
Configuring hugepages and NUMA for optimized workloads
Kernel tuning for high-performance computing and database servers

---

### **11. Monitoring High Availability and Critical Services**

Monitoring daemon and service performance
Using `systemctl status` and `systemd-analyze`
Setting up alerting for service failures
Monitoring cluster and HA setup metrics

---

### **12. Benchmarking and Stress Testing**

CPU benchmarking using `stress`, `stress-ng`, and `sysbench`
Memory stress testing
Disk I/O benchmarking with `fio` or `dd`
Network stress testing and throughput measurement

---

### **13. Historical and Real-Time Monitoring Solutions**

Using `Nagios`, `Zabbix`, `Prometheus`, `Grafana`, and `Netdata`
Collecting, storing, and visualizing metrics
Alerting and threshold-based monitoring
Comparing real-time vs historical data for performance tuning

---

### **14. Performance Tuning Best Practices**

Identifying and eliminating bottlenecks
Prioritizing critical services
Balancing system load across CPU, memory, I/O, and network
Documenting system performance and tuning changes
Regular auditing and monitoring schedules

---

**comprehensive study checklist**

---

### **1. Introduction to System Monitoring**

Understand the purpose and importance of system monitoring
Learn Linux performance metrics and their significance
Differentiate between real-time monitoring and historical analysis
Identify common performance bottlenecks (CPU, memory, I/O, network)

---

### **2. CPU Monitoring and Tuning**

Understand CPU utilization and load averages
Monitor CPU using `top`, `htop`, `mpstat`, `vmstat`, `sar`
Identify CPU-bound processes and bottlenecks
Learn CPU affinity and process pinning using `taskset`
Use `nice` and `renice` to adjust process priorities
Tuning CPU scheduler parameters for performance

---

### **3. Memory Monitoring and Optimization**

Monitor memory usage using `free`, `vmstat`, `smem`, `top`
Understand RAM, swap, cache, and buffer behavior
Detect memory leaks and high memory-consuming processes
Tune `swappiness` and kernel memory parameters
Use `ulimit` to control process resource limits
Optimize application memory usage for efficiency

---

### **4. Disk and Storage Monitoring**

Monitor disk usage using `df`, `du`, and `lsblk`
Monitor I/O performance with `iostat`, `iotop`, `dstat`
Identify I/O bottlenecks and heavy disk users
Tune I/O scheduler and block device parameters
Perform filesystem tuning and optimization (ext4, XFS, Btrfs)
Monitor RAID and storage array performance

---

### **5. Network Monitoring and Tuning**

Monitor interfaces and traffic using `ifconfig`, `ip`, `netstat`, `ss`, `nload`
Advanced network monitoring using `tcpdump`, `iftop`, `iperf`, `bmon`
Identify network bottlenecks and latency issues
Tune TCP/IP parameters via `sysctl`
Optimize network buffers and socket settings
Monitor firewall and packet filtering performance

---

### **6. Process and System Load Monitoring**

Monitor processes using `ps`, `top`, `htop`, `pgrep`
Track CPU, memory, and I/O usage per process
Analyze load averages and system performance trends
Detect zombie and defunct processes
Use `systemd-cgtop` for cgroup-based resource monitoring

---

### **7. Logging and Auditing**

Monitor system logs using `journalctl`, `dmesg`, and `/var/log/`
Set up centralized logging using `rsyslog` or `syslog-ng`
Audit performance events using `auditd`
Analyze logs to detect performance degradation

---

### **8. Performance Analysis Tools**

Use `perf`, `strace`, `ltrace`, `blktrace` for detailed analysis
Use `sar` and `sysstat` for historical performance data
Profile applications for CPU, memory, and I/O usage
Use `vmstat`, `dstat`, and `iostat` for system-wide metrics

---

### **9. Resource Management and Limits**

Configure `ulimit` and shell resource limits
Use `cgroups` to manage process resource allocation
Container-based resource management (Docker, LXC)
Control CPU, memory, I/O, and network usage per service

---

### **10. Kernel Tuning**

Tune kernel parameters via `/proc` and `sysctl`
Adjust network, I/O, and memory kernel settings
Configure hugepages and NUMA for optimized workloads
Tuning kernel for high-performance applications and databases

---

### **11. Monitoring High Availability and Critical Services**

Monitor daemons and system services
Use `systemctl status` and `systemd-analyze`
Set up alerting for service failures
Monitor cluster and HA setup performance metrics

---

### **12. Benchmarking and Stress Testing**

CPU benchmarking using `stress`, `stress-ng`, and `sysbench`
Memory stress testing and leak detection
Disk I/O benchmarking using `fio` or `dd`
Network throughput testing using `iperf`

---

### **13. Historical and Real-Time Monitoring Solutions**

Set up monitoring tools like Nagios, Zabbix, Prometheus, Grafana, or Netdata
Collect, store, and visualize metrics
Set up alerting and thresholds for critical resources
Compare real-time and historical data for trend analysis

---

### **14. Performance Tuning Best Practices**

Identify and eliminate system bottlenecks
Balance system load across CPU, memory, I/O, and network
Prioritize critical services
Document system performance and tuning adjustments
Regularly audit, monitor, and refine performance settings

---

Here’s a **list of hands-on exercises**

---

### **1. Getting Started with System Monitoring**

Check system uptime and load averages using `uptime`
View system information using `uname -a`, `hostnamectl`
Monitor current users and sessions using `who` and `w`
Display detailed system information using `lsb_release -a`, `dmidecode`

---

### **2. CPU Monitoring and Tuning**

Monitor CPU usage with `top` and `htop`
View per-CPU utilization using `mpstat -P ALL`
Check system-wide CPU statistics using `vmstat 2 5`
Identify CPU-bound processes using `ps aux --sort=-%cpu`
Change process priority with `nice` and `renice`
Pin a process to a specific CPU using `taskset`

---

### **3. Memory Monitoring and Optimization**

Check memory and swap usage using `free -h`
Monitor memory usage per process using `smem` or `top`
Analyze cache and buffer usage using `vmstat`
Check for memory leaks in processes using `pmap`
Adjust system swappiness with `sysctl vm.swappiness=10`
Set per-process memory limits using `ulimit -m` or `ulimit -v`

---

### **4. Disk and Storage Monitoring**

Check disk usage with `df -h` and `du -sh /path`
Monitor disk I/O using `iostat -x 2 5`
View real-time I/O by process with `iotop`
Check block device details using `lsblk` and `blkid`
Benchmark disk performance using `dd` or `fio`
Tune I/O scheduler for performance (`noop`, `deadline`, `cfq`)

---

### **5. Network Monitoring and Tuning**

Check network interfaces with `ifconfig` or `ip a`
Monitor open ports and sockets using `netstat -tulnp` or `ss -tulnp`
Monitor real-time traffic using `iftop`, `nload`, or `bmon`
Capture network packets with `tcpdump`
Test network throughput using `iperf`
Tune TCP/IP parameters via `sysctl` (`net.core.somaxconn`, `tcp_fin_timeout`)

---

### **6. Process and System Load Monitoring**

List all processes using `ps aux`
Monitor system load and process activity with `top` and `htop`
Check zombie and defunct processes using `ps -ef | grep defunct`
Use `systemd-cgtop` to monitor cgroup resource usage
Trace system calls for a process using `strace`

---

### **7. Logging and Auditing**

View kernel and system logs with `dmesg`
Monitor journal logs in real-time using `journalctl -f`
Audit system events using `auditctl` and `ausearch`
Analyze logs for performance issues or failures

---

### **8. Performance Analysis Tools**

Profile CPU usage with `perf top` or `perf record`
Trace function calls with `strace` and `ltrace`
Monitor disk and I/O activity with `blktrace`
Collect historical system statistics using `sar` from `sysstat` package

---

### **9. Resource Management**

Limit CPU usage for processes using `cpulimit`
Manage resources with cgroups (`systemd-run --scope -p MemoryMax=500M`)
Set process limits using `ulimit`
Control container resources in Docker or LXC environments

---

### **10. Kernel Tuning**

View and modify kernel parameters using `sysctl -a`
Adjust memory, network, and I/O kernel parameters for performance
Configure hugepages for memory-intensive applications
Tune NUMA settings for multi-socket systems

---

### **11. Benchmarking and Stress Testing**

Stress CPU with `stress-ng --cpu 4 --timeout 60s`
Stress memory using `stress-ng --vm 2 --vm-bytes 1G --timeout 60s`
Perform disk I/O benchmarking with `fio` or `dd`
Test network throughput and latency with `iperf3`

---

### **12. Historical and Real-Time Monitoring Solutions**

Install and configure Netdata for real-time metrics
Set up Prometheus and Grafana for monitoring and visualization
Configure alerting for CPU, memory, disk, and network thresholds
Collect and analyze historical data using `sar` or `sysstat`

---

### **13. Performance Tuning Best Practices**

Identify and remove bottlenecks in CPU, memory, disk, and network
Balance load across CPU cores and memory usage
Optimize I/O scheduler and network stack parameters
Document tuning changes and test system stability
Implement continuous monitoring for proactive performance management

---

</details>

<details>
  <summary>MariaDB</summary>

**list of topics in MariaDB administration**

---

### **1. Introduction to MariaDB**

Overview of MariaDB and its features
Differences between MariaDB and MySQL
Understanding the architecture of MariaDB
Use cases and advantages in Linux environments

---

### **2. Installation and Configuration**

Installing MariaDB on different Linux distributions (RHEL, CentOS, Ubuntu, Debian)
Initializing MariaDB database
Starting, stopping, and enabling MariaDB service (`systemctl`)
Understanding configuration files (`/etc/my.cnf`, `/etc/mysql/mariadb.conf.d/`)
Basic configuration tuning (port, data directory, buffer sizes)

---

### **3. User and Privilege Management**

Creating, modifying, and deleting database users
Granting and revoking privileges
Understanding privilege types: global, database, table, column, and routines
Using `GRANT`, `REVOKE`, and `SHOW GRANTS`
Securing root user and remote access

---

### **4. Database and Table Management**

Creating, modifying, and dropping databases
Creating and altering tables (data types, constraints, indexes)
Understanding storage engines: InnoDB, Aria, MyISAM
Working with views, triggers, and stored procedures
Managing sequences and auto-increment fields

---

### **5. Data Manipulation**

Inserting, updating, and deleting records
Selecting data with filters, joins, and aggregations
Using transactions: `START TRANSACTION`, `COMMIT`, `ROLLBACK`
Understanding ACID properties and isolation levels
Using prepared statements and parameterized queries

---

### **6. Backup and Recovery**

Performing full and incremental backups with `mysqldump` and `mariabackup`
Restoring databases from backups
Automating backup schedules using cron jobs
Understanding point-in-time recovery (PITR)

---

### **7. Performance Tuning**

Monitoring query performance with `EXPLAIN` and `ANALYZE`
Optimizing indexes for faster queries
Configuring cache settings: query cache, InnoDB buffer pool
Understanding slow query logs and profiling queries
Tuning server variables for CPU, memory, and I/O efficiency

---

### **8. Replication and High Availability**

Setting up master-slave replication
Understanding GTID-based replication
Monitoring replication status with `SHOW SLAVE STATUS`
Configuring multi-source replication and failover
Introduction to Galera Cluster for synchronous multi-master replication

---

### **9. Security and Auditing**

Enabling SSL/TLS for encrypted connections
Configuring firewall rules for MariaDB ports
Auditing database activity using MariaDB Audit Plugin
Hardening MariaDB by disabling remote root login and unnecessary plugins

---

### **10. Monitoring and Maintenance**

Monitoring server status using `SHOW STATUS` and `SHOW PROCESSLIST`
Checking database health and table integrity
Using `mysqladmin` for diagnostics
Configuring alerting for performance thresholds
Cleaning up unused tables, indexes, and logs

---

### **11. Advanced Topics**

Partitioning large tables for performance
Full-text indexing and search optimization
Working with JSON and dynamic columns
Stored procedures, triggers, and events for automation
Understanding MariaDB Galera Cluster and high-availability setups

---

### **12. Integration and Tools**

Using MariaDB with PHP, Python, and Java applications
Connecting via command-line clients, GUI tools (phpMyAdmin, DBeaver)
Using monitoring tools: Percona Monitoring, Zabbix, Prometheus
Automating administrative tasks with scripts

---

**comprehensive study checklist**

---

### **1. Introduction to MariaDB**

Understand the purpose and advantages of MariaDB
Compare MariaDB with MySQL and other relational databases
Learn MariaDB architecture and components
Identify use cases and applications in Linux environments

---

### **2. Installation and Configuration**

Install MariaDB on different Linux distributions (RHEL, CentOS, Ubuntu, Debian)
Initialize the MariaDB database
Start, stop, enable, and check the service using `systemctl`
Understand main configuration files (`/etc/my.cnf`, `/etc/mysql/mariadb.conf.d/`)
Perform basic tuning: port, data directory, buffer sizes, character sets

---

### **3. User and Privilege Management**

Create, modify, and delete database users
Grant and revoke privileges at global, database, table, and column levels
Secure the root user and manage remote access
Use `GRANT`, `REVOKE`, and `SHOW GRANTS` commands
Implement best practices for database security

---

### **4. Database and Table Management**

Create, alter, and drop databases and tables
Understand and choose appropriate storage engines: InnoDB, Aria, MyISAM
Manage indexes, primary keys, foreign keys, and constraints
Work with views, triggers, stored procedures, and events
Handle auto-increment fields and sequences

---

### **5. Data Manipulation**

Insert, update, delete, and select data
Use filtering, joins, and aggregation in queries
Understand transactions, ACID properties, and isolation levels
Use `START TRANSACTION`, `COMMIT`, `ROLLBACK`
Work with prepared statements and parameterized queries

---

### **6. Backup and Recovery**

Perform full and incremental backups with `mysqldump` and `mariabackup`
Restore databases from backups
Automate backup schedules using cron jobs
Understand point-in-time recovery (PITR) procedures
Test backup integrity and recovery procedures

---

### **7. Performance Tuning**

Monitor query performance using `EXPLAIN` and `ANALYZE`
Optimize indexes and queries
Tune InnoDB buffer pool, query cache, and temporary tables
Enable and analyze slow query logs
Adjust server variables for CPU, memory, and I/O efficiency

---

### **8. Replication and High Availability**

Set up master-slave replication
Understand GTID-based replication
Monitor replication status using `SHOW SLAVE STATUS`
Configure multi-source replication and failover strategies
Learn the basics of Galera Cluster for synchronous multi-master replication

---

### **9. Security and Auditing**

Enable SSL/TLS for encrypted connections
Configure firewall rules for MariaDB ports
Audit database activity with MariaDB Audit Plugin
Harden MariaDB by disabling remote root login and unnecessary plugins
Follow best practices for secure database administration

---

### **10. Monitoring and Maintenance**

Check server status with `SHOW STATUS` and `SHOW PROCESSLIST`
Monitor database health and table integrity
Use `mysqladmin` and `mysqlcheck` for diagnostics
Set up monitoring and alerting for performance issues
Clean up unused tables, indexes, and logs

---

### **11. Advanced Topics**

Partition large tables for performance improvement
Implement full-text search and indexing
Work with JSON and dynamic columns
Automate tasks with stored procedures, triggers, and events
Understand Galera Cluster advanced configurations and high availability

---

### **12. Integration and Tools**

Connect MariaDB to PHP, Python, Java, and other applications
Use command-line clients and GUI tools (phpMyAdmin, DBeaver)
Monitor MariaDB with tools like Percona Monitoring, Zabbix, Prometheus
Automate administrative tasks using scripts and cron jobs

---

**list of hands-on exercises**

---

### **1. Installation and Service Management**

Install MariaDB on various Linux distributions (RHEL, CentOS, Ubuntu, Debian)
Start, stop, enable, and check the status of MariaDB service using `systemctl`
Verify installation using `mysql --version` and `mariadb --version`
Locate and understand main configuration files (`/etc/my.cnf`, `/etc/mysql/mariadb.conf.d/`)

---

### **2. Initial Configuration**

Secure MariaDB installation using `mysql_secure_installation`
Change the root password and remove anonymous users
Configure MariaDB to listen on local or remote interfaces
Set default storage engine and character set
Adjust basic configuration parameters (port, data directory, buffer sizes)

---

### **3. User and Privilege Management**

Create new users with specific privileges (`CREATE USER`)
Grant and revoke privileges at global, database, table, and column levels
Test user access for local and remote connections
Use `SHOW GRANTS` to verify privileges
Remove users and confirm revoked access

---

### **4. Database and Table Management**

Create and drop databases (`CREATE DATABASE`, `DROP DATABASE`)
Create, alter, and drop tables (`CREATE TABLE`, `ALTER TABLE`, `DROP TABLE`)
Add primary keys, foreign keys, indexes, and constraints
Create and manage views
Test stored procedures, triggers, and events

---

### **5. Data Manipulation**

Insert, update, delete, and select data (`INSERT`, `UPDATE`, `DELETE`, `SELECT`)
Use joins, aggregations, and subqueries
Implement transactions: `START TRANSACTION`, `COMMIT`, `ROLLBACK`
Test transaction isolation levels
Use prepared statements and parameterized queries

---

### **6. Backup and Recovery**

Perform full backups using `mysqldump`
Perform incremental backups using `mariabackup`
Restore databases from backups
Automate backups with cron jobs
Test point-in-time recovery (PITR) scenarios

---

### **7. Performance Tuning**

Analyze slow queries using slow query logs
Optimize queries using `EXPLAIN` and `ANALYZE`
Create and optimize indexes for frequently used queries
Tune InnoDB buffer pool, query cache, and temporary tables
Monitor resource usage with `SHOW STATUS` and `mysqladmin`

---

### **8. Replication and High Availability**

Set up master-slave replication
Monitor replication status using `SHOW SLAVE STATUS`
Configure multi-source replication
Test failover scenarios
Set up a basic Galera Cluster for synchronous multi-master replication

---

### **9. Security and Auditing**

Enable SSL/TLS for encrypted connections
Configure firewall rules for MariaDB ports (default 3306)
Audit user activity using MariaDB Audit Plugin
Remove unnecessary plugins and disable remote root login
Test access restrictions and encryption configuration

---

### **10. Monitoring and Maintenance**

Monitor running processes using `SHOW PROCESSLIST`
Check server status with `SHOW STATUS`
Use `mysqladmin` and `mysqlcheck` for diagnostics
Repair and optimize tables
Clean up unused tables, logs, and indexes

---

### **11. Advanced Features**

Partition large tables for performance
Create full-text indexes and test searches
Work with JSON columns and dynamic data types
Implement stored procedures, triggers, and events for automation
Test replication lag and cluster synchronization in Galera Cluster

---

### **12. Integration and Tools**

Connect MariaDB with PHP, Python, and Java applications
Use GUI tools such as phpMyAdmin, DBeaver, or HeidiSQL
Monitor MariaDB using Percona Monitoring Tools, Zabbix, or Prometheus
Write scripts to automate routine administrative tasks

---

</details>

<details>
  <summary>MySQL</summary>

**list of topics in MySQL administration**

---

### **1. Introduction to MySQL**

Overview of MySQL and its features
Differences between MySQL and MariaDB
Understanding MySQL architecture (server, storage engines, clients)
Use cases and advantages in Linux environments

---

### **2. Installation and Configuration**

Installing MySQL on Linux distributions (RHEL, CentOS, Ubuntu, Debian)
Initializing the MySQL data directory
Starting, stopping, and enabling the MySQL service (`systemctl`)
Understanding configuration files (`/etc/my.cnf`, `/etc/mysql/my.cnf`)
Basic tuning: port, data directory, buffer sizes, character set

---

### **3. User and Privilege Management**

Creating, modifying, and deleting MySQL users
Granting and revoking privileges at global, database, table, and column levels
Using `GRANT`, `REVOKE`, and `SHOW GRANTS`
Securing root user and managing remote access
Best practices for user authentication and password policies

---

### **4. Database and Table Management**

Creating, modifying, and dropping databases
Creating and altering tables (data types, constraints, indexes)
Understanding storage engines: InnoDB, MyISAM, MEMORY, etc.
Working with views, triggers, and stored procedures
Handling auto-increment columns and sequences

---

### **5. Data Manipulation**

Inserting, updating, deleting, and selecting data
Filtering data using `WHERE`, `LIKE`, `IN`, `BETWEEN`
Using joins, subqueries, and aggregations
Working with transactions (`START TRANSACTION`, `COMMIT`, `ROLLBACK`)
Understanding isolation levels and ACID properties
Prepared statements and parameterized queries

---

### **6. Backup and Recovery**

Performing full and incremental backups with `mysqldump` and `mysqlpump`
Restoring databases from backups
Automating backups with cron jobs
Using binary logs for point-in-time recovery (PITR)

---

### **7. Performance Tuning**

Monitoring query performance with `EXPLAIN` and `ANALYZE`
Using indexes for query optimization
Tuning InnoDB buffer pool, query cache, and temporary tables
Analyzing slow query logs
Adjusting server variables for CPU, memory, and I/O efficiency

---

### **8. Replication and High Availability**

Setting up master-slave replication
Monitoring replication using `SHOW SLAVE STATUS`
GTID-based replication
Multi-source replication setup
Introduction to MySQL Group Replication and Cluster for high availability

---

### **9. Security and Auditing**

Enabling SSL/TLS for encrypted connections
Configuring firewall rules for MySQL ports (default 3306)
Auditing user activity using MySQL Audit Plugin
Hardening MySQL by disabling remote root login and unused plugins
Implementing role-based access control

---

### **10. Monitoring and Maintenance**

Monitoring server status using `SHOW STATUS` and `SHOW PROCESSLIST`
Checking database health and table integrity
Using `mysqladmin` and `mysqlcheck` for diagnostics
Cleaning up unused tables, indexes, and logs
Setting up monitoring with Nagios, Zabbix, Prometheus, or Grafana

---

### **11. Advanced Features**

Partitioning large tables for performance
Using full-text indexes and search
Working with JSON data types
Stored procedures, triggers, and events for automation
Performance schema and profiling queries
High-performance replication setups and failover

---

### **12. Integration and Tools**

Connecting MySQL to PHP, Python, Java, and other applications
Using command-line clients and GUI tools (phpMyAdmin, DBeaver)
Monitoring MySQL with Percona Monitoring Tools
Automating routine administrative tasks using scripts

---

**comprehensive study checklist**

---

### **1. Introduction to MySQL**

Understand the purpose and advantages of MySQL
Learn differences between MySQL and MariaDB
Study MySQL architecture: server, storage engines, clients
Identify use cases for MySQL in Linux environments

---

### **2. Installation and Configuration**

Install MySQL on various Linux distributions (RHEL, CentOS, Ubuntu, Debian)
Initialize the MySQL database and data directory
Start, stop, enable, and check MySQL service status using `systemctl`
Understand main configuration files (`/etc/my.cnf`, `/etc/mysql/my.cnf`)
Perform basic tuning: port, data directory, buffer sizes, character set

---

### **3. User and Privilege Management**

Create, modify, and delete MySQL users
Grant and revoke privileges at global, database, table, and column levels
Use `GRANT`, `REVOKE`, and `SHOW GRANTS`
Secure root user and manage remote access
Implement best practices for authentication and password policies

---

### **4. Database and Table Management**

Create, modify, and drop databases
Create and alter tables: data types, constraints, indexes
Understand storage engines: InnoDB, MyISAM, MEMORY, etc.
Work with views, triggers, and stored procedures
Handle auto-increment columns and sequences

---

### **5. Data Manipulation**

Insert, update, delete, and select data
Use filtering (`WHERE`), joins, subqueries, and aggregations
Work with transactions (`START TRANSACTION`, `COMMIT`, `ROLLBACK`)
Understand isolation levels and ACID properties
Use prepared statements and parameterized queries

---

### **6. Backup and Recovery**

Perform full and incremental backups with `mysqldump` or `mysqlpump`
Restore databases from backups
Automate backups using cron jobs
Use binary logs for point-in-time recovery (PITR)
Test backup and restore procedures

---

### **7. Performance Tuning**

Monitor query performance using `EXPLAIN` and `ANALYZE`
Optimize queries using indexes
Tune InnoDB buffer pool, query cache, and temporary tables
Enable and analyze slow query logs
Adjust server variables for CPU, memory, and I/O efficiency

---

### **8. Replication and High Availability**

Set up master-slave replication
Monitor replication using `SHOW SLAVE STATUS`
Configure GTID-based replication
Set up multi-source replication
Understand MySQL Group Replication and Cluster for HA

---

### **9. Security and Auditing**

Enable SSL/TLS for encrypted connections
Configure firewall rules for MySQL ports
Audit user activity using MySQL Audit Plugin
Disable remote root login and unused plugins
Implement role-based access control and least privilege

---

### **10. Monitoring and Maintenance**

Monitor server status using `SHOW STATUS` and `SHOW PROCESSLIST`
Check database health and table integrity
Use `mysqladmin` and `mysqlcheck` for diagnostics
Clean up unused tables, indexes, and logs
Set up monitoring and alerting with Nagios, Zabbix, Prometheus, Grafana

---

### **11. Advanced Features**

Partition large tables for performance
Use full-text search and indexes
Work with JSON and dynamic columns
Implement stored procedures, triggers, and events for automation
Use Performance Schema for query profiling and monitoring
Plan and implement high-performance replication and failover

---

### **12. Integration and Tools**

Connect MySQL to PHP, Python, Java, and other applications
Use CLI clients and GUI tools like phpMyAdmin, DBeaver
Monitor MySQL with Percona Monitoring Tools or other monitoring solutions
Automate administrative tasks with scripts and cron jobs

---

**list of hands-on exercises**

---

### **1. Installation and Service Management**

Install MySQL on various Linux distributions (RHEL, CentOS, Ubuntu, Debian)
Start, stop, enable, and check the status of MySQL service (`systemctl`)
Verify installation using `mysql --version`
Locate and explore configuration files (`/etc/my.cnf`, `/etc/mysql/my.cnf`)

---

### **2. Initial Configuration**

Run `mysql_secure_installation` to secure the database
Set and verify the root password
Remove anonymous users and test remote root login restrictions
Configure MySQL to listen on local or remote interfaces
Modify basic configuration parameters (port, data directory, buffer sizes)

---

### **3. User and Privilege Management**

Create new users (`CREATE USER`) and assign passwords
Grant and revoke privileges at global, database, table, and column levels
Test user access for local and remote connections
View user privileges with `SHOW GRANTS`
Delete users and confirm revoked access

---

### **4. Database and Table Management**

Create, alter, and drop databases (`CREATE DATABASE`, `DROP DATABASE`)
Create, alter, and drop tables (`CREATE TABLE`, `ALTER TABLE`, `DROP TABLE`)
Add primary keys, foreign keys, indexes, and constraints
Create and test views
Create and execute stored procedures, triggers, and events

---

### **5. Data Manipulation**

Insert, update, delete, and select records (`INSERT`, `UPDATE`, `DELETE`, `SELECT`)
Use filtering (`WHERE`), joins, subqueries, and aggregations
Implement transactions with `START TRANSACTION`, `COMMIT`, and `ROLLBACK`
Test transaction isolation levels
Use prepared statements and parameterized queries

---

### **6. Backup and Recovery**

Perform full backups using `mysqldump` or `mysqlpump`
Perform incremental backups and restore using binary logs
Restore databases from backups
Automate backups using cron jobs
Test point-in-time recovery (PITR)

---

### **7. Performance Tuning**

Analyze queries using `EXPLAIN` and `ANALYZE`
Identify and optimize slow queries
Create and optimize indexes for frequently used queries
Tune InnoDB buffer pool, query cache, and temporary tables
Monitor resource usage with `SHOW STATUS` and `mysqladmin`

---

### **8. Replication and High Availability**

Set up master-slave replication
Monitor replication using `SHOW SLAVE STATUS`
Configure GTID-based replication
Set up multi-source replication
Test failover and failback scenarios
Set up a simple MySQL Group Replication or Cluster environment

---

### **9. Security and Auditing**

Enable SSL/TLS connections for MySQL
Test firewall access for MySQL ports (default 3306)
Audit user activity using MySQL Audit Plugin
Remove unnecessary plugins and restrict privileges
Test access restrictions and verify encryption settings

---

### **10. Monitoring and Maintenance**

Monitor active processes with `SHOW PROCESSLIST`
Check server status using `SHOW STATUS`
Use `mysqladmin` and `mysqlcheck` for diagnostics and repairs
Clean up unused tables, indexes, and logs
Implement basic monitoring and alerting

---

### **11. Advanced Features**

Partition large tables for better performance
Implement full-text search and indexing
Work with JSON columns and dynamic data
Test triggers, stored procedures, and events for automation
Analyze queries using Performance Schema
Simulate replication lag and monitor synchronization

---

### **12. Integration and Tools**

Connect MySQL to applications (PHP, Python, Java)
Use CLI clients and GUI tools (phpMyAdmin, DBeaver)
Monitor MySQL with Percona Monitoring Tools, Zabbix, or Prometheus
Automate routine tasks using shell scripts or cron jobs

---

</details>

<details>
  <summary>PostgreSQL</summary>

**list of topics in PostgreSQL administration**

---

### **1. Introduction to PostgreSQL**

Overview of PostgreSQL and its features
PostgreSQL architecture: server, databases, schemas, tablespaces
Comparison with other RDBMS like MySQL and MariaDB
Use cases and advantages of PostgreSQL in Linux environments

---

### **2. Installation and Configuration**

Installing PostgreSQL on various Linux distributions (RHEL, CentOS, Ubuntu, Debian)
Initializing a PostgreSQL cluster and data directory
Starting, stopping, enabling, and checking PostgreSQL service (`systemctl`)
Understanding configuration files (`postgresql.conf`, `pg_hba.conf`, `pg_ident.conf`)
Basic tuning: port, data directory, memory, and connection settings

---

### **3. User and Role Management**

Creating and managing roles and users (`CREATE ROLE`, `CREATE USER`)
Granting and revoking privileges (`GRANT`, `REVOKE`)
Managing superuser vs. regular user permissions
Role inheritance and membership
Securing administrative accounts

---

### **4. Database and Schema Management**

Creating and dropping databases (`CREATE DATABASE`, `DROP DATABASE`)
Managing schemas (`CREATE SCHEMA`, `ALTER SCHEMA`, `DROP SCHEMA`)
Understanding tablespaces and managing storage locations
Working with extensions (`CREATE EXTENSION`)
Managing objects: tables, indexes, views, sequences, and functions

---

### **5. Data Manipulation**

Inserting, updating, deleting, and selecting data (`INSERT`, `UPDATE`, `DELETE`, `SELECT`)
Using joins, subqueries, aggregates, and window functions
Transactions and isolation levels (`BEGIN`, `COMMIT`, `ROLLBACK`)
Prepared statements and parameterized queries
Working with JSON, arrays, and other advanced data types

---

### **6. Backup and Recovery**

Performing logical backups with `pg_dump` and `pg_dumpall`
Performing physical backups with `pg_basebackup`
Restoring databases from backups
Setting up continuous archiving and point-in-time recovery (PITR)
Automating backup procedures using cron jobs

---

### **7. Performance Tuning**

Monitoring queries using `EXPLAIN` and `ANALYZE`
Index management and optimization (B-tree, GIN, GiST, BRIN)
Tuning memory settings: shared_buffers, work_mem, maintenance_work_mem
Query and table optimization
Using autovacuum and statistics for performance

---

### **8. Replication and High Availability**

Setting up streaming replication (primary-standby)
Logical replication and publication/subscription
Monitoring replication status (`pg_stat_replication`)
Failover and switchover strategies
Introduction to high-availability tools like Patroni or PgBouncer

---

### **9. Security and Auditing**

Enabling SSL/TLS for encrypted connections
Configuring authentication methods in `pg_hba.conf` (md5, scram-sha-256, trust)
Role-based access control
Auditing using `pgAudit` or PostgreSQL logs
Restricting superuser access and securing sensitive data

---

### **10. Monitoring and Maintenance**

Monitoring server activity (`pg_stat_activity`, `pg_stat_database`)
Monitoring locks and long-running queries
Routine maintenance: `VACUUM`, `ANALYZE`, `REINDEX`
Checking database integrity and table health
Using `pgAdmin`, `psql`, or Prometheus/Grafana for monitoring

---

### **11. Advanced Features**

Partitioning large tables for performance
Full-text search
Stored procedures, triggers, and functions
Foreign data wrappers (FDW) for external data sources
Advanced indexing and query optimization

---

### **12. Integration and Tools**

Connecting PostgreSQL with applications (Python, PHP, Java, Node.js)
Using CLI tools (`psql`, `pg_dump`, `pg_restore`)
GUI tools like pgAdmin, DBeaver, DataGrip
Automation with scripts and cron jobs
Monitoring and alerting with Zabbix, Nagios, Prometheus, or Grafana

---

**comprehensive study checklist**

---

### **1. Introduction to PostgreSQL**

Understand the purpose and advantages of PostgreSQL
Learn PostgreSQL architecture: server, databases, schemas, tablespaces
Compare PostgreSQL with MySQL and MariaDB
Identify common use cases in Linux environments

---

### **2. Installation and Configuration**

Install PostgreSQL on different Linux distributions (RHEL, CentOS, Ubuntu, Debian)
Initialize a PostgreSQL cluster and data directory
Start, stop, enable, and check the service using `systemctl`
Understand configuration files (`postgresql.conf`, `pg_hba.conf`, `pg_ident.conf`)
Perform basic tuning: port, data directory, memory, connection settings

---

### **3. User and Role Management**

Create and manage roles and users (`CREATE ROLE`, `CREATE USER`)
Grant and revoke privileges (`GRANT`, `REVOKE`)
Understand superuser vs regular roles
Manage role inheritance and membership
Secure administrative accounts and enforce strong passwords

---

### **4. Database and Schema Management**

Create and drop databases (`CREATE DATABASE`, `DROP DATABASE`)
Manage schemas (`CREATE SCHEMA`, `ALTER SCHEMA`, `DROP SCHEMA`)
Understand and configure tablespaces
Use extensions (`CREATE EXTENSION`)
Manage database objects: tables, indexes, views, sequences, functions

---

### **5. Data Manipulation**

Insert, update, delete, and select data (`INSERT`, `UPDATE`, `DELETE`, `SELECT`)
Use joins, subqueries, aggregations, and window functions
Manage transactions and isolation levels (`BEGIN`, `COMMIT`, `ROLLBACK`)
Use prepared statements and parameterized queries
Work with JSON, arrays, and advanced data types

---

### **6. Backup and Recovery**

Perform logical backups with `pg_dump` and `pg_dumpall`
Perform physical backups with `pg_basebackup`
Restore databases from backups
Set up continuous archiving and point-in-time recovery (PITR)
Automate backup procedures using cron jobs

---

### **7. Performance Tuning**

Analyze queries using `EXPLAIN` and `ANALYZE`
Manage and optimize indexes (B-tree, GIN, GiST, BRIN)
Tune memory and configuration parameters: shared_buffers, work_mem, maintenance_work_mem
Use autovacuum and analyze for table maintenance
Optimize queries and tables for performance

---

### **8. Replication and High Availability**

Set up streaming replication (primary-standby)
Configure logical replication with publication and subscription
Monitor replication status (`pg_stat_replication`)
Implement failover and switchover strategies
Understand high-availability tools (Patroni, PgBouncer)

---

### **9. Security and Auditing**

Enable SSL/TLS for encrypted connections
Configure authentication methods in `pg_hba.conf` (md5, scram-sha-256, trust)
Implement role-based access control
Enable auditing using `pgAudit` or PostgreSQL logs
Secure superuser access and sensitive data

---

### **10. Monitoring and Maintenance**

Monitor server activity (`pg_stat_activity`, `pg_stat_database`)
Monitor locks, long-running queries, and resource usage
Perform routine maintenance: `VACUUM`, `ANALYZE`, `REINDEX`
Check database integrity and table health
Use monitoring tools: pgAdmin, Prometheus, Grafana, Zabbix

---

### **11. Advanced Features**

Partition large tables for performance
Implement full-text search
Create and manage stored procedures, triggers, and functions
Use foreign data wrappers (FDW) to access external data
Advanced indexing and query optimization techniques

---

### **12. Integration and Tools**

Connect PostgreSQL with applications (Python, PHP, Java, Node.js)
Use CLI tools (`psql`, `pg_dump`, `pg_restore`)
Use GUI tools: pgAdmin, DBeaver, DataGrip
Automate tasks with scripts and cron jobs
Set up monitoring and alerting with Zabbix, Nagios, Prometheus, Grafana

---

**list of hands-on exercises**

---

### **1. Installation and Service Management**

Install PostgreSQL on different Linux distributions (RHEL, CentOS, Ubuntu, Debian)
Initialize a PostgreSQL cluster and data directory
Start, stop, enable, and check PostgreSQL service status using `systemctl`
Verify installation using `psql --version`
Explore configuration files: `postgresql.conf`, `pg_hba.conf`, `pg_ident.conf`

---

### **2. Initial Configuration**

Secure the PostgreSQL installation
Change default ports and data directory settings
Configure authentication methods in `pg_hba.conf` (md5, scram-sha-256, trust)
Enable logging for queries and errors
Tune basic configuration parameters (memory, connection limits, max connections)

---

### **3. User and Role Management**

Create new roles and users (`CREATE ROLE`, `CREATE USER`)
Assign passwords and role attributes (superuser, login, inherit)
Grant and revoke privileges (`GRANT`, `REVOKE`)
Set role memberships and inheritance
Test access permissions for different users

---

### **4. Database and Schema Management**

Create and drop databases (`CREATE DATABASE`, `DROP DATABASE`)
Create and manage schemas (`CREATE SCHEMA`, `ALTER SCHEMA`, `DROP SCHEMA`)
Set tablespaces for databases and tables
Install and use extensions (`CREATE EXTENSION`)
Manage tables, indexes, sequences, views, functions, and triggers

---

### **5. Data Manipulation**

Insert, update, delete, and select records (`INSERT`, `UPDATE`, `DELETE`, `SELECT`)
Use filtering, joins, subqueries, aggregations, and window functions
Perform transactions (`BEGIN`, `COMMIT`, `ROLLBACK`)
Test transaction isolation levels
Use prepared statements and parameterized queries

---

### **6. Backup and Recovery**

Perform logical backups using `pg_dump` and `pg_dumpall`
Perform physical backups using `pg_basebackup`
Restore databases from logical and physical backups
Set up continuous archiving for point-in-time recovery (PITR)
Automate backups using cron jobs and test recovery

---

### **7. Performance Tuning**

Analyze queries using `EXPLAIN` and `ANALYZE`
Create and optimize indexes (B-tree, GIN, GiST, BRIN)
Tune memory and configuration parameters: `shared_buffers`, `work_mem`, `maintenance_work_mem`
Monitor autovacuum and table statistics
Optimize queries and table design for better performance

---

### **8. Replication and High Availability**

Set up streaming replication (primary-standby)
Monitor replication using `pg_stat_replication`
Configure logical replication (publication and subscription)
Simulate failover and test switchover
Set up a basic high-availability cluster using Patroni or PgBouncer

---

### **9. Security and Auditing**

Enable SSL/TLS connections
Configure role-based access control
Audit database activity using `pgAudit` or PostgreSQL logs
Restrict superuser access
Test user privileges and connection security

---

### **10. Monitoring and Maintenance**

Monitor active connections and queries (`pg_stat_activity`)
Monitor locks and long-running queries
Perform routine maintenance: `VACUUM`, `ANALYZE`, `REINDEX`
Check database health and table integrity
Use monitoring tools like `pgAdmin`, Prometheus, Grafana, or Zabbix

---

### **11. Advanced Features**

Partition large tables and test performance improvement
Implement full-text search queries
Create and test stored procedures, functions, and triggers
Use foreign data wrappers (FDW) to access external databases
Monitor query execution and optimize using Performance Schema

---

### **12. Integration and Tools**

Connect PostgreSQL to applications (Python, PHP, Java, Node.js)
Use CLI tools (`psql`, `pg_dump`, `pg_restore`)
Use GUI tools: pgAdmin, DBeaver, DataGrip
Automate administrative tasks with shell scripts and cron jobs
Set up monitoring and alerts with Prometheus, Grafana, or Zabbix

---

</details>

<details>
  <summary>MongoDB</summary>
  
**list of topics in MongoDB administration**

---

### **1. Introduction to MongoDB**

Overview of MongoDB and its features
Difference between relational and NoSQL databases
MongoDB architecture: server, databases, collections, documents
Use cases and advantages of MongoDB in Linux environments

---

### **2. Installation and Configuration**

Installing MongoDB on Linux (RHEL, CentOS, Ubuntu, Debian)
Starting, stopping, enabling, and checking the MongoDB service (`systemctl`)
Configuration files (`mongod.conf`) and parameters
Setting data directory, log paths, and network interfaces
Authentication and security configuration

---

### **3. Database and Collection Management**

Creating and dropping databases (`use <db>`, `db.dropDatabase()`)
Creating, modifying, and dropping collections (`db.createCollection()`, `db.collection.drop()`)
Working with capped collections
Understanding schema-less design and document structure

---

### **4. CRUD Operations**

Inserting documents (`insertOne()`, `insertMany()`)
Querying documents (`find()`, `findOne()`)
Updating documents (`updateOne()`, `updateMany()`, `replaceOne()`)
Deleting documents (`deleteOne()`, `deleteMany()`)
Working with embedded documents and arrays

---

### **5. Indexing and Performance Tuning**

Creating and managing indexes (`createIndex()`, `dropIndex()`)
Understanding compound and multikey indexes
Using TTL indexes for automatic document expiration
Query optimization using `explain()`
Monitoring performance metrics (`mongotop`, `mongostat`)

---

### **6. Aggregation and Data Processing**

Using aggregation framework (`$match`, `$group`, `$project`, `$sort`)
Pipeline operations for data transformation
MapReduce basics for large data processing
Working with text search and geospatial queries

---

### **7. User and Role Management**

Creating users (`db.createUser()`)
Assigning roles and privileges
Authentication mechanisms: SCRAM, x.509 certificates
Managing roles at database and cluster levels
Securing admin accounts

---

### **8. Backup and Recovery**

Performing backups using `mongodump` and `mongorestore`
Point-in-time backups using oplogs
Setting up automated backups
Restoring data to a new cluster or database
Testing backup integrity

---

### **9. Replication and High Availability**

Setting up replica sets
Primary, secondary, and arbiter roles
Monitoring replication status (`rs.status()`)
Handling failover and election processes
Read and write concerns in replication

---

### **10. Sharding and Scalability**

Understanding sharding concepts
Configuring shard keys and balancer
Setting up a sharded cluster
Monitoring and managing sharded data
Scaling out read and write operations

---

### **11. Security and Auditing**

Enabling authentication and authorization
Using SSL/TLS for encrypted connections
Role-based access control (RBAC)
Audit logging and monitoring access events
Securing MongoDB deployment against common attacks

---

### **12. Monitoring and Maintenance**

Monitoring server and database performance (`mongostat`, `mongotop`)
Checking logs and diagnosing issues
Index and database maintenance
Upgrading MongoDB versions safely
Automating routine maintenance tasks

---

### **13. Advanced Features**

Transactions in replica sets
Change streams for real-time data tracking
TTL collections for data expiration
Working with GridFS for large file storage
Integrating MongoDB with other applications and BI tools

---

**comprehensive study checklist**

---

### **1. Introduction to MongoDB**

Understand the purpose and advantages of MongoDB
Learn differences between relational and NoSQL databases
Study MongoDB architecture: server, databases, collections, documents
Identify use cases and scenarios for MongoDB in Linux environments

---

### **2. Installation and Configuration**

Install MongoDB on Linux distributions (RHEL, CentOS, Ubuntu, Debian)
Start, stop, enable, and check service status using `systemctl`
Understand configuration files (`mongod.conf`) and key parameters
Configure data directory, log paths, and network interfaces
Set up basic authentication and security settings

---

### **3. Database and Collection Management**

Create and drop databases (`use <db>`, `db.dropDatabase()`)
Create, modify, and drop collections (`db.createCollection()`, `db.collection.drop()`)
Work with capped collections
Understand schema-less design and document structure

---

### **4. CRUD Operations**

Insert documents (`insertOne()`, `insertMany()`)
Query documents (`find()`, `findOne()`)
Update documents (`updateOne()`, `updateMany()`, `replaceOne()`)
Delete documents (`deleteOne()`, `deleteMany()`)
Work with embedded documents and arrays

---

### **5. Indexing and Performance Tuning**

Create and manage indexes (`createIndex()`, `dropIndex()`)
Understand compound and multikey indexes
Use TTL indexes for automatic document expiration
Optimize queries using `explain()`
Monitor performance metrics using `mongotop` and `mongostat`

---

### **6. Aggregation and Data Processing**

Use aggregation framework (`$match`, `$group`, `$project`, `$sort`)
Build pipelines for data transformation
Understand MapReduce basics for large data processing
Work with text search and geospatial queries

---

### **7. User and Role Management**

Create users (`db.createUser()`)
Assign roles and privileges
Authentication mechanisms: SCRAM, x.509 certificates
Manage roles at database and cluster levels
Secure administrative accounts

---

### **8. Backup and Recovery**

Perform logical backups with `mongodump` and restore with `mongorestore`
Set up point-in-time backups using oplogs
Automate backup schedules
Restore data to new cluster or database
Test backup integrity

---

### **9. Replication and High Availability**

Configure replica sets
Understand primary, secondary, and arbiter roles
Monitor replication status (`rs.status()`)
Handle failover and election processes
Set read and write concerns in replication

---

### **10. Sharding and Scalability**

Understand sharding concepts
Configure shard keys and balancer
Set up a sharded cluster
Monitor and manage sharded data
Scale read and write operations efficiently

---

### **11. Security and Auditing**

Enable authentication and authorization
Configure SSL/TLS for encrypted connections
Implement role-based access control (RBAC)
Enable audit logging and monitor access events
Harden MongoDB deployment against common security threats

---

### **12. Monitoring and Maintenance**

Monitor server and database performance (`mongostat`, `mongotop`)
Check logs and diagnose issues
Maintain indexes and database objects
Perform routine maintenance and upgrades
Automate tasks using scripts and cron jobs

---

### **13. Advanced Features**

Use multi-document transactions in replica sets
Implement change streams for real-time tracking
Configure TTL collections for automatic data expiration
Work with GridFS for large file storage
Integrate MongoDB with applications and BI tools

---

**list of hands-on exercises**

---

### **1. Installation and Service Management**

* Install MongoDB on Linux distributions (RHEL, CentOS, Ubuntu, Debian)
* Start, stop, enable, and check MongoDB service status using `systemctl`
* Verify installation using `mongod --version` and `mongo --version`
* Explore and modify the configuration file (`/etc/mongod.conf`)

---

### **2. Initial Configuration**

* Configure MongoDB to use a custom data directory and log file path
* Enable authentication in `mongod.conf`
* Configure network interfaces and bind IP addresses
* Start MongoDB with the updated configuration

---

### **3. Database and Collection Management**

* Create and switch between databases (`use <db>`)
* Drop databases (`db.dropDatabase()`)
* Create collections (`db.createCollection()`)
* Drop collections (`db.collection.drop()`)
* Explore capped collections and document limits

---

### **4. CRUD Operations**

* Insert documents (`insertOne()`, `insertMany()`)
* Query documents (`find()`, `findOne()`) with filters, projections, and sorting
* Update documents (`updateOne()`, `updateMany()`, `replaceOne()`)
* Delete documents (`deleteOne()`, `deleteMany()`)
* Work with embedded documents and arrays

---

### **5. Indexing and Performance Tuning**

* Create single-field and compound indexes (`createIndex()`)
* Drop indexes (`dropIndex()`)
* Implement TTL (Time-To-Live) indexes
* Analyze queries using `explain()`
* Monitor database activity using `mongotop` and `mongostat`

---

### **6. Aggregation and Data Processing**

* Use the aggregation pipeline (`$match`, `$group`, `$project`, `$sort`)
* Perform data transformations and calculations
* Implement MapReduce jobs for large datasets
* Use text search and geospatial queries

---

### **7. User and Role Management**

* Create users with specific roles (`db.createUser()`)
* Grant and revoke roles and privileges
* Test authentication for different users
* Configure SCRAM and x.509 certificate authentication
* Secure administrative accounts

---

### **8. Backup and Recovery**

* Perform logical backups using `mongodump`
* Restore databases using `mongorestore`
* Set up point-in-time backups using oplogs
* Automate backup schedules with cron jobs
* Test restoration on a new cluster or environment

---

### **9. Replication and High Availability**

* Configure a replica set
* Add primary, secondary, and arbiter nodes
* Monitor replication status using `rs.status()`
* Simulate failover and test election processes
* Configure read and write concerns in replication

---

### **10. Sharding and Scalability**

* Enable sharding for a database
* Configure shard keys and shard collections
* Set up a sharded cluster with config servers and query routers
* Monitor sharded cluster performance
* Test scaling read and write operations

---

### **11. Security and Auditing**

* Enable authentication and authorization
* Enable SSL/TLS for encrypted connections
* Implement role-based access control (RBAC)
* Enable and review audit logs
* Test and verify user access restrictions

---

### **12. Monitoring and Maintenance**

* Monitor active queries and connections
* Monitor locks and long-running operations
* Perform maintenance: compact collections, repair database, rebuild indexes
* Review MongoDB logs for errors or warnings
* Automate routine monitoring tasks using scripts

---

### **13. Advanced Features**

* Implement multi-document transactions in a replica set
* Configure change streams to track real-time updates
* Use TTL collections for automatic document expiration
* Work with GridFS for storing large files
* Integrate MongoDB with external applications and BI tools

---

</details>

<details>
  <summary>SELinux</summary>
  
**list of topics in SELinux**

---

### **1. Introduction to SELinux**

* Understanding SELinux and its purpose
* Mandatory Access Control (MAC) vs Discretionary Access Control (DAC)
* SELinux modes: Enforcing, Permissive, and Disabled
* Components of SELinux: Policy, Contexts, Types, Booleans

---

### **2. SELinux Policies**

* Understanding SELinux policies: targeted, strict, MLS
* Policy modules and policy types
* Managing and switching policies
* Understanding how policies enforce access control

---

### **3. SELinux Contexts**

* Understanding SELinux contexts (user, role, type, level)
* Viewing file contexts (`ls -Z`, `ps -Z`)
* Understanding process contexts
* File labeling: default contexts and custom labeling

---

### **4. SELinux File and Directory Management**

* Viewing and modifying SELinux file contexts (`chcon`)
* Restoring default contexts (`restorecon`)
* Managing SELinux file contexts permanently (`semanage fcontext`)
* Understanding boolean controls for files and directories

---

### **5. SELinux User and Role Management**

* SELinux users and roles
* Mapping Linux users to SELinux users
* Role-based access control (RBAC) with SELinux
* Managing and switching SELinux users

---

### **6. SELinux Booleans**

* Understanding SELinux booleans
* Listing booleans (`getsebool -a`)
* Enabling/disabling booleans temporarily (`setsebool`)
* Enabling/disabling booleans permanently (`setsebool -P`)

---

### **7. SELinux Troubleshooting**

* Understanding AVC (Access Vector Cache) denials
* Viewing denials in logs (`/var/log/audit/audit.log`, `ausearch`)
* Using `sealert` and `audit2why` to interpret denials
* Using `audit2allow` to generate custom policy modules

---

### **8. SELinux Network and Process Management**

* Managing SELinux for network services
* Controlling access of processes to files and ports
* Assigning SELinux types to services (`semanage port`)
* Understanding type enforcement for processes

---

### **9. SELinux Policy Management**

* Loading and unloading policy modules (`semodule`)
* Creating custom SELinux policy modules
* Using `checkmodule` and `semodule_package` for module compilation
* Troubleshooting and testing custom policies

---

### **10. SELinux in Enterprise Environments**

* Integrating SELinux with system services (Apache, MySQL, Nginx, Docker)
* SELinux in containers and virtualized environments
* Best practices for production SELinux deployment
* Maintaining SELinux policies during upgrades and migrations

---

### **11. SELinux Automation and Reporting**

* Automating context labeling (`semanage fcontext -a`)
* Monitoring SELinux status (`sestatus`, `getenforce`)
* Reporting SELinux statistics and denials
* Auditing SELinux activity for compliance

---

**comprehensive study checklist**

---

### **1. Introduction to SELinux**

* Understand SELinux and its purpose in Linux security
* Learn the difference between Mandatory Access Control (MAC) and Discretionary Access Control (DAC)
* Study SELinux modes: Enforcing, Permissive, Disabled
* Understand SELinux components: Policy, Contexts, Types, Roles, and Booleans

---

### **2. SELinux Policies**

* Understand different SELinux policies: targeted, strict, MLS
* Learn about policy modules and their types
* Switch and manage SELinux policies
* Understand how SELinux policies enforce access control

---

### **3. SELinux Contexts**

* Understand SELinux contexts (user, role, type, level)
* View file and process contexts (`ls -Z`, `ps -Z`)
* Learn about default vs custom contexts
* Understand how contexts determine access permissions

---

### **4. SELinux File and Directory Management**

* View and modify file contexts using `chcon`
* Restore default file contexts using `restorecon`
* Manage permanent file contexts with `semanage fcontext`
* Understand boolean controls for file access

---

### **5. SELinux User and Role Management**

* Learn about SELinux users and roles
* Map Linux users to SELinux users
* Understand role-based access control (RBAC) in SELinux
* Switch between SELinux users and roles

---

### **6. SELinux Booleans**

* Understand the purpose of SELinux booleans
* List SELinux booleans (`getsebool -a`)
* Enable/disable booleans temporarily (`setsebool`)
* Enable/disable booleans permanently (`setsebool -P`)

---

### **7. SELinux Troubleshooting**

* Understand AVC (Access Vector Cache) denials
* View SELinux denials in logs (`/var/log/audit/audit.log`, `ausearch`)
* Use `sealert` and `audit2why` to analyze denials
* Generate custom policy modules with `audit2allow`

---

### **8. SELinux Network and Process Management**

* Control network service access through SELinux
* Manage process access to files, ports, and resources
* Assign SELinux types to services and ports (`semanage port`)
* Understand type enforcement for processes

---

### **9. SELinux Policy Management**

* Load and unload policy modules (`semodule`)
* Create and compile custom SELinux policy modules (`checkmodule`, `semodule_package`)
* Test and troubleshoot custom policies
* Maintain policies during system upgrades

---

### **10. SELinux in Enterprise Environments**

* Integrate SELinux with system services (Apache, MySQL, Nginx, Docker)
* Understand SELinux usage in containers and virtualized environments
* Follow best practices for production SELinux deployment
* Manage SELinux policies in large-scale enterprise environments

---

### **11. SELinux Automation and Reporting**

* Automate context labeling for files and directories
* Monitor SELinux status (`sestatus`, `getenforce`)
* Generate SELinux reports and audit logs
* Implement SELinux auditing for compliance and security monitoring

---

**list of hands-on exercises**

---

### **1. SELinux Installation and Service Management**

* Verify SELinux installation on Linux (`sestatus`, `getenforce`)
* Enable or disable SELinux temporarily and permanently
* Switch between SELinux modes: Enforcing, Permissive, Disabled
* Check SELinux version and installed policies

---

### **2. Working with SELinux Policies**

* View current SELinux policy (`sestatus`, `selinuxenabled`)
* Switch between targeted and strict policies (if installed)
* List policy modules (`semodule -l`)
* Update and reload SELinux policies

---

### **3. Managing SELinux Contexts**

* View file and directory contexts (`ls -Z`)
* View process contexts (`ps -Z`)
* Modify file or directory context temporarily (`chcon`)
* Restore default contexts (`restorecon`)
* Add permanent context mapping (`semanage fcontext`)

---

### **4. File and Directory Management**

* Change file types for custom access control
* Apply and verify SELinux context changes on directories recursively
* Test access permissions based on SELinux contexts
* Work with default and custom contexts for system and user files

---

### **5. SELinux User and Role Management**

* List SELinux users (`semanage login -l`)
* Map Linux users to SELinux users
* Switch roles for a user session (`newrole`)
* Test role-based access control (RBAC) restrictions

---

### **6. Managing SELinux Booleans**

* List all SELinux booleans (`getsebool -a`)
* Enable/disable a boolean temporarily (`setsebool`)
* Enable/disable a boolean permanently (`setsebool -P`)
* Test effect of changing booleans on services (e.g., HTTP, FTP)

---

### **7. Troubleshooting SELinux**

* Check AVC denials in logs (`/var/log/audit/audit.log`)
* Use `ausearch` to filter denials
* Analyze denials using `sealert` and `audit2why`
* Generate custom allow rules using `audit2allow`
* Test changes and verify access success

---

### **8. SELinux Network and Process Management**

* Assign SELinux types to network ports (`semanage port`)
* Modify process types to allow access to restricted resources
* Test service access with enforced SELinux rules (Apache, SSH, MySQL)
* Monitor process denials and log analysis

---

### **9. Policy Management**

* Load and unload custom policy modules (`semodule -i`, `semodule -r`)
* Create a simple custom policy module (`checkmodule`, `semodule_package`)
* Test custom policies on files or services
* Maintain and troubleshoot policies after updates

---

### **10. SELinux in Services and Enterprise Environments**

* Configure SELinux for web services (Apache/Nginx)
* Configure SELinux for database services (MySQL/PostgreSQL)
* Apply SELinux rules for Docker containers
* Test multi-service access with SELinux enforcement

---

### **11. Monitoring and Reporting**

* Monitor SELinux status continuously (`sestatus`, `getenforce`)
* Generate reports on denials and policy enforcement
* Audit SELinux activity for compliance (`auditctl`)
* Automate logging and monitoring with cron jobs

---

### **12. Advanced Exercises**

* Combine SELinux booleans, contexts, and custom policies for complex scenarios
* Simulate real-world access issues and troubleshoot using SELinux tools
* Test SELinux in a multi-user and multi-service environment
* Evaluate SELinux impact on system security and service availability

---

</details>

<details>
  <summary>Backup & Restore</summary>
  
**list of topics in Backup and Restore**

---

### **1. Introduction to Backup and Restore**

* Importance of backup and restore in Linux administration
* Types of backups: full, incremental, differential
* Backup strategies: on-site, off-site, cloud
* Understanding Recovery Point Objective (RPO) and Recovery Time Objective (RTO)

---

### **2. Linux File System and Data Considerations**

* Understanding file systems (ext4, XFS, Btrfs) and their impact on backups
* Handling large files and directories
* Preserving file permissions, ownership, and symbolic links
* Handling special files: device files, sockets, FIFOs

---

### **3. Backup Tools in Linux**

* `tar` for archiving and compressing files
* `rsync` for incremental and remote backups
* `cpio` for legacy backups
* `dd` for disk cloning and image backups
* `dump` and `restore` for ext2/ext3/ext4 file systems
* `rsnapshot` and other backup utilities

---

### **4. Compression and Encryption**

* Using `gzip`, `bzip2`, `xz` for compressed backups
* Encrypting backups with `gpg` or `openssl`
* Managing compressed and encrypted backup archives

---

### **5. Automated Backup Solutions**

* Scheduling backups with `cron` or `systemd timers`
* Writing backup scripts
* Managing rotation and retention of backup files
* Logging and notification for automated backups

---

### **6. Remote and Network Backup**

* Backing up to remote servers using `rsync` over SSH
* NFS, CIFS/SMB, and FTP-based backups
* Using `scp` and `sftp` for file transfer
* Network-attached storage (NAS) and SAN integration

---

### **7. Backup of Databases**

* Logical backups with `mysqldump` for MySQL/MariaDB
* Logical backups with `pg_dump` for PostgreSQL
* Physical backups of databases
* Incremental backups using database-specific tools
* Testing database restores

---

### **8. Disk Imaging and Cloning**

* Creating disk images using `dd`
* Using `partclone` and `Clonezilla` for cloning disks
* Restoring disk images to identical or new hardware
* Bootable recovery media creation

---

### **9. Restore Procedures**

* Restoring from tar/rsync backups
* Restoring full, incremental, and differential backups
* Restoring compressed and encrypted backups
* Restoring databases from logical and physical backups
* Testing restore integrity

---

### **10. Backup Strategy and Best Practices**

* Implementing 3-2-1 backup strategy (3 copies, 2 media, 1 offsite)
* Planning backup schedules and retention policies
* Testing backups regularly
* Documentation of backup and restore procedures

---

### **11. Advanced Backup Solutions**

* Using `Bacula`, `Amanda`, or `Duplicity` for enterprise-level backups
* Integrating cloud storage for backup (AWS S3, Google Cloud Storage, Azure)
* Versioned backups and snapshot management
* Handling live backups of critical systems

---

### **12. Disaster Recovery Planning**

* Developing disaster recovery (DR) procedures
* Restoring systems after total failure
* Recovering bootloader, partitions, and system configuration
* Testing DR plans and backup restoration drills

---

**comprehensive study checklist**

---

### **1. Introduction to Backup and Restore**

* Understand the importance of backup and restore in Linux administration
* Learn types of backups: full, incremental, differential
* Study backup strategies: on-site, off-site, and cloud
* Understand Recovery Point Objective (RPO) and Recovery Time Objective (RTO)

---

### **2. Linux File System and Data Considerations**

* Understand different Linux file systems: ext4, XFS, Btrfs
* Handle large files and directories efficiently
* Preserve file permissions, ownership, and symbolic links during backup
* Handle special files: device files, sockets, FIFOs

---

### **3. Backup Tools in Linux**

* Learn and practice using `tar` for archiving and compressing files
* Use `rsync` for incremental and remote backups
* Understand and use `cpio` for legacy backups
* Use `dd` for disk cloning and image backups
* Learn `dump` and `restore` for ext2/ext3/ext4 file systems
* Explore advanced backup utilities like `rsnapshot`

---

### **4. Compression and Encryption**

* Compress backups using `gzip`, `bzip2`, `xz`
* Encrypt backups using `gpg` or `openssl`
* Manage compressed and encrypted backup archives effectively

---

### **5. Automated Backup Solutions**

* Schedule backups with `cron` or `systemd timers`
* Write and maintain backup scripts
* Manage rotation and retention of backup files
* Implement logging and notifications for automated backups

---

### **6. Remote and Network Backup**

* Back up files to remote servers using `rsync` over SSH
* Use NFS, CIFS/SMB, and FTP for remote backups
* Transfer backups securely with `scp` and `sftp`
* Integrate backups with NAS and SAN systems

---

### **7. Backup of Databases**

* Perform logical backups using `mysqldump` for MySQL/MariaDB
* Perform logical backups using `pg_dump` for PostgreSQL
* Perform physical database backups
* Implement incremental database backups
* Test database restore procedures

---

### **8. Disk Imaging and Cloning**

* Create disk images using `dd`
* Clone disks using `partclone` or `Clonezilla`
* Restore disk images to identical or different hardware
* Create bootable recovery media for disaster recovery

---

### **9. Restore Procedures**

* Restore files and directories from `tar` or `rsync` backups
* Restore full, incremental, and differential backups
* Restore compressed and encrypted backups
* Restore databases from logical and physical backups
* Test restore integrity regularly

---

### **10. Backup Strategy and Best Practices**

* Implement the 3-2-1 backup rule (3 copies, 2 media types, 1 offsite)
* Plan backup schedules and retention policies
* Perform regular backup testing
* Document backup and restore procedures

---

### **11. Advanced Backup Solutions**

* Use enterprise backup solutions: `Bacula`, `Amanda`, `Duplicity`
* Integrate backups with cloud storage (AWS S3, Google Cloud Storage, Azure)
* Implement versioned backups and snapshot management
* Perform live backups of critical systems

---

### **12. Disaster Recovery Planning**

* Develop a disaster recovery (DR) plan
* Restore systems after total failure
* Recover bootloader, partitions, and system configurations
* Test DR plans and perform regular backup restoration drills

---

**list of hands-on exercises**

---

### **1. Basic File Backup and Restore**

* Create a backup of files and directories using `tar`
* Extract files from a `tar` archive
* Compress backups with `gzip`, `bzip2`, and `xz`
* Restore compressed backup archives

---

### **2. Incremental and Differential Backups**

* Perform incremental backups using `rsync`
* Perform differential backups using `rsync` or `tar`
* Compare full, incremental, and differential backups
* Restore incremental and differential backups correctly

---

### **3. Disk Imaging and Cloning**

* Create disk or partition images using `dd`
* Restore disk images using `dd`
* Clone a disk to another disk using `dd` or `partclone`
* Create bootable recovery media using Clonezilla

---

### **4. Remote Backup**

* Back up files to a remote server using `rsync` over SSH
* Transfer backup archives using `scp` or `sftp`
* Mount remote file systems using NFS or CIFS and perform backups
* Test restoring backups from remote locations

---

### **5. Automated Backup Scripts**

* Write a shell script for daily backups using `tar` or `rsync`
* Schedule automated backups using `cron`
* Test backup rotation and retention policies
* Log backup activities and configure email notifications

---

### **6. Backup of Special Files**

* Backup and restore symbolic links, device files, and sockets
* Preserve file permissions and ownership during backups
* Handle hidden files and directories in backups

---

### **7. Database Backups**

* Perform logical backups of MySQL/MariaDB databases using `mysqldump`
* Restore MySQL/MariaDB databases from dump files
* Perform logical backups of PostgreSQL databases using `pg_dump`
* Restore PostgreSQL databases from backups
* Test incremental and point-in-time recovery for databases

---

### **8. Backup Compression and Encryption**

* Compress backup files using `gzip`, `bzip2`, or `xz`
* Encrypt backups using `gpg` or `openssl`
* Test decryption and restoration of encrypted backups

---

### **9. Advanced Backup Solutions**

* Configure automated backups using `rsnapshot`
* Set up enterprise backup solutions like `Bacula` or `Amanda`
* Integrate backups with cloud storage (AWS S3, Google Cloud Storage, Azure)
* Perform snapshot-based backups for live systems

---

### **10. Restore and Disaster Recovery Exercises**

* Restore full backups from local storage
* Restore incremental/differential backups
* Restore databases and verify data integrity
* Simulate system failure and perform a complete disaster recovery
* Recover bootloader, partitions, and system configurations from backups

---

### **11. Monitoring and Validation**

* Verify backup integrity using checksums (`md5sum` or `sha256sum`)
* Monitor backup schedules and log files
* Test restore procedures regularly
* Document backup and restore processes

---

</details>

<details>
  <summary>Troubleshooting</summary>
  
**list of topics in Troubleshooting**

---

### **1. Introduction to Linux Troubleshooting**

* Importance of troubleshooting skills in Linux administration
* Common types of issues: system, network, hardware, application
* Understanding system logs and monitoring tools
* Steps in a systematic troubleshooting approach

---

### **2. Boot and Startup Issues**

* Understanding the Linux boot process (BIOS/UEFI → GRUB → Kernel → init/systemd)
* Troubleshooting GRUB bootloader issues
* Managing init and systemd services (`systemctl`)
* Recovering from boot failures using rescue mode or live media

---

### **3. System Performance Issues**

* Monitoring CPU, memory, and disk usage (`top`, `htop`, `free`, `vmstat`)
* Identifying high load processes (`ps`, `pidstat`)
* Troubleshooting disk space issues (`df`, `du`)
* Monitoring I/O performance (`iostat`, `iotop`)

---

### **4. Process and Service Issues**

* Managing processes (`ps`, `kill`, `pkill`, `systemctl`)
* Checking service status and logs (`systemctl status`, `journalctl`)
* Restarting or reloading services
* Identifying hung or zombie processes

---

### **5. Network Troubleshooting**

* Checking network configuration (`ifconfig`, `ip addr`, `nmcli`)
* Testing connectivity (`ping`, `traceroute`, `curl`, `wget`)
* Diagnosing routing and gateway issues (`route`, `ip route`)
* Monitoring open ports and network connections (`netstat`, `ss`, `lsof`)
* Troubleshooting firewall issues (`iptables`, `firewalld`, `ufw`)

---

### **6. Disk and File System Issues**

* Checking disk health (`smartctl`, `fsck`)
* Troubleshooting mount issues (`mount`, `umount`, `/etc/fstab`)
* Recovering deleted files
* Resolving file permission and ownership issues
* Working with disk quotas

---

### **7. Package and Dependency Issues**

* Installing, updating, and removing packages (`yum`, `dnf`, `apt`, `rpm`)
* Resolving broken dependencies and conflicts
* Managing software repositories
* Troubleshooting package scripts and post-installation errors

---

### **8. Log Management and Analysis**

* Understanding system logs (`/var/log/`, `journalctl`)
* Monitoring real-time logs (`tail -f`, `less`, `grep`)
* Filtering and analyzing logs for errors
* Configuring log rotation (`logrotate`)

---

### **9. Hardware Troubleshooting**

* Identifying connected hardware (`lspci`, `lsusb`, `dmidecode`)
* Diagnosing memory issues (`memtest86+`)
* Troubleshooting disk failures and RAID issues
* Checking system temperature and sensors (`sensors`, `lm_sensors`)

---

### **10. User and Permission Issues**

* Resolving login failures
* Checking and modifying user permissions (`chmod`, `chown`, `usermod`)
* Troubleshooting sudo and authentication problems
* Managing password and account lockouts

---

### **11. Kernel and Module Issues**

* Checking kernel version and modules (`uname -r`, `lsmod`)
* Loading and unloading kernel modules (`modprobe`, `insmod`, `rmmod`)
* Resolving module or driver conflicts
* Analyzing kernel logs (`dmesg`)

---

### **12. Security and SELinux Troubleshooting**

* Identifying SELinux-related access denials (`audit.log`, `sealert`)
* Troubleshooting firewall and iptables issues
* Resolving permission denied errors due to AppArmor or SELinux
* Auditing security-related errors

---

### **13. Application and Service-Specific Troubleshooting**

* Web servers (Apache, Nginx) error resolution
* Database issues (MySQL, PostgreSQL)
* Mail server troubleshooting
* Troubleshooting scripts and cron jobs

---

### **14. Backup and Recovery Troubleshooting**

* Identifying failed backups
* Recovering corrupted backup files
* Restoring files from incremental backups
* Testing backup integrity

---

### **15. Advanced Troubleshooting Tools**

* Using `strace` and `ltrace` for debugging programs
* Using `tcpdump` and `wireshark` for network troubleshooting
* Using `perf` and `sar` for performance analysis
* Using `systemtap` and `gdb` for advanced kernel/application debugging

---

**comprehensive study checklist**

---

### **1. Introduction to Linux Troubleshooting**

* Understand the importance of troubleshooting skills in Linux administration
* Learn types of issues: system, network, hardware, application
* Understand system logs and monitoring tools
* Follow a systematic troubleshooting methodology

---

### **2. Boot and Startup Issues**

* Understand the Linux boot process (BIOS/UEFI → GRUB → Kernel → init/systemd)
* Troubleshoot GRUB bootloader problems
* Manage init/systemd services (`systemctl`)
* Recover from boot failures using rescue mode or live media

---

### **3. System Performance Issues**

* Monitor CPU, memory, and disk usage (`top`, `htop`, `free`, `vmstat`)
* Identify high load processes (`ps`, `pidstat`)
* Troubleshoot disk space issues (`df`, `du`)
* Monitor I/O performance (`iostat`, `iotop`)

---

### **4. Process and Service Issues**

* Manage processes (`ps`, `kill`, `pkill`, `systemctl`)
* Check service status and logs (`systemctl status`, `journalctl`)
* Restart or reload services
* Identify hung or zombie processes

---

### **5. Network Troubleshooting**

* Check network configuration (`ifconfig`, `ip addr`, `nmcli`)
* Test connectivity (`ping`, `traceroute`, `curl`, `wget`)
* Diagnose routing and gateway issues (`route`, `ip route`)
* Monitor open ports and network connections (`netstat`, `ss`, `lsof`)
* Troubleshoot firewall issues (`iptables`, `firewalld`, `ufw`)

---

### **6. Disk and File System Issues**

* Check disk health (`smartctl`, `fsck`)
* Troubleshoot mount issues (`mount`, `umount`, `/etc/fstab`)
* Recover deleted files
* Resolve file permission and ownership issues
* Manage disk quotas

---

### **7. Package and Dependency Issues**

* Install, update, and remove packages (`yum`, `dnf`, `apt`, `rpm`)
* Resolve broken dependencies and conflicts
* Manage software repositories
* Troubleshoot package installation scripts

---

### **8. Log Management and Analysis**

* Understand system logs (`/var/log/`, `journalctl`)
* Monitor real-time logs (`tail -f`, `less`, `grep`)
* Filter and analyze logs for errors
* Configure log rotation (`logrotate`)

---

### **9. Hardware Troubleshooting**

* Identify connected hardware (`lspci`, `lsusb`, `dmidecode`)
* Diagnose memory issues (`memtest86+`)
* Troubleshoot disk failures and RAID issues
* Check system temperature and sensors (`sensors`, `lm_sensors`)

---

### **10. User and Permission Issues**

* Resolve login failures
* Check and modify user permissions (`chmod`, `chown`, `usermod`)
* Troubleshoot sudo and authentication problems
* Manage password and account lockouts

---

### **11. Kernel and Module Issues**

* Check kernel version and loaded modules (`uname -r`, `lsmod`)
* Load and unload kernel modules (`modprobe`, `insmod`, `rmmod`)
* Resolve module or driver conflicts
* Analyze kernel logs (`dmesg`)

---

### **12. Security and SELinux Troubleshooting**

* Identify SELinux-related access denials (`audit.log`, `sealert`)
* Troubleshoot firewall and iptables issues
* Resolve permission denied errors due to SELinux/AppArmor
* Audit security-related errors

---

### **13. Application and Service-Specific Troubleshooting**

* Web server (Apache, Nginx) error resolution
* Database troubleshooting (MySQL, PostgreSQL)
* Mail server troubleshooting
* Script and cron job troubleshooting

---

### **14. Backup and Recovery Troubleshooting**

* Identify failed backups
* Recover corrupted backup files
* Restore files from incremental backups
* Test backup integrity

---

### **15. Advanced Troubleshooting Tools**

* Use `strace` and `ltrace` for program debugging
* Use `tcpdump` and `wireshark` for network troubleshooting
* Use `perf` and `sar` for performance analysis
* Use `systemtap` and `gdb` for advanced kernel/application debugging

---

**list of hands-on exercises**

---

### **1. Boot and Startup Troubleshooting**

* Boot into rescue mode using a live CD or GRUB menu
* Repair or reinstall GRUB bootloader
* Check and fix issues with `/etc/fstab` causing boot failures
* Start, stop, enable, and disable services with `systemctl`
* Analyze boot logs using `journalctl -b`

---

### **2. System Performance Troubleshooting**

* Monitor CPU and memory usage using `top` and `htop`
* Identify high CPU/memory consuming processes (`ps`, `pidstat`)
* Check disk usage with `df -h` and `du -sh`
* Analyze I/O bottlenecks using `iostat` and `iotop`
* Kill or restart resource-hogging processes

---

### **3. Process and Service Troubleshooting**

* Check process status and hierarchy (`ps -ef`, `pstree`)
* Find and terminate hung or zombie processes
* Restart or reload services (`systemctl restart`, `systemctl reload`)
* Check service logs (`journalctl -u <service>`)
* Enable or disable services at boot

---

### **4. Network Troubleshooting**

* Check network interface configuration (`ip addr`, `ifconfig`)
* Test connectivity using `ping`, `traceroute`, `curl`, `wget`
* Diagnose routing issues (`ip route`, `route`)
* Monitor open ports and connections (`netstat -tulnp`, `ss -tulnp`)
* Troubleshoot firewall rules using `iptables`, `firewalld`, or `ufw`
* Capture and analyze network traffic using `tcpdump`

---

### **5. Disk and File System Troubleshooting**

* Check disk health and SMART status (`smartctl`)
* Repair filesystem errors with `fsck`
* Recover deleted files using `extundelete` or `testdisk`
* Fix mount issues and verify `/etc/fstab`
* Analyze disk usage and locate large files (`du`, `ncdu`)

---

### **6. Package and Dependency Troubleshooting**

* Install, update, and remove packages (`yum`, `dnf`, `apt`, `rpm`)
* Resolve broken dependencies and package conflicts
* Check package installation logs for errors
* Rebuild or reinstall packages causing issues

---

### **7. Log Analysis and Monitoring**

* View and monitor system logs in `/var/log/`
* Use `journalctl` for analyzing systemd logs
* Filter logs with `grep` and `awk` for specific errors
* Set up log monitoring and alerting for critical events

---

### **8. User and Permission Troubleshooting**

* Resolve login issues (`last`, `lastb`, `who`)
* Reset user passwords and unlock accounts (`passwd`, `usermod`)
* Correct file and directory permissions (`chmod`, `chown`)
* Fix sudo and authentication errors

---

### **9. Kernel and Module Troubleshooting**

* Check kernel version and loaded modules (`uname -r`, `lsmod`)
* Load and unload kernel modules (`modprobe`, `insmod`, `rmmod`)
* Analyze kernel messages with `dmesg`
* Resolve driver or module conflicts

---

### **10. Security and SELinux Troubleshooting**

* Identify SELinux denials using `/var/log/audit/audit.log`
* Use `sealert` and `audit2why` to analyze SELinux issues
* Fix SELinux policy issues temporarily with `setenforce 0` and permanently with custom policies
* Troubleshoot firewall rules blocking services

---

### **11. Application and Service-Specific Troubleshooting**

* Analyze Apache/Nginx error logs and fix configuration issues
* Resolve MySQL/PostgreSQL connection and query issues
* Troubleshoot cron jobs and scheduled scripts
* Fix mail server delivery issues

---

### **12. Backup and Recovery Troubleshooting**

* Identify failed backup logs and errors
* Test restoring from backups (full, incremental, differential)
* Verify backup integrity using checksums (`md5sum`, `sha256sum`)
* Simulate a disaster recovery scenario and restore critical data

---

### **13. Advanced Troubleshooting Tools**

* Trace system calls using `strace`
* Debug library calls with `ltrace`
* Capture and analyze network packets with `tcpdump` or `wireshark`
* Monitor system performance with `perf` and `sar`
* Debug applications or kernel modules using `gdb` or `systemtap`

---

</details>
