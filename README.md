# ansible-role-mamonsu

[![Ansible Galaxy](https://img.shields.io/badge/galaxy-sgrinko.mamonsu-blue)](https://galaxy.ansible.com/sgrinko/mamonsu/)  [![quality](https://img.shields.io/ansible/quality/29220)](https://galaxy.ansible.com/sgrinko/ansible-role-mamonsu) [<img src="https://github.com/sgrinko/ansible-role-mamonsu/workflows/Ansible-lint/badge.svg?branch=master">](https://github.com/sgrinko/ansible-role-mamonsu/actions?query=workflow%3AAnsible-lint)

Установка [mamonsu](https://github.com/postgrespro/mamonsu) (активный агент мониторинга для PostgreSQL) с использованием Ansible.

## Совместимость
Все x86-64 Linux дситрибутивы.

mamonsu написан на языке Python и распространяется в виде deb или rpm пакета.

## Переменные роли
`mamonsu_install` - true если необходимо установить и настроить mamonsu

`mamonsu_zabbix_server_ip` - IP сервера zabbix. Пример: zabbix.server.ru

`proxy_env` - используйте прокси-сервер для загрузки пакетов mamonsu (при необходимости).
###### пример:
```
proxy_env:
  http_proxy: http://10.128.64.9:3128
  https_proxy: http://10.128.64.9:3128
```
###### необязательные переменные:
`mamonsu_plugin_pg_stat_replication` - true если необходимо установить дополнительный пользовательский плагин pg_stat_replication. По умолчанию: `true`

`mamonsu_zabbix_server_port` - порт сервера zabbix. По умолчанию: `10051`

`mamonsu_interval_pgbuffercache` -  устанавливает интервал между вызовами плагина `pg_buffercache.py` в секундах. По умолчанию: `1200`

`mamonsu_log_file` - путь и имя хранения лог файла. По умолчанию: `/var/log/mamonsu/agent.log`

`postgresql_port` - порт для доступа к PostgreSQL службе. По умолчанию: `5432`

`mamonsu_pgprobackup_enable` - false или true если необходимо активировать плагин pgprobackup. По умолчанию: `False`

`mamonsu_pgprobackup_dirs` -  список каталогов через запятую для контроля за их размером. По умолчанию: `"/mnt/pgbak"`

`mamonsu_pgprobackup_path` - полный путь и имя утилиты `pg_probackup`. По умолчанию: `"/usr/bin/pg_probackup-12"`   

Смотрите файл defaults/[main.yml](./defaults/main.yml) для подробностей.

## Зависимости
Нет.

## Example Playbook
    - hosts: servers
      roles:
         - role: ansible-role-mamonsu

## Лицензия
Имеет лицензию MIT. См. Подробности в файле [LICENSE] (./ LICENSE).

## Информация об авторе
Сергей Гринько (PostgreSQL DBA) sergey.grinko@gmail.com
