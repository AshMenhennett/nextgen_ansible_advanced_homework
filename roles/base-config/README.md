Base Server Configuration
=========

Configure the Base System

Requirements
------------

N/A

Role Variables
--------------

```yaml
own_repo_path: example.com
base_packages: []
```

Dependencies
------------

N/A

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

```yaml
- name: setup system
  hosts: frontends
  become: yes
  roles:
    - {name: base-config, tags: base-config}
```

License
-------

BSD

Author Information
------------------

Red Hat Training