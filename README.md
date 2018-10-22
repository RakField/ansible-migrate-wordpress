# Ansible playbook for building up tuukkamerilainen.com

### Requirements
- Ansible 2.0.0 or newer running on Ubuntu 14.04 (might work with newer Ubuntu as well)
- Ubuntu 16.04 server configured so that you can say "ssh insertserverhost"
- tuukkamerilainen.com wordpress site as tar (make sure that when extracting the tar, it extracts all files not one folder which contains files)[this should work with any preinstalled wordpress site]
- mysqldump of tuukkamerilainen.com (existing) wordpress installation as .sql

### 1. What is this
This playbook can be used with tuukkamerilainen.com (any pre installed) wordpress sites. I use this when I need to migrate my personal website to another server.

### 2. What this does
This playbook makes it easy to build up tuukkamerilainen.com in Ubuntu 16.04 server.

It will take care of following things:

 - Update OS
 - Install / Harden SSH
 - Install / Harden Firewall with iptables
 - Install NGINX
 - Install MySQL
 - Migrate tuukkamerilainen.com wordpress
 - Migrate tuukkamerilainen.com database
 -> Everything should work as is working at tuukkamerilainen.com

### 3. Running

 - Specify hostname of your server into hosts file
 - Specify hostname of the site in: group_vars/all
 - Specify path of the existing wordpress tar and mysqldump in: group_vars/all
 - MAKE SURE that all other configs are ok in group_vars/all
 - MAKE SURE that you can say "ssh hostname" and it will login without password/user prompt
 - cd to same path where this README.md is located
 - Run: ansible-playbook migrate.yml -i hosts --extra-vars "ansible_sudo_pass=ínsertpasshere"

### 4. Credits
https://github.com/tucsonlabs/ansible-playbook-wordpress-nginx
https://github.com/mikegleasonjr/ansible-role-firewall
