![yamdb workflow](https://github.com/kekoslav42/yamdb_final/workflows/yamdb_workflow/badge.svg)

# infra_sp2 // api_yamdb

Выполнялось api_yamdb с **[chaplinskiy](https://github.com/chaplinskiy)** & **[Seva138](https://github.com/Seva138)**
## Описание

Проект **YaMDb** собирает отзывы пользователей на произведения. 
Произведения делятся на категории: «Книги», «Фильмы», «Музыка». 
Список категорий (Category) может быть расширен (например, можно добавить категорию 
«Изобразительное искусство» или «Ювелирка» через интерфейс Django администратора).


## Как запустить проект:

Клонировать репозиторий и перейти в него в командной строке:

```bash
git clone https://github.com/kekoslav42/infra_sp2.git
```

## Установка
1. Установка docker и docker-compose
Инструкция по установке доступна в официальной инструкции

2. Создать файл .env с переменными окружения

```bash
SECRET_KEY = Секретный ключ django
DEBUG = Режим дебага
ALLOWED_HOSTS = Разрешенные подключения
DB_ENGINE=django.db.backends.postgresql
DB_NAME=postgres
POSTGRES_USER= Пользователь базы данных
POSTGRES_PASSWORD= Пароль базы данных
DB_HOST= Хост базы данных
DB_PORT= Порт базы данных
```

3. Сборка и запуск контейнера

```bash
docker-compose up -d --build
```

4. Сбор статики

```bash
docker-compose exec web python manage.py collectstatic --noinput
```
5. Применение миграций

```bash
docker-compose exec web python manage.py migrate
```

6. Создание суперпользователя Django

```bash
docker-compose exec web python manage.py createsuperuser
```


## Инструкция по API
```json
/redoc/
```
