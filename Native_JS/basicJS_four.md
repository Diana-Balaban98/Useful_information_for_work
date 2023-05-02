# 1 Map. В чём особенность? Какие свойства и методы есть? Как перебрать?
1. [ ] Map — коллекция для хранения данных любого типа в виде пар [ключ, значение], т.е каждое значение сохраняется по уникальному ключу, который потом используется для доступа к этому значению. 
3. [ ] В качестве ключей принимаются значения любого типа.

                                                Основные методы:
* set(ключ, значение) — устанавливает значение;
* get(ключ) — возвращает значение;
* has(ключ) — проверяет наличие переданного ключа;
* values() — возвращает итератор всех значений коллекции;
* keys() — возвращает итератор всех ключей коллекции;
* entries() — возвращает итератор пар[ключ, значение];
* delete(ключ) — удаляет конкретное значение;
* clear() — полностью очищает коллекцию;
* forEach(callback) — перебирает ключи и значения коллекции.
  
                                         Свойство:
* size — для получения количества значений в коллекции.

                                          Создание коллекции:
```js
const map = new Map(); 

const newMap = new Map([['js', 'JavaScript'], ['css', 'Cascading Style Sheets']]); 
```
                                            Работа с коллекцией:
```js
map.set('js', 'JavaScript');

console.log(map.get('js')); // JavaScript

console.log(map.size); // 1    
```
                                            Перебор:
```js
for (let [key, value] of newMap) { // js - JavaScript
    console.log(`${key} - ${value}`); // css - Cascading Style Sheets
}                 

newMap.forEach((value, key) => console.log(`${key} - ${value}`));
```


# 2 Set. В чём особенность? Какие свойства и методы есть? Как перебрать?
1. [ ] Set — коллекция для хранения уникальных значений любого типа. Одно и то же значение нельзя добавить в Set больше одного раза.
2. [ ] Set — это неиндексированная коллекция, положить элемент в коллекцию можно, но достать нельзя. По элементам коллекции можно 
итерироваться.

                                             Основные методы:
* add() — добавить элемент.
* delete() — удалить элемент.
* has() — проверить, есть ли элемент в коллекции.
* clear() — очистить коллекцию.
* forEach() — выполнить функцию для каждого элемента в коллекции, аналогично одноимённому методу массива.

                                               Свойство:
* size — для получения количества элементов в коллекции.

                                            Создание коллекции:
```js
const uniqueIds = new Set();

const filled = new Set([1, 2, 3, 3, 3, 'hello']);
```
                                             Работа с коллекцией:
```js
console.log(filled); // Set(4) { 1, 2, 3, 'hello' }

uniqueIds.add(123);

uniqueIds.add(456);

console.log(uniqueIds); // Set(2) { 123, 456 }

console.log(uniqueIds.size); // 2
```
                                                    Перебор:
```js
for (let value of filled) { 
     console.log(value); 
}                 
                                            
filled.forEach(value => console.log(value));
```


# 3 Пример деструктурирующего присваивания(ДП)?
```js
const arr = ["Alex", "Diana", "Elena"];

const [oneName, , threeName] = arr;

console.log(oneName); // "Alex"

console.log(threeName); // "Elena"
```


# 4 В каких случаях используется ДП?
1. Подмена переменных:
```js
let a = 1;

let b = 2;

[a, b] = [b, a];

console.log(a, b); // 2, 1
```
2. Обращение к элементу массива (если массив пуст и мы хотим получить значение по умолчанию):
```js
const colors = [];

const [firstColor = "white"] = colors;

console.log(firstColor); // "white"
```
3. Принцип неизменности - immutability (React). ДП в сочетании с оператором ... удаляет элементы из начала массива.
```js
const numbers = [1, 2, 3]; 

const [, ...fooNumbers] = numbers;

console.log(fooNumbers); // [ 2, 3 ]
```
4. ДП итерируемых объектов (строк, массивов):
```js
const str = "fruit";

const [firstChar, ...rest] = str;

console.log(firstChar); // f

console.log(rest); // [ 'r', 'u', 'i', 't' ]
```
5. ДП динамических свойств объекта:
```js
const movie = {
    title: "all"
};

const { title } = movie;

console.log(title); // "all"
```


