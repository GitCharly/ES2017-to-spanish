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


| Nombre en la especificación | [[Descripcion]]             | Valor y propósito   |
| ------------ | -------------- | --------------- |
| @@hasInstance | Symbol.hasInstance"  | Un método que determina si un objeto constructor reconoce un objeto como una de las instancias de su constructor. Invocada por las semánticas del operador `instanceof`   |
| @@isConcatSpreadable  | "Symbol.isConcatSpreadable" | Una propiedad con valor booleano que es si es `true` indica que `Array.prototype.concat` debe aplanar un objeto a sus elementos array.     |
| @@iterator | "Symbol.iterator" | Un método que devuelve el Iterador por defecto para un objeto. Invocado por las semánticas de la sentencia `for-of`.                     |
| @@match | "Symbol.match" | Un método de expresión regular que hace coincidir la expresión regular contra una string. Invocada por el método `String.prototype.match`         |
| @@replace | "Symbol.replace" | Un métodod de expresión regular que reemplaza la substring coincidente en una string. Invocada por el método `String.prototype.replace`      |
| @@search  | "Symbol.search" | Un método de expresión regular que devuelve el índice dentro de una string que coincide con la expresión regular. Invocado por el método `String.prototype.search`  |
| @@species | "Symbol.species" | Una propiedad con valor función que es la función constructor que es usada para crear objetos derivados.   |
| @@split | "Symbol.split" | Un método de expresión regular que divide un string en el índice que coincide con la expresión regular. Invocado por el método `String.prototype.split` |
| @@toPrimitive | "Symbol.toPrimitive" | Un método que convierte un objeto en un valor primitivo correspondiente. invocado por la operación abstracta *ToPrimitive*  |
| @@toStringTag | "Symbol.toStringTag" | Una propiedad con valor String que es usada en la creación de la descripción string por defecto del objeto. Accesible a través del método incorporado `Object.prototype.toString` |
| @@unscopables | "Symbol.unscoplables" | Una propiedad con valor objeto, cuyos nombres de propiedad propios y heredados están excluidos del marco de entorno de `with` asociado al objeto. |


## 6.1.6 El tipo Number
<span class="original-title">The Number Type</span>

El tipo número tiene exactamente 18.437.736.874.454.810.627 valores (o sea, 2<sup>64</sup>-2<sup>53</sup>+3), representando los valores de doble precisión de 64-bits con formato IEEE 754-2008 especificados en el estándar IEEE para la Aritmética Binario de punto flotante, excepto que los 9.007.199.254.740.990 valores "Not-a-Number" del estándar IEEE son representados en ECMAScript como un solo valor especial `NaN`. (Note que el valor **NaN** es producido por la expresión del programa `NaN`). En algunas implementaciones, código externo podría ser capaz de detectar la diferencia entre varios valores NaN, pero tal comportamiento es dependiente de la implementación; para el código ECMAScript, todos los valores **NaN** son indistiguibles uno de otro.

> NOTA: El patrón de bits que puede observarse en un *ArrayBuffer* (24.1) o en un *SharedArrayBuffer* (24.2) después de que un valor Number ha sido almacenado, no es necesariamente el mismo que la representación interna usada por la implementación ECMAScript de ese valor Number.

Hay otros dos valores especiales, llamados **infinito positivo** y **infinito negativo**. Para comodidad y propósitos expositorios, estos valores serán referenciados por los símbolos +<span>&#8734;</span> y -<span>&#8734;</span>, respectivamente. (Observe que estos dos valores Number infinito son producidos por las expresiones del programa __+Infitinity__(o simplemente **Infinity**) y __-Infinity__).

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

