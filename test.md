
Linux Daemon Services

<details>
  <summary>DNS</summary>
Here’s a comprehensive list of **DNS administration topics** specifically within the context of **Linux system administration**. These cover both foundational concepts and hands-on administration skills:

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
