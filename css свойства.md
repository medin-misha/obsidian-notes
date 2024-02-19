# display
как я знаю у елементов на веб-странице есть 2 состояния

- `display:inline;` - занимает столько места сколько занимает текст в нём некоторые свойства `block` не может принимать к нему не может быть применина строгая ширина и высота

- `display:block;` - занимает всё возможное пространство по ширине 

- `display:None;` - убирает елемент

- `display:inline-block` - не занимает всю доступную ширину но при этом имеет свойства блока

# margin-padding
применяеться только для блочных елементов

1. **margin** - внешние границы объекта если `margin:30px` то ничто не может приблизиться к объекту меньше чем 30px
2. padding - внутренние границы если `padding:30px` то ни что не приблизится к границе объекта меньше чем на 30px
- у margin & padding есть 
	- -left
	- -right
	- bottom
	- top
- если у двух объектов есть `margin:30;` & `margin:40;` то будет работать тот margin который больше
# border
обводка елемента
1. border-width - ширина обводки
2. border-style - то как он выглядит
3. border-color - цвет
так же можно использовать и кородкую запись
`border: 10px solid black`

так же существует стороны обводки
border - 
- top - верх
- right - право
- left - лево
- bottom - низ
всё это отдельные свойства
# min/max - width/height
обозначение минимальной и максимальной высоты и ширины блока
- min-width - минимальная ширина
- min-height - минимальная высота
- max-width - максимальная ширина
- max-height - максимальная высота
# box-sizing
допустим у нас есть блок 
```css
.block {
    background-color:blueviolet;
    width: 100px;
    height: 100px;
    padding: 20px;
}
```
на блок будет padding + width + padding на padding + height + padding
свойство `box-sizing:border-box` 
```css
.block {
    background-color:blueviolet;
    width: 100px;
    height: 100px;
    box-sizing: border-box;
    padding: 20px;
}
```
делает так что бы padding не увеличивал размер блока, но при этом работал
это если что общепринятая норма
## font-famaly
меняет шрифт
```css
font-family: sans-serif
```
есть множество стилей шрифта по умолчанию а так же можно и скачать отдельные или указать ссылкой или импортом

[[css]]
