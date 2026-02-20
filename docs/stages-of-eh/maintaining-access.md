# Maintaining Access

Once a foothold has been established, attackers often need to **maintain access** across reboots and user sessions.  This is the “post‑exploitation persistence” phase.

## Establishing persistence

Common techniques include:

- **Scheduled tasks / cron jobs:** create periodic tasks that run malware or reverse shells.
- **Startup scripts & registry:** on Windows, add entries to `HKCU\Software\Microsoft\Windows\CurrentVersion\Run` or drop shortcuts in the Startup folder.  On Linux, modify `/etc/rc.local` or create `systemd` services.
- **Service replacement:** replace or wrap legitimate services (e.g., SSH) with trojaned versions.
- **DLL hijacking & load order abuse:** place malicious DLLs in directories where applications will load them.

## Credential harvesting & reuse

Harvested credentials (from `hashdump`, `mimikatz`, etc.) allow re‑authentication even if the original exploit is patched.  Store and reuse these credentials for lateral movement.

## Pivoting and lateral movement

Establish SOCKS proxies or port‑forwarding tunnels (e.g., with Meterpreter’s `autoroute` or `ssh -D`) to access internal hosts.  This step is critical for moving deeper into the network while maintaining your initial access.

## Cleanup considerations

Persistence increases the risk of detection.  Remove or disable persistence mechanisms when they are no longer needed, and ensure actions comply with the agreed rules of engagement.
