# Intrusion Detection and Protection (IDS/IPS)

* Overview
* Host vs Network based
* Signature vs Anomoly based
* Examples

---

# What it is

Intrusion detection and protection systems at their core do the following:

* monitor systems or networks for policy violations
* report/log all violations
* perform/execute some action based on violations (IPS)

---

# Host Intrusion Detection Systems (HIDS)

* Operates on a host system
* Monitors network traffic in and out of system
* Monitors logs and files on the system
  * If critical files change, error/report
  * If logs show patterns known as attack, error/report

---

`/var/log/auth.log`

![ssh-log](./img/ssh-log.png)

---

# How to move from detect to protect

![fail2ban](./img/fail2ban.jpg){height=15%}

* detect (multiple failed login attempts)
* report (email admin/ log in central location)
* protect (use iptables to block all communication from that IP address)

Works with almost anything that has an authentication log file 

---

![distributed](./img/fail2banpirate.png)

---

# HIDS beyond logs

### Can detect more intrusions than just inspecting logs.

* File integrity monitoring (tripwire)
  * `/sbin`, `/bin`, `/usr/bin`, everything except `/home`
  * `C:\Windows`, `C:\Program Files`, everything except `C:\Users`
  * If files change in these directories, thsi could be considered an anomoly/outside the norm
* Binary analysis
  * Look for already known signatures/hashes/patterns of malicious activity or files

---

# Signature vs Anomoly detection

### Signature based detection (binary analysis and others)

  * assumes that we know what we are looking for
  * assumes we (or whoever made our rules) has seen this before
  * we need a good rule set/ signature database
  * and it will only grow...

### Anomoly based detection (we called this statistical previously)

 * assumes we know what should NOT change
 * assumes we have a baseline for normal behavior
 * frequently uses machine learning to model good behaviour
 * compares new behavior against the model to determine if it is malicious

 ---

# Network Intrusion Detection System (NIDS)

* Operates at the network level
* Monitors traffic to ALL hosts on network
* Location Location Location...
  * Typically just behind the firewall
  * Has access to all outbound traffic
  * Has access to all inbound traffic that is NOT dropped by firewall
  * Can be in multiple places / distributed across the network
  * Ideally would have access to all internal traffic

---

# Signature vs Anomoly again

The same ideas that we applied in HIDS can be applied here.

Snort (now owned by Cisco) is a powerful NIDS

Signature based

 * snort blacklist of bad acting IP addresses
 * snort signature database of known malicious attack patterns (from previously seen network attacks)

Anomoly based detection

 * typically needs to be application aware
 * needs to know which ports a given application is running on

---

# Examples

* Antivirus/anti-malware (can be IDS and IPS)
* fail2ban (IPS)
* tripwire (IDS but could protect with better rules)
* OSSEC 
* snort (IDS and IPS when allowed to alter rules based on detection)
* selinux (not IDS per se but can detect and log intrusions)
* Kismet (wireless IDS)

---

# Links

* [Wikipedia IDS](https://en.wikipedia.org/wiki/Intrusion_detection_system)
* [Linux IDS](https://www.redhat.com/sysadmin/security-intrusion-detection)
* [Kismet](https://www.kismetwireless.net/)
* [Snort](https://www.snort.org/#documents)
* [Snort blacklist](https://snort-org-site.s3.amazonaws.com/production/document_files/files/000/010/603/original/ip_filter.blf?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAU7AK5ITMGOEV4EFM%2F20211118%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20211118T131248Z&X-Amz-Expires=3600&X-Amz-SignedHeaders=host&X-Amz-Signature=5e83f53e64c9bad8d5d140825753b676c7e2feb38f2c903ef8312f19b0a30359)
* [Snort conf](https://fossies.org/linux/snort/etc/snort.conf)
* [Snort rules](https://snort.org/rules_explanation)

