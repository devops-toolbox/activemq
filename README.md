Role Name
=========

activemq: Activemq

[![Build Status](https://travis-ci.org/cmihai-ansible/activemq.svg?branch=master)](https://travis-ci.org/cmihai-ansible/activemq)

Ansible galaxy:
---------------

[https://galaxy.ansible.com/devops-toolbox.activemq](https://galaxy.ansible.com/devops-toolbox.activemq)

```bash
ansible-galaxy install devops-toolbox.activemq
```

Requirements
------------

- For RHEL, a Red Hat subscription or functional local repository.
- Ansible 2.4 or higher

Role Variables
--------------

```yaml
activemq_packages_state: present
activemq_remove_packages: true
activemq_enable_service: true
activemq_enable_selinux: true
activemq_copy_templates: true
activemq_firewall_configure: true
activemq_firewall_rules:
  - service: ssh
  - port: 3389
activemq_users:
  - user: devops
    group: docker
activemq_selinux_booleans:
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
- name: Install activemq on localhost
  hosts:
    - localhost
  connection: local

  tasks:
    - name: activemq is configured
      import_role:
        name: devops-toolbox.activemq
      vars:
        activemq_packages_state: present
        activemq_remove_packages: true
        activemq_enable_service: true
        activemq_enable_selinux: true
        activemq_copy_templates: true
        activemq_firewall_configure: true
        activemq_firewall_rules:
          - service: ssh
          - port: 3389
        activemq_users:
          - user: devops
            group: docker
        activemq_selinux_booleans:
          - name: ftp_home_dir
            state: true
            persistent: true
      tags: activemq
```

License
-------

MIT

Author Information
------------------

- [Mihai Criveti](https://www.linkedin.com/in/devops-toolbox.)
