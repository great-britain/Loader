# Loader
The script allows you to upload files up to 2GB to the server from the web interface
Простой веб-сервер для загрузки файлов с аутентификацией по паролю.
СТруктура папок
/path/to/project/
├── app.py               # Основной скрипт сервера
├── templates/           # HTML-шаблоны
│   ├── index.html       # Основная страница загрузки
├── uploads/             # Папка для загруженных файлов
├── README.md            # Документация


Убедитесь что установлен pip3 install flask flask-wtf werkzeug
Запуск python3 app.py

 Настройка автозапуска через systemd

Чтобы сервер работал постоянно, настрой systemd:

1. Создайте сервис-файл:

sudo nano /etc/systemd/system/upload_server.service

2. Добавьте в него:

[Unit]
Description=Flask Upload Server
After=network.target

[Service]
User=root
WorkingDirectory=/path/to/project
ExecStart=/usr/bin/python3 /path/to/project/app.py
Restart=always

[Install]
WantedBy=multi-user.target

Замените /path/to/project на реальный путь.

3. Перезагрузите systemd и запустите сервис:

sudo systemctl daemon-reload
sudo systemctl start upload_server
sudo systemctl enable upload_server

Теперь сервер будет автоматически запускаться при старте системы.
Все загрузки в папке uploads к которой можно иметь доступ через SFTP клиент

