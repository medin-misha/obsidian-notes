1. Проект должен запускатся путем клонирования его из гита установки env опций и запуска

2. Админ панель с помощью **django admin**

3. Создать файл README.md 

4. нужно добавить [[фикстуру данных]] c базовой информацией работы проекта
	- пользователи 
	- администраторы
	- несколько продуктов
	- отзывов

5. Базовый процесс разворачивания проекта: 
	- git clone; 
	- изменение файла .env; 
	- python manage.py migrate; 
	- другие шаги по настройке (конфигурирование очередей и других сервисов проекта); 
	- python manage.py runserver 0.0.0.0:8000.
- 

6. структура сайта должна быть такой:
	- главная
		1. избранные категории товаров
		2. каталог
		3. топ товаров
		4. ограниченный тераж 16 товаров
	- каталог с товарами фильтрами и сортировкой
			1. фильтрация
				1. названию
				2. характеристикам
			2. сортировка 
				1. по кол-ву покупок
				2. по цене
				3. по кол-ву отзывов
				4. по времени
				- каждый переключатель можно установить по возрастанию и убыванию
			3. навигация
			4. каждый товар должен иметь
				1. название
				2. превью
				3. краткое описание
				4. цену
				5. отзывы
				6. кнопку купить
		- страница с деталями товара
			1. подробная инфа
			2. подгрузка отзывов
			3. возможность добавить свой отзыв
	- оформление заказа
		- карзина
		- оформление заказа
			- выбираеться способ доставки города и адреса
				- обычная доставка
					- если стоимость заказа меньше 2000р то 200 если больше то бесплатно должно быть в  админке
					- експресс доставка 
					- доставка такие же правила но  +500 должно быть в админке
			- выбираеться способ оплаты
				- онлайн картой и
				- онолайн со случайного счёта
			- блок поддержки заказа
				- ФИО
				- email
				- телефон
				- комментарий к заказу
		- оплата
			- номер не длиннее 8 цыфр
			- со случайного счёта (генерит 8 значный код)
			- кнопка оплатить
				- если счёт чётный и не заканчиваеться на 0 то оплата проходит
				- иначе ошибка оплаты
	- личный кабинет
		- Личный кабинет 
			- аватарка
			- ФИО
			- телефон и email должны быть разные у разных пользователей
		- профиль
		- история заказов
	- админка
		- товары
		- заказы
		- категории каталога

7. роли на сайте
	1. админ
	2. пользователь
	3. не зареганый пользователь

8. содержание сайта
	1. шапка
		1. лого
		2. ссылок на сотсети
		3. личный кабинет 
		4. корзину
	2. футер 
		1. названия сайта 
		2. статичной инфой
		
	