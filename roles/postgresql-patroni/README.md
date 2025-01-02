patroni postgresql
=========

This ansible galaxy role automates the setup and configuration of `PostgreSQL` with `Patroni`, ensuring high availability and automated failover for `PostgreSQL` databases.

Requirements
------------

No specific requirements.

Role Variables
--------------

```
_postgresql_patroni_installation_dir: /usr/lib/postgresql
_postgresql_patroni_local_ip_address: "{{ lookup('vars', 'ansible_' + postgresql_patroni_interface_name)['ipv4']['address'] }}"
```

Вот таблица с заполненными описаниями:

| Параметр                                | Дефолтное значение                                         | Описание                        |
|-----------------------------------------|-----------------------------------------------------------|---------------------------------|
| postgresql_patroni_node_name            | devops-pg11                                                | Имя ноды Patroni                |
| postgresql_patroni_interface_name       | eth0                                                      | Имя интерфейса                   |
| postgresql_patroni_etcd_host            | 158.160.75.244                                            | IP-адрес хоста etcd              |
| postgresql_patroni_python_venv_name     | pg                                                        | Имя виртуальной среды Python     |
| postgresql_patroni_python_venv_path     | "/usr/local/share/venv/{{ postgresql_patroni_python_venv_name }}" | Путь к виртуальной среде Python  |
| postgresql_patroni_postgresql_major_version | 16                                                | Основная версия PostgreSQL       |
| postgresql_patroni_apt_key_url          | https://www.postgresql.org/media/keys/ACCC4CF8.asc        | URL ключа APT                   |
| postgresql_patroni_apt_repo_url         | https://apt.postgresql.org/pub/repos/apt                  | URL репозитория APT             |
| postgresql_patroni_data_dir             | /dev/data/patroni                                         | Директория для данных Patroni    |
| postgresql_patroni_superuser_login      | postgres                                                 | Логин суперпользователя          |
| postgresql_patroni_superuser_password   | password                                                 | Пароль суперпользователя         |
| postgresql_patroni_replication_login    | replicator                                               | Логин для репликации             |
| postgresql_patroni_replication_password | password                                                 | Пароль для репликации            |
| postgresql_patroni_patroni_config_path  | /etc/patroni.yml                                         | Путь к файлу конфигурации Patroni|
| postgresql_patroni_postgresql_remote_user | postgres                                           | Пользователь удалённой БД        |
| postgresql_patroni_postgres_users       | - name: admin<br>password: admin<br>- name: auth<br>password: auth | Список пользователей PostgreSQL  |
| postgresql_patroni_postgres_databases   | - name: admin<br>owner: admin<br>- name: auth<br>owner: auth | Список баз данных PostgreSQL     |
| postgresql_patroni_postgres_parameters  | unix_socket_directories:.<br>synchronous_commit:"on"<br>synchronous_standby_names:"*" | Параметры PostgreSQL             |

License
-------

BSD-3-Clause
