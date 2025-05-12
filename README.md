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
