## Проект YaMDb

Сервис доступен по IP: 130.193.48.171

![yamdb workflow](https://github.com/Ludmila-Glushkova/yamdb_final/actions/workflows/yamdb_workflow.yml/badge.svg)


Проект YaMDb собирает отзывы пользователей на произведения. Произведения делятся на категории: «Книги», «Фильмы», «Музыка».
Произведению может быть присвоен жанр.
Читатели оставляют к произведениям отзывы и выставляют рейтинг (от 1 до 10).
Cредняя оценка произведения высчитывается автоматически.

Аутентификация по JWT-токену

Поддерживает методы GET, POST, PUT, PATCH, DELETE


## Технологии

- Python 3.7

- Django 2.2.19

- Nginx

- Docker-compose


## Шаблон наполнения env-файла:

1. Указываем, секретный ключ для settings.py:
```
SECRET_KEY=default-key
```
2. Указываем, что работаем с postgresql:
```
DB_ENGINE=django.db.backends.postgresql
```
3. Указываем имя базы данных:
```
DB_NAME=postgres
```
4. Указываем логин для подключения к базе данных:
```
POSTGRES_USER=postgres
```
5. Указываем пароль для подключения к БД:
```
POSTGRES_PASSWORD=postgres
```
6. Указываем название сервиса (контейнера):
```
DB_HOST=db
```
7. Указываем порт для подключения к БД:
```
DB_PORT=5432
```

## Установка

Для запуска приложения проделайте следующие шаги:

1. Склонируйте репозиторий.
2. Перейдити в папку infra и запустите docker-compose.yaml (при установленном и запущенном Docker)
```
docker-compose up
```
3. Для пересборки контейнеров выполните команду:
```
docker-compose up -d --build
```
4. В контейнере web выполните миграции:
```
docker-compose exec web python manage.py migrate
```
5. Создатйте суперпользователя:
```
docker-compose exec web python manage.py createsuperuser
```
6. Соберите статику:
```
docker-compose exec web python manage.py collectstatic --no-input
```
Проект запущен и доступен по адресу: [localhost](http://localhost/admin/)

