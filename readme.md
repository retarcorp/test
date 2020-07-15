# Тест для разработчика

Нужно скачать этот файл, заполнить соответствующие поля и прислать модифицированный md-файл по почте.

### 1. Напишите, какие бывают типы http запросов (Request methods)? 

~~~
# Напишите тут типы запросов.

GET
POST
PUT
DELETE
OPTIONS
HEAD
PATCH
HEAD

В целом, HTTP-протокол не ограничивает данными методами и позволяет, помимо указанных, использовать методы с любым названием, абы он был корректно указан в заголовке HTTP-запроса и мог быть обработан веб-сервером.

~~~


Нужно заполнить таблицу действий над ресурсами согласно REST-подходу.

*Поставьте «галочки» в нужных ячейках*.

**Depending on used HTTP method, these URLs can be used to perform different types of actions according to REST.**

|      | A                                  | /books | /books/17 |
| ---- | ---------------------------------- | ------ | --------- |
| 1    | Получить коллекцию                 |   + (HTTP GET)    |           |
| 2    | Создать новую запись о книге       |   + (HTTP POST)     |           |
| 3    | Изменить отдельную запись о книге  |        |     + (HTTP PUT/POST)      |
| 4    | Удалить всю коллекцию книг         |   + (HTTP DELETE)     |           |
| 5    | Удалить отдельную запись о книге   |        |     + (HTTP DELETE)       |
| 6    | Получить запись об отдельной книге |        |     + (HTTP GET)    |



### 2. Разница между процессом и потоком

*Поставьте «галочки» в нужных ячейках*.

|      | Свойство                                                   | Процессы | Потоки |
| ---- | ---------------------------------------------------------- | -------- | ------ |
| 1    | Взаимодействуют только через механизмы, предоставляемые ОС |          |    +    |
| 2    | Делят между собой память                                   |          |    +    |
| 3    | Владеют ресурсами                                          |    +      |        |
| 4    | Хранят больше информации о состоянии                       |    +      |        |
| 5    | "Легче" происходит переключение контекста                  |          |    +    |
| 6    | Имеют отдельное адресное пространство                      |    +      |        |
| 7    | Могут создавать объекты такого же типа                     |    +      |        |
| 8    | Могут владеть объектами того же типа                       |    +      |        |


### 3. Медиана трех чисел

Нужно написать функцию, которая возвращает среднее по значению число из трех чисел.

Для [5, 1, 2] результат будет 2.

~~~javascript
// Сигнатура на js
function median3(a, b, c) {
    return [a, b, c].sort((a, b) => a - b)[1];
}
~~~

### 4. В чем проблема этого кода? Как улучшить?

~~~javascript
var done = false;

$.ajax(url, function() {
    done = true;
});

while (!done) {
    doSomething();
}
~~~

**Мне не нравится, что здесь есть сильная связность кода, флаг создается, меняется и применяется в трех разных местах. Кроме того, использование бесконечного цикла в JS на флаге приведет к забиванию потока выполнения кода (даже если, например, doSomething() меняет кадр анимации прелоадера, сама функция выполняется синхронно, а потому дерево документа будет заблокировано и пользователь не увидит никакой анимации ровно до тех пор, пока флаг не станет true). Адекватным решением второй проблемы было бы использование рекурсивного таймера. С использованием промисов или коллбэка можно обойтись и классическим интервалом без использования флага:**

~~~js


// Опишите проблему и напишите код, который её исправляет
  
  const pendingInterval = window.setInterval(() => {
    doSomething();
  }, 100) 
  const request = axios.get(url).then(() => {
    window.clearInterval(pendingInterval);
  })

~~~


### 5. Баблинг событий интерфейса

Допустим, мы повесили обработчик на событие “click” гиперссылки. Что нужно дописать в обработчике, чтобы прекратить обработку события и предотвратить переход по этой ссылке?

**Этот механизм называется не всплытием, а действием по умолчанию. При отмене действия по умолчанию (как в примере кода ниже) событие все равно продолжит всплывать.**

~~~javascript

// Напишите код тут
 a.addEventListener((e) => e.preventDefault());

~~~


### 6. Заполните таблицу сложности алгоритмов

*Поставьте «галочки» в нужных ячейках*.

