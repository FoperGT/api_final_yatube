### Как запустить проект:


Клонировать репозиторий и перейти в него в командной строке:

```shell
git clone https://github.com/IvanMareev/api_final_yatube.git
```

```shell
cd api_final_yatube
```

Cоздать и активировать виртуальное окружение:

```shell
virtualenv -p python3 venv 
source venv/bin/activate 
```

Установить зависимости из файла requirements.txt:

```shell
pip install -r requirements.txt
```

Выполнить миграции:

```shell
python manage.py migrate
```

Создать суперпользователя для доступа к админ-панели:

```shell
python manage.py createsuperuser
```

Запустить проект:

```shell
python manage.py runserver
```

### Примеры запросов

#### Работа с постами

##### Получение списка постов

```http
GET api/v1/posts/
```

Пример ответа:
```json
[
  {
    "id": 1,
    "author": "user1",
    "text": "Пример поста",
    "created": "2024-01-01T12:00:00Z"
  }
]
```

##### Создание поста

```http
POST api/v1/posts/
```

Тело запроса:
```json
{
  "text": "Новый пост"
}
```

#### Работа с комментариями

##### Получение комментариев к посту

```http
GET api/v1/posts/{post_id}/comments/
```

Пример ответа:
```json
[
  {
    "id": 1,
    "author": "user2",
    "text": "Пример комментария",
    "created": "2024-01-01T13:00:00Z"
  }
]
```

##### Создание комментария

```http
POST api/v1/posts/{post_id}/comments/
```

Тело запроса:
```json
{
  "text": "Новый комментарий"
}
```

#### Работа с подписками

##### Подписка на пользователя

```http
POST api/v1/follow/
```

Тело запроса:
```json
{
  "following": "user3"
}
```

Пример ответа:
```json
{
  "user": "user1",
  "following": "user3"
}
```

### Авторизация через Djoser

Для управления аутентификацией и авторизацией используется библиотека [Djoser](https://djoser.readthedocs.io/). Она предоставляет готовые эндпоинты для регистрации, входа в систему, выхода и управления пользователями.

#### Регистрация пользователя

```http
POST api/v1/auth/users/
```

Тело запроса:
```json
{
  "username": "newuser",
  "password": "securepassword",
  "email": "newuser@example.com"
}
```

#### Получение токена для аутентификации

```http
POST api/v1/auth/token/login/
```

Тело запроса:
```json
{
  "username": "newuser",
  "password": "securepassword"
}
```

Пример ответа:
```json
{
  "auth_token": "123abc456def"
}
```

#### Выход из системы

```http
POST api/v1/auth/token/logout/
```

Запрос должен содержать токен в заголовке:
```http
Authorization: Token 123abc456def
```
