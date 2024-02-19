тут будет общее описание как пользоваться Django Rest Framework

## установка в проект
Установка пакета `rest_ramework`

тут нужно установить 2 библиотеки
- `pip install djangorestframework` сам инструмент
- `pip install django-cors-headers` инструмент безопасности
второе нужно устанавливать для того что бы твоим софтом было безопасно пользоваться



Далее в `INSTALLED_APPS` нужно подключить `rest_framework` и `corsheaders` а так же в `MIDDLEWARE` нужно подключить 
```python
INSTALLED_APPS = [
	"rest_framework",
	'corsheaders',
]
MIDDLEWARE = [
	'corsheaders.middleware.CorsMiddleware',
]
```
так 
## настройка (не обязательно oно будет к стати)
```python
REST_FRAMEWORK = {    "DEFAULT_PAGINATION_CLASS":"rest_framework.pagination.PageNumberPagination",
    "PAGE_SIZE":10,
}
```
Настройка `"DEFAULT_PAGINATION_CLASS"` в Django REST framework определяет класс, который будет использоваться по умолчанию для разбиения результатов запроса на страницы при использовании пагинации.

В данном случае, установлено значение
`"rest_framework.pagination.PageNumberPagination"`. 
Этот класс реализует пагинацию по номерам страниц. Когда он активен, результаты запроса будут разбиты на страницы, и клиент может запрашивать конкретную страницу, указывая ее номер.

полезно но не обязательно

## первый rest_view
```python
from rest_framework.response import Response
from rest_framework.request import Request
from rest_framework.decorators import api_view
  
@api_view()
def first_api_view(request:Request) -> Response:
    return Response(
        {
            "name":"misha",
            "age":15,
            "gmail":"med@gmail.com"
        }
    )
```
 - `Response` это ответ API он отличаеться от Http тем что не возвращяет [[html]] шаблон
 - `Request` - запрос
 - `api_view` это декоратор который делает возможным это api предстовление
по своей сути api ответ это обычный `dict` или json так с ним и надо работать.

## class based views
```python
class MyAPIView(APIView):
    def get(self, request:Request) -> Response:
         return Response(
        {
            "name":"misha",
            "age":15,
            "gmail":"med@gmail.com"
        }
    )
```
по сути всё точно также как в и обычном `class based views` но с `API`
так же вот примеры других штук



## serializers
***Сериализатор*** это как инструмент который позволяет мне передавать сложные типы данных (модели django) по сети. 
создадим файл `serializers.py`
```python
from rest_framework import serializers
from .models import Product

class ProductSerializer(serializers.ModelSerializer):
    class Meta:
        model = Product
        fields = ["name", "description", "price", "archived"]
```
## view generic
это шаблоны для `Class based view` их довольно много из самых часто используемых
- APIView - по сути это как функция но с ооп стилем, нужно для каких то мега кастомов
- CreateAPIView - создание модели, в него нужно закинуть `serializer_class` и по ниму будет создаваться модель
- ListAPIView - список сущностей модели принимает `queryset`, `serializer_class`


[[django]]
[[DRF auth]]