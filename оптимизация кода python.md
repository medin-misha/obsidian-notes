# __slots__
это свойство класса которое нужно вписать что бы класс не занимал много места
вот пример:
```python
class GameLife:  
    __slots__ = ('field_size', "playing_field")  
    def __init__(self, field_size: tuple = (50, 50)):  
	  self.field_size = field_size  
	  self.playing_field = ()
      ```
  > у класса есть такой атрибут `__dict__` и по сути мы его обявлением 
  > `__slots__` убираем что позваоляет нам использовать меньше памяти
  > и программа работает быстрее за счёт этого

[[python tutorials]]