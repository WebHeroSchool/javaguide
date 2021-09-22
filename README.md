# JavaScript Style Guide
## 1. Объявление переменных
- Используйте const для объявления переменных; избегайте var.
``` js
// плохо
var a = 1;
var b = 2;

// хорошо
const a = 1;
const b = 2;
```
- Если вам необходимо переопределять значения, то используйте let вместо var.
``` js
// плохо
var count = 1;
if (true) {
  count += 1;
}

// хорошо, используйте let.
let count = 1;
if (true) {
  count += 1;
}
```
## 2. Объекты
- Для создания объекта используйте литеральную нотацию.
``` js
// плохо
const item = new Object();

// хорошо
const item = {};
```
- Не вызывайте напрямую методы Object.prototype, такие как hasOwnProperty, propertyIsEnumerable, и isPrototypeOf.
``` js
// плохо
console.log(object.hasOwnProperty(key));

// хорошо
console.log(Object.prototype.hasOwnProperty.call(object, key));
```
## 3. Массивы
- Для создания массива используйте литеральную нотацию.
``` js
// плохо
const items = new Array();

// хорошо
const items = [];
```
- Для добавления элемента в массив используйте #push вместо прямого присваивания.
``` js
const someStack = [];

// плохо
someStack[someStack.length] = 'abracadabra';

// хорошо
someStack.push('abracadabra');
```
## 4. Деструктуризация
-  При обращении к нескольким свойствам объекта используйте деструктуризацию объекта. 
``` js
// плохо
function getFullName(user) {
  const firstName = user.firstName;
  const lastName = user.lastName;

  return `${firstName} ${lastName}`;
}

// хорошо
function getFullName(user) {
  const { firstName, lastName } = user;
  return `${firstName} ${lastName}`;
}
```
- Используйте деструктуризацию массивов.
``` js
const arr = [1, 2, 3, 4];

// плохо
const first = arr[0];
const second = arr[1];

// хорошо
const [first, second] = arr;
```
## 5. Строки
- Используйте одинарные кавычки '' для строк. 
``` js
// плохо
const name = "Capt. Janeway";

// плохо 
const name = `Capt. Janeway`;

// хорошо
const name = 'Capt. Janeway';
```
- При создании строки программным путём используйте шаблонные строки вместо конкатенации. 
``` js
// плохо
function sayHi(name) {
  return 'How are you, ' + name + '?';
}

// плохо
function sayHi(name) {
  return ['How are you, ', name, '?'].join();
}

// плохо
function sayHi(name) {
  return `How are you, ${ name }?`;
}

// хорошо
function sayHi(name) {
  return `How are you, ${name}?`;
}
```
## 6. Функции
- Используйте функциональные выражения вместо объявлений функций.
``` js
// плохо
function foo() {
  // ...
}

// плохо
const foo = function () {
  // ...
};

// хорошо
// лексическое имя, отличное от вызываемой(-ых) переменной(-ых)
const foo = function uniqueMoreDescriptiveLexicalFoo() {
  // ...
};
```
-  Оборачивайте в скобки немедленно вызываемые функции.
``` js
// Немедленно вызываемая функция
(function () {
  console.log('Welcome to the Internet. Please follow me.');
}());
```
## 7. Стрелочные функции
-   Когда вам необходимо использовать анонимную функцию (например, при передаче встроенной функции обратного вызова), используйте стрелочную функцию/
``` js
// плохо
[1, 2, 3].map(function (x) {
  const y = x + 1;
  return x * y;
});

// хорошо
[1, 2, 3].map((x) => {
  const y = x + 1;
  return x * y;
});
```
- Если выражение располагается на нескольких строках, то необходимо обернуть его в скобки для лучшей читаемости.
``` js
// плохо
['get', 'post', 'put'].map((httpMethod) => Object.prototype.hasOwnProperty.call(
    httpMagicObjectWithAVeryLongName,
    httpMethod,
  )
);

// хорошо
['get', 'post', 'put'].map((httpMethod) => (
  Object.prototype.hasOwnProperty.call(
    httpMagicObjectWithAVeryLongName,
    httpMethod,
  )
));
```
## 8. Классы и конструкторы
- Всегда используйте class. Избегайте прямых манипуляций с prototype.
``` js
// плохо
function Queue(contents = []) {
  this.queue = [...contents];
}
Queue.prototype.pop = function () {
  const value = this.queue[0];
  this.queue.splice(0, 1);
  return value;
};

// хорошо
class Queue {
  constructor(contents = []) {
    this.queue = [...contents];
  }
  pop() {
    const value = this.queue[0];
    this.queue.splice(0, 1);
    return value;
  }
}
```
- Избегайте дублирующих членов класса.
``` js
// плохо
class Foo {
  bar() { return 1; }
  bar() { return 2; }
}

// хорошо
class Foo {
  bar() { return 1; }
}

// хорошо
class Foo {
  bar() { return 2; }
}
```
## 9. Модули
- Всегда используйте модули (import/export) вместо нестандартных модульных систем. Вы всегда сможете транспилировать код в вашу любимую модульную систему.
``` js
// плохо
const AirbnbStyleGuide = require('./AirbnbStyleGuide');
module.exports = AirbnbStyleGuide.es6;

// хорошо
import AirbnbStyleGuide from './AirbnbStyleGuide';
export default AirbnbStyleGuide.es6;

// отлично
import { es6 } from './AirbnbStyleGuide';
export default es6;
```
-  Не используйте импорт через *.
``` js
// плохо
import * as AirbnbStyleGuide from './AirbnbStyleGuide';

// хорошо
import AirbnbStyleGuide from './AirbnbStyleGuide';
```
## 10. Свойства
- Используйте точечную нотацию для доступа к свойствам.
``` js
const luke = {
  jedi: true,
  age: 28,
};

// плохо
const isJedi = luke['jedi'];

// хорошо
const isJedi = luke.jedi;
```
- Используйте скобочную нотацию [], когда название свойства хранится в переменной.
``` js
const luke = {
  jedi: true,
  age: 28,
};

function getProp(prop) {
  return luke[prop];
}

const isJedi = getProp('jedi');
```
