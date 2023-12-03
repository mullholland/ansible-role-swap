# [Ansible role swap](#swap)

Configure swapfile

|GitHub|Downloads|Version|
|------|---------|-------|
|[![github](https://github.com/mullholland/ansible-role-swap/actions/workflows/molecule.yml/badge.svg)](https://github.com/mullholland/ansible-role-swap/actions/workflows/molecule.yml)|[![downloads](https://img.shields.io/ansible/role/d/mullholland/swap)](https://galaxy.ansible.com/mullholland/swap)|[![Version](https://img.shields.io/github/release/mullholland/ansible-role-swap.svg)](https://github.com/mullholland/ansible-role-swap/releases/)|
## [Example Playbook](#example-playbook)

This example is taken from [`molecule/default/converge.yml`](https://github.com/mullholland/ansible-role-swap/blob/master/molecule/default/converge.yml) and is tested on each push, pull request and release.

```yaml
---
- name: Converge
  hosts: all
  become: true
  gather_facts: true

  pre_tasks:
    - name: show virtualization type fot Ansible role testing
      ansible.builtin.debug:
        msg: "{{ ansible_virtualization_type }}"

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
|[EL](https://hub.docker.com/r/mullholland/enterpriselinux)|all|
|[Amazon](https://hub.docker.com/r/mullholland/amazonlinux)|Candidate|
|[Fedora](https://hub.docker.com/r/mullholland/fedora/)|all|
|[Ubuntu](https://hub.docker.com/r/mullholland/ubuntu)|all|
|[Debian](https://hub.docker.com/r/mullholland/debian)|all|

The minimum version of Ansible required is 2.10, tests have been done to:

- The previous version.
- The current version.
- The development version.

If you find issues, please register them in [GitHub](https://github.com/mullholland/ansible-role-swap/issues).

## [License](#license)

[MIT](https://github.com/mullholland/ansible-role-swap/blob/master/LICENSE).

## [Author Information](#author-information)

[Mullholland](https://mullholland.net)
