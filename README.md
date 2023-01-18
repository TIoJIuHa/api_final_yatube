# API для Yatube

### Описание проекта

Проект выполнен в учебных целяx для курса Яндекс.Практикума.
В нём реализован REST API и CRUD для основных моделей проекта социальной сети Yatube.

Пользователю доступен следующий функционал:
- аутентификация с помощью JWT-токенов, обновление токена;
- создание, просмотр, изменение, удаление постов;
- просмотр сообществ;
- создание, просмотр, изменение, удаление комментариев к любым постам;
- подписка на авторов.

В проекте также реализована пагинация, возможен поиск по подпискам и имеется ограничение прав для некоторых действий пользователя.

### Стек технологий:

<div>
  <img src="https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54"/>
  <img src="https://img.shields.io/badge/Django-092E20?style=for-the-badge&logo=django&logoColor=green"/>
  <img src="https://img.shields.io/badge/django%20rest-ff1709?style=for-the-badge&logo=django&logoColor=white"/>
  <img src="https://img.shields.io/badge/JWT-000000?style=for-the-badge&logo=JSON%20web%20tokens&logoColor=white"/>
  <img src="https://img.shields.io/badge/SQLite-07405E?style=for-the-badge&logo=sqlite&logoColor=white"/>
</div>

### Как запустить проект:

Клонировать репозиторий и перейти в него в командной строке:
```
git clone https://github.com/TIoJIuHa/api_final_yatube.git
```
```
cd api_final_yatube
```

Cоздать и активировать виртуальное окружение:
```
python -m venv env
```
```
source venv/Scripts/activate
```
```
python -m pip install --upgrade pip
```

Установить зависимости из файла `requirements.txt`:
```
pip install -r requirements.txt
```

Перейти в папку с фалом `manage.py`:
```
cd yatube_api
```

Выполнить миграции:
```
python manage.py migrate
```

Запустить проект:

```
python3 manage.py runserver
```
### Примеры запросов к API

После запуска проекта по адресу `http://127.0.0.1:8000/redoc/` будет доступна документация для API Yatube. В ней полностью описано как работает API.

Пример запроса:
```
GET http://127.0.0.1:8000/api/v1/posts/
```
Пример ответа сервера:
```
[
    {
        "id": 1,
        "author": "user1",
        "image": null,
        "text": "good morning",
        "pub_date": "2022-10-19T09:43:18.880555Z",
        "group": null
    },
    {
        "id": 2,
        "author": "user2",
        "image": null,
        "text": "hello *-*",
        "pub_date": "2022-10-19T20:19:10.845395Z",
        "group": null
    },
    {
        "id": 3,
        "author": "user2",
        "image": "http://127.0.0.1:8000/posts/temp_ahCVasT.png",
        "text": "wow  it's working",
        "pub_date": "2022-10-19T20:20:46.312494Z",
        "group": null
    }
]
```
Пример запроса:
```
POST http://127.0.0.1:8000/api/v1/posts/1/comments/
```
```
{
    "text": "my comment"
}
```
Пример ответа сервера:
```
{
    "id": 6,
    "author": "user2",
    "post": 1,
    "text": "my comment",
    "created": "2022-10-20T19:00:04.375377Z"
}
```
Пример запроса:
```
GET http://127.0.0.1:8000/api/v1/groups/1/
```
Пример ответа сервера:
```
{
    "id": 1,
    "title": "first_group",
    "slug": "first-group",
    "description": "This group about nothing"
}
```