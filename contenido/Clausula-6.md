# 6 Valores y tipos de datos en ECMA-Script
<span class="original-title">ECMAScript Data Types and Values</span>

Los algoritmos de esta especificación manipulan datos, cada uno de los cuales tiene un tipo asociado. Los tipos de valores posibles, son exactamente los definidos en esta cláusula. Los tipos están subclasificados en tipos del lenguaje ECMAScript y tipos de la especificación. 

Dentro de esta especificación, la notación "*Type(x)*" es usada como una abreviación para: "*el tipo de x*", donde "*tipo*" se refiere a los tipos del lenguaje ECMAScript y de la especificación definidos en esta cláusula. Cuando la palabra "empty" se usa como si estuviera nombrando un valor, es equivalente a decir "sin valor de ningún tipo".

## 6.1 Tipos del lenguaje ECMAScript
<span class="original-title">ECMAScript Language Types</span>

Un *tipo del lenguaje ECMAScript* corresponde a valores que son directamente manipulados por un programador de ECMAScript usando el lenguaje ECMAScript. Los tipos del lenguaje ECMAScript son: **Undefined, Null, Boolean, String, Symbol, Number**, y **Object**. Un *valor del lenguaje ECMAScript* es una valor que está caracterizado por un tipo del lenguaje ECMAScript.

### 6.1.1 El tipo Undefined
<span class="original-title">The Undefined Type</span>

El tipo `Undefined` tiene exactamente un solo valor, llamado `undefined`. Cualquier variable a la que no se le haya asignado un valor, tiene el valor `undefined`.

### 6.1.2 El tipo Null
<span class="original-title">The Null type</span>

El tipo `Null` tiene exactamente un solo valor, llamado `null`.

### 6.1.3 El tipo Boolean
<span class="original-title">The Null type</span>

El tipo `Boolean` representa una entidad lógica que tiene dos valores, llamados: `true` and `false`.

### 6.1.4 El tipo String
<span class="original-title">The String type</span>

El tipo String es el conjunto de todas las secuencias ordenadas de cero o más valores enteros de 16 bits unsigned (*elementos*) hasta un largo máximo de 2<sup>53</sup> elementos. El tipo String es generalmente utilizado para representar datos de texto en un programa ECMAScript en ejecución, en cuyo caso, cada elemento en la String es tratado como una unidad de valor UTF-16 de 16 bits. Cada elemento se considera como ocupando una posición dentro de la secuencia. Estas posiciones están indexadas con enteros no-negativos. El primer elemento, si es que lo hay, está en el índice 0, el siguiente elemento (si hay uno) está en el índice 1, y así consecutivamente. El largo de la String es el número de elementos (o sea, de valores de 16 bits) dentro de ella. Una String vacía tiene un largo cero y por lo mismo, no contiene elementos.

Ahí donde las operaciones de ECMAScript interpretan valores String, cada elemento es interpretado como una sola unidad de código UTF-16. Sin embargo, ECMAScript no coloca ninguna restricción o requerimiento en la secuencia de unidades de código en un valor String, asi que ellos pueden estar malformados cuando son interpretados como secuencias de unidades de código UTF-16. Las operacioes que no interpretan contenido String las tratan como secuencias de enteros indiferenciados de 16 bits unsigned. La función `String.prototype.normalize` (ver 21.1.3.12) puede ser usada para normalizar explícitamente un valor String. `String.prototype.localeCompare` (ver 21.1.3.10) normaliza valores String internamente, y no hay otras operaciones que normalicen implícitamente las Strings sobre las que operan. Solo las operaciones que son explícitamente definidas como sensibles al lenguaje o al locale*[(ver)][6-001] producen resultados sensibles al lenguaje. 

> NOTA: El motivo tras este diseño fue mantener la implementación de Strings tan simple y de alto rendimiento como fuera posible. Si el texto fuente ECMAScript está en la Forma Normalizada C, los literales string se garantiza que serán normalizados a su vez, ya que ellos no contienen ninguna secuencia de escape Unicode.

Algunas operaciones interpretan el contenido String como unidades de código UTF-16 codificadas. En tal caso la interpretación es: 
+ una unidade de codigo en el rango 0 a 0xD7FF o en el rango 0XE000 a 0xFFFF es interpretada como una unidad de código con el mismo valor.
+ una secuencia de dos unidades de código, donde la primera unidad de código, *c1*, está en el rango 0xD800 a 0xDBFF y la segunda unidad de código, *c2*, está en el rango 0xDC00 a 0xDFFF, es un par sustito y se interpreta como un punto de código con el valor:
    + (*c1* - 0xD800) x 0x400 + (*c2* - 0xDC00) + 0x10000 (ver 10.1.2)
