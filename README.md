# Api_final_yatube

### Описание
YaTube - социальная сеть блогеров.
В этом пректе реализован REST API для приложения YaTube - программный интерфейс, позволяющий:
- получать информацию о постах всех пользователей;
- получать информацию о сообществах;
- управлять своими постами (создание, редактирование, удаление);
- управлять своими комментариями к постам (создание, редактирование, удаление);
- подписываться на авторов других постов.

Данные передаются в формате JSON.
Для неавторизованных пользователей данные доступны только для чтения (информация о подписках достуна только авторизованным пользователям).
### Технологии
- Python 3.9
- Django 3.2.16
- djangorestframework 3.12.4
- SimpleJWT

### Запуск проекта в dev-режиме
- Клонируйте репозитоий
```
git clone https://github.com/ZebraHr/api_final_yatube/
```
- Установите и активируйте виртуальное окружение
```
python3 -m venv venv
source venv/Scripts/activate
```
```
python3 -m pip install --upgrade pip
```
- Установите зависимости из файла requirements.txt
```
pip install -r requirements.txt
``` 
- Выполните миграции:
```
python3 manage.py migrate
```

- Запустите проект:

```
python3 manage.py runserver
```
### Примеры запросов
Пример GET-запроса получение всех публикаций. При указании параметров limit и offset выдача должна работать с пагинацией
```
GET .../api/v1/posts/
GET .../api/v1/posts/?offset=4&limit=6/
```
Ответ
```
{
"count": 123,
"next": "http://api.example.org/accounts/?offset=400&limit=100",
"previous": "http://api.example.org/accounts/?offset=200&limit=100",
"results": [
{...}
]
}
```
Пример POST-запроса добавление нового поста
```
POST .../api/v1/posts/
```
```
{
"text": "string",
"image": "string",
"group": 1
}
```
Ответ
```
{
    "id": 1,
    "author": "user",
    "text": "string",
    "pub_date": "2023-06-19T09:43:41.387928Z",
    "image": "string",
    "group": 1
}
```
Пример GET-запроса получения комментария по id
```
GET .../api/v1/posts/{post_id}/comments/{id}/
```
Ответ
```
{
"id": 0,
"author": "string",
"text": "string",
"created": "2019-08-24T14:15:22Z",
"post": 0
}
```
##### Весь доступный функционал API:
```
/redoc/
```
### Автор
Анна Победоносцева
Студент Яндекс Практикума "Python-разаботчик плюс"
г. Москва
GitHub: https://github.com/ZebraHr
