# Good Photo
![example workflow](https://github.com/devbkd/good_photo/actions/workflows/main.yml/badge.svg) ![Статус проекта: Альфа версия](https://img.shields.io/badge/%D0%A1%D1%82%D0%B0%D1%82%D1%83%D1%81-%D0%90%D0%BB%D1%8C%D1%84%D0%B0%20%D0%B2%D0%B5%D1%80%D1%81%D0%B8%D1%8F-yellowgreen.svg)

### Описание
Good Photo — социальная сеть для обмена фотографиями . Состоит из бэкенд-приложения на Django и фронтенд-приложения на React. Поддерживает регистрацию и авторизацию, можно добавить нового котика на сайт или изменить существующего, а также просмотреть записи других пользователей.

### Используемые технологии
- Python 3.10
- Django 3.2
- Django REST Framework 3.12
- Node.js
- React
- Gunicorn
- Nginx 20.1
- Docker
- GitHub Actions

### Как развернуть проект локально
1. Клонировать репозиторий:
    ```bash
    git clone git@github.com:devbkd/good_photo.git
    cd good_photo/
    ```

2. Создать в папке good_photo/ файл `.env` с переменными окружения (см. [.env.example](.env.example)).

3. Собрать и запустить докер-контейнеры через Docker Compose:
    ```bash
    docker compose up --build
    ```

### Как развернуть проект на сервере
1. Создать папку kittygram/ с файлом `.env` в домашней директории сервера (см. [.env.example](.env.example)).
    ```bash
    cd ~
    mkdir kittygram
    nano kittygram/.env
    ```
2. Настроить в nginx перенаправление запросов на порт 9000:
    ```nginx
    server {
        server_name <...>;
        server_tokens off;

        location / {
            proxy_pass http://127.0.0.1:9000;
        }
    }
    ```
3. Добавить в GitHub Actions следующие секреты:
- DOCKER_USERNAME - логин от Docker Hub
- DOCKER_PASSWORD - пароль от Docker Hub
- SSH_KEY - закрытый ssh-ключ для подключения к серверу
- SSH_PASSPHRASE - passphrase от этого ключа
- USER - имя пользователя на сервере
- HOST - IP-адрес сервера
- TELEGRAM_TO - ID телеграм-аккаунта для оповещения об успешном деплое
- TELEGRAM_TOKEN - токен телеграм-бота

## Автор:
Рузал Закиров [GitHub](https://github.com/devbkd/)
