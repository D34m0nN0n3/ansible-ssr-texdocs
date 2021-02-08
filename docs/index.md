# Общее описание

TeX Docs - сервис автоматической генерации документации на основе файлов с разметкой MarkDown. Данная разметка применяется для описания различных проектов в системе контроля версий `git` и поддерживается сервисами: `GitHub` и `GitLab`, а так же многими редакторами и средами разработки, такими как `VSCode`.

![GitHub](images/github.PNG)
![VSCode](images/vscode.PNG)

Решение основано на программном обеспечение с открытом исходным кодом. Основные компоненты:

* MKDocs
* MKDocs-Material
* MKDocs-pdf-export-plugin

!!! note
    Решение является модульным за счет подключения различных модулей написанных на Python.

!!! info
    В данном руководстве приводятся рекомендации для создания документации и ссылки на дополнительные материалы. 

## Структура проекта

Базовая структура проекта:

    .
    |
    |-docs
    |    |-assets
    |    |      |_ ...  
    |    |_index.md
    |    |_seealso.md
    |    |_ ...
    |
    |-material
    |        |_ ...
    |
    |-theme-handler
    |             |_ ...
    |
    |_mkdocs.yml

| Директории и файлы       | Описание                                |
|:------------------------:|:----------------------------------------|
| docs                     | основная директория с документацией     |
| material и theme-handler | тема формирования стиля `html` страниц  |
| mkdocs.yml               | конфигурационный файл с настройками     |

## Файл конфигурации проекта  

!!! example "mkdocs.yml"
    ``` yaml
    site_name: TeX Docs
    site_description: "Documentation for TeX Docs site"
    copyright: Copyright &copy; <a href="https://github.com/D34m0nN0n3">Dmitriy Prigoda</a>.

    repo_name: ""
    repo_url: ""

    use_directory_urls: false

    nav:
        - Общее описание: 'index.md'
        - Дополнительные материалы: 'seealso.md'

    plugins:
        - search
        - pdf-export:
            verbose: true
            media_type: print
            combined: true
            combined_output_path: 'pdf/combined.pdf'
            theme_handler_path: theme-handler/material.py

    theme:
    name: material
      ...

    extra:
        search:
            language: 'ru, en'

    extra_css:
        - material/assets/css/main.css
        - material/assets/libs/magnific-popup/magnific-popup.css

    extra_javascript:
        - material/assets/libs/jquery/jquery-3.4.0.min.js
        - material/assets/libs/magnific-popup/jquery.magnific-popup.min.js
        - material/assets/js/main.js

    markdown_extensions:
    - admonition
    - codehilite:
          linenums: true
    - toc:
          permalink: true
    ...
    ```

| Разделы и параметры      | Описание                                                                    |
|:------------------------:|:----------------------------------------------------------------------------|
| site_name                | Основное имя проекта                                                        |
| site_description         | Краткое описание проекта                                                    |
| repo_name                | Имя проекта в `git`, необходимо для формирования ссылки для редактирования  |
| repo_url                 | Ссылка на проект в `git`                                                    |
| nav                      | Подключаемые файлы с документацией                                          |
| plugins                  | Подключяемые расширения                                                     |
| combined_output_path     | Имя файла `pdf`. По умолчанию: `combined.pdf`                               |
| theme                    | Тема оформления `html` страниц                                              |
| extra                    | Дополнительные настройки                                                    |
| markdown_extensions      | Модули обработки разметки                                                   |
