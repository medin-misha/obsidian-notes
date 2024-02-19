# основные основы
в файлике compose.yaml запишем такую хуету
````yaml
services:
  web:
    build: .
    ports:
      - "8000:5000"
  redis:
    image: "redis:alpine"
````
	сдесь создаёться 2 сервиса:
	1. web
		1. это наше приложение и название может быть произвольным
	2. redis мы берём из публичного образа redis:alpine
далее когда мы сделали [[docker file]] и compose.yaml мы можем ввести соманду:
[[Docker commands]]
`docker compose up`
при чём даже если ты не создал образ 
(`docker build -t appname .`)
будет работать 


рассмотрим следуйщий код

```yaml
services:
  web:
    build: .
    ports:
      - "8000:5000"
    volumes:
      - .:/code
    environment:
      FLASK_DEBUG: "true"
  redis:
    image: "redis:alpine"
```
мы добавляем к приложению web параметры volumes & enviroment
	1. volumes
		сюда мы указываем папки в к которым [[docker container]] связывает наш коталог . с каталогом контейнера /code и теперь все изменения в нашем коталоге отображаються в коталоге /code
	2. enviroment 
		используеться для настроки переменных окружения то есть у нас есть файл с переменными окружения и эти переменные влияют на проэкт тут нужно уточнить что `FLASK_DEBUG: "true"` это переменная которая написанна граматически правильно
после изменений вводим [[Docker commands]] docker compose upcd com
[[Docker]]