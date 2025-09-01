# My Homelab Infrastructure

This repository documents my homelab, which I use to practice and showcase skills in **virtualization, containerization, storage, and systems administration**.  
It serves as a personal lab environment where I deploy services, experiment with automation, and simulate production-like workloads.

---

## 🔹 Hardware Environment

- **Server**: Supermicro H12SSL-NT  
- **CPU**: AMD EPYC 7543 (32 cores, 64 threads)  
- **Memory**: 256 GiB DDR4 ECC (Multi-bit)  

---

## 🔹 Storage Overview

| Storage Pool | Drives | Controller / HBA | Purpose | Notes |
|--------------|--------|-----------------|---------|-------|
| **Unraid Array** | 10 × 14 TB WD HDD | Genuine LSI 6Gbps SAS HBA | Bulk storage, media, backups | Parity-protected array for fault tolerance |
| **Unraid Cache** | 4 × 4 TB Crucial NVMe SSD | Direct NVMe slots | High-speed caching for Unraid | Performance-sensitive workloads |
| **TrueNAS VM** | 10 × 18 TB Seagate HDD | LSI 9300-8e 12Gbps 8-lane external SAS HBA (passed through) | Enterprise-grade storage VM | ZFS RAIDZ2, hosted in Supermicro CSE-847 36-Bay chassis |

---

## 🔹 Architecture Overview

```mermaid
graph TD
  Internet --> Router[Router]
  Router --> Switch[Gigabit Switch]
  Switch --> Unraid[Unraid Server]

  Unraid --> Docker[Docker Containers]
  Unraid --> VMs[Virtual Machines]
  Unraid --> Shares[Network Shares]

  Docker --> Nextcloud[Nextcloud]
  Docker --> DB[Databases]
  Docker --> Tunnel[Cloudflare Tunnel]

  VMs --> UbuntuMain[Ubuntu (Main Workstation)]
  VMs --> UbuntuServer[Ubuntu Server (ntfy)]
  VMs --> UbuntuDesktop[Ubuntu Desktop (Testing)]
  VMs --> Windows[Windows VM]
  VMs --> HA[Home Assistant]
  VMs --> TrueNAS[TrueNAS (10x18TB RAIDZ2 via LSI 9300-8e)]