En esta especificación, la frase "el valor Number para *x*" donde *x* representa un cantidad matemática real exacta distinta de cero (la que puede ser incluso un número irracional como <span>#&960;</span>) implica un valor Number elegido de la siguiente manera. Considere el conjunto de todos los valores finitos del tipo Number, con __-0__ removido y con los dos valores adicionales que son representables en el tipo Number, es decir 2<sup>1024</sup> (+1 x 2<sup>53</sup> x 2<sup>971</sup>) y -2<sup>1024</sup> (-1 x 2<sup>53</sup> x 2<sup>971</sup>), agregados. Se elige el miembro de este conjunto que está más cerca de en valor a *x*. Si dos valores están igualmente cerca, entonces aquél con *signigicante par* es el elegido; para este propósito, los 2 valores extra 2<sup>1024</sup> y -2<sup>1024</sup> se consideran como teniendo *significante par*. Finalmente, si 2<sup>1024</sup> es elegido, se reemplaza con +<span>#&8734;</span>, si lo es -2<sup>1024</sup>, se reemplaza con -<span>&#8734;</span> si __+0__ es elegido, se reemplaza con __-0__ si y solo si *x* es menor que cero; cualquier otro valor elegido permanece sin cambios. El resultado es el valor Number para *x*. (Este procedimiento corresponde exactamente con el comportamiento del modo IEEE 754-2008 "redondea al màs cercano, ajusta al par").

Algunos operadores ECMAScript trabajan solo con enteros en rangos específicos, como -2<sup>31</sup> hasta 2<sup>31</sup>-1, inclusives, o en el rango 0 hasta 2<sup>16</sup>-1, inclusives. Estos operadores aceptan cualquier valor del tipo Number, peor primero convierten cada uno de aquellos valores a un valor entero en el rango esperado. Vea las descripciones de las operaciones de conversión numéricas en 7.1.

### 6.1.7 El tipo Object
<span class="original-title">The Object Type</span>

Un objeto es lógicamente una colección de propiedades. Cada propiedad es o bien una propiedad de dato, o una propiedad de acceso. 
- *Una propiedad de dato* asocia el valor de una clave con un valor del lenguage ECMAScript y un conjunto de atributos booleanos. 
- *Una propiedad de acceso* asocia el valor de una clave con una o dos funciones de acceso, y un conjunto de atributos booleanos. Las funciones de acceso son utilizadas para almacenar o recuperar un valor del lenguaje ECMAScript que está asociado con la propiedad.

Las propiedades son identificadas usando los valores de las claves. Un valor de clave de propiedad es o un valor String ECMAScript o un valor Symbol. Todos los valores String y Symbol, incluyendo la string vacía, son válidas como claves de propiedades. Un *nombre de propiedad* es una clave de propiedad que es un valor String.

Un *indice entero* es un clave de propiedad con valor String que es una String numérica canónica y cuyo valor numérico es o bien +0 o un entero positivo menor o igual a 2<sup>53</sup>-1. Un *índice arreglo* es un índice entero cuyo valor numérico *i* está en el rango +0 <span>&#8804;</span> *i* < 2<sup>32</sup>-1.

Las claves de propiedades son usadas para acceder a las propiedades y sus valores. Hay dos clases de acceso a las propiedades: *get* y *set*, correspondiendo a la recuperaciòn de un valor o a su asignación, respectivamente. Las propiedades accesibles a traves de get y set incluyen tanto las *propiedades propias* que son parte directa de un objeto y las *propiedades heredadas* que son suministradas por otro objeto asociado, a través de una relación de herencia. Incluso, las propiedades heredadas, pueden ser tanto propiedades propias como heredadas del objeto asociado. Cada propiedad propia de un objeto debe tener un valor de clave que es distinto al valor de clave la de las propiedades propias del otro objeto. 

Todos los objetos son lógicamente colecciones de propiedades, pero hay múltiples formas de objetos que difieren en su semántica tanto para el acceso como para la manipulación de sus propiedades. Los *objeto ordinarios* son la forma más común de objetos y tienen las semánticas por defecto de un objeto. Un *objeto exótico* es cualquier forma de objeto en que la semántica de sus propiedades difiere de cualquier manera de las semánticas por defecto.

#### 6.1.7.1 Atributos de las propiedades
<span class="original-title">Property Attributes</span>

Los atributos son usados en esta especificaciòn para definir y explicar el estado de las propiedades de un Objeto. Una propiedad de datos asocia el valor de una clave con los atributos listados en la siguiente tabla (2): 

| Nombre de atributo | Dominio del valor                      | Descripción                                                  |
| ------------------ | -------------------------------------- | ------------------------------------------------------------ |
| [[value]]          | Cualquier tipo del lenguaje ECMAScript | El valor recuperado a través del acceso get de la propiedad. |
| [[Writable]]       | Boolean                                | Si es **false**, los intentos de código ECMAScript de cambiar el atributo [[Value]] de la propiedad usando [[Set]] no funcionarán.                                            |
| [[Enumerable]]     | Boolean                                | Si es **true**, la propiedad será enumerada por una enumeración for-in (vea 13.7.5). En caso contrario, se dice que la propiedad no es enumerable.                                             |
| [[Configurable]]   | Boolean                                | Si es **false**, los intentos de borrar la propiedad, cambiar la propiedad a una propiedad de acceso, o cambiar sus atributos (distintos a [[Value]], o cambiar [[Writable]] a **false** ) fallarán.                                             |

Una propiedad de acceso asocia una valor de clave con los atributos listados en la siguiente tabla (3): 

| Nombre del atributo | Dominio del valor | Descripción  |
| ------------------- | ----------------- | ------------ |
| [[Get]]             | Object\|Undefined | Si el valor es un Objeto, debe ser un objeto función. El método interno de la función [[Call]] (tabla 6) es invocado con una lista de argumentos vacía para recuperar el valor de la propiedad cada vez que un acceso de propiedad get es ejecutado. |
| [[Set]]             | Object\|Undefined | Si el valor es un Objeto, debe ser un objeto función. El método interno de la función [[Call]] (tabla 6) es invocado con una lista de argumento, conteniendo el valor asignado como su único argumento cada vez que un acceso de la propiedad set es ejecutado. El método interno de una propiedad [[Set]] puede, pero no es requisito, tener un efecto en el valor devuelto por llamadas subsecuentes al método interno de la propiedad [[Get]]. |
| [[Enumerable]]      | Boolean           | Si es **true**, la propiedad debe ser enumerada por una enumeración for-in (ver 13.7.5). De lo contrario, se dice de la propiedad que no es enumerable. |
| [[Configurable]]    | Boolean           | Si es **false**, los intentos de borrar la propiedad, cambiarla a una propiedad de dato, o cambiar sus atributos, fallarán.|


Si los valores iniciales de los atributos de una propiedad no son especificados explícitamente por esta especificación, los valores por defecto definidos en la tabla 4 serán utilizados: 

| Nombre del atributo | Valor por defecto |
| ------------------- | ----------------- |
| [[Value]]           | undefined         |
| [[Get]]             | undefined         |
| [[Set]]             | undefined         |
| [[Writable]]        | false             |
| [[Enumerable]]      | false             |
| [[Configurable]]    | false             |


#### 6.1.7.2 Metodos internos y ranuras internas del objeto
<span class="original-title">Object Internal Methods and Internal Slots</span>

La semántica interna de los objetos en ECMAScript, está especificada a través de algoritmos llamados "*métodos internos*". Cada objeto en un motor ECMAScript es asociado con un conjunto de métodos internos que definen su comportamiento en tiempo de ejecución. Estos métodos internos no son parte del lenguaje ECMAScript. Ellos son definidos por esta especificación solo con propósitos expositorios. Sin embargo, cada objeto dentro de una implementación ECMAScript debe comportarse según lo especificado por el método interno asociado con él. La manera exacta en la que lo logra es determinado por la implementación. 

Los nombres de los métodos internos son polimórficos. Esto quiere decir que valores objeto distinto pueden ejecutar algoritmos distintos cuando un nombre común de método interno es invocado sobre ellos. El objeto puntual sobre el cual un método interno es invocado es el "target" de la invocación. Si, durante el tiempo de ejecución, la implementación de un algoritmo intenta usar un método interno de un objeto que el objeto no soporta, será arrojada una excepción **TypeError**.

Las ranuras internas corresponden al estado interno que es asociado con los objetos y usado por varios algoritmos de la especificación ECMAScript. Las ranuras internas no son propiedades de objeto y no son heredables. Dependiendo de la especificación de una ranura interna específica, aquel estado puede consistir en valores de cualquier tipo del lenguaje ECMAScript o de los valores de los tipos de la especificación ECMAScript. A no ser que se especifique lo contrario, las ranuras internas son asignadas com parte del proceso de creación de un objeto y no pueden ser agregadas dinámicamente a un objeto. A menos que se indique lo contrario, el valor inicial de una ranura interna es el valor **undefined** . Varios algoritmos dentro de esta especificación crean objetos que tienen ranuras internas. Sin embargo, el lenguaje ECMAScript no suministra ninguna manera directa de asociar una ranura interna a un objeto. 

Tanto las ranuras como los métodos internos, son identificados en esta especificación usando nombres encerrados en doble corchete cuadrado [[*nombre*]].

La tabla 5 resume los *métodos internos esenciales* usados por esta especificación que son aplicables a todos los objetos creados o manipulados por código ECMAScript. Cada objeto debe tener algoritmos para todos los métodos internos esenciales. Sin embargo, no todos los objetos usan necesariamente los mismos algoritmos para los mismos métodos. 

La columna "firma" de la tabla 5 y otras tablas similares, describen el patrón de invocación para cada método interno. El patrón de invocación siempre incluye una lista en paréntesis de los nombres descriptivos de los parámetros. Si un nombre de parámetro es el mismo que un nombre de tipo ECMAScript entonces el nombre describe el tipo del valor requerido para tal parámetro. Si un método interno explícitamente retorna un valor, su lista parámetro es seguido por el símbolo "<span>&#8594;</span>" y el nombre del tipo del valor retornado. Los nombres de tipo usados en la firma se refieren a los tipos definidos en la cláusula 6 aumentados por el siguiente nombre adicional. "*any*" quiere decir que el valor puede ser de cualquier tipo del lenguaje ECMAScript. Un método interno implícitamente devuelve un "Registro de finalización" (sic: **Completion Record**). En adición a su parámetro, un método interno siempre tiene acceso al objeto que es el target de su invocación.

> [**Tabla 5**][6-006] 

|Método Interno|Firma|Descripción|
|--------------|-----|-----------|
|[[GetPrototypeOf]]|()<span>&#8594;</span>Object \| Null|Determina el objeto que suministra propiedades heredadas para este objeto. Un valor `null` indica que no hay propiedades heredadas.|
|[[SetPrototypeOf]]|(Object \| Null)<span>&#8594;</span>Boolean|Asocia este objeto con otro objeto que suministra propiedades heredables. Pasarle `null` indica que no hay propiedades heredables. Devuelve `true` indicando que la operación fue finalizada exitosamente, o `false` indicando que la operación no fue exitosa.|
|[[IsExtensible]]|()<span>&#8594;</span>Boolean|Determina si está permitido agregar propiedades adicionales a este objeto.|
|[[PreventExtensions]]|()<span>&#8594;</span>Boolean|Controla si nuevas propiedades pueden ser agregadas a un objeto. Devuelve `true` si la operación fue completada exitosamente o `false` si la operación no fue exitosa.|
|[[GetOwnProperty]]|(*propertyKey*)<span>&#8594;</span>Undefined \| Property Descriptor|Devuelve un descriptor de propiedades (sic *Property Descriptor*, para la propia propiedad de este objeto cuya clave es *propertyKey*, o `undefined` si tal propiedad no existe.|
|[[DefineOwnProperty]]|(*propertyKey, PropertyDescriptor*)<span>&#8594;</span>Boolean|Crea o modifica la propia propiedad, cuyo valor es *propertyKey*, para tener el estado descrito por *PropertyDescriptor*. Devuelve `true` si la propiedad fue creada/actualizada exitosamente, o `false` si la propiedad no pudo ser creada o actualizada.|
|[[HasProperty]]|(*propertyKey*)<span>&#8594;</span>Boolean|Devuelve un valor booleano indicando si el objeto ya tiene un propiedad, propia o heredada, cuya clave es *propertyKey*.|
|[[Get]]|(*propertyKey, Receiver*)<span>&#8594;</span>*any*|Devuelve el valor de la propiedad cuyo valor es *propertyKey* de este objeto. Si cualquier código ECMAScript debe ser ejecutado para recuperar el valor de la propiedad, *Receiver* es usado como el valor `this` cuando se evalúa el código.|
|[[Set]]|(*propertyKey, value, Receiver*)<span>&#8594;</span>Boolean|Configura el valor de la propiedad cuya clave es *propertyKey* a *value*. Si cualquier código ECMAScript debe ser ejecutado para configurar el valor de la propiedad, *Receiver* es usado como el valor `this` cuando se evalua el código. Devuelve `true` si la propiedad fue configurada o `false` si no lo fue.|
|[[Delete]]|(*propertyKey*)<span>&#8594;</span>Boolean|Elimina la propiedad propia cuya clave es *propertyKey* de este objeto. Devuelve `false` si la propiedad no fue eliminada y aún está presente. Devuelve `true` si la propiedad fue eliminada o ya no está presente.|
|[[OwnPropertyKeys]]|()<span>&#8594;</span>**List** of propertyKeys|Devuelve una **Lista** cuyos elementos son todas las propiedades propias para un objeto.|

La tabla 6, resume métodos internos esenciales adicionales que son soportados por objetos que pueden ser llamados como una función. Un objeto función es un objeto que soporta el método interno [[Call]]. Un *constructor* es un objeto función que soporta el método interno [[Construct]].

> [**Tabla 6**][6-007] 

|Método interno|Firma|Descripción|
|--------------|-----|-----------|
|[[Call]]|(*any*, a **List** of *any*) <span>&#8594;</span> *any*|Ejecuta código asociado con este objeto. Invocado a través de la expresión de llamada de la función. Los argumentos para el método interno son un valor **this** y una lista conteniendo los argumentos pasados a la función a través de la expresión de llamada. Los objetos que pueden implementar este método interno son llamados "*callables*"| 
|[[Construct]]|(a **List** of *any*, Object) <span>&#8594;</span> Object|Crea un objeto. Invocado a traves de los operadores `new` o `super`. El primer argumento para el método interno es una lista conteniendo los argumentos del operador. El segundo argumento es el objeto al cual el operador `new` fue inicialmente aplicado. Los objetos que implementan este método interno son llamados "*constructors*". Una función objeto no es necesariamente un constructor y tal función "no-constructor" no tiene un método interno [[Construct]].|

Las semánticas de los métodos internos esenciales para los objetos ordinarios y los objetos exóticos estándar están especificadas en la cláusula 9. Si cualquiera de los usos especificados de un método interno de un objeto exótico no es soportado por una implementación, ese uso debe arrojar una excepción del tipo **TypeError** cuando sea intentado. 

#### 6.1.7.3 Invariantes de los métodos internos esenciales
<span class="">Invariants of the Essential Internal Methods</span>

Los métodos internos de los objetos de un motor ECMAScript deben ajustarse a la lista de invariantes especificadas más abajo. Tanto los objetos ordinarios como los objetos exóticos estándar de ECMAScript en esta especificación mantienen estas invariantes. Los objetos Proxy de ECMAScript mantienen estas invariantes mediante la comprobación en tiempo de ejecución del resultado de las trampas invocadas en el objeto [[ProxyHandler]].

Cualquier implementación que suministre objetos exóticos debe también mantener estas invariantes para estos objetos. La violación de estas invariantes puede causar que el código ECMAScript se comporte de manera impredecible y crear problemas de seguridad. Aun así, la violación de estas invariantes nunca debe comprometer la seguridad de memoria de una implementación. 

Una implementación no debe permitir esquivar estas invariantes de ninguna manera, como por ejemplo proporcionando interfaces alternativas que implementen la funcionalidad de los métodos internos esenciales sin imponer sus invariantes. 

Definiciones: 

- El *target* de un método interno es el objeto sobre el cual se invoca el método interno.
- Un target es *non-extensible* si se ha observado que su método interno [[IsExtensible]] devuelve `false`, o si [[PreventExtensions]] devuelve `true`.
- Una propiedad *non-existent* es una propiedad que no existe como propiedad propia en un target non-extensible.
- Todas las referencias a *SameValue* están de acuerdo a la definición del algoritmo [**SameValue**][6-008].

__[[GetPrototypeOf]] ()__

- El tipo del valor devuelto debe ser `object` o `Null`.
- Si el target es *non-extensible*, y [[GetPrototypeOf]] devuelve un valor *v*, entonces toda llamada futura a [[GetPrototypeOf]] debería devolver **Same Value** en *v*.

> NOTA 1: La cadena de prototipo de un objeto debería tener un largo finito (esto es, comenzando en cualquier objeto, la aplicación recursiva del método interno [[GetPrototypeOf]] a su resultado debería eventualmente conducir a un valor `null`). Sin embargo, este requisito no es imponible al nivel invariante de un objeto si la cadena de prototipo incluye cualquier objeto exótico que no usa la definición de objetos ordinarios para [[GetPrototypeOf]]. Tal cadena de prototipo circular puede resultar en loops infinitos cuando se accede a las propiedades del objeto.

__[[SetPrototypeOf]] (*V*)__

- El tipo del valor devuelto debe ser `Boolean`.
- Si el target es *non-extensible*, [[SetPrototype]] debe devolver **false**, a no ser que *V* sea **SameValue** que el valor del [[GetPrototypeOf]] del target observado.

__[[IsExtensible]] ()__

- El tipo del valor devuelto debe ser `Boolean`.
- Si [[IsExtensible]] devuelve **false**, todas las llamadas a [[IsExtensible]] en el target deben devolver **false**.

__[[PreventExtensions]] ()__

- El tipo del valor devuelto debe ser `Boolean`.
- Si [[PreventExtensions]] devuelve **true**, todas las futuras llamadas a [[IsExtensible]] en el target deben devolver **false** y el target se considerará *non-extensible*.

__[[GetOwnProperty]] (*P*)__

- El tipo del valor devuelto debe ser o `Undefined` o [_Property Descriptor_][6-009].
- Si el tipo del valor devuelto es *Property Descriptor*, el valor devuelto debe ser un property descriptor completo. [(vea 6.2.5.6)][6-010]. 
- Si una propiedad *P* es descrita como una propiedad de datos con Desc.[[Value]] igual a v, y Desc.[[Writable]] y Desc.[[Configurable]] ambos falsos, entonces el *SameValue* debe ser devuelto para el atributo de la propiedad Desc.[[Value]] en todas las llamadas futuras a [[GetOwnProperty]] (P).
- Si otros atributos de P distintos que [[Writable]] pueden cambiar en el tiempo, o si la propiedad pudiera desaparecer, entonces el atributo de P [[Configurable]] debe ser true.
- Si el atributo [[Writable]] puede cambiar de false a true, entonces el atributo [[Configurable]] debe ser true.
- Si el target es *non-extensible* y P es non-existent, entonces todas las futuras llamadas a [[GetOwnProperty]] (P) en el target deben describir P como non-existent (o sea, [[GetOwnProperty]] (P) debe devolver undefined).

> NOTA 2: Como consecuencia del tercer invariante, si una propiedad es descrita como una propiedad de datos y esta puede devolver valores diferentes en el tiempo, entonces uno o ambos atributos Desc.[[Writable]] y Desc.[[Configurable]] deben devolver true incluso si ningún mecanismo para cambiar el valor es expuesto a través de otro método interno.

__[[DefineOwnProperty]] (*P, Desc*)__

- El tipo del valor devuelto debe ser `Boolean`.
- [[DefineOwnProperty]] debe devolver false si P se ha observado previamente como una propiedad propia non-configurable del target, a menos que: 
    - P sea una propiedad propia de datos non-configurable writable. Una propiedad de datos non-configurable writable puede ser cambiada en una propiedad de datos non-configurable, non-writable.
    - Todos los atributos en Desc son el **SameValue** de los atributos de P.
- [[DefineOwnProperty]] (P, Desc) debe devolver false si el target es non-extensible y P es una propiedad propia non-existent. Esto es, un objeto target non-extensible no puede ser extendido con nuevas propiedades.

__[[HasProperty]] (*P*)__

- El tipo del valor devuelto debe ser `Boolean`.
- Si P fue observado previamente como un dato non-configurable o un propiedad de acceso propia del target, [[HasProperty]] debe devolver true.

__[[Get]] (*P, Receiver*)__

- Si P fue observado previamente como una propiedad propia de datos non-configurable, non-writable del target con valor *v*, entonces [[Get]] debe devolver **SameValue**.
- Si P fue observado previamente como una propiedad propia de acceso non-configurable del target cuyo atributo [[Get]] es undefined, la operación [[Get]] debe devolver undefined.

__[[Set]] (*P, V, Receiver*)__

- El tipo del valor devuelto debe ser `Boolean`.
- Si P fue observado previamente como una propiedad propia de datos non-writable del target, entonces [[Set]] debe devolver false a menos que V sea **SameValue** que el atributo [[Value]] de P.
- Si P fue observado previamente como una propiedad propia de acceso del target cuyo atributo [[Set]] es undefined, la operación [[Set]] debe devolver false.

__[[Delete]] (*P*)__

- El tipo del valor devuelto debe ser `Boolean`.
- Si P fue observado previamente como una propiedad propia de acceso non-configurable del target, [[Delete]] debe devolver false.

__[[OwnPropertyKeys]] ()__

- El valor devuelto debe ser una [**List**][6-011].
- El tipo de cada elemento de la List devuelta debe ser `String` o `Symbol`.
- La List devuelta debe contener al menos las claves de todas las propiedades propias non-configurables que han sido previamente observadas. 
- Si el objeto es non-extensible, la List devuelta debe contener solo las claves de todas las propiedades propias del objeto que es observable utilizando [[GetOwnProperty]].

__[[Construct]] ()__

- El tipo del valor devuelto debe ser `Object`.

#### 6.1.7.4 Objetos Intrínsecos bien-conocidos
<span class="original-title">Well-Known Intrinsic Objects</span>

Los objeto bien-conocidos intrínsecos, son objetos que están explícitamente referenciados por los algoritmos de esta especificación, los cuales usualmente tienen identidades especificas a un [realm][6-012]. A menos que se especifique lo contrario, cada objeto intrínseco en realidad corresponde a un conjunto de objetos similares, uno por *realm*.

Dentro de esta especificación, una referencia del tipo _%nombre%_ significa un objeto intrínseco, asociado con el correspondiente *realm*, según su nombre. La determinación del *realm* actual y sus intrínsecos es descrita en [8.3][6-013]. Los objetos intrínsecos bien-conocidos están listados en la siguiente tabla: 

> [Tabla 7: Objetos intrínsecos bien conocidos][6-014]

|Nombre Intrínseco|Nombre Global|Asociación en el Lenguaje ECMAScript|
|-----------------|-------------|------------------------------------|
|[%Array%][6-015]|Array|[()][6-015]|
|[%ArrayBuffer%][6-015]|ArrayBuffer|[()][6-015]|
|[%ArrayBufferPrototype%][6-015]|ArrayBuffer.prototype|[()][6-015]|
|[%ArrayIteratorPrototype%][6-015]||[()][6-015]|
|[%ArrayPrototype%][6-015]|Array.prototype|[()][6-015]|
|[%ArrayProto_values%][6-015]|Array.prototype.values|[()][6-015]|
|[%AsyncFunction%][6-015]||[()][6-015]|
|[%AsyncFunctionPrototype%][6-015]||[()][6-015]|
|[%Atomics%][6-015]|Atomics|[()][6-015]|
|[%Boolean%][6-015]|Boolean|[()][6-015]|
|[%BooleanPrototype%][6-015]|Boolean.Prototype|[()][6-015]|
|[%DataView%][6-015]|DataView|[()][6-015]|
|[%DataViewPrototype%][6-015]|DataView.prototype|[()][6-015]|
|[%Date%][6-015]|Date|[()][6-015]|
|[%DatePrototype%][6-015]|Date.prototype|[()][6-015]|
|[%decodeURI%][6-015]|decodeURI|[()][6-015]|
|[%decodeURIComponent%][6-015]|decodeURIComponent|[()][6-015]|
|[%encodeURI%][6-015]|encodeURI|[()][6-015]|
|[%encodeURIComponent%][6-015]|encodeURIComponent|[()][6-015]|
|[%Error%][6-015]|Error|[()][6-015]|
|[%ErrorPrototype%][6-015]|Error.prototype|[()][6-015]|
|[%eval%][6-015]|eval|[()][6-015]|
|[%EvalError%][6-015]|EvalError|[()][6-015]|
|[%EvalErrorPrototype%][6-015]|EvalError.prototype|[()][6-015]|
|[%Float32Array%][6-015]|Float32Array|[()][6-015]|
|[%Float32ArrayPrototype%][6-015]|Float32Array.prototype|[()][6-015]|
|[%Float64Array%][6-015]|Float64Array|[()][6-015]|
|[%Float64ArrayPrototype%][6-015]|Float64.prototype|[()][6-015]|
|[%Function%][6-015]|Function|[()][6-015]|
|[%FunctionPrototype%][6-015]|Function.prototype|[()][6-015]|
|[%Generator%][6-015]||[()][6-015]|
|[%GeneratorFunction%][6-015]||[()][6-015]|
|[%GeneratorPrototype%][6-015]||[()][6-015]|
|[%Int8Array%][6-015]|Int8Array|[()][6-015]|
|[%Int8ArrayPrototype%][6-015]|Int8Array.prototype|[()][6-015]|
|[%Int16Array%][6-015]|int16Array|[()][6-015]|
|[%Int16ArrayPrototype%][6-015]|Int16Array.prototype|[()][6-015]|
|[%Int32Array%][6-015]|Int32Array|[()][6-015]|
|[%Int32ArrayPrototype%][6-015]|Int32Array.prototype|[()][6-015]|
|[%isFinite%][6-015]|isFinite|[()][6-015]|
|[%isNaN%][6-015]|isNaN|[()][6-015]|
|[%IteratorPrototype%][6-015]||[()][6-015]|
|[%JSON%][6-015]|JSON|[()][6-015]|
|[%Map%][6-015]|Map|[()][6-015]|
|[%MapIteratorPrototype%][6-015]||[()][6-015]|
|[%MapPrototype%][6-015]|Map.prototype|[()][6-015]|
|[%Math%][6-015]|Math|[()][6-015]|
|[%Number%][6-015]|Number|[()][6-015]|6-015
|[%NumberPrototype%][6-015]|Number.prototype|[()][6-015]|
|[%Object%][6-015]|Object|[()][6-015]|
|[%ObjectPrototype%][6-015]|Object.prototype|[()][6-015]|
|[%ObjProto_toString%][6-015]|Object.prototype.toString|[()][6-015]|
|[%ObjProto_valueOf%][6-015]|Object.prototype.valueOf|[()][6-015]| 
|[%parseFloat%][6-015]|parseFloat|[()][6-015]|
|[%parseInt%][6-015]|parseInt|[()][6-015]|
|[%Promise%][6-015]|Promise|[()][6-015]|
|[%PromisePrototype%][6-015]|Promise.prototype|[()][6-015]|
|[%Proxy%][6-015]|Proxy|[()][6-015]|
|[%RangeError%][6-015]|RangeError|[()][6-015]|
|[%RangeErrorPrototype%][6-015]|RangeError.prototype|[()][6-015]|
|[%ReferenceError%][6-015]|ReferenceError|[()][6-015]|
|[%ReferenceErrorPrototype%][6-015]|ReferenceError.prototype|[()][6-015]|
|[%Reflect%][6-015]|Reflect|[()][6-015]|
|[%RegExp%][6-015]|RegExp|[()][6-015]|
|[%RegExpPrototype%][6-015]|RegExp.prototype|[()][6-015]|
|[%Set%][6-015]|Set|[()][6-015]|
|[%SetIteratorPrototype%][6-015]||[()][6-015]|
|[%SetPrototype%][6-015]|Set.prototype|[()][6-015]|
|[%SharedArrayBuffer%][6-015]|SharedArrayBuffer|[()][6-015]|
|[%SharedArrayBufferPrototype%][6-015]|SharedArrayBuffer.prototype|[()][6-015]|
|[%StringPrototype%][6-015]|String|[()][6-015]|
|[%Symbol%][6-015]||[()][6-015]|
|[%SymbolPrototype%][6-015]|String.prototype|[()][6-015]|
|[%SyntaxError%][6-015]|Symbol|[()][6-015]|
|[%SyntaxErrorPrototype%][6-015]|Symbo.prototype|[()][6-015]|
|[%ThrowTypeError%][6-015]|SyntaxError|[()][6-015]|
|[%TypedArray%][6-015]|SyntaxError.prototype|[()][6-015]|
|[%TypedArrayPrototype%][6-015]||[()][6-015]|
|[%TypeError%][6-015]|TypeError|[()][6-015]|
|[%TypeErrorPrototype%][6-015]|TypeError.prototype|[()][6-015]|
|[%Uint8Array%][6-015]|Uint8Array|[()][6-015]|
|[%Uint8ArrayPrototype%][6-015]|Uint8Array.prototype|[()][6-015]|
|[%Uint8ClampedArray%][6-015]|Uint8ClampedArray|[()][6-015]|
|[%Uint8ClampedArrayPrototype%][6-015]|Uint8ClampedArray.prototype|[()][6-015]|
|[%Uint16Array%][6-015]|Uint16Array|[()][6-015]|
|[%Uint16ArrayPrototype%][6-015]|Uint16Array.prototype|[()][6-015]|
|[%Uint32Array%][6-015]|Uint32Array|[()][6-015]|
|[%Uint32ArrayPrototype%][6-015]|Uint32Array.prototype|[()][6-015]|
|[%URIError%][6-015]|URIError|[()][6-015]|
|[%URIErrorPrototype%][6-015]|URIError.prototype|[()][6-015]|
|[%WeakMap%][6-015]|WeakMap|[()][6-015]|
|[%WeakMapPrototype%][6-015]|WeakMap.prototype|[()][6-015]|
|[%WeakSet%][6-015]|WeakSet|[()][6-015]|
|[%WeakSetPrototype%][6-015]|WeakSet.prototype|[()][6-015]|


|[%%][]||[()][]|
|[%%][]||[()][]|
|[%%][]||[()][]|
|[%%][]||[()][]|
|[%%][]||[()][]|
|[%%][]||[()][]|
|[%%][]||[()][]|

[6-001]: www.aca-va-una-explicacion-sobre-lo-que-es-locale.com
[6-006]: www.aca-una-referencia-cruzada-a-la-tabla-5.com
[6-007]: www.aca-una-referencia-cruzada-a-la-tabla-6.com
[6-008]: www.referencia-cruzada-a-7-2-9.com
[6-009]: www.referencia-cruzada-a-6-2-5.com
[6-010]: www.referencia-cruzada-a-6-2-5-6.com
[6-011]: www.referencia-cruzada-a-6-2-1.com
[6-012]: www.referencia-cruzada-a-8-2.com
[6-013]: www.referencia-cruzada-a-8-3.com
[6-014]: www.referencia-cruzada-a-tabla-7.com

[6-015]: www.referencia-cruzada-a-8-3.com
[6-016]: www.referencia-cruzada-a-8-3.com
[6-017]: www.referencia-cruzada-a-8-3.com
[6-018]: www.referencia-cruzada-a-8-3.com
[6-019]: www.referencia-cruzada-a-8-3.com
[6-020]: www.referencia-cruzada-a-8-3.com
[6-021]: www.referencia-cruzada-a-8-3.com
[6-022]: www.referencia-cruzada-a-8-3.com
[6-023]: www.referencia-cruzada-a-8-3.com
[6-024]: www.referencia-cruzada-a-8-3.com
[6-025]: www.referencia-cruzada-a-8-3.com
[6-026]: www.referencia-cruzada-a-8-3.com
[6-027]: www.referencia-cruzada-a-8-3.com
[6-028]: www.referencia-cruzada-a-8-3.com
[6-029]: www.referencia-cruzada-a-8-3.com
[6-030]: www.referencia-cruzada-a-8-3.com

[6-013]: www.referencia-cruzada-a-8-3.com
[6-013]: www.referencia-cruzada-a-8-3.com
[6-013]: www.referencia-cruzada-a-8-3.com
[6-013]: www.referencia-cruzada-a-8-3.com
[6-013]: www.referencia-cruzada-a-8-3.com
[6-013]: www.referencia-cruzada-a-8-3.com
[6-013]: www.referencia-cruzada-a-8-3.com
[6-013]: www.referencia-cruzada-a-8-3.com
[6-013]: www.referencia-cruzada-a-8-3.com
[6-013]: www.referencia-cruzada-a-8-3.com
[6-013]: www.referencia-cruzada-a-8-3.com
[6-013]: www.referencia-cruzada-a-8-3.com
[6-013]: www.referencia-cruzada-a-8-3.com
[6-013]: www.referencia-cruzada-a-8-3.com
[6-013]: www.referencia-cruzada-a-8-3.com
[6-013]: www.referencia-cruzada-a-8-3.com
[6-013]: www.referencia-cruzada-a-8-3.com
[6-013]: www.referencia-cruzada-a-8-3.com
[6-013]: www.referencia-cruzada-a-8-3.com
[6-013]: www.referencia-cruzada-a-8-3.com
[6-013]: www.referencia-cruzada-a-8-3.com
[6-013]: www.referencia-cruzada-a-8-3.com
[6-013]: www.referencia-cruzada-a-8-3.com
[6-013]: www.referencia-cruzada-a-8-3.com
[6-013]: www.referencia-cruzada-a-8-3.com
[6-013]: www.referencia-cruzada-a-8-3.com
[6-013]: www.referencia-cruzada-a-8-3.com
[6-013]: www.referencia-cruzada-a-8-3.com
[6-013]: www.referencia-cruzada-a-8-3.com
[6-013]: www.referencia-cruzada-a-8-3.com
[6-013]: www.referencia-cruzada-a-8-3.com
[6-013]: www.referencia-cruzada-a-8-3.com
[6-013]: www.referencia-cruzada-a-8-3.com
[6-013]: www.referencia-cruzada-a-8-3.com
[6-013]: www.referencia-cruzada-a-8-3.com
[6-013]: www.referencia-cruzada-a-8-3.com
[6-013]: www.referencia-cruzada-a-8-3.com
[6-013]: www.referencia-cruzada-a-8-3.com
[6-013]: www.referencia-cruzada-a-8-3.com
[6-013]: www.referencia-cruzada-a-8-3.com
[6-013]: www.referencia-cruzada-a-8-3.com
[6-013]: www.referencia-cruzada-a-8-3.com
[6-013]: www.referencia-cruzada-a-8-3.com
[6-013]: www.referencia-cruzada-a-8-3.com
[6-013]: www.referencia-cruzada-a-8-3.com
[6-013]: www.referencia-cruzada-a-8-3.com
[6-013]: www.referencia-cruzada-a-8-3.com
[6-013]: www.referencia-cruzada-a-8-3.com
[6-013]: www.referencia-cruzada-a-8-3.com
[6-013]: www.referencia-cruzada-a-8-3.com
[6-013]: www.referencia-cruzada-a-8-3.com
[6-013]: www.referencia-cruzada-a-8-3.com
[6-013]: www.referencia-cruzada-a-8-3.com
[6-013]: www.referencia-cruzada-a-8-3.com
[6-013]: www.referencia-cruzada-a-8-3.com
[6-013]: www.referencia-cruzada-a-8-3.com
[6-013]: www.referencia-cruzada-a-8-3.com
[6-013]: www.referencia-cruzada-a-8-3.com
[6-013]: www.referencia-cruzada-a-8-3.com
[6-013]: www.referencia-cruzada-a-8-3.com
[6-013]: www.referencia-cruzada-a-8-3.com
[6-013]: www.referencia-cruzada-a-8-3.com
[6-013]: www.referencia-cruzada-a-8-3.com
[6-013]: www.referencia-cruzada-a-8-3.com
[6-013]: www.referencia-cruzada-a-8-3.com
[6-013]: www.referencia-cruzada-a-8-3.com
[6-013]: www.referencia-cruzada-a-8-3.com
[6-013]: www.referencia-cruzada-a-8-3.com
[6-013]: www.referencia-cruzada-a-8-3.com
[6-013]: www.referencia-cruzada-a-8-3.com
[6-013]: www.referencia-cruzada-a-8-3.com
[6-013]: www.referencia-cruzada-a-8-3.com
[6-013]: www.referencia-cruzada-a-8-3.com
[6-013]: www.referencia-cruzada-a-8-3.com
[6-013]: www.referencia-cruzada-a-8-3.com
