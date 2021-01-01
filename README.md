# ansible-syncthing (work in progress)

Collection of Ansible definitions to manage [Synthing](https://syncthing.net)
nodes.

## Features

- [X] Deploy Syncthing to headless machines
- [X] Configure the known devices
- [X] Configure the shared folders
- [ ] Refer to headless machines by their host, not their device ID
- [ ] Automatically reference local host in shared folders' devices

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

See `host_vars/raspberrypi.example` for the required (and an example of) variables.

```
% ansible-playbook -i hosts install-syncthing.yaml
% ansible-playbook -i hosts configure-devices.yaml
% ansible-playbook -i hosts configure-folders.yaml
```

## Caveats

- The installation playbook is idempotent, but we don't know know the target's
  device ID in advance (we let Syncthing generate everything). This means the
  steps described above are not 100% automatic. After having installed Syncthing
  on all targets, we have to stop and fill in the device ID's in the host
  variables.

- Another effect of not knowing what each target's device ID is, is that the
  host variables defining shared folders must list all devices *including the
  local one*.