+ una unidad de código que está en el rango 0xD800 a 0xDFFF, pero no es parte de un par sustituto, es interpretada como un punto de código con el mismo valor.

### 6.1.5 El tipo Symbol
<span class="original-title">The Symbol Type</span>

El tipo `Symbol` es el conjunto de todos los valores no-string que pueden ser usados como la clave de la propiedad de un Objeto. (ver 6.1.7)

Cada valor posible de `Symbol` es único e inmutable.

Cada valor de `Symbol` mantiene inmutablemente una asociación con un valor llamado [[Description]] que es o bien un `undefined` o un valor `String`.

### 6.1.6 Symbols bien conocidos
<span class="original-title">Well-Known Symbols</span>

Los Symbols bien conocidos, son valores `Symbols` incorporados que hacen referencia explícita a algoritmos de esta especificación. A no ser que se indique lo contrario, los Symbols bien conocidos son compartidos por todos los *realms*. (8.2)

Dentro de esta especificación un symbol bien conocido es referido utilizando una notación con la forma @@nombre, donde "nombre" es uno de los valores listados en la tabla a continuación: 

| Nombre en la especificación | [[Descripcion]]             | Valor y propósito | 
| --------------------------- | --------------------------- | --------------------------------------------------- |
| @@hasInstance               | "Symbol.hasInstance"        | Un método que determina si un objeto constructor reconoce un objeto como una de las instancias de su constructor. Invocada por las semánticas del operador `instanceof`           |
| @@isConcatSpreadable        | "Symbol.isConcatSpreadable" | Una propiedad con valor booleano que es si es `true` indica que `Array.prototype.concat` debe aplanar un objeto a sus elementos array.                                            |
| @@iterator                  | "Symbol.iterator"           | Un método que devuelve el Iterador por defecto para un objeto. Invocado por las semánticas de la sentencia `for-of`.                                                              |
| @@match                     | "Symbol.match"              | Un método de expresión regular que hace coincidir la expresión regular contra una string. Invocada por el método `String.prototype.match`                                         |
| @@replace                   | "Symbol.replace"            | Un métodod de expresión regular que reemplaza la substring coincidente en una string. Invocada por el método `String.prototype.replace`                                           |
| @@search                    | "Symbol.search"             | Un método de expresión regular que devuelve el índice dentro de una string que coincide con la expresión regular. Invocado por el método `String.prototype.search`                |
| @@species                   | "Symbol.species"            | Una propiedad con valor función que es la función constructor que es usada para crear objetos derivados.                                                                          |
| @@split                     | "Symbol.split"              | Un método de expresión regular que divide un string en el índice que coincide con la expresión regular. Invocado por el método `String.prototype.split`                           |
| @@toPrimitive               | "Symbol.toPrimitive"        | Un método que convierte un objeto en un valor primitivo correspondiente. invocado por la operación abstracta *ToPrimitive*                                                        |
| @@toStringTag               | "Symbol.toStringTag"        | Una propiedad con valor String que es usada en la creación de la descripción string por defecto del objeto. Accesible a través del método incorporado `Object.prototype.toString` |
| @@unscopables               | "Symbol.unscoplables"       | Una propiedad con valor objeto, cuyos nombres de propiedad propios y heredados están excluidos del marco de entorno de `with` asociado al objeto.                                 |

## 6.1.6 El tipo Number
<span class="original-title">The Number Type</span>

El tipo número tiene exactamente 18.437.736.874.454.810.627 valores (o sea, 2<sup>64</sup>-2<sup>53</sup>+3), representando los valores de doble precisión de 64-bits con formato IEEE 754-2008 especificados en el estándar IEEE para la Aritmética Binario de punto flotante, excepto que los 9.007.199.254.740.990 valores "Not-a-Number" del estándar IEEE son representados en ECMAScript como un solo valor especial `NaN`. (Note que el valor **NaN** es producido por la expresión del programa `NaN`). En algunas implementaciones, código externo podría ser capaz de detectar la diferencia entre varios valores NaN, pero tal comportamiento es dependiente de la implementación; para el código ECMAScript, todos los valores **NaN** son indistiguibles uno de otro.

> NOTA: El patrón de bits que puede observarse en un *ArrayBuffer* (24.1) o en un *SharedArrayBuffer* (24.2) después de que un valor Number ha sido almacenado, no es necesariamente el mismo que la representación interna usada por la implementación ECMAScript de ese valor Number.

