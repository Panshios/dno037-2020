## Diseño y Nuevos Medios v10

### Clase 3 → Miércoles 25 de marzo, 2020

#### Tipos de datos

Si compartiera con ustedes el número 18261884, sin contexto alguno, resultaría inútil. Pero sería distinto de la siguiente manera: 

| País      |  Población       | Superficie     |
|:----------|:-----------------|:---------------|
| Chile     | 18261884         | 756102         |

Entendiendo cómo funciona una tabla, ustedes cuentan con una clara orientación para la utilización de tal número como información sobre algo concreto: La población en Chile. 

Además del dato de la población de Chile, contamos con su superficie. Si dividimos el primer dato por el segundo, obtenemos [la densidad de la población](https://es.wikipedia.org/wiki/Densidad_de_población) en Chile. El resultado de aquella división es 24,15267252.

Los números 18261884 y 24,15267252 tienen una diferencia que corresponde señalar al momento de disponerlos para su tratamiento en computación: 

- **18261884** es un número entero, un `int` (del inglés *integer*) en varios lenguajes de programación.

- **24,15267252** es un número de coma flotante, un `float` (del inglés *floating point number*) en varios lenguajes de programación.

A estos dos tipos de datos numéricos, podemos agregar otros tipos de datos: 

- **true** o **false** como las dos opciones posibles de un [tipo de dato lógico](https://es.wikipedia.org/wiki/Tipo_de_dato_l%C3%B3gico) (bool: *boolean*)

- **"A"** como un carácter (char: *character*)

Podrán notar que en el tipo de dato numérico y booleano no se usaron comillas, pero en el caso del caracter sí se utiliza. 

Mencionamos `int`, `bool`, `char` y `float` porque son palabras reservadas en [C++](https://es.wikipedia.org/wiki/C%2B%2B) para **declarar que una variable que almacenará cierto [tipo de dato](https://beginnersbook.com/2017/08/cpp-data-types/)**. 

**En el contexto computacional, una variable debe entenderse como un espacio en la memoria del computador donde se almacenará un dato que puede variar en la ejecución del programa del que sea parte.**

- - - - - - - - - - - - - - - - -

#### Datos en JS

**En programación, los datos puede ser contenidos en las variables. En JS las variables se pueden crear con una única palabra reservada,`var`**.

Y digo que se **pueden** crear con `var`, porque no necesariamente se deben crear con `var`. Para entender la diferencia, favor consulten el artículo [Var, let y const. ¿Donde, cuando y por qué?](https://medium.com/@tatymolys/var-let-y-const-donde-cuando-y-por-qu%C3%A9-d4a0ee66883b). Lo importante es que en JavaScript no se debe cambiar la palabra reservada para decir algo respecto del tipo de dato que contendrá la variable: 

```
var a = 18261884;

var b = 24,15267252;

var c = false;

var d = "Fake News";

var e = ["Marge Simpson", "Homer Simpson", "Bart Simpson", "Lisa Simpson", "Maggie Simpson"];

var f = {mom:"Luann Van Houten", dad:"Kirk Van Houten", children:"Milhouse Van Houten"};

var g = {mom:"Marge Simpson", dad:"Homer Simpson", children:["Bart Simpson", "Lisa Simpson", "Maggie Simpson"]};

var h = [
  {mom:"Luann", dad:"Kirk", children:["Milhouse"]}, 
  {mom:"Marge", dad:"Homer", children:["Bart", "Lisa", "Maggie"]},
  {mom: "Manjula", dad: "Apu", children:["Poonam","Sashi","Pria","Uma","Anoop","Sandeep","Nabendu","Gheet"]}
];

```

**Lo que cambia viene después del signo igual, que en este caso está asignando valor a cada variable.** 

Las variables `a`, `b` y `c` no requieren comillas. La variable `d`, que contiene una cadena de caracteres (*string*) sí usa comillas. La variable `e`, que contiene un arreglo, usa paréntesis cuadrado y cada elemento, por tratarse de un *string*, usa comillas. La variable `f` que contiene un objeto, usa paréntesis de llave que en su interior contiene pares separados por comas. Las variables `g` y `h` son mezclas de las anteriores; la varible `g` ofrece un elemento cuyo tercer par, de índice `children`, es un arreglo. Mientras que la variable `h` es un arreglo de tres objetos. 

Si necesito el valor de las variables `a`, `b`, `c` o `d`, basta pedirlas dirtamente; o sea, ustedes dicen `a` y ya tienen 18261884. Pero el caso es distinto si necesito un valor específico dentro de las variables  `e`, `f`, `g` o `h`.

Partamos con la variable `e`. Digamos que necesito a `Marge Simpson`. Para solicitarla debo decir `e[0]`, porque está en la primera posición de tal arreglo. Si escribo `e[1]`, lo que obtendría sería `Homer Simpson` que no es lo que necesitaba en principio. Entonces **debes recordar que la primera posición es cero, no uno**.

Pasemos a la variable `f`. Digamos que necesitamos escribir en la Consola de JavaScript de su navegador que `Kirk Van Houten dibujó la dignidad`. Tendría que escribir `f.dad + " dibujó la dignidad"`. Si quieren hacer la prueba, antes de escribir la instrucción, copien y peguen la variable `f`. 

Vamos por la variable `g` y la recomendación para la prueba es la misma: Cópienla y péguenla en la consola. Si necesitan, por ejemplo, obtener a `Maggie Simpson`, tendría que escribir `g.children[2]`, porque se encuentra en la tarcera posición de ese arreglo que tiene el índice `children`.

Así como avanzando, bien podrían intentar resolver cómo obtener `Pria` de la variable `h`. Sería algo como `h[?].children[?]`, reemplanzando el `?` por el número que corresponda.

¿Pero qué pasa si necesito todo los `children` en `h`, da lo mismo quien sea su `mom` o `dad`? Ahí tenemos que programar una consulta, y para revisarla conviene avanzar un subtítulo. 

### Ciclos y condiciones

Pimero, desde una perspectiva lógica, tendría que pedir cada elemento de cada arreglo `children`, tantas veces como elementos tenga pero recordando que la primera posición es 0. 

Pero partamos en algo más simple: Si tengo `var frutas = ["manzana","pera","durazno","limón"]` tengo que pedir `frutas[0]`, `frutas[1]`, `frutas[2]` y `frutas[3]`. O sea, voy a partir por cero y llegar como máximo al total de elementos menos uno; eran tres elementos, pero llegué a dos.

Para automatizar la solicitud de cada fruta se podría utilizar el [método `forEach()`](https://developer.mozilla.org/es/docs/Web/JavaScript/Referencia/Objetos_globales/Array/forEach). Otra opción es crear un ciclo utilizando el [ciclo `for()`](https://developer.mozilla.org/es/docs/Web/JavaScript/Referencia/Sentencias/for). La segunda opción se podría ver así:

```
var frutas = ["manzana","pera","durazno","limón"];

for (let x = 0; x < frutas.length; x++){
  console.log(frutas[x]);
}
```

Favor copia y pega las líneas de código de arriba en Consola de JavaScript de tu Navegador y presiona la tecla `Enter`. Lo que ocurre es que mientras `x` es menor que 4 se cumple un ciclo que incrementa su valor en 1 (eso es lo que significa `x++`), siendo primero frutas[0], que es el valor inicial de `x`, luego frutas[1], siguido de frutas[2], después frutas[3] y hasta ahí no más porque se cumple la condición 3 < 4.

Pero digamos que quiero solamente frutas que tengan una letra e, bien podría encargar una consulta por esa condición, si acaso incluye ese caracter. En este caso, podrían probar copiando y pegando lo que sigue en la Consola:

```
var frutas = ["manzana","pera","durazno","limón"];

for (let x = 0; x < frutas.length; x++){
  if(frutas[x].includes("e")){
  	console.log(frutas[x]);
  }
}
```

Recién utilizamos la condición [`if()`](https://developer.mozilla.org/es/docs/Web/JavaScript/Referencia/Sentencias/if...else) dentro del ciclo [`for()`](https://developer.mozilla.org/es/docs/Web/JavaScript/Referencia/Sentencias/for). O sea, igualmente pasa por frutas[0], …[1], …[2] y …[3], pero solo se imprime la "pera", que es la fruta que cumple con la condición de incluir una "e".

**Con el ciclo [`for()`](https://developer.mozilla.org/es/docs/Web/JavaScript/Referencia/Sentencias/for) y la condición [`if()`](https://developer.mozilla.org/es/docs/Web/JavaScript/Referencia/Sentencias/if...else) ya presentadas, podemos volver al desafío que teníamos en un principio, de consultar por todos los `children` en la variable `h`.**

Así como podemos poner una condición dentro de un ciclo, podemos poner un ciclo dentro de otro: 

```
var h = [
  {mom:"Luann", dad:"Kirk", children:["Milhouse"]}, 
  {mom:"Marge", dad:"Homer", children:["Bart", "Lisa", "Maggie"]},
  {mom: "Manjula", dad: "Apu", children:["Poonam","Sashi","Pria","Uma","Anoop","Sandeep","Nabendu","Gheet"]}
];

for (let x = 0; x < h.length; x++){
	for (let y = 0; y < h[x].children.length; y++){
		console.log(h[x].children[y]);
	}	
}
```

¡Prueba el código en la Consola de JavaScript de tu Navegador!

Y dentro de un ciclo tú puedes programar la modificación de una variable. No simplemente modificarla en su valor, con operaciones matemáticas en cada vuelta del ciclo. Bien se puede modificar un arreglo sumándole elementos. O sea, podemos llenar un arreglo dentro de un ciclo [`for()`](https://developer.mozilla.org/es/docs/Web/JavaScript/Referencia/Sentencias/for) con el [método `push()`](https://developer.mozilla.org/es/docs/Web/JavaScript/Referencia/Objetos_globales/Array/push). Y si prefieres las cosas ordenadas, fuera del ciclo, puedes usar el [método `sort()`](https://developer.mozilla.org/es/docs/Web/JavaScript/Referencia/Objetos_globales/Array/sort). 

A continuación vamos a crear un arreglo de nombre `chiquillada`; parte vacío pero corresponde agregar el paréntesis cuadrado para que el computador entienda que se trata de un arreglo. En `chiquillada` vamos a guardar cada `children` de `h`, mezclando al Van Houten, los Simpson y los Nahasapeemapetilon, para luego ordenarlos alfabéticamente:

```
var h = [
  {mom:"Luann", dad:"Kirk", children:["Milhouse"]}, 
  {mom:"Marge", dad:"Homer", children:["Bart", "Lisa", "Maggie"]},
  {mom: "Manjula", dad: "Apu", children:["Poonam","Sashi","Pria","Uma","Anoop","Sandeep","Nabendu","Gheet"]}
];

var chiquillada = [];

for (let x = 0; x < h.length; x++){
	for (let y = 0; y < h[x].children.length; y++){
		chiquillada.push(h[x].children[y]);
	}	
}

chiquillada.sort();
console.log(chiquillada);
```

La inquietud a la que me gustaría empujarte ahora es la siguiente: ¿Cómo puedo hacer para tener más datos, crear con conocidos una variable `i` que contenga a todas las familias de Los Simpson y poder consultarla sin tener que copiar y pegarla en todas partes? Y la respuesta que le vamos a dar a tal inquietud exige el último subtítulo de la clase de hoy.

> Te recomiendo pasar al siguiente subtítulo después de haber revisado todos las referencias vinculadas más arriba. Y si tales referencias no fueron suficientes para comprender lo que se ha presentado, favor vuelve sobre al libro de "Introducción a P5.js": Además de recomendarte revisar nuevamente los apéndices en páginas finales, podrías revisar el contenido entre páginas 56 y 66 (subtítulos "Un poco de matemáticas" y "Repetición"). 

#### JSON

Partamos con un copy/paste de https://www.json.org/json-es.html

>JSON (JavaScript Object Notation - Notación de Objetos de JavaScript) es un formato ligero de intercambio de datos. Leerlo y escribirlo es simple para humanos, mientras que para las máquinas es simple interpretarlo y generarlo. 

JSON está constituído por dos estructuras (1) Una colección de pares de nombre/valor y (2) una lista ordenada de valores. Se parece tanto al modo que escribimos objetos en JavaScript que habría que mirar con atención lo que sigue para no confundirlo con el contenido de la variable `h`, que vimos más arriba. Lo que sigue se podría guardar de modo indepediente y compartido en línea como un `h.json`:

```
[
   {
      "mom":"Luann",
      "dad":"Kirk",
      "children":[
         "Milhouse"
      ]
   },
   {
      "mom":"Marge",
      "dad":"Homer",
      "children":[
         "Bart",
         "Lisa",
         "Maggie"
      ]
   },
   {
      "mom":"Manjula",
      "dad":"Apu",
      "children":[
         "Poonam",
         "Sashi",
         "Pria",
         "Uma",
         "Anoop",
         "Sandeep",
         "Nabendu",
         "Gheet"
      ]
   }
]
```

- - - - - - - - - -

Una vez terminada las lecturas, favor selecciona un país del cinturón del Fuego del Pacífico que NO sea Chile – https://es.wikipedia.org/wiki/Cinturón_de_Fuego_del_Pacífico

Revisa si el país seleccionado está incluido, con su nombre en inglés, entre los registros de https://pomber.github.io/covid19/timeseries.json - Por ejemplo, Japan - Deja que se cargue completamente antes de buscar el nombre (puede demorar). Prefiere usar cmd + F o Crtl + F para facilitarte la búsqueda.

Anota el nombre del país tal y como aparezca en el JSON recién referido. Envía un correo indicando ese nombre y como respuseta recibirás los archivos para completar el ejercicio que corresponde dejar en tu repositorio para clase-03

- - - - - - - -

#### Referencias

- [{ } myjson - A simple JSON store for your web or mobile app](http://myjson.com/)

- [A collection of small corpuses of interesting data for the creation of bots and similar stuff](https://github.com/dariusk/corpora)

- [crossorigin.me, the free CORS proxy for everyone!](https://corsproxy.github.io/)

- [Fundamentos de JavaScript](https://developer.mozilla.org/es/docs/Learn/Getting_started_with_the_web/JavaScript_basics)

- [JavaScript for Beginner](http://xahlee.info/js/js_basics_index.html)

- [JSONLint - The JSON Validator](https://jsonlint.com/)

- [Open Notify - Open APIs From Space](http://open-notify.org/)

- [USGS - GeoJSON Summary Format](https://earthquake.usgs.gov/earthquakes/feed/v1.0/geojson.php)

- - - - - - - 

###### [SIGUIENTE CLASE →](https://github.com/profesorfaco/dno037-2020/tree/gh-pages/clase-04)
