
![yamdb_workflow.yml](https://github.com/Bogdan-Kirilyuk/yamdb_final/actions/workflows/yamdb_workflow.yml/badge.svg?branch=master&event=push)

# API_YAMDB 
Проект YaMDb собирает отзывы пользователей на произведения. Произведения делятся на категории: «Книги», «Фильмы», «Музыка», список категорий может быть расширен.

Проект развернут по адресу: http://84.252.131.146/redoc/

### Локальный запуск проекта: 
Клонируем репозиторий и переходим в него: 
```bash 
git clone https://github.com/Bogdan-Kirilyuk/yamdb_final
cd yamdb_final 
cd api_yamdb 
``` 

Создаем и активируем виртуальное окружение: 
```bash 
python -m venv venv 
source /venv/Scripts/activate
``` 

Ставим зависимости из requirements.txt: 
```bash 
pip install -r requirements.txt 
``` 

Переходим в папку с файлом docker-compose.yaml и поднимаем контейнеры: 
```bash 
cd infra
sudo docker-compose up -d --build 
``` 

Выполняем миграции: 
```bash 
sudo docker-compose exec web python manage.py makemigrations reviews 
``` 
```bash 
sudo docker-compose exec web python manage.py migrate --run-syncdb
``` 

Создаем суперпользователя: 
```bash 
sudo docker-compose exec web python manage.py createsuperuser 
``` 

Србираем статику: 
```bash 
sudo docker-compose exec web python manage.py collectstatic --no-input 
``` 

Для остановки контейнеров: 
```bash 
sudo docker-compose down -v 
``` 


Автор: Студент факультета "Python-разработчик" Яндекс.практикума, когорта 21. Богдан Кирилюк.