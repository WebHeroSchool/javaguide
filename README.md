#  JavaScript Best Practice Guide
## 2. Используйте === вместо ==
- В JavaScript используются два вида операторов равенства: === | !== и == | != . Рекомендуется всегда использовать первый набор при сравнении, потому что он предотвращает ошибки приведения типов
``` js
// плохо
a == b 
foo == true
bananas != 1
value == undefined

// хорошо
typeof foo === 'undefined'
'hello' !== 'world'
0 === 0
true === true
foo === null
```
