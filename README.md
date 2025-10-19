# My Homelab Infrastructure

This repository documents my homelab, which I use to practice and showcase skills in **virtualization, containerization, storage, and systems administration**.  
It serves as a personal lab environment where I deploy services, experiment with automation, and simulate production-like workloads.

---

## 🔹 Hardware Environment

- **Server**: Supermicro H12SSL-NT  
- **CPU**: AMD EPYC 7543 (32 cores, 64 threads)  
- **Memory**: 256 GiB DDR4 ECC (Multi-bit)  

---
## 🔹 Local LLM Deployment

LM Studio Integration: Deployed local Large Language Models on high-performance AMD Ryzen AI Max+ hardware for personal experiments and automation.

Use Cases:

- **Automating system monitoring and log analysis
- **Generating scripts and command sequences for infrastructure tasks
- **Natural language interaction with homelab services and dashboards

## 🔹 AI-Enhanced Automation

- **Task Scheduling & Automation: Combined Celery and LLM-based reasoning to trigger system actions intelligently.
- **Data Processing Pipelines: Used LLMs for structured/unstructured data analysis from logs, web scraping, and system metrics.
- **Integration with Existing Services: LLM workflows interact with Docker containers, VMs, and monitoring tools for real-time insights and suggestions.

## 🔹 Skills Demonstrated

- **Local LLM deployment and optimization on high-core-count hardware
- **Python scripting for AI integration with backend services
- **Automating repetitive infrastructure tasks using intelligent agents=
- **Experimentation with offline AI inference for secure, low-latency workflows
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

  VMs --> UbuntuMain[Ubuntu Main Workstation]
  VMs --> UbuntuServer[Ubuntu Server ntfy]
  VMs --> UbuntuDesktop[Ubuntu Desktop Testing]
  VMs --> Windows[Windows VM]
  VMs --> HA[Home Assistant]
  VMs --> TrueNAS[TrueNAS 10x18TB RAIDZ2 via LSI 9300-8e]

``````

---

## 🔹 Services & Projects

### Docker
- **Nextcloud**: Self-hosted file cloud and collaboration platform  
- **Databases**: Backends for applications (Postgres, MariaDB, MongoDB as needed)  
- **Cloudflare Tunnel**: Secure remote access without port forwarding  

### Virtual Machines
- **Ubuntu (Main Workstation)**: Daily-use environment  
- **Ubuntu Server (ntfy)**: Self-hosted push notification service  
- **Ubuntu Desktop (Testing)**: Sandbox for Linux desktop testing  
- **Windows VM**: Isolated workloads and software testing  
- **Home Assistant**: Smart home automation hub  
- **TrueNAS**: Dedicated storage VM  
  - 10 × 18 TB Seagate drives with **ZFS RAIDZ2**  
  - Connected via **LSI 9300-8e SAS HBA** passthrough  
  - Hosted in **Supermicro CSE-847 36-Bay 4U chassis**  

### Network Shares
- **Bulk Storage (Unraid)**: 10 × 14 TB WD HDDs on **LSI 6Gbps SAS HBA**  
- **High-Speed Cache (Unraid)**: 4 × Crucial 4 TB NVMe SSDs  
- **Enterprise Storage (TrueNAS)**: 10 × 18 TB Seagate drives in ZFS RAIDZ2 (HBA passthrough)  

---

## 🔹 Skills Demonstrated

### Virtualization & Systems
- VM provisioning and management on Unraid  
- PCIe/HBA passthrough for near-native performance in VMs  
- Multi-OS environment (Linux server/desktop, Windows, BSD-based TrueNAS)  

### Containerization
- Service orchestration with Docker Compose  
- Application hosting (Nextcloud, databases, tunnels)  

### Storage & Networking
- **ZFS RAIDZ2**: redundancy, checksumming, and data integrity  
- Hybrid storage architecture: Unraid + ZFS (bulk + enterprise storage)  
- Enterprise hardware: dual LSI HBAs, 36-bay chassis, NVMe cache tiering  
- Network share provisioning (SMB/NFS)  

### Security & Remote Access
- Cloudflare Tunnel integration for secure service exposure  
- Isolated workloads in VMs for segmentation  

### Monitoring & Observability
- Uptime tracking, metrics collection, and dashboards  
- Notifications with **ntfy** for real-time alerts  

### Automation
- Infrastructure-as-Code with YAML configs  
- GitHub for version control of configurations  

---

## 🔹 Goals of This Homelab

- Operate a **production-like environment** for continuous learning  
- Explore **advanced storage concepts** (ZFS RAIDZ2, NVMe caching, Unraid parity)  
- Enhance **automation and orchestration** skills (Kubernetes, Ansible in future plans)  
- Strengthen expertise in **DevOps, SRE, and enterprise storage administration**  
