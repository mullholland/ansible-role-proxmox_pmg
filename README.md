# [proxmox_pmg](#proxmox_pmg)

Configure Proxmox Mailgateway Repositories

|GitHub|GitLab|Quality|Downloads|Version|
|------|------|-------|---------|-------|
|[![github](https://github.com/mullholland/ansible-role-proxmox_pmg/workflows/Ansible%20Molecule/badge.svg)](https://github.com/mullholland/ansible-role-proxmox_pmg/actions)|[![gitlab](https://gitlab.com/opensourceunicorn/ansible-role-proxmox_pmg/badges/master/pipeline.svg)](https://gitlab.com/opensourceunicorn/ansible-role-proxmox_pmg)|[![quality](https://img.shields.io/ansible/quality/60153)](https://galaxy.ansible.com/mullholland/proxmox_pmg)|[![downloads](https://img.shields.io/ansible/role/d/60153)](https://galaxy.ansible.com/mullholland/proxmox_pmg)|[![Version](https://img.shields.io/github/release/mullholland/ansible-role-proxmox_pmg.svg)](https://github.com/mullholland/ansible-role-proxmox_pmg/releases/)|

## [Example Playbook](#example-playbook)

This example is taken from [`molecule/default/converge.yml`](https://github.com/mullholland/ansible-role-proxmox_pmg/blob/master/molecule/default/converge.yml) and is tested on each push, pull request and release.

```yaml
---
- name: Converge
  hosts: all
  become: true
  gather_facts: true
  # vars:
  #   example_var: "value"
  roles:
    - role: "mullholland.proxmox_pmg"
```

The machine needs to be prepared. In CI this is done using [`molecule/default/prepare.yml`](https://github.com/mullholland/ansible-role-proxmox_pmg/blob/master/molecule/default/prepare.yml):

```yaml
---
- name: Prepare
  hosts: all
  become: true
  gather_facts: true

  tasks:
    - name: Copy PVE Repository Template
      ansible.builtin.copy:
        content: |
            deb https://enterprise.proxmox.com/debian/pmg {{ ansible_distribution_release }} pmg-enterprise
        dest: /etc/apt/sources.list.d/pmg-enterprise.list
```


## [Role Variables](#role-variables)

The default values for the variables are set in [`defaults/main.yml`](https://github.com/mullholland/ansible-role-proxmox_pmg/blob/master/defaults/main.yml):

```yaml
---
# Mostly tested and planned for Proxmox Mail Gateway 7+/Debian 11 Bullseye
# Older versions may work

# https://pmg.proxmox.com/docs/installation.html#secureapt
proxmox_pmg_repository_key: "https://enterprise.proxmox.com/debian/proxmox-release-{{ ansible_distribution_release }}.gpg"

# manages the Proxmox /etc/apt/sources.list
proxmox_pmg_enable_default_repository: true

# Disable Enterprise Repository
# https://pve.proxmox.com/wiki/Package_Repositories#sysadmin_enterprise_repo
proxmox_pmg_enable_enterprise_repository: false

# Enable the no subscription repository
# https://pve.proxmox.com/wiki/Package_Repositories#sysadmin_no_subscription_repo
# NOT recommended for production use
proxmox_pmg_enable_no_subscription_repository: true
```

## [Requirements](#requirements)

- pip packages listed in [requirements.txt](https://github.com/mullholland/ansible-role-proxmox_pmg/blob/master/requirements.txt).


## [Context](#context)

This role is a part of many compatible roles. Have a look at [the documentation of these roles](https://mullholland.net) for further information.

Here is an overview of related roles:
![dependencies](https://raw.githubusercontent.com/mullholland/ansible-role-proxmox_pmg/png/requirements.png "Dependencies")

## [Compatibility](#compatibility)

This role has been tested on these [container images](https://hub.docker.com/u/mullholland):

|container|tags|
|---------|----|
|[Debian](https://hub.docker.com/repository/docker/mullholland/docker-debian-systemd/general)|all|

The minimum version of Ansible required is 2.10, tests have been done to:

- The previous version.
- The current version.
- The development version.

If you find issues, please register them in [GitHub](https://github.com/mullholland/ansible-role-proxmox_pmg/issues)

## [License](#license)

[MIT](https://github.com/mullholland/ansible-role-proxmox_pmg/blob/master/LICENSE).

## [Author Information](#author-information)

[Mullholland](https://mullholland.net)

Please consider [sponsoring me](https://github.com/sponsors/mullholland).
