<h1>✨ Introducción</h1>
Historia de JavaScript: ¿Qué es ECMAScript?
Eventos importantes

1950 → Inicio de las computadoras
1969 → Se creo la red ARPANET,
1970-1990 → Se explora ARPANET
1990 → Tim Berners-lee presento lo que hoy conocemos como internet. Se conoció el termino World Wide Web (forma de acceder documentos, archivos y enlaces al alcance de todos)
1993 → Nacimiento de un Navegador.
Marc Andreessen: le dio vida a una gran empresa Netscape. Creo un navegador que podías acceder a internet (HTML simple, enlaces, algunas fotografías)

Browser wars: Guerra de los navegadores
Debido a la popularidad de Netscape, Microsoft en 1995 lanzó Internet Explorer. Debido a esta guerra nacieron tecnologías como CSS (propuesta de Microsoft para hacer temas a nivel de interfaz), conceptos como la empresa Mozilla y JavaScript.

En el año 1995, dentro de Netscape gracias a Brendan Eich nació el lenguaje Javascript. En sus inicio fue llamado Mocha, para después cambiar su nombre por LiveScript y finalmente termino siendo JavaScript por la popularidad del lenguaje Java.

Debito a esto, Microsoft lazó su propio lenguaje para su navegador, JScript. Así es como nacé, ECMAScript (1997). ECMAScript es un consorcio Europeo que permitió generar un estándar para que los navegadores lo siguieran.

¿Qué es el TC39?
TC39: Es un grupo de hackers, académicos y personas afines a la tecnología que se encargan, junto con la comunidad, de traer nuevas funcionalidades al lenguaje, bajo el mando de ECMA.

ESNext es el nombre que se le asigna a la próxima versión de JavaScript. Cada feature o propuesta debe de pasar los siguientes stages:

Stage0: Strawperson (Borrador, cualquier persona puede tener una idea para implementar)
Stage1: Proposal (Propuesta formal)
Stage2: Draft (Borrador, como va a funcionar la implementación y el impacto)
Stage3: Candidate (Esta lista para feedback y últimos detalles por lo implementadores y usuarios)
Stage4: Finished (Va a ser desplegada en la siguiente versión)
<h1>✨ ¿Qué se implementó en ES6?</h1>
let y const, y arrow functions
Nuevas palabras reservadas para guardar variables. Antes solo existía var.

Let permite la reasignación de valores de una variable. Con const el valor no puede ser reasignado. Ambas tienen un scope de bloque.

Untitled
Arrow functions
Es una alternativa compacta para declarar una function. Su sintaxis es la siguiente:

const miFuncion = (params) => {
	// code
}
https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions

Strings
Con la llegada de ES6 los string recibieron una de las features más importantes, los template literals. Es una manera diferente de poder tener texto en multilinea, interpolación de variables.

Concatenación
Antes:

let hello = "Hello"
let world = "World"

let frase = hello + " " * world;

console.log(frase);
Después:

let hello = "Hello"
let world = "World"

let templateLiterals = `${hello} ${word}!`;

console.log(templateLiterals);
Multilinea
Antes:

let lorem = "Esto es una linea de texto \n" + "Esta es otra línea";
console.log(lorem);
Después:

let lorem = `Esta es una línea de texto
y esta es otra línea.`;
console.log(lorem);
Template literals (Template strings) - JavaScript | MDN

Parámetros por defecto
Los parámetros por defecto nos ayudan a definir un valor inicial a las variables que son recibidas en la función. Esto permite que se tenga la seguridad que nuestra variable tendrá un valor.

Antes:

