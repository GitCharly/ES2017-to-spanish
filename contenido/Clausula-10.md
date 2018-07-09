# Lenguaje ECMAScript - Código fuente
<span class="original-title">ECMAScript Language: Source Code</span>

## 10.1 Texto fuente
<span class="original-title">Source Text</span>

Síntaxis

> *SourceCharacter* ::
> > `any Unicode code point`

El código ECMAScript es expresado utilizando Unicode. Un texto fuente ECMAScript es una secuencia de puntos de código (Unicode point code). Todos los valores de puntos de código Unicode desde U+0000 hasta U+10FFFF, incluyendo los puntos de código sustitutos, pueden aparecer en el texto fuente ahí donde las gramaticas de ECMAScript lo permitan. El verdaderas codificaciones usadas para almacenar e intercambiar texto fuente ECMAScript no es relevante a esta especificación. Independiente de la codificación externa de texto fuente, una implementación ECMAScript procesa el texto fuente como si fuera una secuencia equivalente de valores *SourceCharacter*, cada *SourceCharacter* siendo un punto de código Unicode. Las implementaciones conformes de ECMAScrit no requieren realizar ninguna normalización del texto fuente, ni comportarse como si estuvieran ejecutando la normalización del texto fuente. 

Los componentes de una secuencia combinada de caracteres son tratados como puntos de código Unicode individuales, aun cuando el usuario pueda pensar en la secuencia completa como un solo caracter.

> NOTA: en los `string literals`, `regexp literals`, `template literals`, e `identifiers`, cualquier punto de código Unicode puede ser expresado usando sencuencias de escape que expresan explícitamente un valor de un punto de código numérico. En un comentario, tal secuencia de escape es efectivamente ignorada como parte del comentario.  
> 
> ECMAScript se diferencia del lenguaje de programación Java en el comportamiento de las secuencias de escape Unicode. En un programa Java, si la secuencia de escape Unicode __\u000A__, por ejemplo, aparece dentro de un comentario de una sola línea, es interpretado como un finalizador de línea (el punto de código Unicode U+000A es 'LINE FEED (LF)') y por lo tanto el próximo punto de código no es parte del comentario. De manera similar, si la secuencia de escape Unicode __\u000A__ aparece dentro de una `string literal` en un programa Java, es también interpretado como un finalizador de línea, que no es permitido dentro de una `string literal` -uno debe escribir __\n__ en vez de __\u000A__ para provocar un salto de linea (LINE FEED (FD)) que se considere parte del valor `String` de una `string literal`. En un programa ECMAScript, una secuencia de escape Unicode que aparezca dentro de un comentario nunca es interpretada y por lo tanto, no puede contribuir a terminar el comentario. De manera similar, una secuencia de escape Unicode que ocurra dentro de una `string literal` en un programa ECMAScript siempre contribuye al valor literal, y nunca es interpretada como un finalizador de línea o como un punto de código que pueda terminar una `string literal`. 

### 10.1.1 Semánticas estáticas: codificación UTF16 (*cp*)
<span class="original-title">Static Semantics: UTF16Encoding (*cp*)</span>

La codificación UTF16 de un valor de punto de código numérico, *cp*, está determinada de la siguiente manera: 

1. [Assert][10-001]: 0 <= *cp* <= 0x10FFFF. 
2. If *cp* <= 0xFFFF, return *cp*.
3. Let *cu1* be [*floor*][10-002]((*cp* - 0x10000)) / 0x400 + 0xD800.
4. Let *cu2* be ((*cp* - 0x10000) [modulo][10-002] 0x400) + 0xDC00.
5. Return the code unit sequence consisting of *cu1* followed by *cu2*.

### 10.1.2 Semánticas estáticas: decodificación UTF16 (*lead*, *trail*)
<span class="original-title">Static Semantics: UTF16Decode (*lead, trail*)</span>

Dos unidades de código, *lead* y *trail*, que forman un [surrogate pair][10-003]<sub>(par sustituto)</sub> UTF16 son convertidos a un punto de códiog que realiza los siguiente pasos: 

1. [Assert][10-001]: *lead* is a [leading surrogate][10-003] and *trail* is a [trailing surrogate][10-003].
2. Let *cp* be (*lead* - 0xD800) x 0x400 + (*trail* - 0xDC00) + 0x10000.
3. Return the code point *cp*.

## 10.2 Tipos de codigo fuente
<span class="original-title">Types of Source Code</span>

Hay cuatro tipos de código ECMAScript:

