# Kali Command

This chapter summarises the essential Kali Linux commands recorded in your notes.  These commands help you manage services, inspect network configuration, manage users and quickly host files【921587106537029†L11-L24】.

## Service management

- **Start/stop Apache:** `sudo service apache2 start` and `sudo service apache2 stop` control the built‑in Apache web server【921587106537029†L11-L24】.  On systems using systemd, you can instead use `sudo systemctl start apache2` and `sudo systemctl stop apache2`【921587106537029†L11-L24】.

## Network diagnostics

- **View routing table:** `ip r` displays the kernel’s routing table; the older `route` command offers similar output【921587106537029†L11-L24】.
- **List neighbours:** `ip n` shows ARP/Neighbour cache entries, letting you see devices the system has communicated with【921587106537029†L11-L24】.

## User and group management

- **Create a new user:** `sudo adduser <username>` creates a user and prompts for details such as password and full name【921587106537029†L11-L24】.
- **Create a group:** `sudo groupadd <groupname>` adds a new group【921587106537029†L11-L24】.
- **Modify permissions:** `chmod` changes file modes.  For example, `chmod +x script.sh` makes a script executable【921587106537029†L11-L24】.
- **Change ownership:** `chown user:group file` assigns new owner and group.

## Hosting files quickly

- **Python HTTP server:** to share the contents of a directory over HTTP, run `python3 -m http.server <port>` from inside that directory【921587106537029†L11-L24】.

## Git basics

- **Clone a repository:** `git clone <repository‑URL>` pulls down a remote Git repository for local work【921587106537029†L11-L24】.

Keep these snippets handy during labs and assessments – they’re the building blocks for service setup, system enumeration and environment preparation.
