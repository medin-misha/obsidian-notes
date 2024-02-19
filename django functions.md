## get_object_or_404
>взять проэкт или вирнуть ошибку  404 оно импортируеться из 'django.shortcuts'
>работает очень просто 
```python 
>def get(self, request:HttpRequest, pk:int):  
    model = get_object_or_404(Product, pk = pk)  
    context = {  
        "product":model  
    }  
    return render(request, "shop/detail-product/index.html", context = context)
>
```
принимает модель и свойство по которому мы ищем сущность модели

[[django]]