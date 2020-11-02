# TeX Docs

Copyright (C) 2020 Dmitriy Prigoda deamon.none@gmail.com This script is free software: Everyone is permitted to copy and distribute verbatim copies of the GNU General Public License as published by the Free Software Foundation, either version 3 of the License.

## Общее описание

TeX Docs - сервис автоматической генерации документации на основе файлов с разметкой MarkDown. Решение представляет набор сценариев `Ansible` для автоматической установки и настройки ПО `MKdocs` на предприятие. Установка производится на ОС CentOS 8 с использованием `RPM` и `PyPi` пакетов.

Устанавливаемые компоненты:

1. MKdocs
2. Plugins (MKDocs-Material, MKDocs-pdf-export-plugin)
3. Nginx
4. GitLab-Runner

Для установки необходимо сделать клон проекта, настроить параметры в файле `inventory`, запустить `playbook`

```
    > git clone https://github.com/D34m0nN0n3/ansible-ssr-texdocs.git
    > cd ansible-ssr-texdocs
    > mkdir inventory
    > vim inventory/hosts
    > ansible-playbook -i inventory/hosts playbook.yml --ask-pass --become --ask-become-pass
```

## Параметры

Название переменной   Тип переменной   Тип значения   Значения по умолчанию   Описание

## Теги

Тег  Описание

## Примеры


## Дополнительные материалы

- [Ansible installation guide](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html)
- [Ansible Documentations](https://docs.ansible.com/)
- [Ansible tags](https://docs.ansible.com/ansible/latest/user_guide/playbooks_tags.html)
- [Connection methods](https://docs.ansible.com/ansible/latest/user_guide/connection_details.html)
- [Ansible passing sudo](https://8gwifi.org/docs/ansible-sudo-ssh-password.jsp)
