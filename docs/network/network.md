# Network

This section distills the key networking concepts from your PJPT course notes.  It covers the basics of IP addressing, network address translation, and common port numbers.

## IP addressing

### IPv4

- **Length & format** – IPv4 addresses are 32‑bit values, traditionally written as four 8‑bit octets separated by dots (e.g., `192.168.1.1`)【460080210145980†L10-L63】.  Each octet can range from 0–255.
- **Classes & CIDR** – Historically addresses were grouped into classes (A, B, C), but modern networks use Classless Inter‑Domain Routing (CIDR) to define arbitrary network/host boundaries.
- **Private ranges** – Addresses in `192.168.0.0/16`, `10.0.0.0/8` and `172.16.0.0/12` are reserved for private use【460080210145980†L10-L63】.

### NAT (Network Address Translation)

When a private host needs to access the internet, a router performs NAT – mapping internal IPs to a single public IP.  Your notes emphasise that “192” addresses are private and must be translated before leaving the network【460080210145980†L10-L63】.

### IPv6

- **Length & format** – IPv6 uses 128‑bit addresses written in hexadecimal, separated by colons (e.g., `2001:0db8:85a3::8a2e:0370:7334`)【460080210145980†L10-L63】.
- **Compression rules** – Leading zeros in each hextet may be omitted, and a double colon (`::`) represents consecutive zeroes once per address.
- **Benefits** – Vast address space, built‑in security features, and simplified routing compared with IPv4.

### MAC addresses

Media Access Control (MAC) addresses uniquely identify network interfaces at layer 2.  They are 48‑bit values written as six pairs of hex digits (e.g., `00:1A:2B:3C:4D:5E`).  The first half identifies the vendor; the second half is a unique serial【460080210145980†L10-L63】.

## Well‑known ports

Your notes list several “famous ports and services”【460080210145980†L10-L63】.  Remembering these helps you recognise services during scanning:

| Port | Protocol/service |
|---|---|
| **21** | FTP – file transfer |
| **22** | SSH – secure remote login |
| **23** | Telnet – unencrypted remote login |
| **25** | SMTP – e‑mail relay |
| **53** | DNS – domain name system |
| **80** | HTTP – web traffic |
| **110** | POP3 – e‑mail retrieval |
| **143** | IMAP – e‑mail retrieval |
| **443** | HTTPS – secure web |
| **3306** | MySQL database |
| **3389** | RDP – Windows Remote Desktop |

These port numbers frequently appear during enumeration.  Always verify the associated service rather than assuming defaults.

## Subnetting basics

Subnetting divides a network into smaller segments.  Bits in the subnet mask determine how many hosts fit into a subnet.  Your notes discuss how each bit position halves or doubles the host range【460080210145980†L10-L63】.  For example:

- A `/24` network (`255.255.255.0`) has 8 host bits ⇒ `2^8 – 2 = 254` usable hosts.
- A `/30` network (`255.255.255.252`) has 2 host bits ⇒ `2^2 – 2 = 2` usable hosts (often used for point‑to‑point links).

When designing networks, choose subnet sizes that fit your number of hosts and avoid overlapping ranges.
