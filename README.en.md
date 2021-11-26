# ansible-role-mamonsu

[![Ansible Galaxy](https://img.shields.io/badge/galaxy-sgrinko.mamonsu-blue)](https://galaxy.ansible.com/sgrinko/mamonsu/)  [![quality](https://img.shields.io/ansible/quality/29220)](https://galaxy.ansible.com/sgrinko/ansible-role-mamonsu) [<img src="https://github.com/sgrinko/ansible-role-mamonsu/workflows/Ansible-lint/badge.svg?branch=master">](https://github.com/sgrinko/ansible-role-mamonsu/actions?query=workflow%3AAnsible-lint)

Install [mamonsu](https://github.com/postgrespro/mamonsu) (Monitoring agent for PostgreSQL) with Ansible.

## Compatibility
All x86-64 Linux distributions.

mamonsu is written on Python language and distributed as a deb or rpm package. You can also install from the source code with GitHub.

## Role Variables
`mamonsu_install` - true if need install mamonsu

`mamonsu_install_src` - true If you need to install Mamonsu from the source code on GitHub. Default: `true`

`mamonsu_version` - mamonsu version to be installed

`mamonsu_service_user` - user under which you want to start the service. For example a custom postgres may be required when using some plugins

`mamonsu_zabbix_server_ip` - IP zabbix server. Example: zabbix.server.ru

`proxy_env` - use proxy server to download mamonsu packages (if required).
###### example:
```
proxy_env:
  http_proxy: http://10.128.64.9:3128
  https_proxy: http://10.128.64.9:3128
```

`postgresql_bin_dir` - Full way to access bin files PSQL. It is necessary to correctly set before launching the script

###### optional variable:
`mamonsu_plugin_pg_stat_partition` - true if need install addon plugin pg_partition. Default: `true`

`mamonsu_zabbix_server_port` - port zabbix server. Default: `10051`

`mamonsu_interval_pgbuffercache` -  set interval call for plugin pg_buffercache.py in seconds. Default: `1200`

`mamonsu_log_file` - path and name log file. Default: `/var/log/mamonsu/agent.log`

`postgresql_port` - Port for access to PostgreSQL service. Default: `5432`

`mamonsu_pgprobackup_enable` -  (default) or true if you need to enable plugin pgprobackup. Default: `False`

`mamonsu_pgprobackup_dirs` - dirs for check size: /mnt/pgbak. Default: `"/mnt/pgbak"`

`mamonsu_pgprobackup_path` - full path name for utility `pg_probackup`. Default: `"/usr/bin/pg_probackup-12"`

`mamonsu_memoryleakdiagnostic_enable` - true if you need to enable plugin memoryleakdiagnostic. Default `True`
 
`mamonsu_memoryleakdiagnostic_anonmem` - memory volume threshold after which we need an investigation about memory leak. Default `4GB`
 
`mamonsu_relationssize_enable` - true if you need to enable plugin relationssize. Default `False`
 
`mamonsu_relationssize_list` - Relations - comma separated list of objects - tables and indexes (database_name.schema.relation) used to calculate relations size. 
Sample: `postgres.pg_catalog.pg_class,postgres.pg_catalog.pg_user`


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
