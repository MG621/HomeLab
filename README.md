# Ubuntu Self-Hosted Homelab Infrastructure

A production-style, containerized Linux home server environment architected for media streaming, retro gaming network shares, local network security, and 24/7 system monitoring.

---

## Architecture & Core Stack
* **Operating System:** Ubuntu Server (Headless)
* **Container Management:** Docker & Docker Compose, managed via Portainer
* **Network Security:** UFW (Uncomplicated Firewall), Fail2Ban, and Passwordless SSH (Key-based auth with disabled root login)

---

## Services & Infrastructure Breakdown

### 1. Media & Storage
* **Plex & Jellyfin:** Self-hosted media streaming servers configured for local library indexing and multi-device playback.
* **Samba (SMB) File Server:** Configured to host network shares, acting as the storage backend to stream retro PlayStation 2 ISOs directly to legacy hardware via **Open PS2 Loader (OPL)**.

### 2. Network-Wide Privacy & Services
* **Pi-hole:** Network-wide DNS sinkhole acting as the primary local DNS server to block ads, telemetry, and tracking at the network layer.
* **Minecraft Server:** Dedicated multiplayer server containerized with persistent volume storage for automated backups.
### Tailscale VPN & Secure Remote Access
* **Zero-Trust Mesh Network:** Integrated with **Tailscale** (built on WireGuard) to establish a secure, encrypted virtual private network across all remote devices without exposing raw ports to the public internet.
* **Remote Connectivity:** Enables seamless, passwordless remote access to the Ubuntu server, Docker management tools, and media shares from anywhere in the world.
* **Controlled Access:** Utilized for secure peer-to-peer connectivity, allowing trusted external users (such as friends joining the Minecraft server) to connect to internal local services safely and privately.

### 3. Monitoring & Reliability
* **Glances:** Real-time, cross-platform system performance monitoring (CPU, RAM, disk I/O, and network bandwidth utilization).
* **Uptime Kuma:** Self-hosted uptime monitoring tool tracking service health and container status with alert webhooks.
* **Network UPS Tools (NUT):** Integrated power management monitoring uninterruptible power supply (UPS) status to ensure graceful shutdowns during power anomalies.

### 4. Container Management & Access
* **Portainer:** Lightweight container management GUI providing visibility into active Docker stacks, volumes, and logs.
* **SSH Security Hardening:** Password authentication entirely disabled; access restricted strictly to ed25519 SSH keys.

---

## Repository Structure
```text
├── docker-compose.yml       # Centralized container stack definitions
├── scripts/                 # Automated backup and maintenance utilities
├── ufw/                     # Firewall rule templates and hardening notes
└── README.md                # Infrastructure documentation
