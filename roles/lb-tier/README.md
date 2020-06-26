3-Tier Application Load Balancers
=========

Configure the HAProxy Application Load Balancers.

Requirements
------------

N/A

Role Variables
--------------

```yaml
backend_port: 8080
listen_port: 80
```

Dependencies
------------

N/A

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

```yaml
- name: setup load-balancer tier
  hosts: frontends
  become: yes
  roles:
    - {name: base-config, tags: base-config}
    - {name: lb-tier, backend_port: "{{apps_port}}", listen_port: "{{frontend_port}}", tags: [lbs, haproxy]}
```

License
-------

BSD

Author Information
------------------

Red Hat Training