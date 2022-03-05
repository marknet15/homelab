## Overview

A simple role to create a Cloud Init VM template in Proxmox

## Usage

```yaml
---
- hosts: proxmox
  gather_facts: yes
  roles:
    - marknet15.homelab.proxmox_template
  vars:
    pve_host: example.com
    pve_user: user@pam
    pve_password: password
    pve_node: node_name
    pve_storage: local
    vm_template:
      name: "ubuntu-focal-template"
      storage: "local:1,format=raw"
      ip_config: "ip=192.168.0.0/24"
      cloud_init_user: user
      cloud_init_password: password
```
