# Network Security Lab — Overview  
ARP Spoofing • TCP SYN Flood • Smurf Attack

## Table of Contents
1. [Introduction](#1-introduction)  
2. [Lab Environment](#2-lab-environment)  
3. [Attack Summaries](#3-attack-summaries)  
   - [ARP Spoofing](#31-arp-spoofing)  
   - [TCP SYN Flood](#32-tcp-syn-flood)  
   - [Smurf Attack](#33-smurf-attack)  
4. [Full Documentation](#4-full-documentation)  
5. [Conclusion](#5-conclusion)  
6. [Author](#6-author)

---

## 1. Introduction

This lab explores three fundamental network attacks performed in a controlled environment using Kali Linux and Metasploitable:

- ARP Spoofing  
- TCP SYN Flood  
- Smurf Attack (ICMP Amplification)

The objective is to understand protocol weaknesses, observe attack behavior, and analyze the impact using Wireshark and system tools.

---

## 2. Lab Environment

- **Attacker:** Kali Linux  
- **Victim:** Metasploitable  
- **Network:** 192.168.43.0/24  
- **Tools Used:**  
  - Metasploit Framework  
  - Scapy  
  - Wireshark  
  - netstat, arp, ping  

---

## 3. Attack Summaries

### 3.1 ARP Spoofing  
A Layer‑2 attack where the attacker poisons the ARP cache of the victim and gateway, redirecting traffic through the attacker.  
Impact: Man‑in‑the‑middle, credential interception, session hijacking.

👉 Full details: see `/docs/arp-spoofing.md`

---

### 3.2 TCP SYN Flood  
A Denial‑of‑Service attack exploiting the TCP handshake by sending large numbers of SYN packets without completing the connection.  
Impact: Service slowdown or unavailability.

👉 Full details: see `/docs/syn-flood.md`

---

### 3.3 Smurf Attack  
An ICMP amplification attack where broadcast pings cause multiple hosts to reply to the victim.  
Impact: High ICMP traffic volume, potential DoS.

👉 Full details: see `/docs/smurf-attack.md`

---

## 4. Full Documentation

- [ARP Spoofing](docs/arp-spoofing.md)  
- [TCP SYN Flood](docs/syn-flood.md)  
- [Smurf Attack](docs/smurf-attack.md)

---

## 5. Conclusion

This lab demonstrates how simple packet‑level attacks can disrupt network confidentiality, integrity, and availability.  
Understanding these offensive techniques strengthens defensive capabilities and supports secure network design.

---

## 6. Author

**Oussema — Cybersecurity Student**
