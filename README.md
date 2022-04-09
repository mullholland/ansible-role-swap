# [swap](#swap)

|GitHub|GitLab|
|------|------|
|[![github](https://github.com/mullholland/ansible-role-swap/workflows/Ansible%20Molecule/badge.svg)](https://github.com/mullholland/ansible-role-swap/actions)|[![gitlab](https://gitlab.com/mullholland/ansible-role-swap/badges/master/pipeline.svg)](https://gitlab.com/mullholland/ansible-role-swap)|[![quality](https://img.shields.io/ansible/quality/unset)](https://galaxy.ansible.com/mullholland/swap)|

description

## [Role Variables](#role-variables)

These variables are set in `defaults/main.yml`:
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


## [Example Playbook](#example-playbook)

This example is taken from `molecule/default/converge.yml` and is tested on each push, pull request and release.
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





## [Compatibility](#compatibility)

This role has been tested on these [container images](https://hub.docker.com/u/mullholland):

-   [debian9](https://hub.docker.com/r/mullholland/docker-molecule-debian9)
-   [debian10](https://hub.docker.com/r/mullholland/docker-molecule-debian10)
-   [debian11](https://hub.docker.com/r/mullholland/docker-molecule-debian11)
-   [ubuntu1804](https://hub.docker.com/r/mullholland/docker-molecule-ubuntu1804)
-   [ubuntu2004](https://hub.docker.com/r/mullholland/docker-molecule-ubuntu2004)
-   [centos7](https://hub.docker.com/r/mullholland/docker-molecule-centos7)
-   [centos-stream8](https://hub.docker.com/r/mullholland/docker-molecule-centos-stream8)
-   [centos-stream9](https://hub.docker.com/r/mullholland/docker-molecule-centos-stream9)
-   [ubi8](https://hub.docker.com/r/mullholland/docker-molecule-ubi8)
-   [fedora34](https://hub.docker.com/r/mullholland/docker-molecule-fedora34)
-   [fedora35](https://hub.docker.com/r/mullholland/docker-molecule-fedora35)
-   [amazonlinux](https://hub.docker.com/r/mullholland/docker-molecule-amazonlinux)
-   [rockylinux8](https://hub.docker.com/r/mullholland/docker-molecule-rockylinux8)
-   [almalinux8](https://hub.docker.com/r/mullholland/docker-molecule-almalinux8)

The minimum version of Ansible required is 2.10, tests have been done to:

-   The previous versions.
-   The current version.
-   The [devel](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html#installing-devel-from-github-with-pip) version.





If you find issues, please register them in [GitHub](https://github.com/mullholland/ansible-role-swap/issues)

## [License](#license)

MIT


## [Author Information](#author-information)

[Mullholland](https://github.com/mullholland)

## [Special Thanks](#special-thanks)

Template inspired by [Robert de Bock](https://github.com/robertdebock)
