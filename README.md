
# Подготовка сервера, сборка и выкладка сервиса "Социальная сеть"


## Содержание
- [Требования](#requirements)
- [Технологии](#technologies)
- [Начало работы](#start)
- [Теги запуска playbook](#tag_methods)
- [To Do](#todo)
- [Команда проекта](#command)


## <a id="requirements">Требования</a>
Для установки и запуска проекта, необходимо:
- python 3.9
- ansible
- docker
- openssl

## <a id="technologies">Технологии</a>
- docker, docker build, postgreSQL, ansible, react, fastAPI, Python

## <a id="start">Начало работы</a>

- Скачать репозиторий проекта
```
git clone https://github.com/rudikrudik/socialNetwork-devops.git
```
- Перейти в каталог проекта
```
cd socialNetwork-devops
```
- Изменить файл <b>group_vars/all/vault.yml</b> поставив значения соединения с БД и сгенерировать ключ <b>openssl rand -hex 32</b>
- В файле inventory указать ip адрес сервера
  - Сборка докер образа и запуск происходит на каждой машине 

## <a id="tag_methods">Теги запуска playbook</a>
```
main.yml # подготавливает систему, собирает и разворачивает сервис
main.yml --tags="build" # сборка обазов 
main.yml --tags="deploy" # выкладка сервисов app и postgresql
main.yml --tags="name" # сборка и выкладка одного сервиса, вместо name подставить нужный ["app_backend", "app_frontend", "postgres"]
main.yml --tags="zabbix-agent-app" # Агент мориторинга серверов backend и frontends
main.yml --tags="zabbix-agent-db" # Агент мориторинга серверов Postgres
```

## <a id="todo">To do</a>
- ~~health check для контейнеров~~
- ~~SQL скрипт создания базы, таблиц~~
- ~~SQL скрипт тестовых данных~~
- ~~мониторинг~~
- Потоковуя репликация postgres
- Синхронная репликация postgres

## <a id="command">Команда проекта</a>
- Бахман Рудольф - DevOps engineer
  - telegram - https://t.me/rudik_rudik
  - email - rudik.login@gmail.com
