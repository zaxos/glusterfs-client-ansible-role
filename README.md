[![Build Status](https://travis-ci.org/zaxos/glusterfs-client-ansible-role.svg?branch=master)](https://travis-ci.org/zaxos/glusterfs-client-ansible-role)
[![Ansible Galaxy](https://img.shields.io/badge/galaxy-_zaxos.glusterfs--client--ansible--role-blue.svg)](https://galaxy.ansible.com/zaxos/glusterfs-client-ansible-role/)

glusterfs-client-ansible-role
=============================

Ansible role to mount GlusterFS volumes.

Requirements
------------
* centos/rhel 7
* ansible >= 2.2

Installation
------------
```
$ ansible-galaxy install zaxos.glusterfs-client-ansible-role
```

Example Playbook
----------------
```yaml
- hosts: servers
  vars:
    glusterfs_version: "3.9"
    glusterfs_volumes:
    - volume: volume1
      state: present
      nodes:
        - node1.glusterfs.example
        - node2.glusterfs.example
      mount:
        path: /mnt/volume1
        owner: exampleuser
        group: examplegroup
        mode: "0770"
            
  roles:
    - role: zaxos.glusterfs-client-ansible-role
```

Example volume
--------------
```yaml
- volume: example
  state: present/absent  # required #
  nodes:  # required, glusterfs nodes list #
    - node1
    - node2
    - ...
  mount:  # required #
    path:  # required #
    owner:  # optional, default is "root" #
    group:  # optional, default is "root" #
    mode:  # optional, default is "0755" #
    options:  # optional, default is "defaults,_netdev,backupvolfile-server=..." #
```

Role Variables
--------------
Some variables that require review:
- `glusterfs_version`: GlusterFS client version to be installed using CentOS Storage SIG Packages. Default is the currently latest available version "3.9".
- `glusterfs_volumes`: List of volumes.
