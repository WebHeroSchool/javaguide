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
