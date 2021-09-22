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
