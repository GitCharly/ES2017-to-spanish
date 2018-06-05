# 1. Alcance  
*Scope*

Este estándar define el lenguaje de programación de propósito general ECMAScript 2017.

# 2. Conformidad

Una implementación conforme de ECMAScript debe proporcionar y soportar todos los tipos, valores, objetos, propiedades, funciones, y semántica y sintáxis de programación descritas en esta especificación.

Una implementación conforme de ECMAScript debe interpretar texto fuente de conformidad con la última versión del estándar Unicode ISO/IEC 10646.

Una implementación conforme de ECMAScript que proporcione una interfaz de aplicación de programación que soporte programas que necesitan adaptarse a las convenciones lingüísticas y culturales de los distintos países, debe implementar la interfaz definida por la más reciente edición del estándar ECMA-402 que sea compatible con esta especificación. 

Una implementación conforme de ECMAScript puede proporcionar tipos, valores, objetos, propiedades y funciones adicionales más allá de las definidas en esta especificación. En particular, una implementación conforme de ECMAScript puede proporcionar propiedades que no están descritas en esta especificación, y valores para esas propiedades, para objetos que si están descritos en esta especificación.

Una implementación conforme de ECMAScript puede soportar síntaxis de programación y de expresiones regulares no descritas en esta especificación. En particular, una implementación conforme de ECMAScript puede soportar síntaxis de programación que hace uso de "futuras palabras reservadas" de las listadas en la subcláusula 11.6.2 de esta especificación.

Una implementación conforme de ECMAScript no debe implementar ninguna extensión que esté listada como "Extensión prohibida" en la subcláusula 16.2

# 3. Rerencias normativas

Los documentos referenciados a continuación son indispensables para la aplicación de este documento. Para referencias datadas, solo la edición citada aplica. Para referencias no datadas, la última edición del documento (correcciones incluidas) referenciado aplica.

ISO/IEC 10646:2006: *Information Technology - Universal Multiple-Octet Coded Character Set (UCS) plus Amendment 1:2005, Amendment 2:2006, Amendment 3:2008, and Amendment 4:2008* más las correcciones adeicionales, o sucesoras. 

ECMA-402, *ECMAScript 2015 International API Specification*.
http://www.ecma-international.org/publications/standards/Ecma-402.htm

ECMA-404, *The Json Data Interchange Format*.
http://www.ecma-international.org/publications/standars/Ecma-404.htm

# 4. Revisión general

Esta sección contiene una revisión general no normativa del lenguaje ECMAScript.

ECMAScript es un lenguaje de programación orientado a objetos para realizar computación y manipular objetos computacionales dentro de un ambiente anfitrión. ECMAScript tal como está definido aquí, no está considerado como un lenguaje computacionalmente autosuficiente; de hecho, en esta especificación no hay provisiones para la entrada de datos externos o para la salida de los resultados computados. En vez de eso, se espera que el entorno computacional de un programa ECMAScript suministre no solo los objetos y los otros recurso descritos en esta especificación, sino también ciertos objetos entorno-específicos, cuya descripción y comportamiento están más allá del alcance de esta especificación excepto para indicar que ellas pueden proveer ciertas propiedades que pueden ser accedidas y ciertas funciones que pueden ser llamadas desde un programa ECMAScript.

ECMAScript fue originalmente diseñado para ser usado como un lenguaje de scripting, pero ha llegado a ser ampliamente usado como un lenguaje de programación de propósito general. Un *lenguaje de scripting* es una lenguaje de programación que es usado para manipular, personalizar y automatizar ciertas facilidades en un sistema existente. En tales sistemas, la funcionalidad básica ya está disponible a través de una interfaz de usuario, y el lenguaje de scripting es una mecanismo para exponer esa funcionalidad al control del programa. En este sentido, se dice del sistema existente que provee el entorno anfitrión de objetos y recursos, los cuales completan las capacidades del lenguaje de scripting. Un lenguaje de scripting está pensado para ser usado tanto por programadores profesionales como por aficionados.

ECMAScript fue originalmente diseñado para ser un *lenguaje de scripting Web*, entregando un mecanismo para animar páginas web en navegadores y para realizar computos de lado del servidor como parte de una arquitectura cliente-servidor basada en web. ECMAScript hoy es utilizado para proveer capacidades de scripting basico para una variedad de entornos anfitriones. Por lo tanto, el núcleo del lenguaje es especificado en este documento aparte de cualquier ambiente anfitrión en particular.

El uso de ECMAScript ha superado el simple scripting y hoy es utilizado para un completo espectro de tareas en muchos entornos distintos y escalas. Así como el uso de ECMAScript se ha expandido, así también lo han hecho sus características y los recursos que entrega. ECMAScript es hoy un completo lenguaje de programación de propósito general.

Algunos de los recursos del ECMAScript son similares a aquellos usados en otros lenguajes de programación; en particular C, Java<sup>TM</sup>, Self y Scheme tal como son descritos en:

ISO/IEC 9899:1996, *Programming Languages - C*.

Gosling, James, Bill Joy and Guy Steele. *The Java<sup>TM</sup> Language Specification*. Addison Wesley Publishing Co., 1996.

Ungar, David, and Smith, Randall B. Self: The Power of Simplicity. *OOPSLA '87 Conference Proceedings,* pp.227-241, Orlando, FL, October 1987.

*IEEE Standard for the Scheme Programming Language*. IEEE Std. 1178-1990.


