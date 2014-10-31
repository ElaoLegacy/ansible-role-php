Ansible Role - Php
==================

A php role for elao symfony standard vagrant box


Requirements
------------

This role only run on elao symfony standard vagrant box. See https://vagrantcloud.com/elao/symfony-standard-debian


Role Handlers
-------------

    php restart  # Restart php service

Role Variables
--------------

    elao_php_version:    5.5  # Php version (5.4|5.5)
    elao_php_modules:    []   # Php modules
    elao_php_config:     {}   # Global php config
    elao_php_config_cli: {}   # Cli php config
    elao_php_config_fpm: {}   # Fpm php config


Example Playbook
----------------

    - hosts: servers
	    vars:
	      elao_php_version: 5.5
        elao_php_modules: ['intl', 'mysqlnd']
	      elao_php_config:
	        memory_limit:  512M
	        date.timezone: Europe/Paris
	      elao_php_config_cli:
	        memory_limit:  1024M
      roles:
         - { role: elao.php }


License
-------

MIT

Author Information
------------------

http://www.elao.com/
