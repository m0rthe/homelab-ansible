# homelab-ansible

Ansible playbooks to set up and maintain my homelab

## What's running

- **Raspberry Pi 5** - Docker host with various self-hosted services
- **Intel NUC 10** - Proxmox with VMs
- **VMs** - Teamspeak (Debian), Home Assistant OS - more to follow

## Playbooks

| Playbook | Description |
|---|---|
| `setup-pi5.yml` | Sets up a fresh Raspberry Pi 5 from scratch |
| `update-all.yml` | Runs apt update and upgrade on all hosts |
| `shutdown-all.yml` | Gracefully shuts down all hosts and VMs |

## Requirements

- Ansible 2.15+
- SSH key copied to all target hosts: `ssh-copy-id -p 22 pi@<IP>`
- Ansible Vault password stored in `~/.vault_pass`

## Usage

```bash
# Update all hosts
ansible-playbook -i inventory/hosts.yml playbooks/update-all.yml

# Set up a fresh Pi 5
ansible-playbook -i inventory/hosts.yml playbooks/setup-pi5.yml

# Shut everything down
ansible-playbook -i inventory/hosts.yml playbooks/shutdown-all.yml
```

## Note

Sensitive values like passwords and keys are stored encrypted with Ansible Vault

## Credits

- [Ansible Documentation](https://docs.ansible.com)
- [Docker Documentation](https://docs.docker.com)