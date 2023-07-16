# [swap](#swap)

Configure swapfile

|GitHub|GitLab|Quality|Downloads|Version|
|------|------|-------|---------|-------|
|[![github](https://github.com/mullholland/ansible-role-swap/workflows/Ansible%20Molecule/badge.svg)](https://github.com/mullholland/ansible-role-swap/actions)|[![gitlab](https://gitlab.com/opensourceunicorn/ansible-role-swap/badges/master/pipeline.svg)](https://gitlab.com/opensourceunicorn/ansible-role-swap)|[![quality](https://img.shields.io/ansible/quality/58719)](https://galaxy.ansible.com/mullholland/swap)|[![downloads](https://img.shields.io/ansible/role/d/58719)](https://galaxy.ansible.com/mullholland/swap)|[![Version](https://img.shields.io/github/release/mullholland/ansible-role-swap.svg)](https://github.com/mullholland/ansible-role-swap/releases/)|

## [Example Playbook](#example-playbook)

This example is taken from [`molecule/default/converge.yml`](https://github.com/mullholland/ansible-role-swap/blob/master/molecule/default/converge.yml) and is tested on each push, pull request and release.

```yaml
---
- name: Converge
  hosts: all
  become: true
  gather_facts: true
  # vars:
  #   example_var: "value"
  roles:
    - role: "mullholland.swap"
```

The machine needs to be prepared. In CI this is done using [`molecule/default/prepare.yml`](https://github.com/mullholland/ansible-role-swap/blob/master/molecule/default/prepare.yml):

```yaml
---
- name: Prepare
  hosts: all
  become: true
  gather_facts: true

  tasks:
    - name: Fedora | Install util-linux for fallocate
      ansible.builtin.package:
        name: "util-linux"
        state: present
      when: ansible_distribution == "Fedora"
```


## [Role Variables](#role-variables)

The default values for the variables are set in [`defaults/main.yml`](https://github.com/mullholland/ansible-role-swap/blob/master/defaults/main.yml):

```yaml
---
swap_file_name: "swap"  # Filename of the swapfile
swap_file_path: "/"  # Path of the swap (Path needs an "/" at the end)
swap_file_size: "1024"  # Size in MB
swap_file_state: "present"  # Either "present" or "absent"

# create the swapfile with:
# - "fallocate"
# - "dd"
swap_create: "fallocate"

# Configure swappiness
# if variable is empty nothing will be changed on the system
swap_swappiness: ""

# swap_vfs_cache_pressure
# if variable is empty nothing will be changed on the system
swap_vfs_cache_pressure: ""
```

## [Requirements](#requirements)

- pip packages listed in [requirements.txt](https://github.com/mullholland/ansible-role-swap/blob/master/requirements.txt).


## [Context](#context)

This role is a part of many compatible roles. Have a look at [the documentation of these roles](https://mullholland.net) for further information.

Here is an overview of related roles:
![dependencies](https://raw.githubusercontent.com/mullholland/ansible-role-swap/png/requirements.png "Dependencies")

## [Compatibility](#compatibility)

This role has been tested on these [container images](https://hub.docker.com/u/mullholland):

|container|tags|
|---------|----|
|[EL](https://hub.docker.com/repository/docker/mullholland/docker-centos-systemd/general)|all|
|[Amazon](https://hub.docker.com/repository/docker/mullholland/docker-amazonlinux-systemd/general)|Candidate|
|[Fedora](https://hub.docker.com/repository/docker/mullholland/docker-fedora-systemd/general)|all|
|[Ubuntu](https://hub.docker.com/repository/docker/mullholland/docker-ubuntu-systemd/general)|all|
|[Debian](https://hub.docker.com/repository/docker/mullholland/docker-debian-systemd/general)|all|

The minimum version of Ansible required is 2.10, tests have been done to:

- The previous version.
- The current version.
- The development version.

If you find issues, please register them in [GitHub](https://github.com/mullholland/ansible-role-swap/issues)

## [License](#license)

[MIT](https://github.com/mullholland/ansible-role-swap/blob/master/LICENSE).

## [Author Information](#author-information)

[Mullholland](https://mullholland.net)

Please consider [sponsoring me](https://github.com/sponsors/mullholland).
