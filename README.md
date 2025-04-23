# Ansible Role: Common Packages

[![CI](https://github.com/pluggero/ansible-role-common-pkgs/actions/workflows/ci.yml/badge.svg)](https://github.com/pluggero/ansible-role-common-pkgs/actions/workflows/ci.yml) [![Ansible Galaxy downloads](https://img.shields.io/ansible/role/d/pluggero/common_pkgs?label=Ansible%20Galaxy%20downloads&logo=ansible&color=%23096598)](https://galaxy.ansible.com/ui/standalone/roles/pluggero/common_pkgs)

An Ansible Role that installs common packages.

## Requirements

None.

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

```yaml
common_pkgs_pacman: []
common_pkgs_apt: []
```

- This is a list of common packages that should be installed with the package manager of the target system.

## Dependencies

None.

## Example Playbook

```yaml
- hosts: all
  roles:
    - pluggero.common_pkgs
```

## License

MIT / BSD

## Author Information

This role was created in 2024 by Robin Plugge.
