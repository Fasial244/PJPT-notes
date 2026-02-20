# Reconnaissance

Reconnaissance is the first step of an engagement.  The goal is to collect as much information as possible about a target without tipping them off.  Your notes distinguish between **passive** and **active** reconnaissance and list numerous tools【833650362258024†L13-L43】.

## Passive reconnaissance

Passive techniques don’t touch the target directly; instead they rely on publicly available information.

- **OSINT:** gather data from company websites, public records, social media and breach databases.
- **Social/physical recon:** physical observation of facilities or social engineering to learn about people and processes【833650362258024†L13-L43】.
- **Email discovery:** use services like Hunter.io, phonebook.cz, emailfinder and emailhippo to enumerate employee addresses【833650362258024†L13-L43】.
- **Breaches:** check whether discovered usernames or domains appear in credential dumps (e.g., HaveIBeenPwned).

## Active reconnaissance

Active techniques involve contacting the target’s systems to learn more about their configuration.  Common tools include:

- **DNS utilities:**
  - `nslookup` and `dig` to resolve domain names and perform zone transfers【833650362258024†L13-L43】.
  - `dnsrecon` to automate DNS enumeration and uncover subdomains【833650362258024†L13-L43】.
- **Whois:** obtain domain registration data【833650362258024†L13-L43】.
- **Subdomain enumeration:** use tools like `sublist3r` and services such as crt.sh to find subdomains and hosts【833650362258024†L13-L43】.
- **Search engine dorking:** craft advanced Google queries (Google fu) to reveal hidden or sensitive information【833650362258024†L13-L43】.
- **Port scanning:** run `nmap` to identify open ports and running services【833650362258024†L13-L43】.
- **Fingerprinting:** tools such as Wappalyzer and netcat help identify web technologies and services【833650362258024†L13-L43】.

## Tips

- Combine multiple sources (DNS, WHOIS, OSINT) to build a comprehensive picture.
- Be mindful of legality and scope: passive recon is often considered safer, while active scanning should only occur with explicit authorization.