# 5 Как присвоить значение по умолчанию?
* Если в массиве меньше значений, чем в присваивании, то ошибки не будет. 
* Отсутствующие значения считаются нeопределенными (undefined).
```js
let [name = "Dima", surname = "Sokolov"] = ["Alex"];

console.log(name); // Alex - из массива

console.log(surname); // Sokolov - значение по умолчанию
```


# 6 Как записываются остаточные параметры?
"Остаточные параметры" - троеточие ("...");
```js
const [name1, name2, ...rest] = ["Alex", "Pasha", "Nina", "Sergey"];

console.log(rest); // [ 'Nina', 'Sergey' ] - массив из оставшихся элементов.

const obj = {
    name: "Teya",
    age: 18,
    work: "IT"
};

const { name: NAME, age, work: branch, ...last } = obj;

console.log(name); // ReferenceError: name is not defined

console.log(NAME); // "Teya"

console.log(branch); // "IT"

console.log(last); // {} - нет оставшихся свойств у объекта
```


# 7 Что такое Date? Для чего используется?
* Date() - встроенный объект в JS.
* Он содержит дату и время, а также предоставляет методы управления ими. 
* Можно использовать для хранения времени создания / изменения, для измерения или просто для вывода текущей даты. 
* Счёт месяцев начинается с нуля.

# 8 Какие методы есть у Date?
```js
const date = new Date() // создать объект Date с текущими датой и временем

date.getFullYear() // получить год;

date.getMonth() // получить месяц (от 0 до 11);

date.getDate() // получить день месяца (от 1 до 31);

date.getHours() // получить часы;

date.getDay() // получить день недели (от 0 - воскресенье до 6 - суббота);

date.getTime() // для заданной даты возвращает timestamp - количество млсекунд прошедших с 1 января 1970 г. UTC+0
```

# 9 Что такое JSON?
1. [ ] JSON (JavaScript Object Notation) - общий формат для предоставления значений и объектов. 
2. [ ] JSON легко используется для обмена данными.

# 10 Метод JSON.stringify()? Когда используется?
* Используется для преобразования объектов в JSON. Получается строка, которая называется JSON - форматированным объектом. 
* Мы можем отправить его по сети или поместить в обычное хранилище данных. JSON.stringify() применим к примитивам (строки, числа, bool, null).


# 11 Метод JSON.parse()? Когда используется?
Используется, когда строку JSON трансформируют в объект JS
```js
const obj = {
    name: "Diana",
    age: 24
};

const json = JSON.stringify(obj);

console.log(json); // {"name":"Diana","age":24}

const newObj = JSON.parse(json);

console.log(newObj, obj === newObj); // { name: 'Diana', age: 24 } false
```


# 12 Для чего нужен прототип?
* Прототип нужен для того, чтобы наделить объект свойствами другого объекта. На основании прототипов создаются экземпляры объектов.

* Они могут иметь собственные методы и свойства, а также наследуют свойства и методы прототипов.


# 13 Что такое __proto__?
 __proto__ - свойство объекта Object.prototype, которое позволяет связать экземпляр с прототипом. 


# 14 Как присвоить прототип объекту?
Есть 3 способа:
1)  - устаревший способ
```js
const user = {   // экземпляр прототипа
    name: "Pavel"
};

const admin = {   // прототип
    isAdmin: true
};

user.__proto__ = admin; // связь экземпляра с прототипом

console.log(user.isAdmin); // true
```

2) 
```js
const student = {   // экземпляр прототипа
    name: "Pavel"
};

const administrator = {   // прототип
    isAdmin: true
};

Object.setPrototypeOf(student, administrator); // связь экземпляра с прототипом

console.log(student.isAdmin); // true
```

3) - на практике при помощи Object.create() наследование от объекта-прототипа происходит на этапе создания объекта-экземпляра.
```js
const person = {
    name: "Dima",
    age: 35,
    sayHello() {
        console.log("Hi");
    }
};

const man = Object.create(person); // создание экземпляра и его связь с прототипом

man.sayHello(); // "Hi"
```

# 15 Каким типом может быть значение __proto__?
Объектом либо null. Другие типы игнорируются. 


# 16 Как работает this для прототипов объекта?
Для прототипа, для объекта this - всегда объект перед точкой (у кого вызывал, тот и this).


