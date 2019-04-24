# Conceptos Sobre Javascript

¿Que es un Closure?
Un closure o clausura es la combinación de una función y el ámbito léxico en el que se declaró dicha función. Es decir los closures o clausuras son funciones que manejan variables independientes. En otras palabras, la función definida en el closure "recuerda" el ámbito en el que se ha creado.

> Ejemplo de Closure

```
function inicia() {
  var nombre = "Mozilla"; // 'nombre' es una variable local creada por la función 'inicia'
  function muestraNombre() { // 'muestraNombre' es una función interna (un closure)
    alert(nombre); // dentro de esta función usamos una variable declarada en la función padre
  }
  muestraNombre();
}
inicia();  

```

¿Cuales son los modos que podes usar en javascript?
Javascript tiene dos modos para poder programar, el mas conocido usado es el "sloppy mode" (modo poco riguroso) y el stric mode (Modo estricto).
El modo estricto cambia la sintaxis y el comportamiento en tiempo de ejecución. Los cambios generalmente caen dentro de estas categorías: cambios que convierten erratas en errores (como errores de sintaxis o en tiempo de ejecución), cambios que simplifican como una variable particular es calculada, cambios que simplifian el uso de eval y arguments, cambios que hacen más fácil escribir JavaScript "seguro", y cambios que anticipan la evolución futura de EMACScript.

> Para usar el modo estricto en javascript es importante que uses "use strict";

```
// Whole-script strict mode syntax
"use strict";
var v = "Hola! Soy un modo estricto para script!";

```
ECMAScript 2015 introdujo módulos y por tanto una tercera manera de entrar en el modo estricto. Todo el contenido de los módulos de JavaScript se encuentra automáticamente en modo estricto, sin necesidad de una declaración para iniciarlo.

```
function strict() {
    // porque este es un módulo, soy estricto de forma predeterminada
}
export default strict;
```

¿Que es el event loop?
El event loop o bucle de eventos es el encargado de mandar a la cola (stack queue) cuando hay una llamada de webApis para poder procesar de manera asincrona los diferentes eventos y que no sea bloqueante, de esta manera javascript es asincrónico y no bloqueante. Esto es gracias al Event Loop.

¿Que son las web Apis?
Javascript (del lado del cliente en particular) tiene muchas APIs disponibles, estas no son parte del lenguaje Javascript en sí, más bien están construidas sobre Javascript.
Algo interesante acerca de javascript, o mejor dicho de los runtimes de javascript, es que no cuentan nativamente con cosas como setTimeout, DOM, o HTTP request. Estas son llamadas web apis, que el mismo navegador provee, pero no están dentro del runtime JS.

```
// El IIFE (Immediately-Invoked Function Expression) al ejecutarse añade el primer frame al stack de llamada
(() => {
  // Añade un frame al stack de llamada
  console.log('1. Hola');

  // WebApi: Agrega un mensaje a la cola
  setTimeout(() => {
    console.log('2. Mundo');
  });

  // WebApi: Agrega otro mensaje a la cola
  setTimeout(() => {
    console.log('3. A todos');
  }, 0);

  // Añade un frame al stack de llamada
  console.log('4. Este es un mensaje extra');

  // Añade un frame al stack de llamada
  console.log('5. ¿Acertaste el orden de la salida?');

})();

// La consola imprime:
// 1. Hola
// 4. Este es un mensaje extra
// 5. ¿Acertaste el orden de la salida?
// 2. Mundo
// 3. A todos

```

> Terminos  de Javascript
Heap
Los objetos son asignados en un heap el cual sólo es un nombre para denotar una larga y no estructurada región de memoria.

Queue
Un entorno de ejecución Javascript contiene una cola de mensajes (messages queue), el cual es una lista de mensajes a ser procesados.

Una función está asociada a cada mensaje. Cuando el stack tiene suficiente capacidad, un mensaje es tomado del queue y procesado.

El procesamiento consiste en llamar a la función asociada (y por lo tanto crear un stack frame inicial).

El procesamiento del mensajes finaliza cuando el stack vuelve estar vacío de nuevo.
