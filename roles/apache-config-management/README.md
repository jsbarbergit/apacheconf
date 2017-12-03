Role Name
=========

apache-config-management

Role Variables
--------------

vhosts:	Dictionary of virtual host name and paramters - dependent on template being used
apache_modules:	Dictionary of apache2 modules to enable/disable


Example Playbook
----------------
---
- hosts: webservers
  become: True

  vars_files: 
    - group_vars/webservers.yaml

  vars:

  tasks:
  - name: Apply Apache Config
    include_role:
      name: apache-config-management
