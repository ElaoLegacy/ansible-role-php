Php
===

A php role for elao symfony standard vagrant box

Requirements
------------

This role only run on elao symfony standard vagrant box. See https://vagrantcloud.com/elao/symfony-standard-debian

Role Handlers
-------------

* php restart: Restart php5 fpm service

Example Playbook
----------------

    - hosts: servers
      roles:
         - { role: elao.php }

License
-------

MIT

Author Information
------------------

http://www.elao.com/
