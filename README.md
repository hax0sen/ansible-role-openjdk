ansible-role-openjdk
[![CI](https://github.com/hax0sen/ansible-role-openjdk/actions/workflows/ci.yml/badge.svg)](https://github.com/hax0sen/ansible-role-openjdk/actions/workflows/ci.yml)
=========

This Ansible role simplifies the installation and configuration of OpenJDK. By default, this role installs Java 17, but you can easily select your desired Java version by modifying the following variable:
```yaml
# Adoptium openJDK release e.g jdk-17.0.1+12 https://adoptopenjdk.net/releases.html
openjdk_release_version: "jdk-17.0.8.1+1"

```

Requirements
------------
none

Role Variables
--------------
Role variables are listed under defaults/main.yml

```yaml
# Adoptium openJDK release e.g jdk-17.0.1+12 https://adoptopenjdk.net/releases.html
openjdk_release_version: "jdk-17.0.8.1+1"
openjdk_install_dir: "/opt/java"
```
------------

Example Playbook
----------------

Here are some examples of how to use this role within your playbook, either with default variables or by customizing them:

```yaml
- hosts: server
  roles:
    - role: ansible-role-openjdk
```

```yaml
- hosts: server
  vars:
    openjdk_release_version: "jdk-17.0.8.1+1"
    openjdk_install_dir: "/opt/java"
  roles:
    - ansible-role-openjdk
```
For install multiple java version
```yaml

#set in defaults/main.yml
some-variable:
  - release: jdk-17.0.8.1+1
  - release: jdk-16.0.2+7

#playbook
- hosts: server
  vars:
    openjdk_release_version: "{{ outer_item.release }}"
    openjdk_install_dir: "/opt/java"
  loop: "{{ some-variable }}"
  loop_control:
    loop_var: outer_item 
  roles:
    - ansible-role-openjdk
```
License
-------
This role is licensed under the MIT License. See the LICENSE file for details.
------------------
