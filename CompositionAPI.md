
С помощью Composition API мы определяем логику компонента с помощью импортированных функций API. В SFCs Composition API обычно используется с [`<script setup>`](https://vuejs.org/api/sfc-script-setup). Атрибут `setup` - это подсказка, которая заставляет Vue выполнять преобразования во время компиляции, которые позволяют нам использовать Composition API с меньшим количеством шаблонов. Например, импорт и переменные / функции верхнего уровня, объявленные в `<script setup>`, могут использоваться непосредственно в шаблоне.

Вот тот же компонент с точно таким же шаблоном, но использующий Composition API и `<script setup>` вместо:

```js
<script setup>
import {ref, onMounted} from 'vue'
const count = ref(0)

function increment() {
    count.value ++
}
  
onMounted(() => {
  console.log(`The initial count is ${count.value}.`)
})
</script>
```
