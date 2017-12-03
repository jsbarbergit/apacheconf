apt-pkg-management
=========
Install/Uninstall given packages


Role Variables
--------------

apt_pkg_name:	Package to modify with apt package management system. To ustilise a specific version of the package, suffixc package name with :x.x where x.x equates to available version
apt_cache_update: Update apt cache prior to performing operation
apt_pkg_state: Default is present to install package. If set to absent, package will be removed


Example Playbook
----------------

---
- hosts: webservers

  vars_files: 
    - group_vars/webservers.yaml

  vars:
    # Default is to install all listed pkgs. Override with --extra-vars"state=absent" 
    apt_pkg_state: "{{ state | default('present') }}"

    # Update apt cache before running apt cmds
    apt_cache_update: yes

  tasks:
  - name: Install Webserver Packages
    include_role: 
      name: apt-pkg-management
    vars:
      apt_pkg_name: "{{ item }}"
    with_items: "{{ install_pkgs }}"
