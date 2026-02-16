# Overview

### System Specifications

- CPU: Intel Core i5 6200U (2C/4T)
- GPU: AMD Radeon R5 M330
- RAM: 16 GB DDR3L
- Storage:
    - 500 GB HDD (OS)
        - Location:
            - SATA
            - sda (on Proxmox)
    - 1 TB HDD (Shared data)
        - Location:
            - Slimline SATA (HDD Caddy on CD bay)
            - sdb (on Proxmox)
            - scsi2 (on samba)
    - 1 TB HDD (Unplugged)
- Network: 1 Gigabit Ethernet

### Logical Topology

![Logical Topology](../img/proxmox-services.svg)
