# Desafío: javaScript

## Nombre de Desafío: diagrama_flujo

## Instrucciones

Determiná que será impreso en la consola, sin ejecutar el código.

> Investiga cuál es la diferencia entre declarar una variable con `var` y directamente asignarle un valor.

```javascript
x = 1;
var a = 5;
var b = 10;
var c = function (a, b, c) {
  var x = 10;
  console.log(x); // su valor seria 10 
  console.log(a); // su valor seria 8
  var f = function (a, b, c) {
    b = a;
    console.log(b); // su valor seria 8
    b = c;
    var x = 5;
  };
  f(a, b, c);
  console.log(b); //su valor seria 9
};
c(8, 9, 10);
console.log(b); //su valor seria 10
console.log(x); //su valor seria 1
```

```javascript
console.log(bar); //Undefined
console.log(baz); //Undefined
foo();
function foo() {
  console.log("Hola!"); // Imprime el String 'Hola', sin importar que llamemos la funcion encima de la function o debajo
}
var bar = 1;
baz = 2;
```

```javascript
var instructor = "Jhoswe";
if (true) {
  var instructor = "Jose"; 
}
console.log(instructor); //Nos imprime el String 'Jose' 
```

```javascript
var instructor = "Jhoswe";
console.log(instructor); //Nos imprime el String 'Jhoswe'
(function () {
  if (true) {
    var instructor = "Jose";
    console.log(instructor); //Imprime el String 'Jose'
  }
})();
console.log(instructor); // Imprime el String 'Jose'
```

```javascript
var instructor = "Jhoswe";
let pm = "Jose";
if (true) {
  var instructor = "The Flash";
  let pm = "Reverse Flash";
  console.log(instructor); //Imprime el String 'The Flash'
  console.log(pm); // Imprime el String 'Reverse Flash'
}
console.log(instructor); //Imprime el String 'The Flash'
console.log(pm); // Imprime el String 'Jose'
```

### Coerción de Datos

¿Cuál crees que será el resultado de la ejecución de estas operaciones?:

```javascript
6 / "3"  // 2 numero definido como string. 
"2" * "3" // 6 Operacion invalida, operando dos strings
4 + 5 + "px" // 9px Opera la suma de 4+5, pero el string se puede interpretar como concatenacion u operacion con string que es invalida
"$" + 4 + 5 // $9 Operarse como una suma y se puede interpretar como string o concatenacion 
"4" - 2 // 2 
"4px" - 2 // NaN
7 / 0 // Error, una division no puede divirse en 0
{}[0] // Array dentro de un objeto en posicion 0 o inicial
parseInt("09") // 9
5 && 2 // Es una comparacion de true y false, y en este caso es false, = 2 
2 && 5 // Es una comparacion de true y false, y en este caso es false, = 5 
5 || 0 // Operador OR, toma el primer valor como true, = 5
0 || 5 // Operador OR toma el valor true = 5
[3]+[3]-[10] //  33 - 10 = 23 
3>2>1 // true  
[] == ![] // false  
```

> Si te quedó alguna duda repasá con [este artículo](http://javascript.info/tutorial/object-conversion).

### Hoisting

¿Cuál es el output o salida en consola luego de ejecutar este código? Explicar por qué:

```javascript
function test() {
  console.log(a); // Nos arrojara un error Undefined, debido a que no hemos asignado valor a la variable a 
  console.log(foo()); // En este caso sin importar que llamemos a la funcion antes de definirla, nos arrojara el valor que le asignemos en este caso = 2

  var a = 1;
  function foo() {
    return 2; 
  }
}

test(); //No posee parametros para ejecutar su valor
```

Y el de este código? :

```javascript
var snack = "Meow Mix";

function getFood(food) {
  if (food) {
    var snack = "Friskies";
    return snack;
  }
  return snack;
}

getFood(false); // Me daria un undefined, debido a que es un condicional que no esta cumpliendo y no esta definidio 
```

### This

¿Cuál es el output o salida en consola luego de ejecutar esté código? Explicar por qué:

```javascript
var fullname = "Jhoswe Castro";
var obj = {
  fullname: "Jose Zuñiga",
  fullname: "Jorge Alonso",
  getFullname: function () {
    return this.fullname;
  },
};

console.log(obj.getFullname()); // Retornaria Jorge Alonso, debido a que el codigo se lee linea a linea.

var test = obj.getFullname;

console.log(test()); // No deberia arrojarnos un valor, debido a que la variable que estamos definiendo como test, no identifica de donde proviene su value
```

### Event loop

Considerando el siguiente código, ¿Cuál sería el orden en el que se muestra por consola? ¿Por qué?

```javascript
function printing() {
  console.log(1);
  setTimeout(function () {
    console.log(2);
  }, 1000);
  setTimeout(function () {
    console.log(3);
  }, 0);
  console.log(4);
}

printing(); // El orden de ejecucion en consola seria:  1, 4, 3 , 2
```