# 🐧 Linux Security Cheat Sheet (Task 2)

## 🔍 Reconnaissance
* `nmap -sV [IP]` - Service version detection.
* `nmap -O [IP]` - Operating System identification.
* `nmap -p- [IP]` - Scan all 65,535 ports.

## 🕵️ Packet Analysis
* `tcpdump -i eth0` - Capture traffic on interface eth0.
* `wireshark` - Launch graphical packet analyzer.

## 🛡️ Firewall (iptables)
* `sudo iptables -L` - List all current rules.
* `sudo iptables -A OUTPUT -p tcp --dport 21 -j DROP` - Block outgoing FTP.
* `sudo iptables -F` - Flush (clear) all rules.
