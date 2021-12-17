# yamdb_final
***
Проект YaMDb собирает отзывы пользователей на различные произведения.

![yamdb workflow](https://github.com/kinessa/yamdb_final/workflows/yamdb_workflow/badge.svg)
***
### возможности:
* устанавливать из контейнера Docker
* оставлять отзыв к произведению
* оценивать произведение в диапазоне от одного до десяти 
* смотреть рейтинг произведения
* авторизоваться по токену
*** 
### Необходимые действия:


Клонировать репозиторий:

```
git clone https://github.com/iogin/yamdb_final.git
```

Установить docker и docker-compose:

```
Инструкция по установке доступна в официальной инструкции
```
Создать файл .env с переменными окружения:

```
DB_ENGINE=django.db.backends.postgresql
DB_NAME=postgres # Имя базы данных
POSTGRES_USER=postgres # Администратор базы данных
POSTGRES_PASSWORD=postgres # Пароль администратора
DB_HOST=db
DB_PORT=5432
```
Сборка и запуск контейнера:

```
docker-compose up -d --build
```
Миграции:

```
docker-compose exec web python manage.py makemigrations
docker-compose exec web python manage.py migrate
```

Сбор статики:

```
docker-compose exec web python manage.py collectstatic --noinput
```

Создание суперпользователя Django:

```
docker-compose exec web python manage.py createsuperuser
```



Документация доступна по адресу:
http://127.0.0.1/redoc/
***
###Пример работы API:

Запрос для добавление нового пользователя через подтверждение кода переданного на email:
```python
import requests
url = 'http://127.0.0.1:8000/api/v1/auth/signup/'
email = 'Тут ваш email'
username = 'Тут ваш username'
```
Ответ от API:
```json
{
  "email": "Тут ваш email", 
  "username": "Тут ваш username"
}
```
Подтверждение кода и получение token:
```python
import requests
url = 'http://127.0.0.1:8000/api/v1/auth/token/'
username = 'Тут ваш username'
confirmation_code = 'Тут ваш confirmation_code'
```
Ответ от API:
```json
{
  "token": "Тут ваш token"
}
```
***
#### Почти автор проекта:
Кириленко Инесса

Ссылка на запущенный проект:
http://51.250.29.158/admin/
***
