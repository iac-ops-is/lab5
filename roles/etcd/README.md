etcd
=========

This ansible galaxy role sets up and configures `etcd`, a distributed key-value store, by creating necessary user and group, setting up directories, copying installation scripts, and configuring systemd services.

Requirements
------------

No specific requirements.

Role Variables
--------------

```
# Default password for the etcd_remote_user
_etcd_default_password: postgres

# Name of the etcd installation script
_etcd_installation_script_name: install-etcd.sh

# Full path where the etcd installation script will be placed
_etcd_installation_script_path: "{{ etcd_installation_dir }}/install-etcd.sh"

# Dynamically retrieves the local IP address of the host interface specified by etcd_host_interface_name
_etcd_local_ip_address: "{{ lookup('vars', 'ansible_' + etcd_host_interface_name)['ipv4']['address'] }}"
```

```
# Version of etcd to be installed
etcd_version: v3.5.17

# Username for the remote user that will be created to run etcd
etcd_remote_user: etcd

# Directory where the etcd installation files will be placed
etcd_installation_dir: /home/xvsvg/etcd/install

# Directory where the etcd binary will be installed
etcd_binary_dir: /usr/local/bin

# Directory where the systemd unit file for etcd will be placed
etcd_systemd_dir: /etc/systemd/system

# Name of the etcd node
etcd_node_name: etcd-haproxy

# Directory where etcd will store its data
etcd_data_dir: "/var/lib/etcd/{{ etcd_node_name }}.etcd"

# Network interface name to be used for retrieving the local IP address
etcd_host_interface_name: eth0
```

```
[etcd:vars]
ansible_connection=ssh
ansible_user=xvsvg
ansible_ssh_private_key_file=/Users/xvsvg/.ssh/id_rsa
```

Dependencies
------------

No specific dependencies for this role.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

```
---
- name: Setup etcd on ubuntu 24.02
  hosts: etcd
  become: true
  roles:
    - etcd
```

License
-------

BSD
