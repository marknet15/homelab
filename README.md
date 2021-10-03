# HomeLab Ansible Collection

An Ansible collection for the provisioning of my internal home lab and for general learning purposes.

## Usage

To install the collection run:

```sh
ansible-galaxy collection install git@github.com:marknet15/homelab.git
```

To include a role, simply specify the fully qualified role name, for example:

```yml
include_role: marknet15.homelab.docker_install
```

To run a playbook from the collection:

```sh
ansible-playbook marknet15.homelab.apt_upgrade.yml -i inventory
```

## Requirements

At least Ansible v2.9+ is required.
