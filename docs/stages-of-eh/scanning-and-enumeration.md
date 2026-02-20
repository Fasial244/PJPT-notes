# Scanning & Enumeration

After reconnaissance comes scanning and enumeration: actively probing hosts to discover services and vulnerabilities.  Your notes cover several tools and best practices【109748872142250†L11-L64】.

## Subdomain & service enumeration

- **crt.sh & SSL certificates:** use crt.sh and other certificate transparency logs to find subdomains【109748872142250†L11-L64】.
- **Amass & Sublist3r:** automated tools to enumerate subdomains via DNS records, search engines and certificate data【109748872142250†L11-L64】.
- **WhatWeb:** fingerprints web applications and identifies technologies【109748872142250†L11-L64】.

## Port scanning with Nmap

`nmap -A` performs aggressive scanning, combining version detection, script scanning and OS detection【109748872142250†L11-L64】.  Use `-p-` to scan all ports when necessary.  Combine with `--script` arguments (e.g., `--script smb-protocols`) for deeper insight.

## HTTP/HTTPS enumeration

- **Directory brute‑forcing:** use tools like DirBuster or Dirb with wordlists (e.g., `common.txt`, `php.txt`, `zip.txt`) to discover hidden directories【109748872142250†L11-L64】.
- **Nikto:** scan web servers for misconfigurations and known vulnerabilities【109748872142250†L11-L64】.
- **Take notes:** record which ports host HTTP/HTTPS services, the technologies in use, and any interesting directories or responses【109748872142250†L11-L64】.

## SMB & SSH enumeration

- **SMB:** use `smbclient` or enumeration scripts (`smb-enum-shares.nse`, `smb-os-discovery.nse`) to list shares, users and OS information【109748872142250†L11-L64】.
- **SSH:** gather banners with `nc host 22` or `ssh -v host` to learn about supported algorithms and potential weaknesses【109748872142250†L11-L64】.

## Vulnerability research

- **Rapid7/Metasploit:** search modules for discovered services to identify exploits【109748872142250†L11-L64】.
- **GitHub & searchsploit:** search for public proof‑of‑concept exploits and offensive tools corresponding to the software versions found【109748872142250†L11-L64】.
- **Nessus & automated scanners:** run vulnerability scanners for a broad assessment【109748872142250†L11-L64】.

Enumeration should be thorough: probe every open service, record findings systematically and consult vulnerability databases.  Keep in mind that verbose scanning can be noisy – tune options according to your engagement rules.