- *Global code* es texto fuente que es tratado como un *Script* ECMAScript. el código global de un *Script* particular no incluye ningún texto fuente que se 'parsea' como parte de una [*FunctionDeclaration*][10-004], [*FunctionExpression*][10-004], [*GeneratorDeclaration*][10-005], [*GeneratorExpression*][10-005], [*AsyncFunctionDeclaration*][10-006], [*AsyncFunctionExpression*][10-006], [*AsyncGeneratorDeclaration*][10-007], [*AsyncGeneratorExpression*][10-007], [*MethodDefinition*][10-008], [*ArrowFunction*][10-009], [*AsyncArrowFunction*][10-010], [*ClassDeclaration*][10-011], o [*ClassExpression*][10-011].
- *Eval code* es el texto fuente suministrado a la función incorporada **eval**. Más precisamente, si el parámetro a la función incorporada **eval** es una String, esta es tratada como un *Script* ECMAScript. El código eval para una llamada particular de **eval** es la parte de código global de ese *Script*.
- *Function Code* es un texto fuente que es 'parseado'<sub>analizado</sub> para suministrar el valor de las '*ranuras internas*' [[ECMASCriptCode]] y [[FormalParameters]] (vea [9.2][10-012]) de una [function object][10-013] ECMAScript. El *function code* de una función particular ECMAScript no incluye ningún texto fuente que sea parseado como la *function code* de un [*FunctionDeclaration*][10-004], [*FunctionExpression*][10-004], [*GeneratorDeclaration*][10-005], [*GeneratorExpression*][10-005], [*AsyncFunctionDeclaration*][10-006], [*AsyncFunctionExpression*][10-006], [*AsyncGeneratorDeclaration*][10-007], [*AsyncGeneratorExpression*][10-007], [*MethodDefinition*][10-008], [*ArrowFunction*][10-009], [*AsyncArrowFunction*][10-010], [*ClassDeclaration*][10-011], o [*ClassExpression*][10-011] anidado.
- *Module code* es el texto fuente que es el código suministrado como un [*ModuleBody*][10-014]. es el código que se evalúa directamente cuando un módulo es inicializado. El *module code* de un módulo particular no incluye el texto fuente a ser analizado de ningun [*FunctionDeclaration*][10-004], [*FunctionExpression*][10-004], [*GeneratorDeclaration*][10-005], [*GeneratorExpression*][10-005], [*AsyncFunctionDeclaration*][10-006], [*AsyncFunctionExpression*][10-006], [*AsyncGeneratorDeclaration*][10-007], [*AsyncGeneratorExpression*][10-007], [*MethodDefinition*][10-008], [*ArrowFunction*][10-009], [*AsyncArrowFunction*][10-010], [*ClassDeclaration*][10-011], o [*ClassExpression*][10-011] que esté anidado.

> NOTA: *Function code* es generalmente provisto como el cuerpo de las 'Function Definitions' [(14.1)][10-004], 'Arrow Function Definitions' [(14.2)][10-009], 'Method Definitions' [(14.3)][10-008], 'Generator Function Definitions' [(14.4)][10-005], 'Async Function Definitions' [(14.7)][10-006], 'Asyn Generator Function Definitions' [(14.5)][10-007],  y 'Asyn Arrow Functions' [(14.8)][10-010]. *Funtion code* también es derivado de los argumentos del [constructor][10-013] de **Function** [(19.2.1.1)][10-015], de **GeneratorFunction** [(25.2.1.1)][10-016] y de **AsyncFunction** [(25.7.1.1)][10-017]. 




----
[10-017]: www.enlace-a-25-7-1-1.com
[10-016]: www.enlace-a-25-2-1-1.com
[10-015]: www.enlace-a-19-2-1-1.com
[10-014]: www.enlace-a-15-2.com
[10-013]: www.enlace-a-tabla-6.com
[10-012]: www.enlace-a-9-2.com
[10-011]: www.enlace-a-14-6.com
[10-010]: www.enlace-a-14-8.com
[10-009]: www.enlace-a-14-2.com
[10-008]: www-enlace-a-14-3.com
[10-007]: www.enlace-a-14-5.com
[10-006]: www.enlace-a-14-7.com
[10-005]: www.enlace-a-14-4.com
[10-004]: www.enlace-a-14-1.com
[10-003]: www.enlace-a-6-1-4.com
[10-002]: www.enlace-a-5-2-5.com
[10-001]: www.enlace-a-5-2.com