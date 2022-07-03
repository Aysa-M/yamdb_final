![STATUS](https://github.com/Aysa-M/yamdb_final/actions/workflows/yamdb_workflow.yml/badge.svg)

# ***Групповой проект. Спринт 10. Яндекс.Практикум.***
## **Описание проекта API для YaMDB.**
API для проекта YaMDB - проекта соц.сети, в котором пользователи могут размещать обзоры на произведения в разных категориях (фильмы, музыка, кино) и жанрах, после чего на основании оценок формируется рейтинг произведений. 
- API проекта позволяет: 
    - регистрироваться пользователям;
    - управлять списком категорий, жанров, произведений;
    - получать, размещать изменять и удалять отзывы, комментарии к ним;
    - а еще у нас есть рейтинг произведений и неплохая админка!

*Примечание.* Сами произведения в **YaMDb** не хранятся, здесь нельзя посмотреть фильм или послушать музыку.

## **Технологии (основные инструменты):**
- Python==3.7
- Django==2.2.16
- djangorestframework==3.12.4
- djangorestframework-simplejwt==5.1.0
- gunicorn==20.0.4
- psycopg2-binary==2.8.6 (в идеале psycopg2)
- PyJWT==2.1.0
- pytest==6.2.4
- python-dotenv==0.20.0
- Docker

### Деплой в Dev режиме:
1. Клонируйте репозиторий:
    *$ git clone https://github.com/Aysa-M/yamdb_final.git*
 
2. Создайте виртуальное окружение (venv) - должен быть флажок в начале строки:
    *$ python -m venv venv*
 
3. Установите зависимости:
    *$ pip install -r requirements.txt*

4. Создайте и примените миграции:
    *$ python manage.py makemigrations*
    *$ python manage.py migrate*

5. Запустите django сервер:
    *$ python manage.py runserver*

### Деплой проекта на боевой сервер с помощью образа Docker:
1. Входим на боевой сервер (ваша виртуальная машина).

2. Необходимо установить **Docker** для дальнейшего процесса размещения проекта на боевом сервере. 
    *$ sudo apt install docker.io*

3. Проверьте наличие на сервере docker-compose. Если его нет, то установите его выполнив следующие команды по порядку:
   
    - Установите утилиту curl для скачивания docker-compose:
    *$ sudo apt -y install curl*
  
    - Скачиваем docker-compose с помощью утилитыЖ
    *$ sudo curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose*

    - Добавим право исполняемости файла docker-compose:
    *sudo chmod +x /usr/local/bin/docker-compose*

    - Проверьте, что docker-compose работает путем проверки отображения списка комманд при его вызове:
    *docker-compose*

4. Запустите образ под названием проекта - *yamdb_final* и разверните контейнеры с приложениями:
    *docker run yamdb_final*

5. Создайте и примените миграции внутри основного контейнера **web**:
    *$ docker-compose exec web python manage.py makemigrations*
    *$ docker-compose exec web python manage.py migrate*

6. Сайт доступен по адресу http://51.250.98.29:8000/
    *$ docker-compose exec web python manage.py collectstatic --no-input*

Успех! Теперь вы можете использовать код! Надеемся, что вы будете использовать его только во благо и желаем вам удачи в начинаниях!

## **Документация к API:**
После запуска проекта 
по адресу http://51.250.98.29:8000/redoc/ доступна документация для API **YaMDB**.

## **Авторы:**
*Kuzin Anatoliy, Zhirkov Pavel, Matsakova Aysa*