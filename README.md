MYSQL
=======

[![Build Status](https://travis-ci.org/injectedMonkey/ansible-role-mysql.svg?branch=master)](https://travis-ci.org/injectedMonkey/ansible-role-mysql)
[![License](https://img.shields.io/badge/License-BSD%202--Clause-orange.svg)](https://opensource.org/licenses/BSD-2-Clause)
[![GitHub release](https://img.shields.io/github/release/injectedMonkey/ansible-role-mysql.svg?style=flat)](https://github.com/injectedMonkey/ansible-role-mysql/releases)

Ansible role for mysql. It's designed for my development environment
but might reach sometimes production ready state.

Supported distributions:
- Debian
- Ubuntu


Supported MySQL distributions:
- MariaDB
- MySQL


Requirements
------------

This role requires ansible >= 2.4.

Dictionaries are used for configuration. Partially overriding defaults needs

      hash_behaviour = merge

set in your ansible.cfg or

      ANSIBLE_HASH_BEHAVIOUR=merge

for your environment.

Role Variables
--------------

      mysql:
        packages:
          - mariadb-server
          - mariadb-client
          # or just use mysql
          #- mysql-server
          #- mysql-client
          - python-mysqldb
        charset: utf8mb4
        port: 3306
        socket: /var/run/mysqld/mysqld.sock
        datadir: /var/lib/mysql
        log_error: /var/log/mysql/error.log
        pid_file: /var/run/mysqld/mysqld.pid
        config_path: /etc/mysql/conf.d
        root_password: root
        users:
          - { name: dbuser, password: 123, privileges: '*.*:ALL' }



Dependencies
------------

None.


Example Playbook
----------------

    - hosts: servers
    - include_role:
        name: injectedMonkey.php-fpm
      vars:
        mysql:
          packages:
            - mariadb-server
            - mariadb-client
            # or just use mysql
            #- mysql-server
            #- mysql-client
            - python-mysqldb
          charset: utf8mb4
          port: 3306
          socket: /var/run/mysqld/mysqld.sock
          datadir: /var/lib/mysql
          log_error: /var/log/mysql/error.log
          pid_file: /var/run/mysqld/mysqld.pid
          config_path: /etc/mysql/conf.d
          root_password: root
          users:
            - { name: dbuser, password: 123, privileges: '*.*:ALL' }


License
-------

BSD

Author Information
------------------

injectedMonkey.wtf
