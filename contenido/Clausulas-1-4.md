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

# 4. Vista general

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

## 4.1 Scripting Web
<sub>4.1 Web Scripting</sub>

Un navegador web provee un entorno anfitrión a ECMAScript para la computación de lado del cliente, incluyendo por ejemplo, objetos que representan ventanas, menus, pop-ups, cajas de diálogo, areas de texto, enlaces, cuadros, historial, *cookies*, y entrada y salida de datos. Aún mas, el entorno anfitrión entrega una manera de anexar código de scripting a eventos como el cambio de foco, carga de páginas e imágenes, descargas, errores y cancelaciones, selección, envío de formularios, y acciones del mouse. El código de scripting aparece dentro del html y la página desplegada es una combinación de elementos de interfaz de usuario, y texto e imágenes fijas y *dinámicas*. (sic: computed). El código de scripting es reactivo a la interacción del usuario, y no hay necesidad de un programa central. 

Un servidor web otorga un entorno anfitrión distinto para computación de lado del servidor, incluyendo objetos representando requests, clientes y archivos; y mecanismos para asegurar y compartir datos. Al usar scripting de lado del servidor y del cliente, es posible distribuir los procesos entre el cliente y el servidor mientras se provee una interfaz de usuario personalizada para una aplicación basada en web.

Cada navegador web y servidor que soporta ECMAScript suministra su propio entorno anfitrión, completando el entorno de ejecución ECMAScript.

## 4.2 Revisión general de ECMAScript.  
<sub>4.2 ECMAScript Overview</sub> 

La siguiente es un repaso general de ECMAScript -no todas las partes del lenguaje son descritas. Este vista no es parte del estándar propiamente tal.

ECMAScript es basado en objetos<sub>object-based</sub>: el lenguaje básico y los recursos del anfitrión son provistos por objetos, y un programa ECMAScript es un racimo<sub>cluster</sub> de objetos comunicantes. En ECMAScript, un *objeto* es una colección de cero o más *propiedades* cada una con *atributos* que determinan còmo puede ser usada cada propiedad -por ejemplo, cuando el atributo `Writable` de una propiedad es configurado a **false**, cualquier intento de ejecutar código ECMAScript que asigne un valor diferente a esa propiedad fallará. Las propiedades son contenedores que mantienen otros objetos, *valores primitivos*, o *funciones*. Un valor primitivo es un miembro de uno de los siguientes tipos incorporados: **Undefined, Null, Boolean, Number, String, Symbol**; un objeto, por su parte, es miembro del tipo incorporado **Object**, y una función es una objeto llamable. Una función que es asociada con un objeto a través de una propiedad es llamada *método*.

ECMAScript define una colección de *objetos incorporados* que completan la definición de las entidades ECMAScript. Estos objetos incorporados incluyen el **objeto global**; objetos que son fundamentales para las semánticas en tiempo de ejecución del programa, incluyendo **Object, Function, Boolean, Symbol**, y varios objetos de **Error**; objetos que representan y manipulan valores numéricos incluyendo **Math, Number** y **Date**, los objetos de procesado de texto **String** y **RegExp**; objetos que son colecciones indexadas de valores incluyendo el **Array** y nueve tipos diferentes de Array tipados<sub>Typed Array</sub> cuyos elementos tienen todos, una representación de datos numéricos específica; colecciones con clave incluyendo **Map** y **Set**; objetos que soportan datos estructurados, incluyendo el objeto **JSON, ArrayBuffer, SharedArrayBuffer** y **Dataview**; objetos que soportan abstracciones de control, como los generadores de funciones y **Promise**, y objetos de reflexión incluyendo **Proxy** y **Reflect**. 

ECMAScript también define un conjunto de *operadores* incorporados. Los operadores ECMAScript incluyen varios operadores unarios, operadores multiplicativos, aditivos, de desplazamiento de bit a bit, operadores relacionales, de igualdad, operadores binarios de bit a bit, operadores lógicos binarios, operadores de asignación y el operador coma. 

Grandes programas ECMAScript son soportados mediante *módulos*<sub>module</sub>, los cuales permiten a un programa ser dividido en múltiples secuencias de sentencias y declaraciones. Cada módulo identifica explícitamente las declaraciones que va a usar desde otro módulo y cuáles de sus declaraciones van a estar disponibles para ser usadas por otros módulos. 

La sintaxis de ECMAScript se parece intencionalmente a la sintaxis de Java. La sintaxis de ECMAScript se ha relajado para hacerlo apropiado para servir como un lenguaje de scripting fácil de usar. Por ejemplo, una variable no requiere declarar su tipo o los tipos asociados con sus propiedades, y las funciones definidas no requieren tener declaraciones antes de ser llamadas.
