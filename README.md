# Ansible Role: Common Packages

[![CI](https://github.com/pluggero/ansible-role-common-pkgs/actions/workflows/ci.yml/badge.svg)](https://github.com/pluggero/ansible-role-common-pkgs/actions/workflows/ci.yml) [![Ansible role downloads](https://img.shields.io/ansible/role/d/pluggero/common_pkgs)](https://galaxy.ansible.com/ui/standalone/roles/pluggero/common_pkgs)

An Ansible Role that installs common packages.

## Requirements

None.

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

```yaml
common_pkgs_host: []
common_pkgs_pip_host: []
common_pkgs_go_host: []
common_pkgs_git_repos_host: []
```

In addition to the standardized packages that are defined for the respective distributions in `/vars`, host-specific packages can be defined with the variables shown above.

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