# 17 Как задать прототип конструктору?
```js
const admin = {
    isAdmin: true,
    sayHi() {
        return this.name;
    }
};

function User(name) {
    this.name = name;
}

User.prototype = admin; // присвоение прототипа конструктору

const user = new User("Pavel");

console.log(user.sayHi()); // "Pavel" - в моменте вызова метода присваивается this (а this всегда объект перед точкой).
```


# 18 Встроенные прототипы у объектов?
Number, Boolean, String, BigInt, Symbol, Function, Array


# 19 Прототипы у примитивов. Пример
5 - Number.prototype(методы и свойства) - Object.prototype - null


# 20 Откуда у примитивов взялись методы и свойства?
* Когда мы хотим получить доступ к свойствам и методам у примитивов, то у них создается временный объект-обёртка с использованием встроенных конструкторов: Number.prototype, String.prototype, Boolean.prototype, 
который предоставляет методы и после исчезает. 
* Только у значений undefined и null нет объектов-обёрток.


# 21 Для чего try...catch?
* Конструкция try...catch позволяет обрабатывать ошибки во время исполнения кода. 
* Она позволяет запустить код и перехватить ошибки, которые могут в нём возникнуть. 


# 22 Что содержит объект ошибки?
Объект ошибки содержат следующие свойства:
1. [ ] message – понятное человеку сообщение;
2. [ ] name – строка с именем ошибки (имя конструктора ошибки);
3. [ ] stack – стек на момент ошибки.


# 23 Для чего используется объект ошибки?
Объект ошибки используется для предоставления информации об ошибке.


# 24 throw. Для чего?
Оператор throw генерирует ошибку. 
```js
const error = new Error("Ошибка");

console.log(error.name); // "Error"

console.log(error.message); // "Ошибка"
```

```js
try {
  throw Error("Eww!");     
} 
catch ({name, message, stack}) {
    console.log(stack); // Error: Eww! 
}
```


# 25 Блок finally. Для чего? Когда выполняется?
Выполняется в любом случае:
- после try, если ошибки не было, 
- после catch, если ошибки были.
- Finally используется тогда, когда начали что-то делать и хотят завершить вне зависимости от того, 
будет ошибка либо нет или чтобы выполнить некоторые обязательные действия после завершения соединения
с сервером. 
```js
let flSend = false;
try {
    if (!flSend) {
        flSend = true; // отправка запроса к серверу
    }
} catch (error) {
    console.log("Ошибка обработки запроса");
} finally {
    flSend = false;
}
```


# 26 В чём особенность .call()? Написать пример
```js
const obj = {
    name: "Diana"
}

function printName(a, b) {
    return this.name + a + b;
}

console.log(printName.call(obj, " loves", " coding")); // аргументы передаются через запятую
```

Метод .call() устанавливает контекст и вызывает функцию. 


# 27 В чём особенность .bind()? Написать пример
```js
const object = {
    name: "Diana"
}

 function printName(a, b) {
    return this.name + a + b;
}
         
const res = printName.bind(object);

console.log(res(" loves", " coding")); 
```
Метод .bind() просто устанавливает контекст и возвращает функцию, не вызывая её.

# 28 В чём особенность .apply()? Написать пример
```js
const objA = {
    name: "Diana"
}

function printName(a, b) {
     return this.name + a + b;
}

console.log(printName.apply(objA, [" loves", " coding"])); // аргументы передаются в массиве
```
Метод .apply() устанавливает контекст и вызывает функцию. 


# 29 Написать пример замыкания
```js
const func = a => {
   return function(b) {
       return a + b;
    };
};
                            
const result = func('Hello, ');

console.log(result('world!'));
```


# 30 Написать пример рекурсии 
```js
const fact = n => {
    if (n === 1) {
     return 1;
    } else {
     return n * fact(n - 1);
    }
};
                            
console.log(fact(7));
```


# 31 Написать пример каррирования 
```js
const sum = (a, b, c) => {
     return a + b + c;
};
                            
console.log(sum(2, 3, 4));
                                                    
const curry = fn => {
    return function (a) {
        return function (b) {
            return function (c) {
                return fn(a, b, c);
            };
         };
     };
};
                            
const curryed = curry(sum);

console.log(curryed(2)(3)(4));
```


