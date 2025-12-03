# Ansible Role: Common Packages

[![CI](https://github.com/pluggero/ansible-role-common-pkgs/actions/workflows/ci.yml/badge.svg)](https://github.com/pluggero/ansible-role-common-pkgs/actions/workflows/ci.yml) [![Ansible Galaxy downloads](https://img.shields.io/ansible/role/d/pluggero/common_pkgs?label=Ansible%20Galaxy%20downloads&logo=ansible&color=%23096598)](https://galaxy.ansible.com/ui/standalone/roles/pluggero/common_pkgs)

An Ansible Role that installs common packages.

## Requirements

None.

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

```yaml
common_pkgs_apt:
  install: []
  remove: []
  remove_regex: []
  remove_modified_configs: false

common_pkgs_pacman:
  install: []
  remove: []
  remove_regex: []
  remove_modified_configs: false

common_pkgs_apk:
  install: []
  remove: []
  remove_regex: []
  remove_modified_configs: false
```

- `common_pkgs_<pkg_mgr>.install`: List of packages to install using the defined package manager. Supports two formats:
  - **Simple format** (string): Package name as a string (e.g., `"git"`)
  - **Object format**: Package as an object with the following fields:
    - `name`: Package name to install (required)
    - `depends`: List of packages to install first (optional) - useful for controlling which package provides a virtual package/dependency
- `common_pkgs_<pkg_mgr>.remove`: List of packages to remove using the defined package manager.
- `common_pkgs_<pkg_mgr>.remove_regex`: List of regular expression patterns to match packages for removal.
- `common_pkgs_<pkg_mgr>.remove_modified_configs`: If set to `true`, modified configuration files will be removed when the package is removed.
  - **NOTE**: This is useful for ensuring that the system is in a clean state after removing packages.

## Dependencies

None.

## Example Playbook

### Basic Usage

```yaml
- hosts: all
  roles:
    - role: pluggero.common_pkgs
      vars:
        common_pkgs_apt:
          install:
            - git
            - curl
            - vim
```

### Advanced Usage with Dependency Control

When installing packages that have virtual dependencies provided by multiple packages, you can control which provider is used:

```yaml
- hosts: all
  roles:
    - role: pluggero.common_pkgs
      vars:
        common_pkgs_apt:
          install:
            - git
            - curl
            # Object format with dependency specification
            - name: network-manager-applet
              depends:
                - lxpolkit  # Install lightweight polkit agent instead of cinnamon
```

**Use Case**: On Debian/Ubuntu systems, `network-manager-applet` requires the virtual package `polkit-1-auth-agent`, which can be provided by multiple packages (`cinnamon`, `gnome-shell`, `lxpolkit`, `mate-polkit`, etc.). By default, APT would install the first available provider (often `cinnamon`, which is very large). Using the `depends` field, you can ensure a lightweight alternative like `lxpolkit` is installed first.

### Mixed Format Example

You can mix both simple strings and object formats in the same list:

```yaml
common_pkgs_apt:
  install:
    - git                           # Simple format
    - curl                          # Simple format
    - name: network-manager-applet  # Object format
      depends:
        - lxpolkit
    - vim                           # Simple format
```

## License

MIT / BSD

## Author Information

This role was created in 2024 by Robin Plugge.
