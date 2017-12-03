# Repo: apacheconf
Basic Ansible code to manage main apache2 config, including vhosts on an Ubuntu 12.0.4 System

Config file located at group_vars/webservers.yaml acts as answerfile 

Example usage with included hosts inventory file, overriding local user providing private key file location
ansible-playbook -i inventory/hosts -u ubuntu manage-apache2-webserver.yaml -e "key_file=~/.ssh/infin.pem"

The following tasks will be performed:

- Install all given packages using apt package management if not present - enable and start associated service
- Optionally, if state=absent passed as in --extra-vars, packages will be uninstalled
- Copy apache2.conf file into position if different from existing file and restart apache2 service
- Enable/Disable specified virtual hosts, using ansible template feature
- run basic smoke test against a given uri

Playbook is idempotent and any errors are raised implicitly as a consequence of the declarative nature of the Ansible orchestration tool

Possible Future Enhancements:
- Handle multiple OS
- Expand vhost template to build all sections from template, ie config file dictionary of sub section declarations and values
- Expand smoke test coverage
- Include SSL/TLS certificate management to protect sensitive ares of the sire, e.g. VLE login page
