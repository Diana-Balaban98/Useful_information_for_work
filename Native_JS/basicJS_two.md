# 1 Что такое NaN?
 * NaN - специальное числовое значение, которое означает вычислительную ошибку. 
 * Это результат неправильной математической операции. Любая операция с NaN вернёт NaN.

Исключение:
``` js
console.log(NaN ** 0); //1

console.log(typeof NaN); // "number"
 ```

# 2 Что такое Infinity?
 * Infinity - математическая бесконечность, особое значение, которое больше любого числа.

``` js
console.log(1 / 0); // Infinity

console.log(typeof Infinity); // "number"

Infinity + Infinity; // Infinity

Infinity * Infinity; // Infinity

Infinity - Infinity; // NaN

Infinity / Infinity; // NaN

-Infinity + Infinity // NaN
 ```

# 3 Как работает parseInt?
 * Функция преобразует строку в целое число.
 * Преобразование произойдёт, если целое число стоит вначале строки, иначе будет NaN.

```js
let str = parseInt("10px"); // 10

str = parseInt("15.345"); // 15

str = parseInt("suu 16.3"); // NaN
```


# 4 Что такое Math?
Math - объект, который содержит различные математические функции и константы.


# 5 Для чего Math.max и Math.min?
Возвращает наибольшее и наименьшее число из перечисленных аргументов.
```js
const max = Math.max(13, -343, 10, 100, 2);
const min = Math.min(0, -1, 10, -17, 104);

console.log(max); // 100

console.log(min); // -17
```


# 6 Для чего Math.pow?
Возвращает число n (первый аргумент), возведённое в степень power (второй аргумент)
```js
const pow = Math.pow(5, 7); // тоже, что и 5 ** 7

console.log(pow); // 78125
```
                                

# 7 Как объявить BigInt?
Необходимо в конец числа добавить n или вызвать функцию BigInt.
```js
const bigNum = 10n; 

console.log(bigNum); // 10n

const bigN = BigInt("1716");

console.log(bigN); // 1716n
```


# 8 Какого типа данных null?
object


# 9 Когда можно встретить undefined?
1. При доступе к объявленным переменным без их инициализации:
```js
let a;

console.log(a);
```
2. При вызове функции без return:
```js
function abc(a, b) {
    let c = a + b;
}

console.log(abc(4, 7)); // undefined
```
3. При доступе к несуществующим свойствам объекта:
```js
const obj = {};

console.log(obj.name); // undefined
```
4. При доступе к несуществующим элементам массива:
```js
const array = [];

console.log(array[0]); // undefined
````
5. Оператор typeof возвращает строку undefined для неопределенного значения:
```js
console.log(typeof undefined); // "undefined"
```
6. Оператор void выполняет выражение и возвращает undefined вне зависимости от результата:
```js
console.log(void (16)); // undefined
````

# 10 Что такое объект и для чего он нужен?
Объект - тип данных в JS с помощью которого представляют список данных: ключ-значение.
Используется для хранения коллекций различных значений.
```js
const object = {
    name: "Diana" // name - ключ (строка); "Diana" - значение (строка)
};
```

# 11 Что может быть ключом / значением?
Свойство - пара "ключ - значение", где ключ (имя свойства) - строка или символ; значение - всё, что угодно (любые типы данных)


# 12 Как получить доступ к свойству объекта?
С помощью точечной записи (dot notation), либо с использованием квадратных скобок (bracket notation).
```js
let city = "city";

const person = {
    name: "Alex"
};

console.log(person.name);

console.log(person[city] = "Minsk");

console.log(person); // { name: 'Alex', city: 'Minsk' }
```
Квадратные скобки позволяют взять ключ из переменной:
```js
person[city] = "Minsk";

console.log(person); // { name: 'Alex', age: 24, city: 'Minsk' }
```


# 13 Как изменить значение свойства объекта?
```js
const myCity = {
    city: "Minsk"
}
```

1. используя точечную запись:
```js
myCity.city = "Las Vegas";
console.log(myCity); // { city: 'Las Vegas' }
```

2. используя квадратные скобки:
```js
myCity["city"] = "Vitebsk";
console.log(myCity); // { city: 'Vitebsk' }
```

