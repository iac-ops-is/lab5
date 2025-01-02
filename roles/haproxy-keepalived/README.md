haproxy-keepalived
=========

This ansible galaxy role automates the installation and configuration of `HAProxy` and `Keepalived`, ensuring high availability and load balancing for services.

Requirements
------------

No specific requirements.

Role Variables
--------------

```
haproxy_keepalived_haproxy_cfg_path: /etc/haproxy/haproxy.cfg
haproxy_keepalived_haproxy_cfg_template: "{{ template_path }}/haproxy.cfg.j2"

haproxy_keepalived_keepalived_conf_path: /etc/keepalived/keepalived.conf
haproxy_keepalived_keepalived_conf_template: "{{ template_path }}/keepalived.conf.j2"

haproxy_keepalived_remote_user: xvsvg

haproxy_keepalived_postgresql_hosts:
  - name: pg_1
    host: 158.160.78.97
  - name: pg_2
    host: 51.250.102.166
```

Dependencies
------------

No specific dependencies for this role.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

```
- name: Setup haproxy-keepalived on ubuntu 24.02
  hosts: haproxy_keepalived
  become: true
  roles:
    - haproxy-keepalived
```

License
-------

BSD
