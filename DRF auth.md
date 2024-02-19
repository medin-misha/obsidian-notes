Django REST Framework предоставляет некоторое количество вариантов реализации [[Аутентификация]]

##### свойства
1. `request.user`  присваевается экземпляру класса User django, если пользователь не авторизован то присваевается AnonymousUser 
2. `request.auth` используется для любой доп информации по умолчанию NONE
В Django Rest Framework аутентификация, и регистрация реализована вот так: 
- регистрация и последуйщая аутентификация
  ```python
  def post(self, request:Request) -> Response:
        
        serializer = UserModelSerializer(data = request.data)
        
        if serializer.is_valid():
            model = User.objects.create(
                last_name = data["last_name"],
                username = data["username"],
                password = data["password"],
            )
            request.user = model
            auth_user = authenticate(
	            request=request,
	            username = data.get("username"),
	            password = data.get("password")
	       )
           login(request=request, user = auth_user)
           
           return Response(status = 200)
        return Response(status = 400)
``` 
	мы получаем данные из формы и кидаем их в Serializer который в зарание подготовили
	```python
	class UserModelSerializer(ModelSerializer):
	    class Meta:
	        model = User
	        fields = ["last_name", "username", "password"]
	```
	Блок `if` проверяет правильность вводимых данных если они правильны то создаём юзера создаём переменную и аутентифицируем этого юзера и в `login` он входит в аккаунт
- аутентификация 
	```python
	class LoginAPIView(APIView):
    def post(self, request:Request):
        data = get_data_from_request(request=request)
        user = User.objects.get(username = data.get("username"))
        login(request = request, user = user )
        return Response({}, status=200)
```
тут плюс минус тоже самое только мы получаем request.user через request.data получаем username или другие данные и логируем его
- выход из аккаунта
  ```python
  class LogoutAPIView(APIView):
    def post(self, request:Request) -> Response:
        logout(request=request)
        return Response(status=200)
```

[[DRF]]