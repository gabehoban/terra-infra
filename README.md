# home-ops 🏠 🛠

Mono repository for managing my Homelab infrastructure 🏠 🛠

## Overview 📝

> [!NOTE]
> This repository is a constant work in progress and I will continue to update it as I learn more.

The goals of this repository are:

- Automate the configuration of my Homelab infrastructure and deployment of applications.
- Adhere to best practices.
- Learn and test new technologies and concepts.
- Document my Homelab setup and configuration for future reference and in case of disaster recovery.
- Share knowledge and learnings with others.

---

## <img src="https://fonts.gstatic.com/s/e/notoemoji/latest/2699_fe0f/512.gif" alt="⚙" width="20" height="20"> Hardware

| Device                          | Num | OS Disk Size | Data Disk Size                  | Ram  | OS            | Function                |
|---------------------------------|-----|--------------|---------------------------------|------|---------------|-------------------------|
| Raspberry Pi 4B+                | 3   | 256GB SD     | -                               | 2GB  | Ubuntu Server | Stratum 1 NTP, DNS, CA  |
| Beelink Mini S12 Pro            | 2   | 512GB SSD    | 1TB SSD                         | 32GB | Talos         | Kubernetes              |
| Beelink SER6 MAX                | 1   | 512GB NVME   | 1TB SSD                         | 32GB | Talos         | Kubernetes              |
| PowerEdge R710                  | 1   | 256GB USB    | 6x4TB SAS ZFS (16TB Usable)     | 64GB | UNRAID OS     | NFS + Backup Server     |
| Mikrotik RouterBoard RB3011UiAS | 1   | -            | -                               | -    | -             | Router                  |
| TPLINK TL-SG3428 Switch         | 1   | -            | -                               | -    | -             | 1GB Switch              |
| APC BR1500MS2                   | 1   | -            | -                               | -    | -             | 1500VA UPS              |

---

## Ansible Playbooks (RPI Hosts)

Ansible playbooks used to configure my Homelab infrastructure are located in the [playbooks](playbooks) directory.

| Hostname                        | OS            | Function                | Ansible Playbook                             |
|---------------------------------|---------------|-------------------------|----------------------------------------------|
| host-casio.lab4.cc              | Ubuntu Server | Primary DNS/NTP Server  | [host-casio.yaml](playbooks/host-casio.yaml) |
| host-sekio.lab4.cc              | Ubuntu Server | Backup DNS/NTP Server   | [host-sekio.yaml](playbooks/host-sekio.yaml) |
| host-autio.lab4.cc              | Ubuntu Server | Step-CA Cert Authority  | WIP                                          |
