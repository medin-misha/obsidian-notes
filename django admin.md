
В [[django]] есть admin понель которая позволяет при грамотной настройке манипулиовать моделями как хочешь, админ панель так же может управлять 
1. пользователями
2. группами пользователей 
3. моделями 
Так же стоит понимать что Admin понель должна быть доступна не всем а только админам или людям которые помогают с администрирование проэкта

## настройка 
В `admin.py` в приложении напишем 
```python 
from django.contrib import admin
from .models import ProductImage, Product

@admin.register(Product)
class ProductAdmin(admin.ModelAdmin):
    list_display = ("pk", "name", "price")
```
этот код позволит нам зарегистрировать модель  Product а так же свойство `list_display` указывает какие поля будут видны в списке сущностей модели

таких свойств как `list_display` много:
- list_display указывает поля которые будут видны в таблице моделей, принимает картеж со сроками
- list_display_link - указвает поля по которым можно будет нажать и перейти в редактирование модели
- fields = ( ("name", "price"), "description", "preview", "archived" ) связывание двух полей допустим `name` и `price` будет на одной линии
- fieldsets позволяет очень удобно сортировать поля по секциям 
```python
    fieldsets = (
        ("info", {
            "fields":("name", "price", "description")
        }),
        ("files", {
            "fields":("preview",)
        }),
        ("settings", {
            "fields":("archived",)
        })
    )
```

## inlines
в какой то момент нужно будет что бы в админ панели отображалась связь один к одному или многие ко многим или один ко многим так вот как это делается

один ко многим
```python 
class ProductImageInline(admin.TabularInline):
    model = ProductImage
    extra = 1 # количество свободных полей
```

многие ко многим
```python 
class ProductInline(admin.TabularInline):
    model = Product.tags.through
    extra = 1
```
