#  JavaScript Best Practice Guide
## 1. Избегайте глобальных переменных
- Глобальные переменные легко переписать в различных местах кода, потому что они везде доступны.
- Глобальные переменные могут переписывать объект window, так как являются свойствами объекта window.
``` js
// плохо
var name = 'Jeffrey';  
var lastName = 'Way';    
function doSomething() {...}    
console.log(name); // Jeffrey -- or window.name

// хорошо
var DudeNameSpace = {  
   name : 'Jeffrey',  
   lastName : 'Way',  
   doSomething : function() {...}  
}  
console.log(DudeNameSpace.name); // Jeffrey  
```
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
## 3. Объявляйте переменные снаружи от цикла For
- При выполнении длинных циклов «for» не создавайте дополнительной нагрузки на движок. 
``` js
// плохо
for(var i = 0; i < someArray.length; i++) {
    var container = document.getElementById('container');
    container.innerHtml += 'my number: ' + i;
    console.log(i);
 }
 
 // хорошо
 var container = document.getElementById('container');
 for(var i = 0, len = someArray.length; i < len;  i++) {
    container.innerHtml += 'my number: ' + i;
    console.log(i);
 }
 ```
