# ansible-syncthing (work in progress)

Collection of Ansible definitions to manage [Synthing](https://syncthing.net)
nodes.

## Features

- [X] Deploy Syncthing to headless machines
- [ ] Configure the known devices
- [ ] Configure the shared folders

## Requirements

[Setup Ansible](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html)
on the host.

The target machines must be accessible to Ansible.
Simply make sure you can SSH to them without password (either through your own
SSH public key or SSH keyring).

Tested against a Raspberry Pi 1B rev2.

## Usage

Assuming you have a local inventory, e.g. copy `hosts.example` to `hosts` and
list your own target machines for the `syncthing` group.

```
% ansible-playbook -i hosts site.yaml
```
