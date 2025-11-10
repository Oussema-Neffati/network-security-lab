# Network Security Lab — TP1 (ARP Spoofing, SYN Flood, Smurf)

## 📚 Context
This lab was conducted in a controlled environment (Kali Linux, Metasploitable) as part of a cybersecurity course at ESPRIT.  
It demonstrates three classic network attacks and analyzes their impact using tools such as Metasploit, Scapy, and Wireshark.

## 🎯 Objectives
- Perform ARP Spoofing to intercept traffic.
- Launch a TCP SYN Flood to disrupt a web service.
- Simulate a Smurf attack using ICMP broadcast amplification.
- Document results and propose mitigation strategies.

## 🛠 Tools Used
- Kali Linux, Metasploitable
- Metasploit Framework
- Scapy
- Wireshark
- netstat, arp

## 🔑 Key Learnings
- **ARP Spoofing**: ARP lacks authentication, making spoofing possible.
- **SYN Flood**: Exploits TCP handshake backlog to degrade service.
- **Smurf Attack**: Amplifies ICMP traffic via broadcast with spoofed source.

### Mitigation Strategies
- ARP: Dynamic ARP Inspection, static ARP entries.
- TCP: SYN cookies, rate limiting.
- ICMP: Disable broadcast ping, anti-spoofing filters.

---

## 🌍 Résumé en Français
Ce TP démontre trois attaques réseau classiques (ARP Spoofing, SYN Flood, Smurf) dans un environnement isolé.  
Les résultats sont analysés avec Wireshark et netstat, et des mesures de mitigation sont proposées (DAI, SYN cookies, filtrage ICMP).

---

## ⚠️ Disclaimer
All experiments were performed in a safe lab environment for **educational purposes only**.  
Never reproduce these techniques on production systems or unauthorized networks.

## 👤 Author
- Oussema — ESPRIT, Network Infrastructure & Data Security
