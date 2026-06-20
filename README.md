<!-- BEGIN_ANSIBLE_DOCS -->
# Ansible Role: ansible_bin
Manage binaries and scripts install, update, download, ...


## Requirements

| Platform | Versions |
| -------- | -------- |
| Debian | bullseye, bookworm |
| EL | 8 |

## Role Arguments


### Entrypoint: main

Manage binaries and scripts install, update, download, ...

Setup custom APT repositories (Debian systems only)

Install base packages list (Debian and RHEL-based systems)

Provides tasks to upgrade packages on manages systems, supporting an exclusion list (Debian and RHEL-based systems)

|Option|Description|Type|Required|Default|
|---|---|---|---|---|
| ansible_bin_apt_custom_repositories_common | List of custom apt repositories that must be present on managed nodes There are two lists available, which are merged on run. Useful for instance to have one common in group_vars and another specific for each host This one is intended to be the common list | list of dicts of 'ansible_bin_apt_custom_repositories_common' options | no | [] |
| ansible_bin_apt_custom_repositories | List of custom apt repositories that must be present on managed nodes There are two lists available, which are merged on run. Useful for instance to have one common in group_vars and another specific for each host This one is intended to be a more specific list | list of dicts of 'ansible_bin_apt_custom_repositories' options | no | [] |
| ansible_bin_dnf_packages_common | List of rpm packages (installed through dnf) that must be present on managed nodes There are two lists available, which are merged on run. Useful for instance to have one common in group_vars and another specific for each host This one is intended to be the common list | list of 'str' | no | [] |
| ansible_bin_dnf_packages | List of rpm packages (installed through dnf) that must be present on managed nodes There are two lists available, which are merged on run. Useful for instance to have one common in group_vars and another specific for each host This one is intended to be a more specific list | list of 'str' | no | [] |
| ansible_bin_apt_packages_common | List of dpkg packages (installed through apt) that must be present on managed nodes There are two lists available, which are merged on run. Useful for instance to have one common in group_vars and another specific for each host This one is intended to be the common list | list of 'str' | no | [] |
| ansible_bin_apt_packages | List of dpkg packages (installed through apt) that must be present on managed nodes There are two lists available, which are merged on run. Useful for instance to have one common in group_vars and another specific for each host This one is intended to be a more specific list | list of 'str' | no | [] |
| ansible_bin_packages_versionlock_common | List of packages to exclude from update tasks There are two lists available, which are merged on run. Useful for instance to have one common in group_vars and another specific for each host This one is intended to be the common list | list of 'str' | no | [] |
| ansible_bin_packages_versionlock | List of packages to exclude from update tasks There are two lists available, which are merged on run. Useful for instance to have one common in group_vars and another specific for each host This one is intended to be a more specific list | list of 'str' | no | [] |
| ansible_bin_autoreboot | Whether to automatically reboot systems after updates, if required | bool | no | False |
| ansible_bin_flatpak_custom_repositories_common | List of custom flatpak remotes that must be present on managed nodes There are two lists available, which are merged on run. Useful for instance to have one common in group_vars and another specific for each host This one is intended to be the common list | list of dicts of 'ansible_bin_flatpak_custom_repositories_common' options | no | [{'repoName': 'flathub', 'repoUrl': 'https://dl.flathub.org/repo/flathub.flatpakrepo', 'repoInstallMethod': 'user'}] |
| ansible_bin_flatpak_custom_repositories | List of custom flatpak remotes that must be present on managed nodes There are two lists available, which are merged on run. Useful for instance to have one common in group_vars and another specific for each host This one is intended to be a more specific list | list of dicts of 'ansible_bin_flatpak_custom_repositories' options | no | [{'repoName': 'flathub', 'repoUrl': 'https://dl.flathub.org/repo/flathub.flatpakrepo', 'repoInstallMethod': 'user'}] |
| ansible_bin_flatpak_packages_common | List of flatpak packages that must be present on managed nodes There are two lists available, which are merged on run. Useful for instance to have one common in group_vars and another specific for each host This one is intended to be the common list | list of 'str' | no | [] |
| ansible_bin_flatpak_packages | List of flatpak packages that must be present on managed nodes There are two lists available, which are merged on run. Useful for instance to have one common in group_vars and another specific for each host This one is intended to be a more specific list | list of 'str' | no | [] |

#### Options for main > ansible_bin_apt_custom_repositories_common

|Option|Description|Type|Required|Default|
|---|---|---|---|---|
| repoName | Repository name. doesn't need to match anything | str | yes |  |
| repoBaseUrl | Repository base URL | str | yes |  |
| repoTypes | Repository types (binaries, sources or both) | list of '' | no | ['deb'] |
| repoDistributionReleases | Repository releases / suites (bookworm, stable, ...) | list of '' | no | ['/'] |
| repoComponents | Repository components (contrib, non-free, ...) | list of '' | no | [] |
| repoArchitecture | Repository intended architectures (amd64, arm64, ...) | list of '' | no | ['amd64'] |
| repoSigningKey | Public signing key (usually GPG) used to sign repository binaries (and / or metadata). Has to be armored Key is passed as-is instead of a link for module to download as I understand there wouldn't be any verification | str | no | None |
| repoIsTrusted | Whether repository is trusted. Skips signatures verification | bool | no | None |

#### Options for main > ansible_bin_apt_custom_repositories

|Option|Description|Type|Required|Default|
|---|---|---|---|---|
| repoName | Repository name. doesn't need to match anything | str | yes |  |
| repoBaseUrl | Repository base URL | str | yes |  |
| repoTypes | Repository types (binaries, sources or both) | list of '' | no | ['deb'] |
| repoDistributionReleases | Repository releases / suites (bookworm, stable, ...) | list of '' | no | ['/'] |
| repoComponents | Repository components (contrib, non-free, ...) | list of '' | no | [] |
| repoArchitecture | Repository intended architectures (amd64, arm64, ...) | list of '' | no | ['amd64'] |
| repoSigningKey | Public signing key (usually GPG) used to sign repository binaries (and / or metadata). Has to be armored Key is passed as-is instead of a link for module to download as I understand there wouldn't be any verification | str | no | None |
| repoIsTrusted | Whether repository is trusted. Skips signatures verification | bool | no | None |

#### Options for main > ansible_bin_flatpak_custom_repositories_common

|Option|Description|Type|Required|Default|
|---|---|---|---|---|
| repoName | Repository (remote) name. doesn't need to match anything | str | yes |  |
| repoUrl | Repository (remote) URL | str | yes |  |
| repoInstallMethod | Whether repository (remote) is installed globally (system) or only for the current user | str | no | user |

#### Options for main > ansible_bin_flatpak_custom_repositories

|Option|Description|Type|Required|Default|
|---|---|---|---|---|
| repoName | Repository (remote) name. doesn't need to match anything | str | yes |  |
| repoUrl | Repository (remote) URL | str | yes |  |
| repoInstallMethod | Whether repository (remote) is installed globally (system) or only for the current user | str | no | user |

#### Choices for main > ansible_bin_apt_custom_repositories_common > repoTypes

|Choice|
|---|
| deb |
| deb-src |

#### Choices for main > ansible_bin_apt_custom_repositories > repoTypes

|Choice|
|---|
| deb |
| deb-src |



## Dependencies
None.

## Example Playbook

```
- hosts: all
  tasks:
    - name: Importing role: ansible_bin
      ansible.builtin.import_role:
        name: ansible_bin
      vars:
```

## License

MIT

## Author and Project Information
Pierre TOURON

<!-- END_ANSIBLE_DOCS -->
