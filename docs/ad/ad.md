# Active Directory (AD)

Active Directory (AD) is Microsoft’s directory service used to manage users, computers, groups and policies in Windows environments.  Your notes outline its architecture and several common attack techniques【61765084085766†L10-L117】.

## AD architecture

### Physical components

- **Domain controllers (DCs):** servers that host the Active Directory Domain Services (AD DS) database and respond to authentication requests【61765084085766†L10-L117】.
- **AD DS database:** stores information about users, computers, printers and other objects.  Changes replicate between DCs.

### Logical components

- **Schema:** defines object classes (users, computers, groups) and attributes【61765084085766†L10-L117】.
- **Domains:** a security boundary; all objects within a domain share a central directory database.【61765084085766†L10-L117】
- **Trees and forests:** trees are collections of domains in a contiguous namespace; forests are collections of one or more trees that share a schema and global catalogue.  Trusts connect domains and forests.
- **Organizational Units (OUs):** logical containers used to group objects and apply Group Policy.

## Common AD attacks

Your notes describe several attack paths and tools【61765084085766†L10-L117】:

### LLMNR/NBT‑NS poisoning

Link‑Local Multicast Name Resolution (LLMNR) and NetBIOS Name Service (NBT‑NS) are fallback name resolution protocols.  Attackers can respond to requests with a rogue server using Responder:

```bash
sudo responder -I tun0 -dwP
```

Captured NTLM hashes can then be cracked with `hashcat`.  Mitigation: disable LLMNR and NBT‑NS on endpoints【61765084085766†L10-L117】.

### SMB relay

SMB signing is disabled in many environments.  This allows attackers to relay captured credentials to another service using `ntlmrelayx.py`【61765084085766†L10-L117】.  Steps include:

1. Use Nmap’s `--script smb-protocols` to detect SMB signing status.
2. Edit `Responder.conf` to disable HTTP/SMB poisoning and run Responder【61765084085766†L10-L117】.
3. Launch `ntlmrelayx.py -t ldap://<dc_ip>` to relay NTLM authentication and create a new user or grant privileges.
4. Connect to the target via `psexec.py` or Metasploit to gain a shell【61765084085766†L10-L117】.

**Mitigation:** enable SMB signing and use network segmentation to prevent relays.

### IPv6 & passback attacks

In IPv6 environments, `mitm6` can spoof DHCPv6 and DNS to coerce systems to authenticate to you.  Combine with `impacket‑ntlmrelayx -6` to relay IPv6 authentication【61765084085766†L10-L117】.  “Passback” attacks abuse misconfigured devices (printers/IoT) to relay credentials back to the attacker.

### Enumeration & privilege escalation (general)

Although not fully captured in the notes, typical enumeration techniques include:

- **BloodHound/SharpHound:** collect AD graphs to identify attack paths and privilege escalation opportunities.
- **ldapsearch/ldapdomaindump:** query LDAP for users, groups and policies.
- **Kerberoasting:** request service tickets (TGS) for service accounts and crack them offline.
- **AS‑REP Roasting:** target accounts without pre‑auth to obtain encrypted credentials.
- **Pass‑the‑Hash/Ticket:** reuse NTLM hashes or Kerberos tickets (silver/golden tickets) to authenticate without the password.

Defenders should apply the principle of least privilege, enforce strong password policies, enable SMB signing, monitor for anomalous Kerberos events and regularly patch domain controllers.
