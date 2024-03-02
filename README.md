# Проект «API для Yatube»

Проект API для Yatube представляет собой API-интерфейс для взаимодействия с социальной сетью Yatube. API позволяет пользователям выполнять различные операции с постами, комментариями, группами и подписками.

## Требования к установке

- Python 3.x
- Установленные зависимости из `requirements.txt`


## Установка зависимостей
Перед установкой зависимостей рекомендуется создать виртуальное окружение:

```bash
python -m venv venv
```
Активируйте виртуальное окружение:

На Windows:
```bash
venv\Scripts\activate
```
На Linux или MacOS:
```bash
source venv/bin/activate
```
Установите зависимости:

```bash
pip install -r requirements.txt
```

## Запуск проекта
Перейти в директорию yatube_api:

```bash
cd yatube_api
```
Выполнить миграции:
```bash
python manage.py migrate
```

Выполнить команду:
```bash
python manage.py runserver
```

## Примеры использования
1. **Получение токена авторизации**
- Запрос
```bash
POST /api/v1/api-token-auth/
Content-Type: application/json

{
    "username": "your_username",
    "password": "your_password"
}
```
- Ответ
```bash
{
"refresh": "your_refresh_token",
"access": "your_access_token"
}
```
2. **Получение списка всех постов**
- Запрос
```bash
GET /api/v1/posts/
Authorization: Token your_access_token
```
- Ответ
```bash
{
"count": 123,
"next": "http://api.example.org/accounts/?offset=400&limit=100",
"previous": "http://api.example.org/accounts/?offset=200&limit=100",
"results": [
    {
        "id": 1,
        "text": "Example post",
        "author": "your_username"
    },
    {
        "id": 2,
        "text": "Another post",
        "author": "another_user"
    }
    ]
}
```

3. **Создание нового поста**
- Запрос
```bash
POST /api/v1/posts/
Content-Type: application/json
Authorization: Token your_access_token

{
    "text": "some post",
    "image": "image_path",
    "group": 0
}
```
- Ответ
```bash
{
    "id": 4,
    "author": "username",
    "text": "post_text",
    "pub_date": "2019-08-24T14:15:22Z",
    "image": "encoded_image",
    "group": 0
}
```
## Лицензия
This project is Licensed under [Apache License, Version 2.0](https://www.apache.org/licenses/LICENSE-2.0).