# 14 В чём особенность хранения объектов?
При присваивании объекта переменной - переменная не хранит сам объект, а только ссылку на него.


# 15 В чём особенность константы и объекта?
1. [ ] Объект, объявленный через const может быть изменен. 
2. [ ] const защищает только переменную от изменения, но изменять содержимое объекта можно.
```js
const abc = {
    a: 1,
    b: 2,
    c: "3"
}

abc.c = 3;

console.log(abc); // { a: 1, b: 2, c: 3 }

abc = {};

console.log(abc); // TypeError: Assignment to constant variable
```


# 16 Как сравниваются объекты?

* Сравниваются по ссылке. 
* При этом при сравнении будут учитываться факты того, что 2 переменные ссылаются на один и тот же объект. 
* Даже если 2 объекта содержат идентичные значения (либо пустые объекты с разными ссылкaми), то они неравны.

```js
const data = {};

const anotherData = data; // переменная anotherData ссылается на объект с именем data

console.log(data === anotherData); // true

const cat = { name: "cat" }; // одна ссылка у объекта

const dog = { name: "cat" };  // другая ссылка у объекта

console.log(cat === dog); // false
```

# 17 Способы клонировать объект
 * Чтобы безопасно менять объекты их предварительно необходимо скопировать. 
 * Таким образом, будет создана другая ссылка, любые изменения не затронут старый объект.

1. НО ЕСЛИ У ОБЪЕКТА ЕСТЬ ВЛОЖЕННЫЙ ОБЪЕКТ, ТО ССЫЛКИ НА НИХ СОХРАНЯЮТСЯ!!!
```js
const person = {
    age: 25
};
const person2 = Object.assign({}, person);

person2.age = 26;

console.log(person); // { age: 25 }

console.log(person2); // { age: 26 }

console.log(person === person2); // false


const person = {
    age: 25
};

let clone = {};

const clone2 = Object.assign(clone, person); // ссылка на объект clone

console.log(clone, clone2, person);

console.log(person === clone);

console.log(clone2 === person);

console.log(clone2 === clone);
```

2. НО ЕСЛИ У ОБЪЕКТА ЕСТЬ ВЛОЖЕННЫЙ ОБЪЕКТ, ТО ССЫЛКИ НА НИХ СОХРАНЯЮТСЯ!!!
```js
const car = {
    color: "black"
};

const car2 = {...car}; // {...obj} - spread-оператор раздедения объекта на свойства

car2["color"] = "red";

console.log(car); // { color: 'black' }

console.log(car2); // { color: 'red' }

console.log(car === car2); // false
```

3. ССЫЛКИ НА ВЛОЖЕННЫЕ ОБЪЕКТЫ НЕ СОХРАНЯЮТСЯ :)
```js
const mobile = {
    model: "xs",
    size: {
        a: 760
    }
};

const mobile2 = JSON.parse(JSON.stringify(mobile));

mobile2.size.a = 780;

console.log(mobile); // { model: 'xs', size: { a: 760 } }

console.log(mobile2); // { model: 'xs', size: { a: 780 } }

console.log(mobile === mobile2); // false
```

4. НО ЕСЛИ У ОБЪЕКТА ЕСТЬ ВЛОЖЕННЫЙ ОБЪЕКТ, ТО ССЫЛКИ НА НИХ СОХРАНЯЮТСЯ!!!
```js
const user = {
    name: "Huan",
    c: {
    a: 13
    }
};

let clone = {};

for (let key in user) {
    clone[key] = user[key]; // копируем все свойства user в пустой объект clone
}

clone.name = "Alice";

clone.c.a = 15;

console.log(user); // { name: 'Huan', c: { a: 15 } }

console.log(clone); // { name: 'Alice', c: { a: 15 } }

console.log(user === clone); // false
```

# 18 Для чего Object.assign?
1. Функция Object.assign получает список объектов и копирует в первый target свойства из остальных.
2. При этом последующие свойства перезаписывают предыдущие.
3. Также используется для клонирования объекта.
4. Object.assign(target, src1, src2...) - синтаксис для копирования свойств одного объекта в другой: 
```js
const user = {
    name: "Diana"
};

const admin = {
    isMan: false
};

Object.assign(user, admin);

console.log(user === admin); // false

console.log(user); // { name: 'Diana', isMan: false }
```

