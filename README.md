# Vault Server

This role installs the HashiCorp Vault server.

## Requirements

There are no pre-requisite requirements for this role.  The variables set below will help to localize the installation.

## Role Variables

The following variables are available in this role.  The default values are shown here:

```yaml
connected_network: true
repo_server: https://repo.homelab.local
repo_path: 'repo/hashicorp'
cert_path: 'certs/hashicorp.gpg'
enable_service: true
hostname: localhost
api_addr: "https://{{ hostname }}:8200"
cluster_addr: "https://{{ hostname }}:8201"
bind_addr: "0.0.0.0:8200"
```

## Dependencies

N/A

## Example Playbook

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

```yaml
- name: Install and Configure HashiCorp Vault
  become: true
  gather_facts: true
  hosts: vault
  roles:
    - role: vault-server
      connected_network: true
      enable_service: true
      hostname: vault.homelab.local
```

## License

MIT

## Author Information

Alex Ackerman, Twitter @Darkhonor