Hay otros dos valores especiales, llamados **infinito positivo** y **infinito negativo**. Para comodidad y propósitos expositorios, estos valores serán referenciados por los símbolos +<span>#&8734;</span> y -<span>#&8734;</span>, respectivamente. (Observe que estos dos valores Number infinito son producidos por las expresiones del programa __+Infitinity__(o simplemente **Infinity**) y __-Infinity__).

Los otros 18.437.736.874.454.810.624 valores (o sea, los 2<sup>64</sup>-2<sup>53</sup>), son llamados los números finitos. La mitad de estos números son números positivos y la otra mitad son los números negativos; para cada valor Number positivo finito posible hay un valor negativo correspondiente con la misma magnitud.

Observe que existen ambos, 0 positivo y 0 negativo. En resumen, estos valores son referidos por comodidad de esta especificación por los símbolos __+0__ y __-0__, respectivamente. (Observe que estos dos valores Number cero diferentes son producidos por las expresiones del programa __+0__ (o simplemente **0**) y __-0__.)

Los 18.437.736.874.454.810.622 (o sea, 2<sup>64</sup>-2<sup>53</sup>-2) valores finitos no cero son de dos clases:

Los 18.428.729.675.200.069.632 (2<sup>64</sup>-2<sup>54</sup>) de ellos que están normalizados tienen la forma:

> *s* x *m* x *2<sup>e</sup>*

donde:
- *s* es +1 o -1,  
- *m* es un entero positive menor que 2<sup>53</sup> pero no menor que 2<sup>52</sup> y,
- *e* es un entero en el rango entre -1074 y 971, ambos incluidos.

Los restants 9.007.199.254.740.990 (2<sup>53</sup>-2) valores que no están normalizados, tienen la forma: 

> *s* x *m* x *2<sup>e</sup>*

donde:
- *s* es un +1 o -1,
- *m* es un entero positivo menor que 2<sup>52</sup>, y
- *e* es -1074.

Observe que todos los enteros positivos y negativos cuya magnitud no es mayor a 2<sup>53</sup> son representables en el tipo Number. (De hecho, el entero 0 tiene dos representaciones, +0 y -0).

Un número finito tiene un *significante impar* si es no-cero y el entero *m* usado para expresarlo (en una de las dos formas mostradas más arriba) es impar. En caso contrario, tendrá un *significante par*.

En esta especificación, la frase "el valor Number para *x*" donde *x* representa un cantidad matemática real exacta distinta de cero (la que puede ser incluso un número irracional como <span>#&960;</span>) implica un valor Number elegido de la siguiente manera. Considere el conjunto de todos los valores finitos del tipo Number, con __-0__ removido y con los dos valores adicionales que son representables en el tipo Number, es decir 2<sup>1024</sup> (+1 x 2<sup>53</sup> x 2<sup>971</sup>) y -2<sup>1024</sup> (-1 x 2<sup>53</sup> x 2<sup>971</sup>), agregados. Se elige el miembro de este conjunto que está más cerca de en valor a *x*. Si dos valores están igualmente cerca, entonces aquél con *signigicante par* es el elegido; para este propósito, los 2 valores extra 2<sup>1024</sup> y -2<sup>1024</sup> se consideran como teniendo *significante par*. Finalmente, si 2<sup>1024</sup> es elegido, se reemplaza con +<span>#&8734;</span>, si lo es -2<sup>1024</sup>, se reemplaza con -<span>#&8734;</span> si __+0__ es elegido, se reemplaza con __-0__ si y solo si *x* es menor que cero; cualquier otro valor elegido permanece sin cambios. El resultado es el valor Number para *x*. (Este procedimiento corresponde exactamente con el comportamiento del modo IEEE 754-2008 "redondea al màs cercano, ajusta al par").

Algunos operadores ECMAScript trabajan solo con enteros en rangos específicos, como -2<sup>31</sup> hasta 2<sup>31</sup>-1, inclusives, o en el rango 0 hasta 2<sup>16</sup>-1, inclusives. Estos operadores aceptan cualquier valor del tipo Number, peor primero convierten cada uno de aquellos valores a un valor entero en el rango esperado. Vea las descripciones de las operaciones de conversión numéricas en 7.1.

### 6.1.7 El tipo Object
<span class="original-title">The Object Type</span>







[6-001]: www.aca-va-una-explicacion-sobre-lo-que-es-locale.com




