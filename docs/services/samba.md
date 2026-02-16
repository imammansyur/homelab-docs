### Samba

General info:

- VMID: 101
- Name: samba
- Type: VM
- OS: Alpine Linux 3.22.3

Resources:

- CPU usage: 1% of 1 CPU
- RAM usage: 160 MiB - 1.8 GiB of 2 GiB
- Storage:
    - Bootdisk size: 15 GiB
        - Location: local-lvm:vm-101-disk-0
    - Shared data: 1 TB HDD through Proxmox

Networking:

- IP address: 192.168.1.111/24

Common guide & troubleshooting:

- Disk passthrough on Proxmox (WIP)
