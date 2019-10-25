MariaDB
=======

An Ansible role for installing and configuring a MariaDB server.
At the moment Debian based distros are supported.
This role is tested on Debian 10 Buster and MariaDB 10.4.

Requirements
------------

This role has no requirements. Pip packages required from Ansible mysql_*
modules are atomatically checked and installed from the role itself.

Role Variables
--------------

```yaml
# MariaDB Role specific variables
mariadb_apt_repo_url: "http://ams2.mirrors.digitalocean.com/mariadb/repo/"
mariadb_keyserver: "keyserver.ubuntu.com"
mariadb_apt_key_id: "0xF1656F24C74CD1D8"
mariadb_version: "10.4"
mariadb_socket_path: /var/run/mysqld/mysqld.sock

# Required packages
mariadb_required_packages:
  - python-pip
  - python3-pip
  - gpg

# Required PIP packages
mariadb_required_pip_packages:
  - PyMySQL

# MariaDB Additional Packages
mariadb_additional_packages:
  - mysqltuner
  - percona-toolkit
  - mariadb-backup

# MariaDB Administrator settings
mariadb_admin_home: "/root"
mariadb_admin_username: "root"
mariadb_admin_password:  ""

mariadb_admin_hosts:
  - localhost
  - 127.0.0.1
  - ::1
```

Dependencies
------------

This role has no dependencies.

Example Playbook
----------------

```yaml
    - hosts: servers
      roles:
         - role: mmartinello.mariadb
           vars:
             mariadb_admin_password: 'strong_password'
```

The `mariadb_admin_password` variable should be specified and saved using
Ansible Vault!
Do not commit a unencrypted password!

License
-------

MIT

Author Information
------------------

Mattia Martinello
