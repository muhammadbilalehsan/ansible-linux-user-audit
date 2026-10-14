# Ansible Linux User Audit

An Ansible playbook that audits local user accounts on Linux servers.

## What it reports
- Hostname, IP address, server time
- Local users in UID range 1000-60000
- Account status: Active or Disabled/Locked
- Administrator status (sudo access): Yes/No
- Contents of /etc/sudoers.d

## Requirements
- Ansible 2.9+
- SSH access to target hosts
- Sudo/root privileges on targets (read-only checks, no changes made)

## Usage
1. Copy `inventory.example` to `inventory` and add your hosts.
2. Run:

   ansible-playbook -i inventory user_audit.yml

## Notes
- This playbook is read-only and does not modify any account.
- `passwd -S` output may vary slightly between Linux distributions.
- Test on a few servers before running at scale.

## Disclaimer
Provided as-is. Review and test before using in production.
