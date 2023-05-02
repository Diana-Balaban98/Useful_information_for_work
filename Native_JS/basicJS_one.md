# 1 Переменные

```js
    var digit;
    console.log(digit); // undefined
    let variable;
    console.log(variable); // undefined
    const PI = 3.14;
    console.log(PI); // 3.14
```


# 2 Отличия var oт let и const и let

                                                             VAR:
```js
var a;
var a = 5;
var a = 10; // можно повторно объявлять одну и ту же переменную
a = 'diana';
console.log(a); // 'diana'
```

Переменная hello ограничена функцией:

```js
function newFunction() {
    var hello = "hello";
    console.log(hello); // "hello"
}
console.log(hello); // hello is not defined
```

Для var не существует блочной области видимости: 

```js
for (var i = 0; i < 10; i++) {
    var d = true;
}
console.log(d); // true
```

Hoisting (поднятие) - можно выводить в консоль до объявления переменной:

```js
console.log(num); // undefined 
var num = 10;
var button;
console.log(button); // undefined
```

                                                        LET:
```js
let b;
let b = "string";
let b = 15; // нельзя повторно объявлять одну и ту же переменную
console.log(b); // SyntaxError: Identifier 'b' has already been declared
```

Имеет блочную область видимости:

```js
if (true) {
    let a = "okey";
    console.log(a);
}
console.log(a); // ReferenceError: a is not defined
```

Переменные с одним именем в глобальной и локальной области видимости:

```js
let c = 5;
if (1) {
    let c = "true";
    console.log(c); // 'true'
}
console.log(c); // 5
```

Hoisting (всплытие):

```js
console.log(hello); //ReferenceError: Cannot access 'hello' before initialization
let hello = "hi";
```

                                                        CONST:
```js
const a; 
console.log(a); // SyntaxError: Missing initializer in const declaration

const birthday = "24.02.1998";
console.log(birthday); // "24.02.1998"
```

Имеет блочную область видимости:

```js
do {
    const run = 5;
    console.log(run); // 5
} while (2 > 3);

console.log(run); // ReferenceError: run is not defined
```

Нельзя объявить или обновить заново:

```js
const access = 7;
const access;
console.log(access); //Identifier 'access' has already been declared
```

Объект не может быть обновлён, но свойства этого объекта можно обновлять:

```js
const object = {
    a: 6,
    b: 10
};

object.c = "new";
console.log(object); // { a: 6, b: 10, c: 'new' }

object = 10;
console.log(object); //TypeError: Assignment to constant variable
```

Hoisting (всплытие):

```js
console.log(hello); //ReferenceError: Cannot access 'hello' before initialization
const hello = "hi";
```


# 3 Hoisting

Hoisting (поднятие) — это механизм в JavaScript, в котором переменные (var) и объявления функций (function dtclaration), передвигаются вверх своей области видимости перед тем, как 
код будет выполнен.

1.
```js
console.log(ann); // undefined
var ann = 'Anna';
```

2.
```js
console.log(getAnswer(5, 7));

function getAnswer (a, b) {
    c = a + b;
    return c;
}
```

# 4 Типы данных (8 типов, из них: 7 - примитивы; объект - ссылочный тип)

```js
let number = 17; //"number"
let string = "hello"; // "string"
let bool = true; // "boolean"
let nothing = null; // null - typof null - "object"
let und; //" undefined"
let bigi = 123n; // "bigint"
let o = {}; // "object"
let symb = Symbol(); // "symbol"
```


# 5 Как узнать какого типа переменная?

C помощью оператора typeof:
```js
let numeric = 100;
console.log(typeof numeric); // "number"
```

# 6 Что и в каком виде возвращает typeof?

Результатом typeof является строка, содержащая тип:
``` js
typeof 0 // "number"

typeof 1n // "bigint"

typeof true // "boolean"

typeof "foo" // "string"

typeof Symbol() // "symbol"

typeof {} // "object"

typeof undefined // "undefined"

typeof () => {} // function

typeof null // object  -  ошибка в JavaScript
 ```


# 7 Какие унарные операторы вы знаете?
```js
let a = 6;

console.log(a++); // инкремент   6

console.log(++a); // инкремент   8

console.log(a--); // декремент   8

console.log(--a); // декремент   6

let b = "6";

console.log(+b); // явное преобразование строки в число 6

console.log(typeof +b); // "number"

console.log(-b); // явное преобразование строки в отрицательное число -6

myFunction(); // вызов функции ()

new Object(); // создание функции-конструктора 

delete object; // удаление свойств объекта
```


# 8 Какие бинарные операторы вы знаете?
```js
a = 5; // присваивание

console.log(5 + 7); // сложение

console.log(5 - 8); //  вычитание

console.log(6 * 2); //  умножение

console.log(4 / 2); //  деление

console.log(1 > 5); // больше

console.log(2 < 10); //  меньше

console.log(2 >= 2); //  больше-равно

console.log(7 <= 5); //  меньше=равно

console.log(2 === "2"); // строгое равно

console.log(2 == 2); //  равно

console.log(1 != 1); //  неравно

console.log(1 !== 1); // строгое неравно

console.log(2 ** 3); //  возведение в степень

console.log(2 % 2);  // остаток от деления

console.log(2 && 2); //  логическое "и"

console.log(2 || 2); // логическое "или"     
```


