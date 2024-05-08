# Vault Server

This role installs the HashiCorp Vault server. Although there are options for
a TLS and Non-TLS configuration, the configuration of the TLS certificate
are still outside the scope of this role. The certificate, key, and CA
trust chain certificates will all have to be added to the host either
before or after this role is applied.

## Requirements

There are no pre-requisite requirements for this role.  The variables set below
will help to localize the installation.

## Role Variables

The following variables are available in this role.  The default values
are shown here:

```yaml
airgap: false
hashicorp_rpm_repo_url: https://rpm.releases.hashicorp.com/RHEL/$releasever/$basearch/stable
hashicorp_gpg_key_url: https://rpm.releases.hashicorp.com/gpg
trust_repository_certs: true
enable_service: true
service_state: started
bind_addr: "0.0.0.0"
enable_tls: true
```

## Dependencies

N/A

## Example Playbook

Here is an example use of this role in for a system that is Internet-connected:

```yaml
- name: Install and Configure HashiCorp Vault
  become: true
  gather_facts: true
  hosts: vault
  roles:
    - role: vault-server
```

Here is an example for a system that is in an airgap environment:

```yaml
- name: Install and Configure HashiCorp Vault
  become: true
  gather_facts: true
  hosts: vault
  roles:
    - role: vault-server
      airgap: true
      hashicorp_rpm_repo_url: "https://repo.network.local/hashicorp/"
      hashicorp_gpg_key_url: "https://repo.network.local/certs/hashicorp.gpg"
```

## License

MIT

## Author Information

Alex Ackerman, GitHub @darkhonor
