
# в проэкте для докера обезательным условием нужен dockerfile

`FROM python:*version*` <- установка в контейнер питона

`WORKDIR /app` <- создание в контейнере папки с проэктом

`COPY requirements.txt requirements.txt` <- копируем в контейнер нужные файл зафисимостей


`RUN pip install -r requirements.txt` <- запуск команды которая устанавливает зависимости
COPY . .
`CMD ["python", "manage.py", "runserver"]` <- команда запуска

после успешного создания dockerfile нужно ввести команду docker build -t appname . [[Docker commands]]

[[Docker]]
``

