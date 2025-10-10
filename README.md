# Ansible Role: PostgreSQL

Ansible роль для установки и настройки PostgreSQL сервера.

## Описание

Данная роль выполняет установку и базовую настройку PostgreSQL СУБД на целевых хостах. Роль поддерживает установку PostgreSQL из официальных репозиториев и позволяет настроить основные параметры конфигурации.

## Требования

- Ansible 2.9 или выше
- Поддерживаемые операционные системы:
  - Ubuntu 18.04/20.04/22.04
  - Debian 10/11/12
  

## Переменные роли

### Основные переменные

```yaml
# defaults file for ansible-role-postgresql
postgresql_install: false
postgresql_version: "16"  # или "latest"
postgresql_host: "192.168.1.10"  # IP сервера PostgreSQL
postgresql_port: 5432

# Database settings
postgresql_database_name: "nexus"
postgresql_schema_name: "nexus"
postgresql_user: "nexus"
postgresql_password: "12345678"

# PostgreSQL listen address (для удаленного подключения)
postgresql_listen_addresses: "*"
```

## Зависимости

Роль не имеет внешних зависимостей от других ролей.

## Пример использования

### Простая установка

```yaml
- hosts: database_servers
  become: yes
  roles:
    - ansible-role-postgresql
```

### Использование с requirements.yml

```yaml
---
- src: https://github.com/filatof/ansible-role-postgresql.git
  scm: git
  version: main
  name: postgresql
```

Установка роли:

```bash
ansible-galaxy install -r requirements.yml
```

## Лицензия

MIT

## Автор

Эта роль создана [filatof](https://github.com/filatof).
