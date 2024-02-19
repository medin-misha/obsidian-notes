# .array
создание массива
```python 
list1 = [
    [i for i in range(16)]
    for _ in range(9)
]

a = np.array(list1, int)

print(a)
```
> физика такая:
> мы создаём list возможно вложеный закивываем его в `array` указываем 
> тип данных например `int` и всё у нас создаёться массив

так же если нам нужно найти елемент в массиве то можно использовать
оператор `in`
```python
list1 = [
    [i for i in range(16)]
    for _ in range(9)
]

a = np.array(list1, int)

print(2 in a)
```
>вывод будет `true` по тому что цыкл записывает числа от 0 до 15 

так же многомерный массив можно конвертировать в одномерный:
```python 
list1 = [
    [i for i in range(16)]
    for _ in range(9)
]

a = np.array(list1, int)

print(a)

print(a.flatten())
```

[[numpy]]
