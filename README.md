![example workflow](https://github.com/schizgod/yamdb_final/actions/workflows/main.yml/badge.svg)

Как запустить проект:
Все описанное ниже относится к ОС Linux.

Клонируем репозиторий и и переходим в него:
git clone git@github.com:themasterid/yamdb_final.git
cd yamdb_final
Создаем и активируем виртуальное окружение:
python3 -m venv venv
Windows:
source venv/Scripts/activate
Linux:
source venv/bin/activate
Обновим pip:
python -m pip install --upgrade pip 
Ставим зависимости из requirements.txt:
pip install -r api_yamdb/requirements.txt 
Переходим в папку с файлом docker-compose.yaml:
cd infra
Предварительно установим Docker на ПК под управлением Linux (Ubuntu 22.10), для Windows немного иная установка, тут не рассматриваем:
sudo apt update && apt upgrade -y
Удаляем старый Docker:
sudo apt remove docker
Устанавливаем Docker:
sudo apt install docker.io
Смотрим версию Docker (должно выдать Docker version 20.10.16, build 20.10.16-0ubuntu1):
docker --version
Активируем Docker в системе, что бы при перезагрузке запускался автоматом:
sudo systemctl enable docker
Запускаем Docker:
sudo systemctl start docker
Смотрим статус (выдаст статус, много букв):
sudo systemctl status docker
Проверим:
sudo docker run hello-world 
Не будет лишнем установить PostgreSQL:
sudo apt install postgresql postgresql-contrib -y
Предварительно в папке infra создаем файл .env с следующим содержимом:
DB_ENGINE=django.db.backends.postgresql 
DB_NAME=postgres 
POSTGRES_USER=postgres 
POSTGRES_PASSWORD=postgres 
DB_HOST=db 
DB_PORT=5432
Так как требование ТЗ и тестов использовать postgresql, то создадим в системе бд, установив локаль:
sudo dpkg-reconfigure locales 
Выбираем ru_RU.UTF-8 нажав пробел и ждем сообщения Generation complete.
Generating locales (this might take a while)...
...
  ru_RU.UTF-8... done
...
Generation complete.
Перезапустим систему:
sudo reboot
Установка PostgreSQL:
sudo apt install postgresql postgresql-contrib -y
Управляем БД:
Остановить
sudo systemctl stop postgresql