|      | A                                                  | O(1) | O(ln(N)) | O(N) | O(N*ln(N)) | O(N^2) | Другой вариант |
| ---- | -------------------------------------------------- | ---- | -------- | ---- | ---------- | ------ | ------------ |
| 1    | Вставка в красно-черное дерево                     |      |     +     |      |            |        |              |
| 2    | Быстрая сортировка в среднем                       |      |          |      |      +      |        |              |
| 3    | Вставка в хеш-таблицу                              |   +   |          |      |            |        |              |
| 4    | Поиск в связном списке                             |      |          |   +   |            |        |              |
| 5    | Двоичный поиск в отсортированном массиве           |      |     +     |      |            |        |              |
| 6    | Обход красно-черного дерева от большего к меньшему |      |     +     |      |            |        |              |
| 7    | Вставка в хеш-таблицу в случае коллизии            |   +   |          |      |            |        |              |
| 8    | "Пузырьковая" сортировка                           |      |          |      |            |    +    |              |
| 9    | Удаление из массива (со сдвигом)                   |      |          |   +   |            |        |              |
| 10   | Поиск в хеш-таблице                                |  +    |          |      |            |        |              |


### 7. arr.push(a) эквивалентен

~~~javascript
// Закоментируйте неправильные варианты
//arr[0] = a
arr[arr.length] = a
//arr[arr.length - 1] = a
//arr[-1] = a
~~~

### 8. Нужно отметить несколько верных утверждений о различных БД

*Поставьте «галочки» в нужных ячейках*.

|      | A                                                            | MongoDB | MySQL | Postgres |
| ---- | ------------------------------------------------------------ | ------- | ----- | -------- |
| 1    | Хранит документы                                             |    +     |       |          |
| 2    | Хранит строки данных                                         |         |    +   |     +     |
| 3    | Гарантирует атомарность изменения нескольких коллекций/таблиц |         |   +    |    +      |
| 4    | Позволяет эффективно сделать запрос к полю JSON              |    +     |       |          |
| 5    | Требует описания "схемы" данных, таблицы                     |         |   +   |    +      |
| 6    | Гарантирует атомарность на уровне документа/строки           |    +     |   +    |    +      |
| 7    | Удовлетворяет критериям ACID                                 |         |   + (with InnoDB)    |      +    |
| 8    | Поддерживает репликацию на несколько машин                   |     +    |   +    |     +     |


### 9. Что может происходить в браузере, когда пользователь вводит адрес (https://ya.ru) в адресной строке и нажимает Enter?

*Поставьте «галочки» в нужных ячейках*.

|      | A                                     |      |
| ---- | ------------------------------------- | ---- |
| 1    | Сжатие исходных JS кода               |      |
| 2    | Проверка сертификатов                 |   +   |
| 3    | Парсинг HTML                          |   +   |
| 4    | Запуск PHP скриптов сайта             |      |
| 5    | Исполнение Javascript                 |   +   |
| 6    | Парсинг CSS                           |   +   |
| 7    | Загрузка данных html страницы по HTTP |   +   |
| 8    | Деобфускация JS кода                  |      |
| 9    | TLS handshake                         |   +   |
| 10   | DNS запрос по UDP                     |   +   |
| 11   | Построение DOM-дерева                 |   +   |


### 10. В чем различие между протоколами TCP и UDP?

*Поставьте «галочки» в нужных ячейках*.

|      | A                                                    | TCP  | UDP  |
| ---- | ---------------------------------------------------- | ---- | ---- |
| 1    | Гарантирует доставку данных                          |   +   |      |
| 2    | Лучше подходит для задач условно "реального времени" |      |   +   |
| 3    | Требует установки соединения                         |  +    |      |
| 4    | Обеспечивает более высокую скорость передачи данных  |      |   +   |
| 5    | Работает внутри IP сетей                             |   +   |      |
| 6    | Гарантирует последовательность доставки              |   +   |      |


### 11. Задача "выколотый массив"

```arr``` - массив чисел от 1 до N, в котором одно число выкинули, а остальной массив перемешали.  

Требуется написать функцию, которая принимает на вход массив ```arr``` и возвращает удаленное число.   
Решение должно быть линейным, не должно модифицировать исходный массив и использовать дополнительную память объем которой зависит от размера входного массива.  

```javascript
// Сигнатура на js
function findMissing(arr) {

    const nums = new Array(arr.length + 1).fill(-1);
    nums[0] = 0;
    arr.forEach(n => nums[n] = 1);
    return nums.indexOf(-1);
}
```

### 12. Задача "таймер" 

Страница загружена в браузере имеет участок html разметки: 

```html
<div>
    <p class="timer">100 секунд</p>
</div>
```  

Требуется написать скрипт, который решает задачу автоматического обновления текста таймера.
После выполнения кода происходит автоматическое изменение текста в элементе `.timer`: 101 секунда, 102 секунды...

```javascript

var state = {time: 100}

// Впишите код тут!

setInterval(updateCounter, 1000)
function updateCounter() {
  state.time += 1
  const elem = document.querySelector('.timer');
  let suffix = 'секунд';
  switch (state.time % 10) {
    case 1:
        suffix = 'секунда';
        break;
    case 2:
    case 3:
    case 4:
        suffix = 'секунды';
        break;
  }
  
  elem.innerText = `${state.time} ${suffix}`;
}

```
