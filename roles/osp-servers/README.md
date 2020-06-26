OSP Instance Provisioning
=========

Provision the OpenStack Instances.

Requirements
------------

N/A

Role Variables
--------------

```yaml
---
# vars file for osp.servers
osp_servers:
  frontend:
    name: frontend
    state: present
    image: rhel-guest
    key_name: ansible_ssh
    flavor: m1.medium
    security_group: frontend
    net_interface: 
      - net-name: int_network
    int_network: int_network
    ext_network: ext_network
    meta:
      - { group: frontends, deployment_name: QA}
  app1:
    name: app1
    state: present
    image: rhel-guest
    key_name: ansible_ssh
    flavor: m1.medium
    security_group: apps
    net_interface: 
      - net-name: int_network
    int_network: int_network
    ext_network: ext_network
    meta:
      - { group: apps, deployment_name: QA}
  app2:
    name: app2
    state: present
    image: rhel-guest
    key_name: ansible_ssh
    flavor: m1.medium
    security_group: apps
    net_interface: 
      - net-name: int_network
    int_network: int_network
    ext_network: ext_network
    meta:
      - { group: apps, deployment_name: QA}
  db:
    name: db
    state: present
    image: rhel-guest
    key_name: ansible_ssh
    flavor: m1.medium
    security_group: db
    net_interface: 
      - net-name: int_network
    int_network: int_network
    ext_network: ext_network
    meta:
      - { group: appdbs, deployment_name: QA}

global_userdata: |-
    #!/bin/bash
    ls -l /home/
    mkdir -p /home/cloud-user/.ssh/authorized_keys 
    curl -o /tmp/openstack.pub http://www.opentlc.com/download/ansible_bootcamp/openstack_keys/openstack.pub
    cat /tmp/openstack.pub >> /home/cloud-user/.ssh/authorized_keys 
    echo '{{extra_ssh_key}}' >> /home/cloud-user/.ssh/authorized_keys

extra_ssh_key: /root/.ssh/somekey.pub
provided_keys: lookup('file', "{{extra_ssh_key}}")

```

Dependencies
------------

N/A

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

```yaml
- hosts: localhost
  connection: local
  become: no
  gather_facts: true
  roles:
   - osp-servers
```

License
-------

BSD

Author Information
------------------

Red Hat Training