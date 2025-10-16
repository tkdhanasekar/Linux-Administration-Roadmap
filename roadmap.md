
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

##  **15. Projects to Practice

* [ ] Create a resource dashboard using Prometheus + Grafana
* [ ] Simulate load and optimize performance using tuning parameters
* [ ] Build a container monitoring solution with Docker + cAdvisor
* [ ] Write a script to alert when CPU or memory usage exceeds a threshold
* [ ] Analyze a performance issue from a real or simulated Linux server

---
</details>






<details>
  <summary>****</summary>

</details>


