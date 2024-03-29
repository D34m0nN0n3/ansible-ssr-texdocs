[![License: GPL v3](https://img.shields.io/badge/License-GPLv3-blue.svg)](https://www.gnu.org/licenses/gpl-3.0)

# TeX Docs
Copyright (C) 2020 Dmitriy Prigoda deamon.none@gmail.com This script is free software: Everyone is permitted to copy and distribute verbatim copies of the GNU General Public License as published by the Free Software Foundation, either version 3 of the License.

## Содержание

- [TeX Docs](#tex-docs)
  - [Содержание](#содержание)
  - [Общее описание](#общее-описание)
  - [Параметры](#параметры)
  - [Теги](#теги)
  - [Примеры](#примеры)
    - [inventory/hosts (Nexus proxy сервер и RH Satellite)](#inventoryhosts-nexus-proxy-сервер-и-rh-satellite)
  - [Документация](#документация)
  - [Дополнительные материалы](#дополнительные-материалы)

## Общее описание

TeX Docs - сервис автоматической генерации документации на основе файлов с разметкой MarkDown. Решение представляет набор сценариев `Ansible` для автоматической установки и настройки ПО `MKdocs` на предприятие. Установка производится на ОС CentOS 8 с использованием `RPM` и `PyPi` пакетов.

Устанавливаемые компоненты:

1. MKdocs
2. Plugins (MKDocs-Material, mkdocs-with-pdf)
3. Nginx
4. GitLab-Runner

Для установки необходимо сделать клон проекта, настроить параметры в файле `inventory`, запустить `playbook`

```
    # Склонировать проект
    > git clone https://github.com/D34m0nN0n3/ansible-ssr-texdocs.git
    # Перейти в директорию с проектом
    > cd ansible-ssr-texdocs
    # Создать файл с параметрами
    > vim inventory/hosts
    # Запустить playbook
    > ansible-playbook -i inventory/hosts playbook.yml --ask-pass --become --ask-become-pass
```

## Параметры

|Название переменной   | Тип переменной | Значения по умолчанию | Описание                                               |
|:--------------------:|:--------------:|:---------------------:|:-------------------------------------------------------|
|pypi_proxy_arg        | string         |                       | Опция `index-url` для проксированного подключения      |
|runner_reg            | boolean        | False                 | Подключение задачи регистрации `runner`                |
|gitlab_api_url        | string         |                       | URL адрес GitLab сервера                               |
|access_token          | string         |                       | Персональный токен пользователя с доступом к проектам  |
|runner_reg_token      | string         |                       | Токен для регистрации `runner`                         |
|enable_satellite_repo | boolean        | True                  | Подключение задачи включения дополнительных пакетов    |
|rhsm_key              | string         |                       | Ключ активации репозитория                             |
|rhsm_org              | string         |                       | Название организации в которой опубликован репозиторий |
|end_point             | string         |                       | Альтернативное имя в `NGINX`                           |

## Теги

|Тег                   | Описание                               |
|:--------------------:|:---------------------------------------|
|install_mkdocs        | Установка MKdocs+Nginx                 |
|install_gitlab_runner | Установка GitLab-Runner                |
|reg-runner            | Регистрация GitLab-Runner              |

## Примеры

### inventory/hosts (Nexus proxy сервер и RH Satellite)

```
    [tex-docs]
    <host_name> ansible_ssh_host=<host_ip> ansible_ssh_user=<user_name_for_connect>

    [tex-docs:vars]
    ansible_connection=ssh
    pypi_proxy_arg='--index-url http://example-nexus.com/repository/pypi-proxy/simple/ --trusted-host example-nexus.com'
    runner_reg=True
    gitlab_api_url='http://example-gitlab.com'
    access_token='<you_api_token>'
    runner_reg_token='<you_reg_token>'
    rhsm_key='gitlab'
    rhsm_org='ORG'
```

## Документация

[Документация](https://d34m0nn0n3.github.io/ansible-ssr-texdocs/)

## Дополнительные материалы

- [Ansible installation guide](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html)
- [Ansible Documentations](https://docs.ansible.com/)
- [Ansible tags](https://docs.ansible.com/ansible/latest/user_guide/playbooks_tags.html)
- [Connection methods](https://docs.ansible.com/ansible/latest/user_guide/connection_details.html)
- [Ansible passing sudo](https://8gwifi.org/docs/ansible-sudo-ssh-password.jsp)
- [GitLab access tokens](https://docs.gitlab.com/ee/user/profile/personal_access_tokens.html)
- [MkDocs](https://www.mkdocs.org/)
- [Material for MkDocs](https://squidfunk.github.io/mkdocs-material/getting-started/)
