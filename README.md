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

    elao_php_version:    5.5                      # Php version (5.4|5.5|5.6)
    elao_php_modules:    []                       # Php modules
    elao_php_config:     {}                       # Global php config
    elao_php_config_cli: {}                       # Cli php config
    elao_php_config_fpm: {}                       # Fpm php config
    elao_php_fpm_pools_path: /etc/php5/fpm/pool.d # Fpm pools path
    elao_php_fpm_pools:                           # Fpm pools
      www: 
        listen: "127.0.0.1:9000"    


Example Playbook
----------------

    - hosts: servers
	    vars:
	      elao_php_version: 5.5
        elao_php_modules: ['intl', 'mysqlnd']
	      elao_php_config:
	        memory_limit:   512M
	        date.timezone:  Europe/Paris
          short_open_tag: "On"
	      elao_php_config_cli:
	        memory_limit:  1024M
      roles:
         - { role: elao.php }


#### Advanced configuration:

##### PHP FPM Pools:

```
elao_php_fpm_pools:
  www:
    prefix:                     "/path/to/pools/$pool"
    listen:                     "127.0.0.1:9000"
    user:                       "www-data"
    group:                      "www-data"
    listen_owner:               "www-data"
    listen_group:               "www-data"
    listen_mode:                "0660"
    listen_backlog:             65535
    listen_allowed_clients:     127.0.0.1
    process_priority:           "-19"
    pm:                         "dynamic"
    pm_max_children:            5
    pm_start_servers:           2
    pm_min_spare_servers:       1
    pm_max_spare_servers:       3
    pm_process_idle_timeout:    "10s"
    pm_max_requests:            500
    pm_status_path:             "/status"
    ping_path:                  "/ping"
    ping_response:              "pong"
    access_log:                 "log/$pool.access.log"
    access_format:              "%R - %u %t \"%m %r%Q%q\" %s %f %{mili}d %{kilo}M %C%%"
    slowlog:                    "log/$pool.log.slow"
    request_slowlog_timeout:    0
    rlimit_files:               1024
    rlimit_core:                0
    chroot:                     ""
    catch_workers_output:       "no"
    clear_env:                  "yes"
    security_limit_extensions:  ".php .php3 .php4 .php5"
    env_hostname:               "$HOSTNAME"
    env_path:                   "/usr/local/bin:/usr/bin:/bin"
    env_tmp:                    "/tmp"
    env_tmpdir:                 "/tmp"
    env_temp:                   "/tmp"
```

License
-------

MIT

Author Information
------------------

http://www.elao.com/
