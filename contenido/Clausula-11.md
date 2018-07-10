# 11 Lenguaje ECMAScript: Gramática Léxica
<span class="original title">ECMASCript Language: Lexical Grammar</span>

El texto fuente de un [*Script*][11-001] o [*Module*][11-002] ECMAScript primero es convertido a una secuencia de elementos de entrada, como son los tokens, finalizadores de línea, comentarios o espacios en blanco. El texto fuente es escaneado de izquierda a derecha, tomando repetidamente la secuencia de puntos de código más larga posible como siguiente elemento de entrada.

Hay varias situaciones donde la identificación de los elementos de léxicos de entrada es sensible al contexto de la gramática sintáctica que está consumiendo los elementos de entrada. Esto requiere múltiples símbolos objetivo (*goal symbols*) para la gramática léxica. El símbolo objetivo *InputElementRegExpOrTemplateTail* (ver apartado "Sintaxis" más abajo) es usado en los contextos de la gramática sintáctica donde un [*RegularExpressionLiteral*][11-003], un [*TemplateMiddle*][11-004] o un [*TemplateTail*][11-004] es permitido. El [simbolo objetive][11-005]<sub>goal symbol</sub> *InputElementRegExp* (ver màs abajo) es usado en todos los contextos gramaticaless sintàcticas donde un [*RegularExpressionLiteral*][11-003] es permitido, pero ni un [*TemplateMiddle*][11-004] o un [*TemplateTail*][11-004] son permitidos. El sìmbolo objetivo *InputElementTemplateTail* (ver màs abajo "Sintaxis) es usado en todos los contextos gramaticales sintàctica donde un [*TemplateMiddle*][11-004] o un [*TemplateTail*][11-004] son permitidos pero un [*RegularExpressionLiteral*][11-003] no lo es. En todos los otros contextos, *InputElementDiv* (ver abajo, 'Sintaxis') es usado como el [simbolo objetive][11-005] lèxico.

> NOTA: El uso de mùltiples objetivos lèxicos asegura que no haya ambigüedades lèxicas que pudieran afectar la inserciòn automàtica de punto y coma. Por ejemplo, no hay contextos gramaticales sintàcticos en los que se permitan una '*leading division*' o una '*division-assignment*' y un 'leading *RegularExpressionLiteral*' al mismo tiempo. Esto no es afectado por la inserciòn del punto y coma [(vea 11.9)][11-006] en ejemplos como los que siguen: 
> ````
> a = b
> / hi / g.exec(c).map(d);
> ````
> donde el primer punto de código no-espacio-en-blanco, no-comentario, después de [*LineTerminator*][11-007] es U+002F (SOLIDUS) y el contexto sintáctico permite division o asignación-división, no hay ningún punto y coma insertado en el [*LineTerminator*][11-007]. Esto es, el ejemplo de arriba es interpretado igualmente de esta manera:
> ```` 
> a = b / hi / g.exec(c).map(d);
>````

Sintaxis: 



----


[11-007]: www.enlace-a-11-3.com
[11-006]: www.enlace-a-11-9.com
[11-005]: www.enlace-a-5-1-1.com
[11-004]: www.enlace-a-11-8-6.com
[11-003]: www.enlace-a-11-8-5.com
[11-002]: www.enlace-a-15-2.com
[11-001]: www-enlace-a-15-1.com