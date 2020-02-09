Role Name
=========

nginx: Nginx

[![Build Status](https://travis-ci.org/cmihai-ansible/nginx.svg?branch=master)](https://travis-ci.org/cmihai-ansible/nginx)

Ansible galaxy:
---------------

[https://galaxy.ansible.com/devopstoolbox.nginx](https://galaxy.ansible.com/devopstoolbox.nginx)

```bash
ansible-galaxy install devopstoolbox.nginx
```

Requirements
------------

- For RHEL, a Red Hat subscription or functional local repository.
- Ansible 2.4 or higher

Role Variables
--------------

```yaml
nginx_packages_state: present
nginx_remove_packages: true
nginx_enable_service: true
nginx_enable_selinux: true
nginx_copy_templates: true
nginx_firewall_configure: true
nginx_firewall_rules:
  - service: ssh
  - port: 3389
nginx_users:
  - user: devops
    group: docker
nginx_selinux_booleans:
  - name: ftp_home_dir
    state: true
    persistent: true
```

Dependencies
------------

- For Red Hat, subscription-manager.

Example Playbook
----------------

```yaml
---
- name: Install nginx on localhost
  hosts:
    - localhost
  connection: local

  tasks:
    - name: nginx is configured
      import_role:
        name: devopstoolbox.nginx
      vars:
        nginx_packages_state: present
        nginx_remove_packages: true
        nginx_enable_service: true
        nginx_enable_selinux: true
        nginx_copy_templates: true
        nginx_firewall_configure: true
        nginx_firewall_rules:
          - service: ssh
          - port: 3389
        nginx_users:
          - user: devops
            group: docker
        nginx_selinux_booleans:
          - name: ftp_home_dir
            state: true
            persistent: true
      tags: nginx
```

License
-------

MIT

Author Information
------------------

- [Mihai Criveti](https://www.linkedin.com/in/devopstoolbox.)
