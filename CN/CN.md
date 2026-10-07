# Computer Networks Interview Topic List

## 1. Computer Network Basics

* What is a Computer Network?
* Advantages of Networking
* Types of Networks

  * PAN (Personal Area Network)
  * LAN (Local Area Network)
  * MAN (Metropolitan Area Network)
  * WAN (Wide Area Network)

### Interview Questions

* What is a Computer Network?
* Difference between LAN, MAN, and WAN?
* What is the Internet?

---

## 2. Network Topologies

### Types

* Bus Topology
* Star Topology
* Ring Topology
* Mesh Topology
* Tree Topology
* Hybrid Topology

### Interview Questions

* What is Network Topology?
* Which topology is most commonly used?

---

## 3. OSI Model

### 7 Layers

| Layer No | Layer Name   |
| -------- | ------------ |
| 7        | Application  |
| 6        | Presentation |
| 5        | Session      |
| 4        | Transport    |
| 3        | Network      |
| 2        | Data Link    |
| 1        | Physical     |

### Responsibilities

#### Application Layer

* HTTP
* HTTPS
* FTP
* SMTP
* DNS

#### Presentation Layer

* Encryption
* Compression

#### Session Layer

* Session Management

#### Transport Layer

* TCP
* UDP

#### Network Layer

* IP Routing

#### Data Link Layer

* MAC Address

#### Physical Layer

* Transmission of Bits

### Interview Questions

* Explain OSI Model.
* Which layer is responsible for Routing?
* Which layer uses MAC Address?

---

## 4. TCP/IP Model

### Layers

| TCP/IP Layer   | Equivalent OSI Layer                 |
| -------------- | ------------------------------------ |
| Application    | Application + Presentation + Session |
| Transport      | Transport                            |
| Internet       | Network                              |
| Network Access | Data Link + Physical                 |

### Interview Questions

* Difference between OSI and TCP/IP Model?

---

## 5. TCP vs UDP

| TCP                 | UDP                       |
| ------------------- | ------------------------- |
| Connection-Oriented | Connectionless            |
| Reliable            | Unreliable                |
| Slower              | Faster                    |
| Error Checking      | Minimal Error Checking    |
| Used in HTTP, HTTPS | Used in Streaming, Gaming |

### Interview Questions

* Difference between TCP and UDP?
* When should UDP be preferred?

---

## 6. IP Addressing

### Types

* IPv4
* IPv6

### IPv4 Example

```text
192.168.1.1
```

### IPv6 Example

```text
2001:db8::1
```

### Interview Questions

* What is an IP Address?
* Difference between IPv4 and IPv6?

---

## 7. MAC Address

### Topics

* Physical Address
* 48-bit Address

### Interview Questions

* Difference between IP Address and MAC Address?

---

## 8. Subnetting

### Topics

* Subnet Mask
* Network ID
* Host ID
* CIDR Notation

### Common Subnet Masks

| CIDR | Subnet Mask   |
| ---- | ------------- |
| /24  | 255.255.255.0 |
| /16  | 255.255.0.0   |
| /8   | 255.0.0.0     |

### Interview Questions

* What is Subnetting?
* Why is Subnetting used?

---

## 9. Routing

### Routing Types

* Static Routing
* Dynamic Routing

### Routing Protocols

* RIP
* OSPF
* BGP

### Interview Questions

* What is Routing?
* Difference between Static and Dynamic Routing?

---

## 10. Switching

### Types

* Circuit Switching
* Packet Switching
* Message Switching

### Interview Questions

* What is Packet Switching?
* Why is Packet Switching used on the Internet?

---

## 11. Network Devices

### Hub

* Broadcasts to all devices

### Switch

* Uses MAC Address

### Router

* Uses IP Address

### Gateway

* Connects Different Networks

### Modem

* Modulates and Demodulates Signals

### Interview Questions

* Difference between Hub, Switch, and Router?

### Hub vs Switch vs Router

| Hub            | Switch          | Router           |
| -------------- | --------------- | ---------------- |
| Physical Layer | Data Link Layer | Network Layer    |
| Broadcast      | MAC Based       | IP Based         |
| Less Secure    | More Secure     | Most Intelligent |

---

## 12. DNS (Domain Name System)

### Topics

* Domain Name Resolution
* DNS Lookup

### Example

```text
google.com → IP Address
```

### Interview Questions

* What is DNS?
* Why is DNS required?

---

## 13. DHCP

### Topics

* Dynamic IP Assignment
* DHCP Process

### Interview Questions

* What is DHCP?
* Why do we use DHCP?

---

## 14. ARP and RARP

### ARP

* IP → MAC

### RARP

* MAC → IP

### Interview Questions

* What is ARP?
* How does ARP work?

---

## 15. Important Protocols

### HTTP

* HyperText Transfer Protocol

### HTTPS

* Secure HTTP

### FTP

* File Transfer Protocol

### SMTP

* Sending Emails

### POP3

* Receiving Emails

### IMAP

* Email Synchronization

### SSH

* Secure Remote Login

### Telnet

* Remote Login

### DNS

* Domain Resolution

### Interview Questions

* Difference between HTTP and HTTPS?
* Difference between POP3 and IMAP?

---

## 16. Ports

### Common Ports

| Protocol | Port |
| -------- | ---- |
| HTTP     | 80   |
| HTTPS    | 443  |
| FTP      | 21   |
| SSH      | 22   |
| SMTP     | 25   |
| DNS      | 53   |
| MySQL    | 3306 |

### Interview Questions

* What is a Port Number?
* What is Port 443?

---

## 17. Network Security

### Topics

* Firewall
* VPN
* SSL/TLS
* Encryption
* Authentication

### Interview Questions

* What is a Firewall?
* What is SSL/TLS?

---

## 18. Congestion Control

### Topics

* Congestion
* Traffic Shaping
* Leaky Bucket Algorithm
* Token Bucket Algorithm

### Interview Questions

* What is Congestion Control?

---

## 19. Error Detection

### Techniques

* Parity Bit
* Checksum
* CRC

### Interview Questions

* What is CRC?
* Why is Error Detection needed?

---

## 20. Socket Programming

### Concepts

* Client
* Server
* Socket

### Interview Questions

* What is a Socket?
* How does Client-Server Communication work?

---

# Most Asked Computer Network Interview Questions

1. What is a Computer Network?
2. Explain OSI Model.
3. Explain TCP/IP Model.
4. TCP vs UDP?
5. What is an IP Address?
6. IPv4 vs IPv6?
7. What is MAC Address?
8. Difference between IP Address and MAC Address?
9. What is DNS?
10. What is DHCP?
11. What is ARP?
12. What is Routing?
13. What is a Router?
14. What is a Switch?
15. Difference between Hub, Switch, and Router?
16. HTTP vs HTTPS?
17. What is SSL/TLS?
18. What is a Firewall?
19. What is a Port Number?
20. What is Socket Programming?

# High-Priority Topics for Freshers (IBM, Cognizant, TCS, Infosys, Wipro, Accenture, CGI)

Focus most on:

1. OSI Model
2. TCP/IP Model
3. TCP vs UDP
4. IP Addressing (IPv4 & IPv6)
5. DNS
6. DHCP
7. ARP
8. HTTP vs HTTPS
9. Hub vs Switch vs Router
10. Common Port Numbers
11. Routing Basics
12. Network Security Basics
13. MAC Address vs IP Address
14. Socket Programming Basics


