## html шаблон django - 
>это аштмл страница в которой можно писать код.
> циклы, условия, функции и другая херня


**И так создадим базовый шаблон в template/appname/base/base.html**
```django
<!DOCTYPE html>  
<html lang="en">  
<head>  
    <meta charset="UTF-8">  
  
    <title>{% block title%} {% endblock %}</title>  
</head>  
<body>  
{% block body %}  
  
{% endblock %}  
</body>  
</html>
```
> Вот эта херня называеться блоком, `{% block title%} {% endblock %}`
> 	блок обязательно должен быть закрыт, иначе будет `ERROR`.
> В базовом шаблоне можно создавать блоки и изначально писать код в них

после создания BASE.html создаём шаблон условной формы для создания `Product`
```django
{% extends "appname/base/base.html"%}  
  
{% block title %} create new product {% endblock %}  
  
{% block body %}  
<form method="post" enctype="multipart/form-data">  
    {% csrf_token%}  
    {{form.as_p}}  
    <label for="images">products images</label>  
    <input name = "images" id = "images" type="file" multiple>  
    <button type="submit">create</button>  
  
</form>  
  
{% endblock %}
```
>В первой же строке мы обращяемся к `base.html` если структура 
>	шаблонов выглядит так:
```
templates[
	shop[
		base[
			base.html
		]
		create-product[
			index.html
		]
	]
]
```
> то путь к из index.html в base.html будет такой:
> `"appname/base/base.html"` иначе не как.
> далее мы переопределяем тег `title` и `body` на свой аштмл код если
> 	нужно

[[django]]