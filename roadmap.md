
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
  <summary>****</summary>

</details>


