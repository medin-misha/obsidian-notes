сюда присойденены все сведенья про свойства и то как пользоваться compose.yaml docker


```yaml
services:
	appname:
		...
```
services - эта штука позволяет создавать сервисы, как показано на картинке


```yaml
appname:
	build:
		context: .
```
свойсто context получает путь ко всем нужным файлам для конкретного сервиса compose.yaml

```yaml
appname:
	prots:
		- 5000:5000
```
свойство ports связывает порты сервиса и нашего компьютера. По скольку изза изоляции docker container ты не можешь подключиться к ниму ты связываешь порты контейнера с портами компа вот и всё
```
appname:
	environment:
		- DEBUG=False
```
environment меняет переменные окружения это полезно когда доступ к настройкам проэкта пиздец как затруднён.

[[compose.yaml]]