для клонирования объекта:
```js
const user = {
    name: "Вася",
    isAdmin: true
};

const user2 = Object.assign({}, user); // новый независимый объект

console.log(user2); // { name: 'Вася', isAdmin: true }
```

# 19 Object.keys. Для чего? Что возвращает?
1. [ ] Для получения ключей объекта. 
2. [ ] Метод возвращает массив собственных счётных ключей объекта.
```js
const object = {
    a: 12,
    b: "oops",
    c: true
};

console.log(Object.keys(object)); // [ 'a', 'b', 'c' ]
```


# 20 Object.values. Для чего? Что возвращает?
1. [ ] Для получения значений свойств объекта. 
2. [ ] Метод возвращает массив собственных счётных значений свойств объекта. 
```js   
const object = {
    a: 12,
    b: "oops",
    c: true
};

console.log(Object.values(object)); // [ 12, 'oops', true ]
```


# 21 Object.entries. Для чего? Что возвращает?
1. [ ] Для получения пар [ключ-значение] объекта. 
2. [ ] Метод возвращает многомерный массив пар [ключ-значение].
```js
const object = {
    a: 12,
    b: "oops",
    c: true
};

console.log(Object.entries(object)); // [ [ 'a', 12 ], [ 'b', 'oops' ], [ 'c', true ] ]
```


# 22 Что такое метод объекта? Способы создания метода
Метод объекта - функция, которая является свойством объекта.

1. 
```js
const user = {
    name: "Sasha"
};

user.sayHi = function() {
        console.log("Hello");
};

user.sayHi(); // "Hello"
```

2.
```js
const user = {};

function sayHi() { // объявляем функцию
    console.log("Hi");
}

user.sayHi = sayHi; // добавляем в качестве метода

user.sayHi(); // "Hi"

console.log(user);
```

3. 
```js
const user = {
    name: "Diana",
    sayHi: function() { 
        console.log(`Hey, ${this.name}`);
    }
};

user.sayHi(); // "Hey"

const user = {
    sayHi() {
        console.log("Привет");
    }
};

user.sayHi(); // "Привет"
```

# 23 Для чего нужны методы?
1. [ ] Методы позволяют объектам "действовать": object.doSome()

# 24 Для чего и как работает this в методах объекта?
1. [ ] this нужен для доступа к информации внутри объекта. Значение this - объект "перед точкой", который используется для вызова метода - методы ссылаются на объект через this.
2. [ ] this не является фиксированным (его можно использовать в любой функции, даже если это не метод объекта)


# 25 Для чего delete у объектов?
1. [ ] Оператор delete удаляет свойства объекта.
2. [ ] После удаления это свойство будет иметь значение undefined.
```js
const obj = {
    name: "Alex"
};

delete obj.name;
console.log(obj.name); // undefined
```


# 26 Для чего нужен конструктор объектов?
1. [ ] Для создания множества однотипных объектов.
2. [ ] Помогает оптимизировать работу, чтобы не создавать много отдельных объектов. 


# 27 - 2 правила для создания конструктора
Функция-конструктор пишется с большой буквы и вызывается с помощью ключевого слова "new".
```js
function User {

};

let user = new User() {

}
```

# 28 Как работает return в конструкторе объектов?
1. [ ] По умолчанию функция-конструктор возвращает this. 
2. [ ] Правило: функция-конструктор возвращает либо объект {}, либо this.


# 29 Как создать строку?
Записать выражение в кавычки:
```js
console.log("World");
```
Использовать функцию String():
```js
console.log(new String(5)); // "5"
```
Использовать JSON.stringify() - преобразует объекты в строки:
```js
const obj = {
    name: "Alex"
};

console.log(JSON.stringify(obj)); // {"name":"Alex"}
```


# 30 Какие виды кавычек вы знаете?
```js
console.log('world'); // одинарные

console.log("world"); // двойные

console.log(`world`); // обратные 
```


