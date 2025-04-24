# Ansible Role: Common Packages

[![CI](https://github.com/pluggero/ansible-role-common-pkgs/actions/workflows/ci.yml/badge.svg)](https://github.com/pluggero/ansible-role-common-pkgs/actions/workflows/ci.yml) [![Ansible Galaxy downloads](https://img.shields.io/ansible/role/d/pluggero/common_pkgs?label=Ansible%20Galaxy%20downloads&logo=ansible&color=%23096598)](https://galaxy.ansible.com/ui/standalone/roles/pluggero/common_pkgs)

An Ansible Role that installs common packages.

## Requirements

None.

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

```yaml
common_pkgs:
  apt:
    install: []
    remove: []
    remove_modified_configs: false
  pacman:
    install: []
    remove: []
    remove_modified_configs: false
```

- `common_pkgs.<pkg_mgr>.install`: List of packages to install using the defined package manager.
- `common_pkgs.<pkg_mgr>.remove`: List of packages to remove using the defined package manager.
- `common_pkgs.<pkg_mgr>.remove_modified_configs`: If set to `true`, modified configuration files will be removed when the package is removed.
  - **NOTE**: This is useful for ensuring that the system is in a clean state after removing packages.

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
