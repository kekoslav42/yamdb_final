![yamdb workflow](https://github.com/kekoslav42/yamdb_final/workflows/yamdb_workflow/badge.svg)
(Ну да, из-за приватности, если нужно могу скрином отправить в слаке)
# yamdb_final

Выполнялось api_yamdb с **[chaplinskiy](https://github.com/chaplinskiy)** & **[Seva138](https://github.com/Seva138)**
## Описание

Проект **YaMDb** собирает отзывы пользователей на произведения. 
Произведения делятся на категории: «Книги», «Фильмы», «Музыка». 
Список категорий (Category) может быть расширен (например, можно добавить категорию 
«Изобразительное искусство» или «Ювелирка» через интерфейс Django администратора).

## API запущено по адресу
```bash
http://51.250.16.59/api/v1/
```

###
Примеры запросов:
```bash
http://51.250.16.59/api/v1/categories/
http://51.250.16.59/api/v1/genres/
http://51.250.16.59/api/v1/titles/
```
Документация:
http://51.250.16.59/redoc/ (Редок сломан, чиню =) )


## Как запустить проект:

Клонировать репозиторий и перейти в него в командной строке:

```bash
git clone https://github.com/kekoslav42/yamdb_final.git
```

## Установка на локальный сервер
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

## Деплой на удаленный сервер
Для запуска проекта на удаленном сервере необходимо:
- скопировать на сервер файлы `docker-compose.yaml`, `.env`, `nginx`:
```
scp docker-compose.yaml  <user>@<server-ip>:
scp .env <user>@<server-ip>:
scp -r nginx/ <user>@<server-ip>:

```
- создать переменные окружения в разделе `secrets` гитхаб репозитория:
```
DOC_PASS # Пароль от Docker Hub
DOC_USER # Логин от Docker Hub
HOST # Публичный ip адрес сервера
USER # Пользователь зарегистрированный на сервере
PASSPHRASE # Если ssh-ключ защищен фразой-паролем
SSH_KEY # Приватный ssh-ключ
TELEGRAM_TO # ID телеграм-аккаунта
TELEGRAM_TOKEN # Токен бота
```

### При пуше в master:
1. Проверка кода на соответствие стандарту PEP8 и запуск yamdb_final
2. Сборка докер-образов.
3. Пуш на DockerHub.
3. Деплой на удаленный сервер.
4. Информирование в телеграмм.


## Инструкция по API
```json
/redoc/
```
