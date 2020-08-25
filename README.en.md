# ansible-role-mamonsu

[![Ansible Galaxy](https://img.shields.io/badge/galaxy-sgrinko.mamonsu-blue)](https://galaxy.ansible.com/sgrinko/mamonsu/) ![GitHub stars](https://img.shields.io/github/stars/sgrinko/ansible-role-mamonsu) [<img src="https://github.com/sgrinko/ansible-role-mamonsu/workflows/Ansible-lint/badge.svg?branch=master">](https://github.com/sgrinko/ansible-role-mamonsu/actions?query=workflow%3AAnsible-lint) [![GitHub license](https://img.shields.io/github/license/sgrinko/ansible-role-mamonsu)](https://github.com/sgrinko/ansible-role-mamonsu/blob/master/LICENSE)

Install [mamonsu](https://github.com/postgrespro/mamonsu) (Monitoring agent for PostgreSQL) with Ansible.

## Compatibility
All x86-64 Linux distributions.

mamonsu is written on Python language and distributed as a deb or rpm package.

## Role Variables
`mamonsu_install` - true if need install mamonsu

`mamonsu_zabbix_server_ip` - IP zabbix server. Example: zabbix.server.ru

`proxy_env` - use proxy server to download mamonsu packages (if required).
###### example:
```
proxy_env:
  http_proxy: http://10.128.64.9:3128
  https_proxy: http://10.128.64.9:3128
```
`apt_repository_keys` - Repository keys (used on Debian/Ubuntu OS only)

`apt_repository` - Repository (used on Debian/Ubuntu OS only)
###### optional variable:
`mamonsu_plugin_pg_stat_replication` - true if need install addon plugin pg_stat_replication. Default: true

`mamonsu_zabbix_server_port` - port zabbix server. Default: 10051

`mamonsu_interval_pgbuffercache` -  set interval call for plugin pg_buffercache.py in seconds. Default: 1200

`mamonsu_log_file` - path and name log file. Default: /var/log/mamonsu/agent.log

`postgresql_port` - Port for access to PostgreSQL service. Default: 5432

See the defaults/[main.yml](./defaults/main.yml) file for details.

## Dependencies
None.

## Example Playbook
    - hosts: servers
      roles:
         - role: ansible-role-mamonsu

## License
Licensed under the MIT License. See the [LICENSE](./LICENSE) file for details.

## Author Information
Sergey Grinko (PostgreSQL DBA) sergey.grinko@gmail.com