# 31 В чем особенность обратных кавычек?
Строки в таких кавычках могут быть многострочными, все переносы сохраняются.
```js
console.log(`я очень длинная строка 
и
переношусь`);
```
В шаблонной строке с помощью синтаксиса ${} можно использовать любые выражения.
```js
console.log(`результат сложения 2 и 3 это ${2 + 3} `);
```


# 32 Как вычислить длину строки?
Свойство length содержит длину строки.
```js
console.log("world".length); // 5

let b = "Hello";

console.log(b.length); // 5
```


# 33 Как достучаться к символу в строке?
c помощью квадратных скобок []. Если символ отсутствует - вернёт undefined:
```js
console.log("world"[0]); // "w"
```
используя метод charAt(). Если символ отсутствует - вернёт "" (пустую строку):
```js
console.log("world".charAt(1)); // "o"
```
с помощью for..of:
```js
for (char of "world") {
    
    console.log(char);
    
} // "w", "o", "r", "l", "d"
```


# 34 Для чего toLowerCase() / toUpperCase()?
1. [ ] Эти методы меняют регистр символов.
```js
console.log("WoRld".toLowerCase()); // world

console.log("wOrLd".toUpperCase()); // WORLD
```


# 35 indexOf() Для чего? Какие параметры? Что возвращает?
1. [ ] Для поиска подстроки.
2. [ ] Ищет подстроку в строке начиная с 0
3. [ ] Возвращает позицию на которой располагается совпадение, либо -1 при отсутствии совпадений.
```js
console.log("i love you".indexOf("love")); // 2

console.log("i love you".indexOf("o", 5)); // 8
```


# 36 includes() Для чего? Какие параметры? Что возвращает?
1. [ ] Проверить на наличие подстроки в строке.
2. [ ] Возвращает true, если в строке есть подстрока, либо false, если нет.
3. [ ] Аргумент позволяет выбирать с какой позиции начать проверку.
```js
console.log("i love you".includes("Love")); // false

console.log("i love you".includes("o", 2)); // true
```


# 37 slice() Для чего? Какие параметры? Что возвращает?
1. [ ] Для извлечения части строки.
2. [ ] Может принимать отрицательные индексы.
3. [ ] Метод принимает 2 параметра (нач. позиция, конечная позиция, не включая конец)
4. [ ] Возвращает извлеченную часть в новой строке.
```js
let a = "I love you".slice(1,);

console.log(a); // "love you"
```


# 38 substring() Для чего? Какие параметры? Что возвращает?
1. [ ] Для извлечения части строки.
2. [ ] Не может принимать отрицательные индексы.
3. [ ] Метод принимает 2 параметра(нач. позиция, конечная позиция), если не указан 2 параметр, оставшаяся часть строки будет вырезана.
5. [ ] Возвращает извлеченную часть в новой строке.
```js
let b = "I love you".substring(1, 6);

console.log(b); // "love"
```


# 39 substr() Для чего? Какие параметры? Что возвращает?
1. [ ] Для извлечения части строки.
2. [ ] Метод похож на slice()
3. [ ] Метод принимает 2 параметра (нач. позиция, длина извлеченной части), если опустить 2 параметр, оставшаяся часть строки будет вырезана.
4. [ ] Возвращает извлеченную часть в новой строке.
```js
let c = "I love you".substr(1, 5);

console.log(c); // "love"
```


# 40 trim() Для чего? Какие параметры? Что возвращает?
1. [ ] Удаляет пробельные символы с обеих сторон строки. 
2. [ ] Параметров не имеет.
3. [ ] Возвращает cтроку с удаленными пробелами.
```js
let str = "    world   ";

console.log(str.trim()); // world
```


# 41 repeat() Для чего? Какие параметры? Что возвращает?
1. [ ] Для повторения строк n раз. Один параметр - количество повторяемых строк.
2. [ ] Возвращает строку n раз, переданных в параметр.
```js
let str = "world ";

console.log(str.repeat(3)); // world world world
```


# 42 Как сравниваются строки?
Сравниваются посимвольно: строчные буквы больше заглавных:
```js
console.log("a" > "A"); // true
```
Буквы, имеющие диакретические знаки идут "не по порядку":
```js
console.log("škola" < "skola"); // false
```


