# ansible-role-linux-user-provisioning

An Ansible role to automate Linux user provisioning, group assignment,
SSH key management, and secure deprovisioning on RHEL and Ubuntu systems.

Built from enterprise experience managing 1,200+ Linux nodes at
Tata Consultancy Services using Ansible and AWX.

---

## Requirements

- Ansible 2.10+
- Target systems: RHEL 8/9, Ubuntu 20.04/22.04
- Become (sudo) privileges on target hosts

---

## Role Variables

### defaults/main.yml

| Variable | Default | Description |
|---|---|---|
| user_groups | [developers, ops] | Groups to create on target systems |
| users | see defaults | List of users to provision |
| users_to_remove | [] | List of users to deprovision and remove |
| password_expires_days | 90 | Password expiry policy in days |
| minimum_password_length | 12 | Minimum password length enforcement |

---

## Example Playbook

```yaml
- name: Provision users on Linux servers
  hosts: linux_servers
  become: true

  roles:
    - role: ansible-role-linux-user-provisioning
      vars:
        user_groups:
          - developers
          - ops
        users:
          - username: nida_firdous
            groups:
              - developers
            shell: /bin/bash
            ssh_key: "ssh-rsa AAAA..."
        users_to_remove:
          - old_employee
```

---

## Platforms

- RHEL 8, RHEL 9
- Ubuntu 20.04 (Focal)
- Ubuntu 22.04 (Jammy)

---

## Author

Nida Firdous
- LinkedIn: linkedin.com/in/nidafirdous
- Portfolio: nida-personal.github.io/nida_firdous_devops_portfolio
