# Network Security Lab — TP1  
ARP Spoofing • TCP SYN Flood • Smurf Attack

## 1. Overview

This project demonstrates three foundational network attacks in a controlled lab environment using Kali Linux and Metasploitable.  
The goal is to understand how these attacks operate at the protocol level, analyze their impact, and identify effective mitigation strategies.

---

## 2. Lab Objectives

- Observe how ARP Spoofing manipulates Layer 2 trust relationships  
- Execute a TCP SYN Flood to exhaust a service’s connection backlog  
- Simulate a Smurf attack using ICMP broadcast amplification  
- Analyze attack behavior using Wireshark and system utilities  
- Connect each attack to practical defensive measures

---

## 3. Environment and Tools

- **Attacker:** Kali Linux  
- **Victim:** Metasploitable  
- **Network:** 192.168.43.0/24  
- **Tools Used:**  
  - Metasploit Framework  
  - Scapy  
  - Wireshark  
  - netstat, arp, ping

---

## 4. Attack Summaries

### 4.1 ARP Spoofing

The attacker sends forged ARP replies to the victim, causing it to associate the gateway’s IP address with the attacker’s MAC address.  
This enables traffic interception and manipulation on an unsecured LAN.

**Key Concepts:**  
- ARP has no authentication  
- Cache poisoning enables man‑in‑the‑middle attacks

---

### 4.2 TCP SYN Flood

A large number of SYN packets are sent to the victim without completing the TCP handshake.  
The server’s backlog queue fills with half‑open connections, degrading or denying service availability.

**Key Concepts:**  
- Exploits TCP handshake design  
- Resource exhaustion leads to DoS conditions

---

### 4.3 Smurf Attack

ICMP Echo Requests are sent to the broadcast address with the victim’s IP spoofed as the source.  
All hosts on the subnet reply to the victim, creating an amplification effect.

**Key Concepts:**  
- Broadcast amplification  
- IP spoofing  
- ICMP misuse

---

## 5. Mitigation Strategies

### ARP Spoofing

- Dynamic ARP Inspection  
- Static ARP entries for critical hosts  
- Network segmentation  
- Monitoring for abnormal ARP activity

### TCP SYN Flood

- SYN cookies  
- Firewall rate limiting  
- Increasing backlog size  
- Reverse proxies or load balancers

### Smurf Attack

- Disable directed broadcast on routers  
- Ingress filtering to block spoofed packets  
- Unicast Reverse Path Forwarding (uRPF)

---

## 6. Key Takeaways

- Many legacy protocols lack authentication and are vulnerable by design  
- Simple packet‑level attacks can significantly impact service availability  
- Network hardening and traffic monitoring are essential defensive practices  
- Understanding offensive techniques strengthens defensive capabilities

---

## 7. Disclaimer

All experiments were performed in an isolated lab environment for educational purposes only.  
These techniques must not be used on production systems or unauthorized networks.

---

## 8. Author

**Oussema — Cybersecurity Student specializing in Network and System Security**

