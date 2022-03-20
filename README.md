
![yamdb_workflow.yml](https://github.com/Bogdan-Kirilyuk/yamdb_final/actions/workflows/yamdb_workflow.yml/badge.svg?branch=master&event=push)

# API_YAMDB 
REST API проект для сервиса YaMDb — сбор отзывов о фильмах, книгах или музыке. 

Проект развернут по адресу: http://84.252.131.146/redoc/
## Описание 
 
Проект YaMDb собирает отзывы пользователей на произведения. 
Произведения делятся на категории: «Книги», «Фильмы», «Музыка». 
Список категорий  может быть расширен (например, можно добавить категорию «Изобразительное искусство» или «Ювелирка»). 
### Локальный запуск проекта: 
Клонируем репозиторий и и переходим в него: 
```bash 
git clone https://github.com/Bogdan-Kirilyuk/yamdb_final
cd yamdb_final 
cd api_yamdb 
``` 
 
Создаем и активируем виртуальное окружение: 
```bash 
python3 -m venv venv 
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

### Документация API YaMDb 
Документация доступна по эндпойнту: http://84.252.131.146/redoc/

Автор: Студент факультета "Python-разработчик" Яндекс.практикума, когорта 21. Богдан Кирилюк.