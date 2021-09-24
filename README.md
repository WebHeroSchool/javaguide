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
## 4. Объявляйте переменные в начале кода
- Хорошая практика объявлять все переменные в начале каждого скрипта или функции. Это дает:
1. Чистый код;
2. Предоставляет единое место для поиска локальных переменных;
3. Уменьшает вероятность повторного объявления переменных;
4. Помогает избегать объявления нежелательных (подразумеваемых) глобальных переменных;
``` js
// Объявление переменных в начале
const firstName, lastName, price, discount, fullPrice;

// Использование после
firstName = "John";
lastName = "Doe";

price = 19.90;
discount = 0.10;

fullPrice = price - discount;
 ```
## 5. Всегда используйте точки с запятой (;)
- Это очень плохая практика, в результате использования которой потенциально могут возникнуть гораздо более крупные и тяжелые для обнаружения проблемы.
``` js
// плохо
var someItem = 'some string'
 function doSomething() {
   return 'something'
 }
 
 // хорошо
 var someItem = 'some string';
 function doSomething() {
   return 'something';
 }
  ```
## 6. Не используйте New Object()
- Используйте {} вместо new Object();
- Используйте '' вместо new String();
- Используйте 0 вместо new Number();
- Используйте false вместо new Boolean();
- Используйте [] вместо new Array();
- Используйте /()/ вместо new RegExp();
- Используйте function (){} вместо new Function();
``` js
let x1 = "";             // new primitive string
let x2 = 0;              // new primitive number
let x3 = false;          // new primitive boolean
const x4 = {};           // new object
const x5 = [];           // new array object
const x6 = /()/;         // new regexp object
const x7 = function(){}; // new function object
```
## 7. Функции-выражения немедленного вызова
- Вместо того, чтобы вызывать функцию, можно довольно просто сделать так, чтобы она вызывалась автоматически при загрузке страницы или после вызова родительской функции. Просто оберните вашу функцию в круглые скобки и затем добавьте дополнительную пару, благодаря которой собственно функция и вызывается.
``` js
(function doSomething() {
    return {
       name: 'jeff',
       lastName: 'way'
    };
 })();
 ```
## 8. Не передавайте строку в "SetInterval" или "SetTimeOut"
- Данный код не только неэффективен, но и ведет себя таким же образом, как и вела бы себя функция "eval". Никогда не передавайте строку в "SetInterval" или "SetTimeOut". Вместо этого передавайте имя функции.
``` js
// плохо
setInterval(
 "document.getElementById('container').innerHTML += 'My new number: ' + i", 3000
 );
 
 // хорошо
 setInterval(someFunction, 3000);
```
## 9. Не используйте Eval 
- Функция «eval» дает нам доступ к компилятору JavaScript. Т.е. мы можем выполнить команду записанную в строковой переменной, которую передадим в качестве параметра в eval. Это не только замедлит вашу программу, но еще и предполагает возниковение огромной дыры безопасности вашего приложения. Это плохо. По возможности избегайте этого.
``` js
// плохо
console.log(eval('2 + 2'));

// хорошо
console.log(2 + 2);
```
## 10. Размещайте скрипт в конце страницы
- Помните, что главная цель – сделать загрузку страницы максимально быстрой для пользователя. При загрузке скрипта браузер не может продолжить (* начать выполнение кода), пока не загружен весь файл. Поэтому пользователь должен будет ждать дольше, чтобы заметить какой-либо прогресс (* если скрипт размещается не в конце файла).
- Если у вас имеются файлы JS, единственная цель которых – добавление какой-то функциональной возможности (например, после нажатия кнопки), то вперед, разместите эти файлы внизу, сразу перед закрывающим тегом body. Это безусловно относится к устоявшейся практике.
``` js
<p>And now you know my favorite kinds of corn. </p>
 <script type="text/javascript" src="path/to/file.js"></script>
 <script type="text/javascript" src="path/to/anotherFile.js"></script>
 </body>
 </html>
```
