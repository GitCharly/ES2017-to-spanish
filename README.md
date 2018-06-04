#  Notas a la traducción del estándar ECMA-262 8º edición. Junio 2018

Siendo 1º de junio, intento por segunda vez la traducción de la especificación del lenguaje ECMAScript, a través de su estándar ECMA-262 8º edición, alias ECMAScript 2017 o ES8.

Las herramientas utilizadas serán VSCode como editor de Markdown, con el plugin Markdown PDF para la salida hacia HTML. 

VSCode utiliza el sabor "CommonMarkdown" para todo lo referente a la interpretación del texto plano.

Debido a que "algo pasó" y fue eliminado el contenido completo del archivo markdown original que contenía todo lo avanzado, creo que esta vez intentaré crear una archivo índice con el arbol de contenidos, y adaptar en el html los enlaces para hacerlos calzar con los archivos correspondientes cada uno a una cláusula completa. 

Si algunas cláusulas merecen estar en más de un archivo por su largo, es algo que decidiré luego.


## 21.1 String Objects
### 21.1.1 The String Constructor
#### 21.1.1.1 String ( value )
### 21.1.2 Properties of the String Constructor
#### 21.1.2.1 String.fromCharCode ( ...codeUnits )
#### 21.1.2.2 String.fromCodePoint ( ...codePoints )
#### 21.1.2.3 String.prototype
#### 21.1.2.4 String.raw ( template, ...substitutions )
### 21.1.3 Properties of the String Prototype Object
#### 21.1.3.1 String.prototype.charAt ( pos )
#### 21.1.3.2 String.prototype.charCodeAt ( pos )
#### 21.1.3.3 String.prototype.codePointAt ( pos )
#### 21.1.3.4 String.prototype.concat ( ...args )
#### 21.1.3.5 String.prototype.constructor
#### 21.1.3.6 String.prototype.endsWith ( searchString [ , endPosition ] )
#### 21.1.3.7 String.prototype.includes ( searchString [ , position ] )
#### 21.1.3.8 String.prototype.indexOf ( searchString [ , position ] )
#### 21.1.3.9 String.prototype.lastIndexOf ( searchString [ , position ] )
#### 21.1.3.10 String.prototype.localeCompare ( that [ , reserved1 [ , reserved2 ] ] )
#### 21.1.3.11 String.prototype.match ( regexp )
#### 21.1.3.12 String.prototype.normalize ( [ form ] )
#### 21.1.3.13 String.prototype.padEnd( maxLength [ , fillString ] )
#### 21.1.3.14 String.prototype.padStart( maxLength [ , fillString ] )
#### 21.1.3.15 String.prototype.repeat ( count )
#### 21.1.3.16 String.prototype.replace ( searchValue, replaceValue )
##### 21.1.3.16.1 RS: GetSubstitution( matched, str, position, captures, replacement )
#### 21.1.3.17 String.prototype.search ( regexp )
#### 21.1.3.18 String.prototype.slice ( start, end )
#### 21.1.3.19 String.prototype.split ( separator, limit )
##### 21.1.3.19.1 RS: SplitMatch ( S, q, R )
#### 21.1.3.20 String.prototype.startsWith ( searchString [ , position ] )
#### 21.1.3.21 String.prototype.substring ( start, end )
#### 21.1.3.22 String.prototype.toLocaleLowerCase ( [ reserved1 [ , reserved2 ] ] )
#### 21.1.3.23 String.prototype.toLocaleUpperCase ( [ reserved1 [ , reserved2 ] ] )
#### 21.1.3.24 String.prototype.toLowerCase ( )
#### 21.1.3.25 String.prototype.toString ( )
#### 21.1.3.26 String.prototype.toUpperCase ( )
#### 21.1.3.27 String.prototype.trim ( )
#### 21.1.3.28 String.prototype.valueOf ( )
#### 21.1.3.29 String.prototype [ @@iterator ] ( )
### 21.1.4 Properties of String Instances
#### 21.1.4.1 length
### 21.1.5 String Iterator Objects
#### 21.1.5.1 CreateStringIterator ( string )
#### 21.1.5.2 The %StringIteratorPrototype% Object
##### 21.1.5.2.1 %StringIteratorPrototype%.next ( )
##### 21.1.5.2.2 %StringIteratorPrototype% [ @@toStringTag ]
#### 21.1.5.3 Properties of String Iterator Instances
## 21.2 RegExp (Regular Expression) Objects
### 21.2.1 Patterns
#### 21.2.1.1 SS: Early Errors
### 21.2.2 Pattern Semantics
#### 21.2.2.1 Notation
#### 21.2.2.2 Pattern
#### 21.2.2.3 Disjunction
#### 21.2.2.4 Alternative
#### 21.2.2.5 Term
#### 21.2.2.5.1 RS: RepeatMatcher ( m, min, max, greedy, x, c, parenIndex, parenCount )
#### 21.2.2.6 Assertion
##### 21.2.2.6.1 RS: WordCharacters ( )
##### 21.2.2.6.2 RS: IsWordChar ( e )
#### 21.2.2.7 Quantifier
#### 21.2.2.8 Atom
##### 21.2.2.8.1 RS: CharacterSetMatcher ( A, invert )
##### 21.2.2.8.2 RS: Canonicalize ( ch )
#### 21.2.2.9 AtomEscape
#### 21.2.2.10 CharacterEscape
#### 21.2.2.11 DecimalEscape
#### 21.2.2.12 CharacterClassEscape
#### 21.2.2.13 CharacterClass
#### 21.2.2.14 ClassRanges
#### 21.2.2.15 NonemptyClassRanges
##### 21.2.2.15.1 RS: CharacterRange ( A, B )
#### 21.2.2.16 NonemptyClassRangesNoDash
#### 21.2.2.17 ClassAtom
#### 21.2.2.18 ClassAtomNoDash
#### 21.2.2.19 ClassEscape
### 21.2.3 The RegExp Constructor
#### 21.2.3.1 RegExp ( pattern, flags )
#### 21.2.3.2 Abstract Operations for the RegExp Constructor
##### 21.2.3.2.1 RS: RegExpAlloc ( newTarget )
##### 21.2.3.2.2 RS: RegExpInitialize ( obj, pattern, flags )
##### 21.2.3.2.3 RS: RegExpCreate ( P, F )
##### 21.2.3.2.4 RS: EscapeRegExpPattern ( P, F )
### 21.2.4 Properties of the RegExp Constructor
#### 21.2.4.1 RegExp.prototype
#### 21.2.4.2 get RegExp [ @@species ]
### 21.2.5 Properties of the RegExp Prototype Object
#### 21.2.5.1 RegExp.prototype.constructor
#### 21.2.5.2 RegExp.prototype.exec ( string )
#### 21.2.5.3 get RegExp.prototype.flags
#### 21.2.5.4 get RegExp.prototype.global
#### 21.2.5.5 get RegExp.prototype.ignoreCase
#### 21.2.5.6 RegExp.prototype [ @@match ] ( string )
#### 21.2.5.7 get RegExp.prototype.multiline
#### 21.2.5.8 RegExp.prototype [ @@replace ] ( string, replaceValue )
#### 21.2.5.9 RegExp.prototype [ @@search ] ( string )
#### 21.2.5.10 get RegExp.prototype.source
#### 21.2.5.11 RegExp.prototype [ @@split ] ( string, limit )
#### 21.2.5.12 get RegExp.prototype.sticky
#### 21.2.5.13 RegExp.prototype.test ( S )
#### 21.2.5.14 RegExp.prototype.toString ( )
#### 21.2.5.15 get RegExp.prototype.unicode
### 21.2.6 Properties of RegExp Instances
#### 21.2.6.1 lastIndex
