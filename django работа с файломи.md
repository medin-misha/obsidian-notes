
## в settings.py создадим 2 переменные

```python
	MEDIA_ROOT = BASE_DIR / "uploads"
	MEDIA_URL = /media/
```
>==MEDIA_ROOT== - тут ты указываешь путь папке с файлами где будут храниться твои файлы
>
>**==MEDIA_URL==** - это ссылка по которой мы будем обрящяться когда нам нужны файлы путь будет выглядить примерно так http://locachost:8000/media/filename

## в главном urls.py 
```python
	from django.conf import settings  
	from django.conf.urls.static import static
	
	if settings.DEBUG:  
    urlpatterns.extend(  
        static(settings.MEDIA_URL, document_root = settings.MEDIA_ROOT)
```
>это можно сказать система безопасности, никому не захочеться отдавать доступ к своим медиафайлам левым людям когда `DEBUG = False` пути к файлам 
>(http://locachost:8000/media/filename) будут закрыты

## создаём модели с FileField 

```python
models.py:
	class product(models.Model):
		name = ..
		description = ..
		description_file = models.FileField(null=True, blank=True,  upload_to = "products/description_files/")
	
```
>Обрати внимание на поле `description_file` это поле для сохранения и привязки файла к сущности модели
>1. null = True означает что в поле может ничего не находиться
>2. blank = True означает что поле может быть пустым
>3. upload_to = products/description_files/ означает то что файл сущности модели нужно сохранять по пути products/description_files/ 
c с переди строки свойства поля будет добавлять MEDIA_ROOT (папка в которой храняться файлы) а с переди имя файла

***так же джанго заботиться о всём о чём можно позаботиться и в случае скидывания того же файла он не перезапишет его***


## ImageField и функции
так же в upload_to можно добавлять функции как генератор пути будет так же показано не на **FileField** а на **ImageFiled**

```python
models.py:
	def save_to_dir(instanse:"Product", filename:str):  
	    return f"product/images/{instanse.pk}/{filename}"
    
	class Product(models.Model):  
	    name = ..  
	    description = ..
	    price = ..  
	    preview= models.ImageField(upload_to=save_to_dir)
```
>Тут фуркция `save_to_dir` принимает как оргумент *instanse* & *filename*
>и возвращяет нам отформатированный путь к файлу, **держим в голове то что к пути с переди добавляеться ещё и `/media/`**

>стоит заметить ещё и то что `ImageField` принимает все те же оргументы что и `FileField`





[[поля]]
[[django]]