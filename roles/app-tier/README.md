Application Tier Deployment
=========

Deploy the Application Tier

Requirements
------------

N/A

Role Variables
--------------

```yaml
tomcat_listen_port: 8080
tomcat_webapp: ROOT
tomcat_webapp_dir: /usr/share/tomcat/webapps/{{tomcat_webapp}}
```

Dependencies
------------

N/A

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

```yaml
- name: setup app tier
  hosts: apps
  become: yes
  gather_facts: false
  roles:
    - {name: base-config, tags: base-config}
    - {name: app-tier, tomcat_listen_port: "{{apps_port}}", tags: [apps, tomcat]}
```

License
-------

BSD

Author Information
------------------

Red Hat Training