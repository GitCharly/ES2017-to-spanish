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



[6-001]: www.aca-va-una-explicacion-sobre-lo-que-es-locale.com




