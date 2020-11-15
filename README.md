## Ansible Role: PHP/PHP-FPM
Role for installing and configuring PHP
## Requirements
Ansible version: 2.9
Centos 7/ Debian
## Dependencies
ansible-role-repo-remi
## Example Playbook
```
- hosts: "{{ var }}"
  vars:
    php_enablerepo: "remi-php74"
    php_packages:
      - php
      - php-zip
      - php-cli
      - php-common
      - php-devel
      - php-fpm
      - php-gd
      - php-imap
      - php-ldap
      - php-mbstring
      - php-opcache
      - php-pdo
      - php-pear
      - php-pecl-apcu
      - php-pecl-geoip
      - php-pecl-redis
      - php-xml
      - php-xmlrpc
      - php-redis
      - php-mysql
      - php-intl
      - php-soap
      - php-redis
      - php-json
      - php-iconv
      - php-ctype
    php_session_save_handler: files
    php_session_save_path: ''
    php_webserver_daemon: "nginx"
    php_conf_paths:
      - /etc
    php_extension_conf_paths:
      - /etc/php.d
    php_apc_conf_filename: 50-apc.ini
    php_opcache_conf_filename: 10-opcache.ini
    php_fpm_daemon: php-fpm
    php_fpm_conf_path: "/etc/fpm"
    php_fpm_pool_conf_path: "/etc/php-fpm.d/www.conf"

    php_fpm_pool_user: developer
    php_fpm_pool_group: developer
    php_enable_php_fpm: true

    php_fpm_listen: "127.0.0.1:9000"
    php_fpm_listen_allowed_clients: "127.0.0.1"
    php_max_execution_time: "120"
    php_upload_max_filesize: "64M"
    php_post_max_size: "32M"
    php_date_timezone: "Europe/Kiev"

    #2Ram
    #php_fpm_pm_max_children: 80
    #php_fpm_pm_start_servers: 25
    #php_fpm_pm_min_spare_servers: 25
    #php_fpm_pm_max_spare_servers: 35
    #php_fpm_pm_max_requests: 500

    #1Ram
    php_fpm_pm_max_children: 40
    php_fpm_pm_start_servers: 15
    php_fpm_pm_min_spare_servers: 15
    php_fpm_pm_max_spare_servers: 25
    php_fpm_pm_max_requests: 250

    php_fpm_session_save_handler: file
    php_fpm_session_save_path: ''
    php_fpm_error_log_path: /var/log/php-fpm/www-error.log
    php_fpm_slow_log_path: /var/log/php-fpm/www-slow.log
  roles:
    - ansible-role-repo-remi
    - ansible-role-php
```
