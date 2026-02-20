# Web Application

This section captures key web application concepts from your notes, including cryptography, HTTP fundamentals and common tools【144790417098188†L10-L100】.

## Hashing, encoding & encryption

- **Hashing:** cryptographic hashes (MD5, SHA‑1, SHA‑256) produce fixed‑length digests of data.  Hashes are one‑way; use salting to defend against rainbow‑table attacks【144790417098188†L10-L100】.
- **Encoding:** transforms data for safe transport/storage.  Examples include Base64 (A–Z, a–z, 0–9, `+`, `/`, `=`), URL encoding (percent‑encoding), and simple ciphers like ROT13.  Encoding **does not provide security**; it’s reversible【144790417098188†L10-L100】.
- **Encryption:** protects confidentiality by making data unreadable without a key.  Your notes mention asymmetric encryption and using tools like `certbot` to generate SSL/TLS certificates【144790417098188†L10-L100】.

## Network & protocol basics

- **OSI vs TCP/IP:** remember the seven‑layer OSI model (Physical → Application) and how protocols map to it.  AD notes mention NetBIOS and NAT vs bridged networking【144790417098188†L10-L100】.
- **DHCP & DNS:** DHCP leases IPs to clients; DNS translates domain names to IPs.  Attackers can exploit DHCP or DNS poisoning if not secured【144790417098188†L10-L100】.
- **DNS record types:**
  - *A* and *AAAA* – map hostnames to IPv4/IPv6 addresses.
  - *MX* – mail exchange records for email delivery.
  - *CNAME* – canonical name (aliases).
  - *PTR* – reverse DNS records【144790417098188†L10-L100】.

## Web server & scanning tools

- **Nmap:** use `nmap -A` for OS detection and service enumeration; combine with firewall checks (iptables), SNMP probes and load‑balancer detection【144790417098188†L10-L100】.
- **Burp Suite:** intercept and modify HTTP traffic.  Notes mention using the Repeater and Sequencer tools to test randomness and manipulate requests【144790417098188†L10-L100】.

## HTTP fundamentals

- **Methods:** GET retrieves resources; POST submits data; HEAD requests headers; OPTIONS asks which methods a server supports.  Understanding these helps craft malicious requests【144790417098188†L10-L100】.
- **Cookies vs sessions:** cookies are stored on the client and contain session identifiers; sessions are server‑side storage tied to a unique cookie【144790417098188†L10-L100】.
- **Status codes:** 307 indicates a temporary redirect (the request method should be repeated using the same method)【144790417098188†L10-L100】.
- **WebDAV:** an extension of HTTP that allows clients to read and write files on a web server.  Misconfigured WebDAV services can allow file upload attacks【144790417098188†L10-L100】.

## Encoding tricks & filters

When bypassing web filters, consider double encoding (e.g., URL‑encode then Base64) or using encoding schemes like ROT13.  Always test payloads in Burp’s Decoder to ensure they decode to the intended input【144790417098188†L10-L100】.

These notes provide a foundation for understanding web security; combine them with hands‑on practice using OWASP Top 10 vulnerabilities and labs.