# 9 Тернарный оператор
```js
let result = (5 === 5) ? "Yes" : "No";

console.log(result);
```



# 10 Почему операторы называются унарными, бинарными, тернарный?
1. [ ] Унарный, т.к один операнд
2. [ ] Бинарный (2 операнда)
3. [ ] Тернарный (3 операнда)



# 11 Какие операторы сравнения вы знаете? 
```js
console.log(1 > 5); // больше

console.log(2 < 10); // меньше

console.log(2 >= 2); // больше-равно

console.log(7 <= 5); // меньше-равно

console.log(2 === "2"); // строгое равно

console.log(2 == 2); // равно

console.log(1 != 1); // неравно

console.log(1 !== 1); // строгое неравно
```


# 12 Что возвращают операторы сравнения?
Все операторы сравнения возвращают boolean (true или false)


# 13 Какая разница между == и ===?
1. == (равно) при сравнении разных типов неявно преобразует тип и затем сравнивает
2. === (строгое равно) производит сравнение не преобразуя тип 


# 14 Как работает if else ?
```js
let newYear = 2023; 

if (newYear === 1998) { // если в условии true, выполнится блок кода в if, иначе выполнится код в блоке else 
    console.log("Yes");
} else {
    console.log("No");
}
```


# 15 Какие логические операторы вы знаете?
1. [ ] && и;
2. [ ] || или;
3. [ ] ! не;


# В чём особенность каждого логического оператора?

1. [ ] || находит первое истинное значение (если все значения ложные, возвращает последний)
2. [ ] && находит первое ложное значение (если все значения истинные, возвращает последний)
3. [ ] ! принимает один аргумент, приводит к true/false, затем возвращает противоположное значение


# 17 Для чего нужны циклы?
Циклы нужны для многократного повторения какого-либо действия


# 18 Какие циклы вы знаете?

1. while
```js
let i = 5;
while (i) {
    console.log(--i)
};
```

2. do while

```js
let s = 6;

do {
    console.log('hello ' + (--s));
} while(s === 0);
```

3. for 
```js
const animals = ["cow", "cat", "dog"];

for (let i = 0; i < animals.length; i++) {
    console.log(animals[i]);
}
```

4. for in
```js
const animals = ["cow", "cat", "dog"];

for (add in animals) {
    console.log(add);
}
```

5. for of
```js
const animals = ["cow", "cat", "dog"];

for (add of animals) {
    console.log(add);
}
```

# 19 В чём особенность каждого цикла?
 * Цикл while - тело цикла выполняется, пока условие истинно
 * Do while - выполняется хотя бы один раз, даже если условие ложно, условие записывается после тела цикла
 * Цикл for самый распространенный (в нем есть начало цикла, условие и шаг)
 * Цикл for of - для перебора массивов (объект - неитерируемый элемент в JS)
 * Цикл for in - для перебора свойств объектов


# 20 Как называются блоки у цикла for?
 * начало let i = 0; выполняется один раз при входе в цикл
 * условие i < 3; проверяется перед каждой итерацией цикла, если условие ложное, цикл остановится
 * тело цикла alert(i); выполняется снова и снова, пока условие true
 * шаг i++ - выполняется после тела цикла на каждой итерации перед проверкой условия


# 21 Для чего нужен switch?
 * Инструкция switch была придумана в качестве альтернативы для нескольких if. 
 * Обычно используется. когда нужно сравнить некоторое значение сразу с несколькими вариантами
(другими значениями) и выполняется соответствующий фрагмент кода из предложенных вариантов. 


# 22 Перечислите и расскажите про каждое ключевое слово в switch?
 * switch (выражение)
 * case (выражение с которым сравнивается главное выражение switch)
 * break (выход из switch)
 * default (выполнится этот дефолтный кейс, если из case не совпало с выражением switch)


# 23 Для чего нужны функции?
 * Функции позволяют повторно использовать код: однажды определив некий блок кода, затем 
можно использовать сколько угодно раз из любого места скрипта.
 * Также используется много раз с разными аргументами, чтобы получить разные результаты.


# 24 Перечислите способы объявления функции

1. ### _function declaration_ - cоздается до начала выполнения скрипта, можно вызвать перед объявлением
``` js
function abc() {
    // тело функции
 }
 ```

2. ### _function expression_ - создается, когда доходит поток кода, вызывается после объявления
``` js
const fO = function() {
     // тело функции
 }
 ```

3. ### _arrow function_ - не имеет своего контекста this
```js   
const array = () => {
   // тело функции
}
```

# 25 Как вызвать функцию?
1. abc();
2. fO();
3. array();

# 26 Как передать параметры в функцию?
 * Строки, числа, логические значения передаются в функцию по значению. 
 * Иными словами при передаче значения в функцию, эта функция получает копию данного значения.
 * Передаются параметры в функцию()


# 27 Что можно передавать в качестве параметра?
Всё, что касается типов данных и целых выражений


# 28 Как присвоить начальное значение, если его не передали?       
```js
function abc(a = 5, b = 10) { // через оператор присваивания, если параметр не задан по умолчанию, то значением будет undefined
    return a + b
}

console.log(abc());
```

# 29 Как вернуть какое-либо значение из функции?
С помощью return