function createNewUser(name, age, country) {
	let name = name || "Zajith";
	let age = age || 27;
	let country = contry || "MX";

	console.log(name, age, country;
}

newUser(); // "Zajith 27 MX".
newUser("Jesus", 27, "USA"); // "Jesus 27 USA"
Después:

function createNewUser(name = "Zajith", age = 27, country = "MX") {
	console.log(name, age, country;
}

newUser(); // "Zajith 27 MX".
newUser("Jesus", 27, "USA"); // "Jesus 27 USA"
Default parameters - JavaScript | MDN

Asignación de desestructuración
La desestructuración permite obtener valores de los objetos o arreglos, sin tener que acceder directamente a su propiedad o indice, en caso de los array.

const person = {
	name: 'Zajith',
	age: 27,
	languages: ["Spanish", "English"]
}

const { name, languages } = person;
console.log(name) // Zajith
console.log(languages) // ["Spanish", "English"]

const [primerIdioma, segundoIdioma] = languages;
console.log(primerIdioma) // Spanish
console.log(segundoIdioma) // English
En la desestructuración de los arreglos, si no se quiere acceder a un indice anterior se tiene que respetar el orden y únicamente separar por comas:

const person = {
	name: 'Zajith',
	age: 27,
	languages: ["Spanish", "English"]
}

const { name, languages } = person;
const [, segundoIdioma] = languages;
console.log(segundoIdioma) // English
Destructuring assignment - JavaScript | MDN

Spread operator
El spred operator u operador de propagación, permite expandir un elemento iterable dentro de los parámetros de un función o dentro de otro objeto, esto con la finalidad de evitar la repetición. Tiene el mismo comportamiento en los objetos y arreglos.

let person = { name: 'Zajith', age: 27 }
let country = 'MX';
let data = {...person, country};

console.log(data); // { name: 'Zajith', age: 27, country: 'MX'}
Así mismo, permite combinar o hacer un copia de un objeto

let person = { name: 'Zajith', age: 27 }
let moreData = { country: 'MX' };
let data = {...person, ...moreData};

console.log(data); // { name: 'Zajith', age: 27, country: 'MX'}

const person2 = {...person}
console.log(person2) // { name: 'Zajith', age: 27 }
Spread syntax (…) - JavaScript | MDN

Rest parametros
Cuando en una función no tenemos el conocimiento de cuantos parámetros van a ser pasados a la función, se puede hacer el uso de rest parameters. De esta manera, únicamente el valor que es definido explicitamente será asignado, todos los demás serán encapsulados dentro del rest parameters.

function sum(num, ...values){
	console.log(values);
	console.log(num + values[0]);
	return num + values[0];
}

sum(2,3,4,5);
Object literals
Permite realizar la asignación de las keys de un objeto sin repetir. Si la key de nuestro objeto, es igual a variable únicamente basta con pasar la variable.

Antes:

function createNewUser(user, age, country) { 
	return { 
		user: user, 
		age: age, 
		country: country
	}
}
Después:

function createNewUser(user, age, country) { 
	return { 
		user, 
		age, 
		country
	}
}
Promesas
Las promesas es un código que será ejecutado, pero su resultado puede llegar en el futuro cercano, lejano o nunca. Todo dependerá del servicio. La función que se le pasa al objeto Promise, recibe dos valores resolve y reject. Resolve, es un callback que se ejecutará en caso de que el resultado sea el correcto, en caso de que ocurra un error o se ejecutará el callback reject.

const myPromise = () => {
    return new Promise((resolve, reject) => {
        if (false) {
            resolve("hey!!");
        } else {
            reject ( "whooooops!");
        }
    })
}

myPromise()
.then(response => console.log(response))
.catch(err => console.log(err));
Promise - JavaScript | MDN

Clases
Las clases nos permiten dividir y encapsular cierto funcionamiento. Las clases están presentes en muchos lenguajes de programación, pero no fue hasta ES6 que javascript las incorporó.

class Person {
  constructor(name, age) {
    this.name = name;
    this.age = age;
  }

  getInfo() {
    console.log(`My name is ${this.name}. I'm ${this.age} years old`);
  }
}

class Student extends Person {
  constructor(name, age) {
    super(name,age); // <- 
  }
}

const person = new Person('Zajith', 27);

person.getInfo(); // My name is Zajith. I'm 27 years old
Classes - JavaScript | MDN

Module
Los módulos nos permiten poder dividir nuestro código en diferentes archivos, lo cual nos brinda la libertad de reutilizar el funcionamiento de ciertas piezas de código a través de todo nuestro proyecto.

Se puede realizar la exportación de funciones, variables, objetos, clases y más. Para realizar la exportación tenemos que hacer uso de la palabra reservada export. Si queremos importar tenemos que hacer uso de la palabra import.

Existen dos tipos de exportación:

Nombrada
Por defecto
La exportación nombrada nos permite realizar multiples exportaciones dentro de un mismo archivo. Debido a que se hacen multiples export en el mismo archivo, en la importación se tiene que ser muy cuidadoso con los nombres ya que tienen que ser lo mismos.

// utils.js
export const sayHello = () => console.log('Hello');
export const sayBye = () => console.log('Bye!');

// main.js
import { sayHello, sayBye } from './utils';
La exportación por defecto, solo nos permite hace una exportación por defecto por archivo.

// utils.js
const sayHello = () => console.log('Hello');

export default sayHello;

// main.js
import sayHello from './utils';
Se pueden combinar ambas exportaciones

// utils.js
const sayHello = () => console.log('Hello');
const sayBye = () => console.log('Bye!');

export { sayBye, sayHello as default };

// main.js
import sayHello, { sayBye } from './utils';

Generator
Los generadores nos permiten crear una función iterable que recuerda su ejecución y su estado interno para próximas ejecuciones. Con la palabra reservada yield se puede pausar una función generadora y mostrar el valor que le sigue a yield, y así proporcionar una opción ligera para iterar valores.

function* iterate(array)  {
    for (let value of array) {
        yield value;
    }
}

const it = iterate(["Oscar", "Alexa", "David", "Gerlis"]);
console.log(it.next().value); // Oscar
console.log(it.next().value); // Alexa
console.log(it.next().value); // David

Set
Un Set es una lista desordenada que no permite tener valores repetidos dentro.

const set = new Set();

set.add('item 1'); // Set ['item 1']
set.add('item 2').add('item 3'); // Set ['item 1','item 2','item 3']
set.has('item 2'); // true
set.delete('item 1'); // Set ['item 2','item 3', 1]                    
set.size(); // 2
Tiene los métodos:

Add
Has
Delete
Size
Set - JavaScript | MDN

<h1>✨ ¿Qué se implementó en ES7?</h1>
Exponentiation operator
Se introdujo una alternativa a Math.pow para poder realizar operaciones más claras:

const square = 4 ** 2 // 16
Exponentiation (**) - JavaScript | MDN

Array includes
Nos permite determinar si un elemento se encuentra dentro un array.

let numbers = [1, 3, 4, 6, 7, 8];

console.log(numbers.includes(9)) // false
console.log(numbers.includes(1)) // true

const list = ["oscar", "David", "Ana"]
console.log(list.includes("oscar")) // true
console.log(list.includes("Pedro")) // false
Array.prototype.includes() - JavaScript | MDN

<h1>✨ ¿Qué se implementó en ES8?</h1>
Object entries
Es un función que no permite transformar un objeto en un array con cada una de las propiedades en un array de la forma [key, value]

const countries = { MX: "Mexico", CO: "Colombia", CL: "Chile", PE: "Peru"}

console.log(Object.entries(countries));
/*[
	['MX', 'Mexico'],
	['CO', 'Colombia'],
	['CL', 'Chile'],
	['PE', 'Peru']
]*/
Object.entries() - JavaScript | MDN

Object values
Es una función que nos permite transformar un objeto en un array de los valores de cada una de las propiedades de nuestro objeto

const countries = { MX: "Mexico", CO: "Colombia", CL: "Chile", PE: "Peru"}

console.log(Object.values(countries)); // ['Mexico', 'Colombia', 'Chile', 'Peu']
Object.values() - JavaScript | MDN

String padding
Es un método que permite rellenar la cadena actual con una cadena dada. El relleno es aplicado desde el inicio de la cadena actual.

str.padStart(targetLength [, padString])
targetLength → Es la longitud de la cadena resultante una vez que haya sido rellenada. Si este parámetro es más pequeño que la longitud de la cadena actual, la cadena se mantendrá igual.

padString → Valor opcional. La cadena para rellenar la cadena actual. Si esta cadena es muy larga, será recortada y la parte más a la izquierda será aplicada

'abc'.padStart(10);         // "       abc"
'abc'.padStart(10, "foo");  // "foofoofabc"
'abc'.padStart(6,"123465"); // "123abc"
String.prototype.padStart() - JavaScript | MDN

Trailing comas
Es la capacidad de agregar nuevos elementos a un objeto o array. Se puede agregar una nueva propiedad o elemento sin modificar el anterior.

const arr = [1, 2, 3,,,];
arr.length; // 5

const object = {
  foo: "bar",
  baz: "qwerty",
  age: 42,
};
Trailing commas - JavaScript | MDN

Funciones asíncronas
Las funciones asíncronas permitieron al lenguaje ejecutar código el cual es necesario obtener el resultado previo. Además, viene a solucionar el callback hell

const fnAsync = () => {
	return new Promise( (resolve, reject ) => {
		(true)
		? setTimeout(() => resolve ("Async!!"), 2000)
        	: reject(new Error("Error"));
	});
}

const anotherFn = async () => {
	const somethig = await fnAsync();
   	 console.log(somethig);
    	console.log("Hello");
}

console.log("before");
anotherFn();
console.log("After");
async function - JavaScript | MDN

<h1>✨ ¿Qué se implementó en ES9?</h1>
Expresiones regulares
En esta versión de ECMA se incorporó la posibilidad de usar grupos nombrados usando una expresión regular. Un match de una expresión regular retorna un objeto. Si un fragmento de la expresión regular esta dentro de los paréntesis, es capturado por el grupo y es almacenado en el grupo en el cual hizo el match.

const eventDate = /([0-9]{4})-([0-9]{2})-([0-9]{2})/;
const matchedObject = eventDate.exec('2019-04-03');

console.log(matchedObject[1]); // 2019
console.log(matchedObject[2]); // 04
console.log(matchedObject[3]); // 23
Después de esta nueva versión, podemos nombrar grupos usando la sintaxis <groupname>, que almacena dentro de la key groups

const eventDate = /(?<year>[0-9]{4})-(?<month>[0-9]{2})-(?<day>[0-9]{2})/;
const matchedObject = eventDate.exec('2019-04-03');

console.log(matchedObject.groups.year); // Prints 2019
console.log(matchedObject.groups.month); // Prints 04
console.log(matchedObject.groups.day); // Prints 03
Spread operator
El spread operator llega para los objetos, permitiendo hacer uso de el.

const foo = {
  empanadas: 6,
  milanesas: 2,
  yerba: "1 Kg",
};

const bar = { ...foo, water: "1 L"  };
console.log(bar); // Prints 

/**
* {
*   empanadas: 6,
*   milanesas: 2,
*   yerba: "1 Kg",
*   water: "1 L",
**/
Si tenemos una key con el mismo nombre, el valor será el último agregado. Esto servirá para sustituir valores por default.

const foo = {
  empanadas: 6,
  milanesas: 2,
  yerba: "1 Kg",
};

const bar = { ...foo, empanadas: 12  };console.log(bar); // Prints
/**
* {
*   empanadas: 12,
*   milanesas: 2,
*   yerba: "1 Kg",
**/
El operador de propagación sirve para crear una copia en un solo nivel de profundidad, esto quiere decir que si existen objetos o arrays dentro de un objeto a copiar. Entonces los sub-elementos en cada nivel, tendrán la misma referencia en la copia y en el original.

const original = { datos: [1, [2, 3], 4, 5] }
const copia = { ...original }

original === copia // false
original["datos"] === copia["datos"] // true
Promise.finally
ES9 introduce un nuevo callback que siempre es ejecutado en las promesas. No importando el resultado, si fue resolved o rejected.

fetch(url)
  .then()
  .catch()
  .finally(() => console.log(`I'm always called!`));
Es útil cuando quieres hacer un borrado o limpieza de operaciones sin importar si el resultado fue éxitoso o no.

Promise.prototype.finally() - JavaScript | MDN

Iteración asíncrona
En esta nueva versión se incluye la posibilidad de usar ciclos de forma asíncrona, esto permitiendo ejecutar código que no bloque el hilo principal de nuestra aplicación.

async function arrayOfNames(array) {
    for await (let value of array) {
        console.log(value);
    }
}

const names =arrayOfNames(["Alexa", "Oscar", "David"]);
console.log("After");

// Afer
// Alexa
// Oscar
// David
<h1>✨ ¿Qué se implementó en ES10?</h1>
Flat
El método flat de los array permite aplanar los elementos internos de un array permitiendo eliminar array internos.

const numbers = [1, 2, 3, 4, [5, 6, [7, 8, 9]]];

numbers.flat(1) // [ 1, 2, 3, 4, 5, 6, [ 7, 8, 9 ] ]
numbers.flat(2) // [ 1, 2, 3, 4, 5, 6, 7, 8, 9 ]
Si se quiere aplanar todo el arreglo sin pasar una profundidad exacta, se puede hacer uso de Infinity.

const numbers = [1, 2, 3, 4, [5, 6, [7, 8, 9]]];

numbers.flat(Infinity) // [ 1, 2, 3, 4, 5, 6, 7, 8, 9 ]
Array.prototype.flat() - JavaScript | MDN

Flat-map
Permite aplanar los elementos de un array en un nivel, pasando un función que mapeara cada elemento del nuevo array.

const numbers2 = [1, 2, 3, 4, 5, 6, 7, 8, 9];

numbers2.flatMap(num => num * 2). // [ 2, 4, 6, 8, 10, 12, 14, 16, 18 ]
Este método no se podría utilizar para array que tengan más de un nivel de profundidad. Sin embargo, se pueden combinar los métodos flat y map para tener un mismo resultado.

const numbers = [1, 2, 3, 4, [5, 6, [7, 8, 9]]];

numbers2.flat(Infinity).map(num => num * 2) // [ 2, 4, 6, 8, 10, 12, 14, 16, 18 ]
Array.prototype.flatMap() - JavaScript | MDN

TrimStart y trimEnd
Permiten eliminar los espacios en blanco, ya sea de el inicio o del final respectivamente.

trimStart() → Elimina los espacio al inicio
trimEnd() → Elimina los espacios al final
const hello = '        Hello!        ';

console.log(hello.trimStart()); // 'Hello!        ';
console.log(hello.trimEnd()); // '        Hello!';
String.prototype.trimStart() - JavaScript | MDN

String.prototype.trimEnd() - JavaScript | MDN

Try catch
Nos permite realizar el manejo de errores de una forma diferente.

try {
	// Lógica
} catch (error) {
	// Manejo de errores
}
try…catch - JavaScript | MDN

FromEntries
Permite hacer la transformación de un array a un objeto:

const entries = [
  ["name", "Zajith"],
  ["age", 27],
];

console.log(entries); // [ [ 'name', 'Zajith' ], [ 'age', 27 ] ]
console.log(Object.fromEntries(entries)); // { name: 'Zajith', age: 27 }
Object.fromEntries() - JavaScript | MDN

<h1>✨ ¿Qué se implementó en ES11?</h1>
Optional chaining
Es una forma de evitar errores solicitando propiedades de forma opcional utilizando el símbolo ? , sirve cuando no estamos seguros de que los valores estén completos.

Este operador es igual que . , excepto que en vez de causar un error si una referencia es nullish(null or undefined), la expresión retorna un valor undefined.

const users = {
	zajith : {
		country: 'MX'
	},
	brenda: {
		country:'MX'
	}
}

console.log(users?.zajith?.country);
Optional chaining (?.) - JavaScript | MDN

BigInt
JavaScript tiene límites numéricos, un máximo Number.MAX_SAFE_INTEGER y un mínimo Number.MIN_SAFE_INTEGER. Fuera de estos límites, los cálculos matemáticos pueden fallar y mostrar resultados erróneos. Con BigInt esto se resuelve.

const aBigNumber = 8907245920742093847n;
const anotherBigNumber = BigInt(8907245920742093847);

console.log(aBigNumber); // 8907245920742093847n
console.log(anotherBigNumber); // 8907245920742093847n
BigInt - JavaScript | MDN

Nullish coalescing
Es un operador lógico ?? que retorna el valor que se encuentra del lado derecho, cuando el valor que se encuentra del lado izquierdo es null o undefined.

const anotherNumber = null;
const myNumber = 10;

const validate = anotherNumber ?? 5;
const validate2 = myNumber ?? 1;

console.log(validate); // 5
console.log(validate2); // 10
Nullish coalescing operator (??) - JavaScript | MDN

Promise.allSettled
Este método retorna una promesa después de que todas las promesas dadas fueron completadas resueltas exitosamente o no, con un array de objetos que describe cada una de llamadas.

Este método es típicamente usado cuando se tienen multiples llamadas asíncronas que no son dependientes una de la otra, o te gustaría saber el resultado de cada una.

const promise1 = Promise.resolve(3);
const promise2 = new Promise((resolve, reject) => setTimeout(reject, 100, 'foo'));
const promises = [promise1, promise2];

Promise.allSettled(promises).
  then((results) => results.forEach((result) => console.log(result.status)));

// expected output:
// "fulfilled"
// "rejected"
Promise.allSettled() - JavaScript | MDN

Global this
La propiedad globalThis provee de una manera estándar de accesar al objeto global this a través de los distintos entornos. A diferencia de las propiedades window y self , esta garantizado su funcionamiento en window y no-window contextos.

globalThis - JavaScript | MDN

MatchAll
El método matchAll() nos retorna un iterado con todos los resultados que hacen match de una expresión regular con un string, incluyendo los grupos de captura.

const regexp = /t(e)(st(\d?))/g;
const str = 'test1test2';

const array = [...str.matchAll(regexp)];

console.log(array[0]);
// expected output: Array ["test1", "e", "st1", "1"]

console.log(array[1]);
// expected output: Array ["test2", "e", "st2", "2"]
String.prototype.matchAll() - JavaScript | MDN

Dynamic Import
Es una función que permite la carga de módulo asíncronamente cuando nosotros deseemos que sean cargados.

// module.js
export function hello() {
	console.log('Hello');
}

// main.js
const button = document.getElementById("btn");

button.addEventListener("click", async function () {
    const { hello } = await import("./module.js");
    hello();
})
import - JavaScript | MDN

<h1>✨ ¿Qué se implementó en ES12?</h1>
Numeric-separators
Nos permite separar los números con _ con la finalidad que la lectura del número sea más fácil y clara.

const number = 1_000_000_000

console.log(number) // 1000000000
ReplaceAll
Retorna un nuevo string con todas las coincidencias de una patrón remplazado por la propiedad replacement

const string = "JavaScript es un maravilloso lenguaje de  programacion";

const replacedString = string.replace("JavaScript", "TypeScript");

console.log(replacedString); // TypeScript es un maravillo lenguaje de programación.
String.prototype.replaceAll() - JavaScript | MDN

Promise-any
Recibe un array de Promises y retorna un único valor de la promesa que se complete exitosamente, sin importar que una de sus predecesoras se complete con error. Si ninguna de las promesas retorna exitosamente un valor, es rechazada con un error AggregateError.

const promise1 = Promise.reject(0);
const promise2 = new Promise((resolve) => setTimeout(resolve, 100, 'quick'));
const promise3 = new Promise((resolve) => setTimeout(resolve, 500, 'slow'));

const promises = [promise1, promise2, promise3];

Promise.any(promises).then((value) => console.log(value));

// expected output: "quick"
Promise.any() - JavaScript | MDN

Métodos privados
Los métodos privados nos permiten tener métodos que no es necesario exponerlos al crear una instancia de nuestra clase. Esto viene a sustituir la convención de _ en los métodos.

class Person {
  constructor(name, age) {
    this.name = name;
    this.age = age;
  }

  #getInfo() {
    console.log(`My name is ${this.name}. I'm ${this.age} years old`);
  }
}

const zajith = new Person('Zajith', 27);

zajith.getInfo() // TypeError: zajith.getInfo is not a function
Working with private class features - JavaScript | MDN

<h1>✨ ¿Qué se implementó en ES13?</h1>
At
El método at() recibe un valor numérico entero y devuelve el elemento en esa posición, permitiendo valores positivos y negativos. Los valores negativos contarán desde el último elemento del array.

const array = ["one", "two", "three", "four", "five", "six"];

console.log(array[array.length - 1]);
console.log(array.at(-1));
Array.prototype.at() - JavaScript | MDN

Top level await
El top level await no permite usar las ventajas de async ... await sin tener que envolver nuestra lógica dentro de una función.

// utils
const response = await fetch("https://api.escuelajs.co/api/v1/products");
const products = await response.json();

export { products };

// main
import { products } from "./products.js";

console.log(products);
console.log("Hey!!");


Material del siguiente link 

https://platzi.com/blog/apuntes-del-curso-37/