Workstation Setup
=========

Configure the OpenStack environment.

Requirements
------------

N/A

Role Variables
--------------

N/A

Dependencies
------------

N/A

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

```yaml
- hosts: localhost
  tasks:
  - name: Create workstation inventory
    add_host:
       name: "workstation-{{OSP_GUID}}.rhpds.opentlc.com"
       group: workstation


- hosts: workstation
  become: yes
  roles:
    - setup-workstation
```

License
-------

BSD

Author Information
------------------

Red Hat Training