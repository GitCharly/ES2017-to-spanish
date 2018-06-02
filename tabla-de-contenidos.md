# Intoduccion
# 1. Alcance
# 2. Conformidad
# 3. Referencias Normativas
# 4. Vista General
## 4.1. Programación Web
## 4.2. Vista general de ECMAScript
### 4.2.1 Objeto
### 4.2.2 La variante estricta de ECMAScript
## 4.3. Términos y definiciones
### 4.3.1. tipo
### 4.3.2. valor primitivo
### 4.3.3. objeto
### 4.3.4. constructor
### 4.3.5. prototipo
### 4.3.6. objeto ordinario
### 4.3.7. objeto exótico
### 4.3.8. objeto estándar
### 4.3.9. objeto incorporado
### 4.3.10. valor undefined
### 4.3.11. tipo Undefined
### 4.3.12. valor null
### 4.3.13. tipo Null
### 4.3.14. valor Boolean
### 4.3.15. tipo Boolean
### 4.3.16. objeto Boolean
### 4.3.17. valor String
### 4.3.18. tipo String
### 4.3.19. objeto String
### 4.3.20. valor Number
### 4.3.21. tipo Number
### 4.3.22. objeto Number
### 4.3.23. Infinity
### 4.3.24. NaN
### 4.3.25. valor Symbol
### 4.3.26. tipo Symbol
### 4.3.27. objeto Symbol
### 4.3.28. función
### 4.3.29. función incorporada
### 4.3.30. propiedad
### 4.3.31. método
### 4.3.32. método incorporado
### 4.3.33. atributo
### 4.3.34. propiedad particular (own)
### 4.3.35. propiedad heredada
## 4.4. Organización de esta especificación
# 5. Convenciones para la notación
## 5.1. Gramáticas sintácticas y léxicas
### 5.1.1. Gramáticas libres de contexto
### 5.1.2. Las gramáticas léxicas y de expresiones regulares (RegExp)
### 5.1.3. La gramática de cadenas numéricas
### 5.1.4. La gramática sintáctica
### 5.1.5. Notación gramática
## 5.2. Convenciones de algoritmos
## 5.3. Reglas semánticas estáticas
# 6. Tipos y Valores ECMAScript
## 6.1. Los tipos del lenguaje ECMAScript
### 6.1.1. El tipo Undefined
### 6.1.2. El tipo Null
### 6.1.3. El tipo Boolean
### 6.1.4. El tipo String
### 6.1.5. El tipo Symbol
#### 6.1.5.1 Well-Known Symbols
### 6.1.6. El tipo Number
### 6.1.7. El tipo Objeto
#### 6.1.7.1. Atributos de propiedades
#### 6.1.7.2. Métodos y ranuras internas de los Objetos
#### 6.1.7.3. Invariante de los métodos internos esenciales
#### 6.1.7.4. Objetos intrínsecos Well-Know 
## 6.2. Especificación de los tipos ECMAScript
### 6.2.1. The List and Record Specificaction Types
### 6.2.2. The set and Relation Specification Types
### 6.2.3. The Completion Record Specification Type
#### 6.2.3.1. Normal Completion
#### 6.2.3.2. Implicit Completion Values
#### 6.2.3.3. Throw an Exception
#### 6.2.3.4. ReturnIfAbrupt
#### 6.2.3.5. UpdateEmpty (completionRecord, value)
### 6.2.4. Tipo de especificación de referencia
#### 6.2.4.1. GetValue (V)
#### 6.2.4.2. PutValue (V, W)
#### 6.2.4.3. GetThisValue (V)
#### 6.2.4.4. InitializeReferenceBinding (V, W)
### 6.2.5 Tipo de especificación del descriptor de propiedades
#### 6.2.5.1. IsAccessorDescriptor (Desc)
#### 6.2.5.2. IsDataDescriptor (Desc)
#### 6.2.5.3. IsGenericDescriptor (Desc)
#### 6.2.5.4. FromPropertyDescriptor (Desc)
#### 6.2.5.5. ToPropertyDescriptor (Desc)
#### 6.2.5.6. CompletePropertyDescriptor (Desc)
### 6.2.6. Tipos de especificación de registro de entorno y entorno léxico
### 6.2.7. Bloques de datos
#### 6.2.7.1. CreateByteDataBlock (size)
#### 6.2.7.2. CreateSharedByteDataBlock (size)
#### 6.2.7.3. CopyDataBlockBytes (toBlock, toIndex, fromBlock, fromIndex, count)
# 7. Operaciones Abstractas
## 7.1. Conversión de tipos
### 7.1.1. ToPrimitive (input [, PreferredType])
#### 7.1.1.1. OrdinaryToPrimitive (O, hint)
### 7.1.2. ToBoolean (argument
### 7.1.3. ToNumber (argument)
#### 7.1.3.1 ToNumber aplicado al tipo String
##### 7.1.3.1.1 RS: MV
### 7.1.4. ToInteger (argument)
### 7.1.5. ToInt32 (argument)
### 7.1.6. ToUint32 (argument)
### 7.1.7. ToInt16 (argument)
### 7.1.8. ToUint16 (argument)
### 7.1.9. ToInt8 (argument)
### 7.1.10. ToUint8 (argument)
### 7.1.11. ToUint8Clamp (argument)
### 7.1.12. ToString (argument)
#### 7.1.12.1. ToString aplicado al tipo Number 
### 7.1.13. ToObject (argument)
### 7.1.14. ToPropertyKey (argument)
### 7.1.15. ToLength (argument)
### 7.1.16. CanonicalNumericIndexString (argument)
### 7.1.17. ToIndex (value)
## 7.2. Testeo y operaciones de comparación
### 7.2.1. RireObjectCoercible (argument)
### 7.2.2. IsArray (argument)
### 7.2.3. IsCallable (argument)
### 7.2.4. IsConstructor (argument)
### 7.2.5. IsExtensible (O)
### 7.2.6. IsInteger (argument)
### 7.2.7. IsPropertyKey (argument)
### 7.2.8. IsRegExp (argument)
### 7.2.9. SameValue (x, y)
### 7.2.10. SameValueZero (x, y)
### 7.2.11. SameValueNonNumber (x, y)
### 7.2.12. Comparación relacional abstracta
### 7.2.13. Comparación de igualdad abstracta
### 7.2.14. Comparación de igualdad estricta
## 7.3. Operaciones en Objetos
### 7.3.1. Get (O, P)
### 7.3.2. GetV (V, P)
### 7.3.3. Set (O, P, V, Throw)
### 7.3.4. CreateDataProperty (O, P, V)
### 7.3.5. CreateMethodProperty (O, P, V)
### 7.3.6. CreateDataPropertyOrThrow (O, P, V)
### 7.3.7. DefinePropertyOrThrow (O, P, desc)
### 7.3.8. DeletePropertyOrThrow (O, P)
### 7.3.9. GetMethod (V, P)
### 7.3.10. HasProperty (O, P)
### 7.3.11. HasOwnProperty (O, P)
### 7.3.12. Call (F, V[, argumentsList])
### 7.3.13. Construct (F[, argumentsList[, newTarget]])
### 7.3.14. SetIntegrityLevel (O, level)
### 7.3.15. TestIntegrityLevel (O, level)
### 7.3.16. CreateArrayFromList (elements)
### 7.3.17. CreateListFromArrayLike (obj[, elementTypes])
### 7.3.18. invoke (V, P[, argumentsList])
### 7.3.19. OrdinaryHasInstance (C, O)
### 7.3.20. SpeciesConstructor (O, defaultConstructor)
### 7.3.21. EnumerableOwnProperties (O, kind)
### 7.3.22. GetFunctionRealm (obj)
## 7.4. Operaciones en Objetos iteradores
### 7.4.1. GetIterator (obj[, method])
### 7.4.2. IteratorNext (iterator[, value])
### 7.4.3. IteratorComplete (iterResult)
### 7.4.4. IteratorValue (iterResult)
### 7.4.5. IteratorStep (iterator)
### 7.4.6. IteratorClose (iterator, completion)
### 7.4.7. CreateIterResultObject (value, done)
### 7.4.8. CreateListIterator (list)
#### 7.4.8.1 ListIterator next()
# 8. Código ejecutable y contextos de ejecución
## 8.1. Entornos léxicos
### 8.1. Registros de entorno (*Environment Records*)
#### 8.1.1. Regitros de entonro declarativos (*Declarative Environment Records*)
##### 8.1.1.1.1. HasBinding (N)
##### 8.1.1.1.2. CreateMutableBinding (N, D)
##### 8.1.1.1.3. CreateImmutableBinding (N, S)
##### 8.1.1.1.4. InitializeBinding (N, V)
##### 8.1.1.1.5. SetMutableBinding (N, V, S)
##### 8.1.1.1.6. GetBindingValue (N, S)
##### 8.1.1.1.7. DeleteBinding (N)
##### 8.1.1.1.8. HasThisBinding ()
##### 8.1.1.1.9. HasSuperBinding ()
##### 8.1.1.1.10. WithBaseObject ()
#### 8.1.1.2. Registros de entorno de Objetos (*Object Environment Records*)
##### 8.1.1.2.1. HasBinding (N)
##### 8.1.1.2.2. CreateMutableBinding (N, D)
##### 8.1.1.2.3. CreateImmutableBinding (N, S)
##### 8.1.1.2.4. InitializeBinding (N, V)
##### 8.1.1.2.5. SetMutableBinding (N, V, S)
##### 8.1.1.2.6. GetBindingValue (N, S)
##### 8.1.1.2.7. DeleteBinding (N)
##### 8.1.1.2.8. HasThisBinding ()
##### 8.1.1.2.9. HasSuperBinding ()
##### 8.1.1.2.10. WithBaseObject ()
#### 8.1.1.3. Registros de entorno de funciones (*Function Environment Records*)
##### 8.1.1.3.1. BindThisValue (V)
##### 8.1.1.3.2. HasThisBinding ()
##### 8.1.1.3.3. HasSuperBinding ()
##### 8.1.1.3.4. GetThisBinding ()
##### 8.1.1.3.5. GetSuperBase ()
#### 8.1.1.4. Registros de entorno Global (*Global Environment Records*)
##### 8.1.1.4.1. HasBinding (N)
##### 8.1.1.4.2. CreateMutableBinding (N, D)
##### 8.1.1.4.3. CreateImmutableBinding (N, S)
##### 8.1.1.4.4. InitializeBinding (N, V)
##### 8.1.1.4.5. SetMutableBinding (N, V, S)
##### 8.1.1.4.6. GetBindingValue (N, S)
##### 8.1.1.4.7. DeleteBinding (N)
##### 8.1.1.4.8. HasThisBinding ()
##### 8.1.1.4.9. HasSuperBinding ()
##### 8.1.1.4.10. WithBaseObject ()
##### 8.1.1.4.11. GetThisBinding ()
##### 8.1.1.4.12. HasVarDeclaration (N)
##### 8.1.1.4.13. HasLexicalDeclaration (N)
##### 8.1.1.4.14. HasRestrictedglobalProperty (N)
##### 8.1.1.4.15. CanDeclareGlobalVar (N)
##### 8.1.1.4.16. CanDeclareGlobalFunction (N)
##### 8.1.1.4.17. CreateGlobalVarBinding (N, D)
##### 8.1.1.4.18. CreateGlobalFunctionBinding (N, V, D)
#### 8.1.1.5. Registros de Entorno de Módulos (*Module Environment Records*)
##### 8.1.1.5.1. GetBindingValue (N, S)
##### 8.1.1.5.2. DeleteBinding (N)
##### 8.1.1.5.3. HasThisBinding ()
##### 8.1.1.5.4. GetThisBinding ()
##### 8.1.1.5.5. CreateImportBinding (N, M, N2)
### 8.1.2. Operaciones de entorno léxico 
#### 8.1.2.1. GetIdentifierReference (lex, name, strict)
#### 8.1.2.2. NewDeclarativeEnvironment (E)
#### 8.1.2.3. NewObjectEnviroment (O, E)
#### 8.1.2.4. NewFunctionEnvironment (F, newTarget)
#### 8.1.2.5. NewGlobalEnvironment (G, thisValue)
#### 8.1.2.6. NewModuleEnvironment (E)
## 8.2. Reinos (*Realms*)
### 8.2.1. CreateRealm ()
### 8.2.2. CreateIntrinsics (realmRec)
### 8.2.3. SetRealmGlobalObject (realmRec, globalObj, thisValue)
### 8.2.4. SetDefaultGlobalBindings (realmRec)
## 8.3. Contextos de ejecución (*Execution Contexts*)
### 8.3.1. GetActiveScriptOrModule ()
### 8.3.2. ResolveBinding (name[, env])
### 8.3.3. GetThisEnvironment ()
### 8.3.4. ResolveThisBinding ()
### 8.3.5. GetNewTarget ()
### 8.3.6. GetGlobalObject ()## 8.4. Trabajos y colas de trabajos (*Jobs and Job Queues*)
### 8.4.1. EnqueueJob (queueName, job, arguments)
## 8.5. InitializeHostDefinedRealm ()
## 8.6. RunJobs ()
## 8.7. Agentes (*Agents*)
### 8.7.1. AgentSignifier ()
### 8.7.2. AgentCanSuspend ()
## 8.8. Agent Clusters
## 8.9. Forward Progress
# 9. Comportamiento de Objetos ordinarios y exóticos (*Ordinary and Exotic Methods Behaviours*)
## 9.1. Métodos internos de objetos ordinarios y ranuras internas. (*Ordinary Object Internal Methods and Internal Slots*)
### 9.1.1. [[GetPrototypeOf]] ()
#### 9.1.1.1. OrdinaryGetPrototypeOf (O)
### 9.1.2. [[SetPrototypeOf]] (V)
#### 9.1.2.1. OrdinarySetPrototypeOf (O, V)
### 9.1.3. [[IsExtensible]] ()
#### 9.1.3.1. OrdinaryIsExtensible (O)
### 9.1.4. [[PreventExtensions]] ()
#### 9.1.4.1 OrdinaryPreventExtensions (O)
### 9.1.5. [[GetOwnProperty]] (P)
#### 9.1.5.1. OrdinaryGetOwnProperty (O, P)
### 9.1.6. [[DefineOwnProperty]] (P, Desc)
#### 9.1.6.1. OrdinaryDefineOwnProperty (O, P, Desc)
#### 9.1.6.2. IsCompatiblePropertyDescriptor (Extensible, Desc, Current)
#### 9.1.6.3. ValidateAndApplyPropertyDescriptor (O, P, extensible, desc, current)
### 9.1.7. [[HasProperty]] (P)
#### 9.1.7.1 OrdinaryHasProperty (O, P)
### 9.1.8. [[Get]] (P, V, Receiver)
#### 9.1.8.1 OrdinaryGet (O, P, Receiver)
### 9.1.9. [[Set]] (P, V, Receiver)
#### 9.1.9.1 OrdinarySet (O, P, V, Receiver)
### 9.1.10. [[Delete]] (P)
#### 9.1.10.1. OrdinaryDelete (O, P)
### 9.1.11. [[OwnPropertyKeys]] ()
#### 9.1.11.1. OrdinaryOwnPropertyKeys (O)
### 9.1.12. ObjectCreate (proto [, internalSlotsList])
### 9.1.13. OrdinaryCreateFromConstructor (constructor, instrinsicDefaultProto[, internalSlotsList])
### 9.1.14. GetPrototypeFromConstructor (constructor, intrinsicDefaultProto)
## 9.2. Objectos función de ECMAScript (*ECMAScript Function Objects*)
### 9.2.1 [[Call]] (thisArgument, argumenstList)
#### 9.2.1.1. PrepareForOrdinaryCall (F, newTarget)
#### 9.2.1.2. OrdinaryCallBindThis (F, calleContext, thisArgument)
#### 9.2.1.3. OrdinaryCallEvaluateBody (F, argumentsList)
### 9.2.2. [[Construct]] (argumentsList, newTarget)
### 9.2.3. FunctionAllocate (functionPrototype, strict, functionKind)
### 9.2.4. FunctionInitialize (F, kind, ParameterList, Body, Scope)
### 9.2.5. FunctionCreate (kind, ParameterList, Body, Scope, strict[, prototype])
### 9.2.6. GeneratorFunctionCreate (kind, ParameterList, Body, Scope, Strict)
### 9.2.7. AddRestrictedFunctionProperties (F, realm)
#### 9.2.7.1. %ThrowTypeError% ()
### 9.2.8. MakeConstructor (F[, writablePrototype[, prototype]])
### 9.2.9. MakeClassConstructor (F)
### 9.2.10. MakeMethod (F, homeObject)
### 9.2.11. SetFunctionName (F, name[, prefix])
### 9.2.12. FunctionDeclarationInstantiation (func, argumentsList)
## 9.3. Objetos función incorporados (*Built-in Function Objects*)
### 9.3.1. [[Call]] (thisArgument, argumentsList)
### 9.3.2. [[Construct]] (argumentsList, newTarget)
### 9.3.3. CreateBuiltinFunction (realm, steps, prototype[, internalSlotsList])
## 9.4. Métodos internos y ranuras de los objetos exóticos incorporados (*Built-in Exotic Object Internal Methods and Slots*)
### 9.4.1. Bound Function Exotic Objects
#### 9.4.1.1. [[Call]] (thisArgument, argumentsList)
#### 9.4.1.2. [[Construct]] (argumentsList, newTarget)
#### 9.4.1.3. BoundFunctionCreate (targetFunction, boundThis, boundArgs)
### 9.4.2. Array Exotic Objects
#### 9.4.2.1. [[DefineOwnProperty]] (P, Desc)
#### 9.4.2.2. ArrayCreate (length [, proto])
#### 9.4.2.3. ArraySpeciesCreate (originalArray, length)
#### 9.4.2.4. ArraySetLength (A, Desc)
### 9.4.3. String Exotic Objects
#### 9.4.3.1. [[GetOwnProperty]] (P)
#### 9.4.3.2. [[DefineOwnProperty]] (P, Desc)
#### 9.4.3.3. [[OwnPropertyKeys]] ()
#### 9.4.3.4. StringCreate (value, prototype)
#### 9.4.3.5. StringGetOwnProperty (S, P)
### 9.4.4. Arguments Exotic Objects
#### 9.4.4.1. [[GetOwnProperty]] (P)
#### 9.4.4.2. [[DefineOwnProperty]] (P, Desc)
#### 9.4.4.3. [[Get]] (P, Receiver)
#### 9.4.4.4. [[Set]] (P, V, Receiver)
#### 9.4.4.5. [[Delete]] (P)
#### 9.4.4.6. CreateUnmappedArgumentsObject (argumentsList)
#### 9.4.4.7. CreateMappedArguementsObject (fun, formals, argumentsList, env)
#### 9.4.4.7.1. MakeArgGetter (name, env)
#### 9.4.4.7.2. MakeArgSetter (name, env)
### 9.4.5. Integer Indexed Exotic Objects
#### 9.4.5.1. [[GetOwnProperty]] (P)
#### 9.4.5.2. [[HasOwnProperty]] (P)
#### 9.4.5.3. [[DefineOwnProperty]] (P, Desc)
#### 9.4.5.4. [[Get]] (P, Receiver)
#### 9.4.5.5. [[Set]] (P, V, Receiver)
#### 9.4.5.6. [[OwnPropertyKeys]] ()
#### 9.4.5.7. IntegerIndexedObjectCreate (prototype, internalSlotsList)
#### 9.4.5.8. IntegerIndexedElementGet (O, index)
#### 9.4.5.9. IntegerIndexedElementSet (O, index, value) 
### 9.4.6. Module Namespace Exotic Objects
#### 9.4.6.1. [[SetPrototypeOf]] (V) 
#### 9.4.6.2. [[IsExtensible]] ()
#### 9.4.6.3. [[PreventExtensions]] ()
#### 9.4.6.4. [[GetOwnProperty]] (P)
#### 9.4.6.5. [[DefineOwnProperty]] (P, Desc)
#### 9.4.6.6. [[HasProperty]] (P)
#### 9.4.6.7. [[Get]] (P, Receiver)
#### 9.4.6.8. [[Set]] (P, V, Receiver)
#### 9.4.6.9. [[Delete]] (P)
#### 9.4.6.10. [[OwnPropertyKeys]] ()
#### 9.4.6.11. ModeleNamespaceCreate (module, exports) 
### 9.4.7. Immutable Prototype Exotic Objects
#### 9.4.7.1. [[SetPrototypeOf]] (V)
#### 9.4.7.2. SetImmutablePrototype (O, V)
## 9.5. Proxy Object Internal Methods and Internal Slots
### 9.5.1. [[GetPrototypeOf]] ()
### 9.5.2. [[SetPrototypeOf]] (V)
### 9.5.3. [[IsExtensible]] ()
### 9.5.4. [[PreventExtensions]] ()
### 9.5.5. [[GetOwnProperty]] (P)
### 9.5.6. [[DefineOwnProperty]] (P, Desc)
### 9.5.7. [[HasProperty]] (P)
### 9.5.8. [[Get]] (P, Receiver)
### 9.5.9. [[Set]] (P, V, Receiver)
### 9.5.10. [[Delete]] (P)
### 9.5.11. [[OwnPropertyKeys]] ()
### 9.5.12. [[Call]] (thisArgument, argumentsList)
### 9.5.13. [[Construct]] (argumentsList, newTarget)
### 9.5.14. ProxyCreate (target, handler)
# 10. Lenguaje ECMAScript: Código Fuente 
## 10.1. Código Fuente
### 10.1.1. SS: UTF16Encoding (cp)
### 10.1.2. SS: UTF16Decode (lead, trail)
## 10.2. Tipos de Código Fuente
### 10.2.1. Modo de código estricto
### 10.2.2. Funciones No-ECMAScript
# 11. Lenguaje ECMAScript: Gramática léxica
## 11.1 Unicode Format-Control Characters (Caracteres de control de formato Unicode)
## 11.2 White Space (Espacio en blanco)
## 11.3 Line Terminators (Finalizadores de línea)
## 11.4 Comments (Comentarios)
## 11.5 Tokens 
## 11.6 Names and Keywords (Nombres y palabras clave)
### 11.6.1 Identifier Names (Identificadores)
#### 11.6.1.1 SS: Early Errors 
#### 11.6.1.2 SS: StringValue
### 11.6.2 Reserved Words (Palabras Reservadas)
#### 11.6.2.1 Keywords (Claves)
#### 11.6.2.2 Future Reserved Words (Futuras palabras reservadas)
## 11.7 Punctuators (Puntuadores)
## 11.8 Literals (Literales)
### 11.8.1 Null Literals (Literales Null)
### 11.8.2 Boolean Literals (Literales booleanos)
### 11.8.3 Numeric Literals (Literales numéricos)
#### 11.8.3.1 SS: MV
### 11.8.4 String Literals (Literales de Strings)
#### 11.8.4.1 SS: Early Errors
#### 11.8.4.2 SS: StringValue
#### 11.8.4.3 SS: SV
### 11.8.5 Regular Expression Literals (Literales de Expresiones Regulares)
#### 11.8.5.1 SS: Early Errors
#### 11.8.5.2 SS: BodyText
#### 11.8.5.3 SS: FlagText
### 11.8.6 Template Literal Lexical Components
#### 11.8.6.1 SS: TV and TRV
## 11.9 Automatic Semicolon Insertion (Inserción automática de punto-y-coma)
### 11.9.1 Rules of Automatic Semicolon Insertion (Reglas de inserción automática de punto-y-coma)
### 11.9.2 Examples of Automatic Semicolon Insertion (Ejemplos de inserción automática de punto-y-coma)
# 12. Lenguaje ECMAScript: Expresiones
## 12.1 Identifiers (*Identificadores*)
### 12.1.1 SS: Early Errors
### 12.1.2 SS: BoundNames
### 12.1.3 SS: IsValidSimpleAssignmentTarget
### 12.1.4 SS: StringValue
### 12.1.5 RS: BindingInitialization
#### 12.1.5.1. RS: InitializeBoundName (name, value, environment)
### 12.1.6 RS: Evaluation
## 12.2 Primary Expression (*Expresiones primarias*)
### 12.2.1 Semantics
#### 12.2.1.1 SS: CoveredParenthesizedExpression
#### 12.2.1.2 SS: HasName
#### 12.2.1.3 SS: IsFunctionDefinition
#### 12.2.1.4 SS: IsIdentifierRef
#### 12.2.1.5 SS: IsValidSimpleAssignmentTarget
### 12.2.2 The *this* Keyword
#### 12.2.2.1. RS: Evaluation
### 12.2.3 Identifier Reference
### 12.2.4 Literals
#### 12.2.4.1. RS: Evalutation
### 12.2.5 Array Initializer
#### 12.2.5.1. SS: ElisionWidth 
#### 12.2.5.2. RS: ArrayAccumulation
#### 12.2.5.3. RS: Evaluation
### 12.2.6 Object Initializer
#### 12.2.6.1 SS: Early Errors
#### 12.2.6.2 SS: ComputedPropertyContains
#### 12.2.6.3 SS: Contains
#### 12.2.6.4 SS: IsComputedPropertyKey
#### 12.2.6.5 SS: PropName
#### 12.2.6.6 SS: PropertyNameList
#### 12.2.6.7 RS: Evaluation
#### 12.2.6.8 RS: PropertyDefinitionEvaluation
### 12.2.7 Function Defining Expressions
### 12.2.8 Regular Expression Literals
#### 12.2.8.1. SS: Early Errors
#### 12.2.8.2. RS: Evaluation
### 12.2.9 Template Literals
#### 12.2.9.1 SS: TemplateStrings
#### 12.2.9.2 RS: ArgumentListEvaluation
#### 12.2.9.3 RS: GetTemplateObject ( templateLiteral )
#### 12.2.9.4 RS: SubstitutionEvaluation
#### 12.2.9.5 RS: Evaluation
### 12.2.10 The Grouping Operator
#### 12.2.10.1 SS: Early Errors
#### 12.2.10.2 SS: IsFunctionDefinition
#### 12.2.10.3 SS: IsValidSimpleAssignmentTarget
#### 12.2.10.4 RS: Evaluation
## 12.3 Left-Hand-Side Expressions (*Expresiones de lado-izquierdo*)
### 12.3.1 Static Semantics
#### 12.3.1.1 SS: CoveredCallExpression
#### 12.3.1.2 SS: Contains
#### 12.3.1.3 SS: IsFunctionDefinition
#### 12.3.1.4 SS: IsDestructuring
#### 12.3.1.5 SS: IsIdentifierRef
#### 12.3.1.6 SS: IsValidSimpleAssignmentTarget
### 12.3.2 Property Accessors
#### 12.3.2.1 RS: Evaluation
### 12.3.3 The new Operator
#### 12.3.3.1 RS: Evaluation
##### 12.3.3.1.1 RS: EvaluateNew ( constructExpr, arguments )
### 12.3.4 Function Calls
#### 12.3.4.1 RS: Evaluation
#### 12.3.4.2 RS: EvaluateCall( ref, arguments, tailPosition )
#### 12.3.4.3 RS: EvaluateDirectCall( func, thisValue, arguments, tailPosition )
### 12.3.5 The super Keyword
#### 12.3.5.1 RS: Evaluation
#### 12.3.5.2 RS: GetSuperConstructor ( )
#### 12.3.5.3 RS: MakeSuperPropertyReference ( propertyKey, strict )
### 12.3.6 Argument Lists
#### 12.3.6.1 RS: ArgumentListEvaluation
### 12.3.7 Tagged Templates
#### 12.3.7.1 RS: Evaluation
### 12.3.8 Meta Properties
#### 12.3.8.1 RS: Evaluation
## 12.4 Update Expressions (*Expresiones de actualización*)
### 12.4.1 SS: Early Errors
### 12.4.2 SS: IsFunctionDefinition
### 12.4.3 SS: IsValidSimpleAssignmentTarget
### 12.4.4 Postfix Increment Operator
#### 12.4.4.1 RS: Evaluation
### 12.4.5 Postfix Decrement Operator
#### 12.4.5.1 RS: Evaluation
### 12.4.6 Prefix Increment Operator
#### 12.4.6.1 RS: Evaluation
### 12.4.7 Prefix Decrement Operator
#### 12.4.7.1 RS: Evaluation
## 12.5 Unary Operators (*Operadores Unarios*)
### 12.5.1 SS: IsFunctionDefinition
### 12.5.2 SS: IsValidSimpleAssignmentTarget
### 12.5.3 The delete Operator
#### 12.5.3.1 SS: Early Errors
#### 12.5.3.2 RS: Evaluation
### 12.5.4 The void Operator
#### 12.5.4.1 RS: Evaluation
### 12.5.5 The typeof Operator
#### 12.5.5.1 RS: Evaluation
### 12.5.6 Unary + Operator
#### 12.5.6.1 RS: Evaluation
### 12.5.7 Unary - Operator
#### 12.5.7.1 RS: Evaluation
### 12.5.8 Bitwise NOT Operator ( ~ )
#### 12.5.8.1 RS: Evaluation
### 12.5.9 Logical NOT Operator ( ! )
#### 12.5.9.1 RS: Evaluation
## 12.6 Exponentiation Operator (*Operador de exponenciación*)
### 12.6.1 SS: IsFunctionDefinition
### 12.6.2 SS: IsValidSimpleAssignmentTarget
### 12.6.3 RS: Evaluation
### 12.6.4 Applying the ** Operator
## 12.7 Multiplicative Operators (*Operadores multiplicativos*)
### 12.7.1 SS: IsFunctionDefinition
### 12.7.2 SS: IsValidSimpleAssignmentTarget
### 12.7.3 RS: Evaluation
#### 12.7.3.1 Applying the * Operator
#### 12.7.3.2 Applying the / Operator
#### 12.7.3.3 Applying the % Operator
## 12.8 Additive Operators (*Operadores aditivos*)
### 12.8.1 SS: IsFunctionDefinition
### 12.8.2 SS: IsValidSimpleAssignmentTarget
### 12.8.3 The Addition Operator ( + )
#### 12.8.3.1 RS: Evaluation
### 12.8.4 The Subtraction Operator ( - )
#### 12.8.4.1 RS: Evaluation
### 12.8.5 Applying the Additive Operators to Numbers
## 12.9 Bitwise Shift Operators (*Operadores de intercambio de bit*)
### 12.9.1 SS: IsFunctionDefinition
### 12.9.2 SS: IsValidSimpleAssignmentTarget
### 12.9.3 The Left Shift Operator ( << )
#### 12.9.3.1 RS: Evaluation
### 12.9.4 The Signed Right Shift Operator ( >> )
#### 12.9.4.1 RS: Evaluation
### 12.9.5 The Unsigned Right Shift Operator ( >>> )
#### 12.9.5.1 RS: Evaluation
## 12.10 Relational Operators (*Operadores relacionales*)
### 12.10.1 SS: IsFunctionDefinition
### 12.10.2 SS: IsValidSimpleAssignmentTarget
### 12.10.3 RS: Evaluation
### 12.10.4 RS: InstanceofOperator ( O, C )
## 12.11 Equality Operators (*Operadores de igualdad*)
### 12.11.1 SS: IsFunctionDefinition
### 12.11.2 SS: IsValidSimpleAssignmentTarget
### 12.11.3 RS: Evaluation
## 12.12 Binary Bitwise Operators (*Operadores Binarios de bit*)
### 12.12.1 SS: IsFunctionDefinition
### 12.12.2 SS: IsValidSimpleAssignmentTarget
### 12.12.3 RS: Evaluation
## 12.13 Binary Logical Operators (*Operadores binarios lógicos*)
### 12.13.1 SS: IsFunctionDefinition
### 12.13.2 SS: IsValidSimpleAssignmentTarget
### 12.13.3 RS: Evaluation
## 12.14 Conditional Operator ( ? : )
### 12.14.1 SS: IsFunctionDefinition
### 12.14.2 SS: IsValidSimpleAssignmentTarget
### 12.14.3 RS: Evaluation
## 12.15 Assignment Operators (*Operadores de asignación*)
### 12.15.1 SS: Early Errors
### 12.15.2 SS: IsFunctionDefinition
### 12.15.3 SS: IsValidSimpleAssignmentTarget
### 12.15.4 RS: Evaluation
### 12.15.5 Destructuring Assignment (*Asignación desestructurada?*)
#### 12.15.5.1 SS: Early Errors
#### 12.15.5.2 RS: DestructuringAssignmentEvaluation
#### 12.15.5.3 RS: IteratorDestructuringAssignmentEvaluation
#### 12.15.5.4 RS: KeyedDestructuringAssignmentEvaluation
## 12.16 Comma Operator ( , )
### 12.16.1 SS: IsFunctionDefinition
### 12.16.2 SS: IsValidSimpleAssignmentTarget
### 12.16.3 RS: Evaluation
# 13. Lenguaje ECMAScript: Sentencias y Declaraciones
## 13.1 Statement Semantics (*Sentencias semánticas*)
### 13.1.1 SS: ContainsDuplicateLabels
### 13.1.2 SS: ContainsUndefinedBreakTarget
### 13.1.3 SS: ContainsUndefinedContinueTarget
### 13.1.4 SS: DeclarationPart
### 13.1.5 SS: VarDeclaredNames
### 13.1.6 SS: VarScopedDeclarations
### 13.1.7 RS: LabelledEvaluation
### 13.1.8 RS: Evaluation
## 13.2 Block
### 13.2.1 SS: Early Errors
### 13.2.2 SS: ContainsDuplicateLabels
### 13.2.3 SS: ContainsUndefinedBreakTarget
### 13.2.4 SS: ContainsUndefinedContinueTarget
### 13.2.5 SS: LexicallyDeclaredNames
### 13.2.6 SS: LexicallyScopedDeclarations
### 13.2.7 SS: TopLevelLexicallyDeclaredNames
### 13.2.8 SS: TopLevelLexicallyScopedDeclarations
### 13.2.9 SS: TopLevelVarDeclaredNames
### 13.2.10 SS: TopLevelVarScopedDeclarations
### 13.2.11 SS: VarDeclaredNames
### 13.2.12 SS: VarScopedDeclarations
### 13.2.13 RS: Evaluation
### 13.2.14 RS: BlockDeclarationInstantiation( code, env )
## 13.3 Declarations and the Variable Statement (*Declaraciones y la sentencia variable*)
### 13.3.1 Let and Const Declarations
#### 13.3.1.1 SS: Early Errors
#### 13.3.1.2 SS: BoundNames
#### 13.3.1.3 SS: IsConstantDeclaration
#### 13.3.1.4 RS: Evaluation
### 13.3.2 Variable Statement
#### 13.3.2.1 SS: BoundNames
#### 13.3.2.2 SS: VarDeclaredNames
#### 13.3.2.3 SS: VarScopedDeclarations
#### 13.3.2.4 RS: Evaluation
### 13.3.3 Destructuring Binding Patterns
#### 13.3.3.1 SS: BoundNames
#### 13.3.3.2 SS: ContainsExpression
#### 13.3.3.3 SS: HasInitializer
#### 13.3.3.4 SS: IsSimpleParameterList
#### 13.3.3.5 RS: BindingInitialization
#### 13.3.3.6 RS: IteratorBindingInitialization
#### 13.3.3.7 RS: KeyedBindingInitialization
## 13.4 Empty Statement (*Sentencias vacias*)
### 13.4.1 RS: Evaluation
## 13.5 Expression Statement (*Sentencias de expresión*)
### 13.5.1 RS: Evaluation
## 13.6 The if Statement (*La sentencia 'if'*)
### 13.6.1 SS: Early Errors
### 13.6.2 SS: ContainsDuplicateLabels
### 13.6.3 SS: ContainsUndefinedBreakTarget
### 13.6.4 SS: ContainsUndefinedContinueTarget
### 13.6.5 SS: VarDeclaredNames
### 13.6.6 SS: VarScopedDeclarations
### 13.6.7 RS: Evaluation
## 13.7 Iteration Statements (*Sentencias de iteración*)
### 13.7.1 Semantics
#### 13.7.1.1 SS: Early Errors
#### 13.7.1.2 RS: LoopContinues ( completion, labelSet )
### 13.7.2 The do-while Statement
#### 13.7.2.1 SS: ContainsDuplicateLabels
#### 13.7.2.2 SS: ContainsUndefinedBreakTarget
#### 13.7.2.3 SS: ContainsUndefinedContinueTarget
#### 13.7.2.4 SS: VarDeclaredNames
#### 13.7.2.5 SS: VarScopedDeclarations
#### 13.7.2.6 RS: LabelledEvaluation
### 13.7.3 The while Statement
#### 13.7.3.1 SS: ContainsDuplicateLabels
#### 13.7.3.2 SS: ContainsUndefinedBreakTarget
#### 13.7.3.3 SS: ContainsUndefinedContinueTarget
#### 13.7.3.4 SS: VarDeclaredNames
#### 13.7.3.5 SS: VarScopedDeclarations
#### 13.7.3.6 RS: LabelledEvaluation
### 13.7.4 The for Statement
#### 13.7.4.1 SS: Early Errors
#### 13.7.4.2 SS: ContainsDuplicateLabels
#### 13.7.4.3 SS: ContainsUndefinedBreakTarget
#### 13.7.4.4 SS: ContainsUndefinedContinueTarget
#### 13.7.4.5 SS: VarDeclaredNames
#### 13.7.4.6 SS: VarScopedDeclarations
#### 13.7.4.7 RS: LabelledEvaluation
#### 13.7.4.8 RS: ForBodyEvaluation( test, increment, stmt, perIterationBindings, labelSet )
#### 13.7.4.9 RS: CreatePerIterationEnvironment( perIterationBindings )
### 13.7.5 The for-in and for-of Statements
#### 13.7.5.1 SS: Early Errors
#### 13.7.5.2 SS: BoundNames
#### 13.7.5.3 SS: ContainsDuplicateLabels
#### 13.7.5.4 SS: ContainsUndefinedBreakTarget
#### 13.7.5.5 SS: ContainsUndefinedContinueTarget
#### 13.7.5.6 SS: IsDestructuring
#### 13.7.5.7 SS: VarDeclaredNames
#### 13.7.5.8 SS: VarScopedDeclarations
#### 13.7.5.9 RS: BindingInitialization
#### 13.7.5.10 RS: BindingInstantiation
#### 13.7.5.11 RS: LabelledEvaluation
#### 13.7.5.12 RS: ForIn/OfHeadEvaluation ( TDZnames, expr, iterationKind )
#### 13.7.5.13 RS: ForIn/OfBodyEvaluation ( lhs, stmt, iterator, iterationKind, lhsKind, labelSet )
#### 13.7.5.14 RS: Evaluation
#### 13.7.5.15 EnumerateObjectProperties ( O )
## 13.8 The continue Statement (*La sentencia 'continue'*)
### 13.8.1 SS: Early Errors
### 13.8.2 SS: ContainsUndefinedContinueTarget
### 13.8.3 RS: Evaluation
## 13.9 The break Statement (*La sentencia break*)
### 13.9.1 SS: Early Errors
### 13.9.2 SS: ContainsUndefinedBreakTarget
### 13.9.3 RS: Evaluation
## 13.10 The return Statement (*La sentencia 'return*)
### 13.10.1 RS: Evaluation
## 13.11 The with Statement (*La sentencia 'with'*)
### 13.11.1 SS: Early Errors
### 13.11.2 SS: ContainsDuplicateLabels
### 13.11.3 SS: ContainsUndefinedBreakTarget
### 13.11.4 SS: ContainsUndefinedContinueTarget
### 13.11.5 SS: VarDeclaredNames
### 13.11.6 SS: VarScopedDeclarations
### 13.11.7 RS: Evaluation
## 13.12 The switch Statement (*La sentencia switch*)
### 13.12.1 SS: Early Errors
### 13.12.2 SS: ContainsDuplicateLabels
### 13.12.3 SS: ContainsUndefinedBreakTarget
### 13.12.4 SS: ContainsUndefinedContinueTarget
### 13.12.5 SS: LexicallyDeclaredNames
### 13.12.6 SS: LexicallyScopedDeclarations
### 13.12.7 SS: VarDeclaredNames
### 13.12.8 SS: VarScopedDeclarations
### 13.12.9 RS: CaseBlockEvaluation
### 13.12.10 RS: CaseSelectorEvaluation
### 13.12.11 RS: Evaluation
## 13.13 Labelled Statements (*Sentencias etiquetadas*)
### 13.13.1 SS: Early Errors
### 13.13.2 SS: ContainsDuplicateLabels
### 13.13.3 SS: ContainsUndefinedBreakTarget
### 13.13.4 SS: ContainsUndefinedContinueTarget
### 13.13.5 SS: IsLabelledFunction ( stmt )
### 13.13.6 SS: LexicallyDeclaredNames
### 13.13.7 SS: LexicallyScopedDeclarations
### 13.13.8 SS: TopLevelLexicallyDeclaredNames
### 13.13.9 SS: TopLevelLexicallyScopedDeclarations
### 13.13.10 SS: TopLevelVarDeclaredNames
### 13.13.11 SS: TopLevelVarScopedDeclarations
### 13.13.12 SS: VarDeclaredNames
### 13.13.13 SS: VarScopedDeclarations
### 13.13.14 RS: LabelledEvaluation
### 13.13.15 RS: Evaluation
## 13.14 The throw Statement (*La sentencia 'throw'*)
### 13.14.1 RS: Evaluation
## 13.15 The try Statement (*La sentencia 'try'*)
### 13.15.1 SS: Early Errors
### 13.15.2 SS: ContainsDuplicateLabels
### 13.15.3 SS: ContainsUndefinedBreakTarget
### 13.15.4 SS: ContainsUndefinedContinueTarget
### 13.15.5 SS: VarDeclaredNames
### 13.15.6 SS: VarScopedDeclarations
### 13.15.7 RS: CatchClauseEvaluation
### 13.15.8 RS: Evaluation
## 13.16 The debugger Statement (*La sentencia 'debugger'*)
### 13.16.1 RS: Evaluation
# 14. Lenguaje ECMAScript: Funciones y Clases
## 14.1 Function Definitions (*Deficiones de función*)
### 14.1.1 Directive Prologues and the Use Strict Directive
### 14.1.2 SS: Early Errors
### 14.1.3 SS: BoundNames
### 14.1.4 SS: Contains
### 14.1.5 SS: ContainsExpression
### 14.1.6 SS: ContainsUseStrict
### 14.1.7 SS: ExpectedArgumentCount
### 14.1.8 SS: HasInitializer
### 14.1.9 SS: HasName
### 14.1.10 SS: IsAnonymousFunctionDefinition ( expr )
### 14.1.11 SS: IsConstantDeclaration
### 14.1.12 SS: IsFunctionDefinition
### 14.1.13 SS: IsSimpleParameterList
### 14.1.14 SS: LexicallyDeclaredNames
### 14.1.15 SS: LexicallyScopedDeclarations
### 14.1.16 SS: VarDeclaredNames
### 14.1.17 SS: VarScopedDeclarations
### 14.1.18 RS: EvaluateBody
### 14.1.19 RS: IteratorBindingInitialization
### 14.1.20 RS: InstantiateFunctionObject
### 14.1.21 RS: Evaluation
## 14.2 Arrow Function Definitions (*Deficiones de función flecha*)
### 14.2.1 SS: Early Errors
### 14.2.2 SS: BoundNames
### 14.2.3 SS: Contains
### 14.2.4 SS: ContainsExpression
### 14.2.5 SS: ContainsUseStrict
### 14.2.6 SS: ExpectedArgumentCount
### 14.2.7 SS: HasName
### 14.2.8 SS: IsSimpleParameterList
### 14.2.9 SS: CoveredFormalsList
### 14.2.10 SS: LexicallyDeclaredNames
### 14.2.11 SS: LexicallyScopedDeclarations
### 14.2.12 SS: VarDeclaredNames
### 14.2.13 SS: VarScopedDeclarations
### 14.2.14 RS: IteratorBindingInitialization
### 14.2.15 RS: EvaluateBody
### 14.2.16 RS: Evaluation
## 14.3 Method Definitions (*Definiciones de Métodos*)
### 14.3.1 SS: Early Errors
### 14.3.2 SS: ComputedPropertyContains
### 14.3.3 SS: ExpectedArgumentCount
### 14.3.4 SS: HasDirectSuper
### 14.3.5 SS: PropName
### 14.3.6 SS: SpecialMethod
### 14.3.7 RS: DefineMethod
### 14.3.8 RS: PropertyDefinitionEvaluation
## 14.4 Generator Function Definitions (*Definiciones del generador de funciones*)
### 14.4.1 SS: Early Errors
### 14.4.2 SS: BoundNames
### 14.4.3 SS: ComputedPropertyContains
### 14.4.4 SS: Contains
### 14.4.5 SS: HasDirectSuper
### 14.4.6 SS: HasName
### 14.4.7 SS: IsConstantDeclaration
### 14.4.8 SS: IsFunctionDefinition
### 14.4.9 SS: PropName
### 14.4.10 RS: EvaluateBody
### 14.4.11 RS: InstantiateFunctionObject
### 14.4.12 RS: PropertyDefinitionEvaluation
### 14.4.13 RS: Evaluation
## 14.5 Class Definitions (*Definiciones de clases*)
### 14.5.1 SS: Early Errors
### 14.5.2 SS: BoundNames
### 14.5.3 SS: ConstructorMethod
### 14.5.4 SS: Contains
### 14.5.5 SS: ComputedPropertyContains
### 14.5.6 SS: HasName
### 14.5.7 SS: IsConstantDeclaration
### 14.5.8 SS: IsFunctionDefinition
### 14.5.9 SS: IsStatic
### 14.5.10 SS: NonConstructorMethodDefinitions
### 14.5.11 SS: PrototypePropertyNameList
### 14.5.12 SS: PropName
### 14.5.13 RS: ClassDefinitionEvaluation
### 14.5.14 RS: BindingClassDeclarationEvaluation
### 14.5.15 RS: Evaluation
## 14.6 Async Function Definitions (*Definiciones de funciones Async*)
### 14.6.1 SS: Early Errors
### 14.6.2 SS: BoundNames
### 14.6.3 SS: ComputedPropertyContains
### 14.6.4 SS: Contains
### 14.6.5 SS: HasDirectSuper
### 14.6.6 SS: HasName
### 14.6.7 SS: IsConstantDeclaration
### 14.6.8 SS: IsFunctionDefinition
### 14.6.9 SS: PropName
### 14.6.10 RS: InstantiateFunctionObject
### 14.6.11 RS: EvaluateBody
### 14.6.12 RS: PropertyDefinitionEvaluation
### 14.6.13 RS: Evaluation
## 14.7 Async Arrow Function Definitions (*Definiciones de funciones flecha Async*)
### 14.7.1 SS: Early Errors
### 14.7.2 SS: CoveredAsyncArrowHead
### 14.7.3 SS: BoundNames
### 14.7.4 SS: Contains
### 14.7.5 SS: ContainsExpression
### 14.7.6 SS: ExpectedArgumentCount
### 14.7.7 SS: HasName
### 14.7.8 SS: IsSimpleParameterList
### 14.7.9 SS: LexicallyDeclaredNames
### 14.7.10 SS: LexicallyScopedDeclarations
### 14.7.11 SS: VarDeclaredNames
### 14.7.12 SS: VarScopedDeclarations
### 14.7.13 RS: IteratorBindingInitialization
### 14.7.14 RS: EvaluateBody
### 14.7.15 RS: Evaluation
## 14.8 Tail Position Calls (*Llamadas a la posición en cola*)
### 14.8.1 SS: IsInTailPosition( call )
### 14.8.2 SS: HasCallInTailPosition
#### 14.8.2.1 Statement Rules
#### 14.8.2.2 Expression Rules
### 14.8.3 RS: PrepareForTailCall ( )
# 15. Lenguaje ECMAScript: Scripts y Modulos
## 15.1 Scripts
### 15.1.1 SS: Early Errors
### 15.1.2 SS: IsStrict
### 15.1.3 SS: LexicallyDeclaredNames
### 15.1.4 SS: LexicallyScopedDeclarations
### 15.1.5 SS: VarDeclaredNames
### 15.1.6 SS: VarScopedDeclarations
### 15.1.7 RS: Evaluation
### 15.1.8 Script Records
### 15.1.9 ParseScript ( sourceText, realm, hostDefined )
### 15.1.10 ScriptEvaluation ( scriptRecord )
### 15.1.11 RS: GlobalDeclarationInstantiation ( script, env )
### 15.1.12 RS: ScriptEvaluationJob ( sourceText, hostDefined )
## 15.2 Modules
### 15.2.1 Module Semantics
#### 15.2.1.1 SS: Early Errors
#### 15.2.1.2 SS: ContainsDuplicateLabels
#### 15.2.1.3 SS: ContainsUndefinedBreakTarget
#### 15.2.1.4 SS: ContainsUndefinedContinueTarget
#### 15.2.1.5 SS: ExportedBindings
#### 15.2.1.6 SS: ExportedNames
#### 15.2.1.7 SS: ExportEntries
#### 15.2.1.8 SS: ImportEntries
#### 15.2.1.9 SS: ImportedLocalNames ( importEntries )
#### 15.2.1.10 SS: ModuleRequests
#### 15.2.1.11 SS: LexicallyDeclaredNames
#### 15.2.1.12 SS: LexicallyScopedDeclarations
#### 15.2.1.13 SS: VarDeclaredNames
#### 15.2.1.14 SS: VarScopedDeclarations
#### 15.2.1.15 Abstract Module Records
#### 15.2.1.16 Source Text Module Records
##### 15.2.1.16.1 ParseModule ( sourceText, realm, hostDefined )
##### 15.2.1.16.2 GetExportedNames( exportStarSet ) Concrete Method
##### 15.2.1.16.3 ResolveExport( exportName, resolveSet ) Concrete Method
##### 15.2.1.16.4 ModuleDeclarationInstantiation( ) Concrete Method
##### 15.2.1.16.5 ModuleEvaluation( ) Concrete Method
#### 15.2.1.17 RS: HostResolveImportedModule ( referencingModule, specifier )
#### 15.2.1.18 RS: GetModuleNamespace( module )
#### 15.2.1.19 RS: TopLevelModuleEvaluationJob ( sourceText, hostDefined )
#### 15.2.1.20 RS: Evaluation
### 15.2.2 Imports
#### 15.2.2.1 SS: Early Errors
#### 15.2.2.2 SS: BoundNames
#### 15.2.2.3 SS: ImportEntries
#### 15.2.2.4 SS: ImportEntriesForModule
#### 15.2.2.5 SS: ModuleRequests
### 15.2.3 Exports
#### 15.2.3.1 SS: Early Errors
#### 15.2.3.2 SS: BoundNames
#### 15.2.3.3 SS: ExportedBindings
#### 15.2.3.4 SS: ExportedNames
#### 15.2.3.5 SS: ExportEntries
#### 15.2.3.6 SS: ExportEntriesForModule
#### 15.2.3.7 SS: IsConstantDeclaration
#### 15.2.3.8 SS: LexicallyScopedDeclarations
#### 15.2.3.9 SS: ModuleRequests
#### 15.2.3.10 SS: ReferencedBindings
#### 15.2.3.11 RS: Evaluation
# 16 Error Handling and Language Extensions (*Manejo de errores y extensiones del lenguaje*)
## 16.1 HostReportErrors ( errorList )
## 16.2 Forbidden Extensions
# 17 ECMAScript Standard Built-in Objects
### 18 The Global Object
## 18.1 Value Properties of the Global Object
### 18.1.1 Infinity
### 18.1.2 NaN
### 18.1.3 undefined
## 18.2 Function Properties of the Global Object
### 18.2.1 eval ( x )
#### 18.2.1.1 RS: PerformEval ( x, evalRealm, strictCaller, direct )
##### 18.2.1.1.1 Additional Early Error Rules for Eval Outside Functions
##### 18.2.1.1.2 Additional Early Error Rules for Eval Outside Methods
##### 18.2.1.1.3 Additional Early Error Rules for Eval Outside Constructor Methods
#### 18.2.1.2 HostEnsureCanCompileStrings( callerRealm, calleeRealm )
#### 18.2.1.3 RS: EvalDeclarationInstantiation( body, varEnv, lexEnv, strict )
### 18.2.2 isFinite ( number )
### 18.2.3 isNaN ( number )
### 18.2.4 parseFloat ( string )
### 18.2.5 parseInt ( string, radix )
### 18.2.6 URI Handling Functions
#### 18.2.6.1 URI Syntax and Semantics
##### 18.2.6.1.1 RS: Encode ( string, unescapedSet )
##### 18.2.6.1.2 RS: Decode ( string, reservedSet )
#### 18.2.6.2 decodeURI ( encodedURI )
#### 18.2.6.3 decodeURIComponent ( encodedURIComponent )
#### 18.2.6.4 encodeURI ( uri )
#### 18.2.6.5 encodeURIComponent ( uriComponent )
## 18.3 Constructor Properties of the Global Object
### 18.3.1 Array ( . . . )
### 18.3.2 ArrayBuffer ( . . . )
### 18.3.3 Boolean ( . . . )
### 18.3.4 DataView ( . . . )
### 18.3.5 Date ( . . . )
### 18.3.6 Error ( . . . )
### 18.3.7 EvalError ( . . . )
### 18.3.8 Float32Array ( . . . )
### 18.3.9 Float64Array ( . . . )
### 18.3.10 Function ( . . . )
### 18.3.11 Int8Array ( . . . )
### 18.3.12 Int16Array ( . . . )
### 18.3.13 Int32Array ( . . . )
### 18.3.14 Map ( . . . )
### 18.3.15 Number ( . . . )
### 18.3.16 Object ( . . . )
### 18.3.17 Proxy ( . . . )
### 18.3.18 Promise ( . . . )
### 18.3.19 RangeError ( . . . )
### 18.3.20 ReferenceError ( . . . )
### 18.3.21 RegExp ( . . . )
### 18.3.22 Set ( . . . )
### 18.3.23 SharedArrayBuffer ( . . . )
### 18.3.24 String ( . . . )
### 18.3.25 Symbol ( . . . )
### 18.3.26 SyntaxError ( . . . )
### 18.3.27 TypeError ( . . . )
### 18.3.28 Uint8Array ( . . . )
### 18.3.29 Uint8ClampedArray ( . . . )
### 18.3.30 Uint16Array ( . . . )
### 18.3.31 Uint32Array ( . . . )
### 18.3.32 URIError ( . . . )
### 18.3.33 WeakMap ( . . . )
### 18.3.34 WeakSet ( . . . )
## 18.4 Other Properties of the Global Object
### 18.4.1 Atomics
### 18.4.2 JSON
### 18.4.3 Math
### 18.4.4 Reflect
# 19 Fundamental Objects
## 19.1 Object Objects
### 19.1.1 The Object Constructor
#### 19.1.1.1 Object ( [ value ] )
### 19.1.2 Properties of the Object Constructor
#### 19.1.2.1 Object.assign ( target, ...sources )
#### 19.1.2.2 Object.create ( O, Properties )
#### 19.1.2.3 Object.defineProperties ( O, Properties )
##### 19.1.2.3.1 RS: ObjectDefineProperties ( O, Properties )
#### 19.1.2.4 Object.defineProperty ( O, P, Attributes )
#### 19.1.2.5 Object.entries ( O )
#### 19.1.2.6 Object.freeze ( O )
#### 19.1.2.7 Object.getOwnPropertyDescriptor ( O, P )
#### 19.1.2.8 Object.getOwnPropertyDescriptors ( O )
#### 19.1.2.9 Object.getOwnPropertyNames ( O )
#### 19.1.2.10 Object.getOwnPropertySymbols ( O )
##### 19.1.2.10.1 RS: GetOwnPropertyKeys ( O, Type )
#### 19.1.2.11 Object.getPrototypeOf ( O )
#### 19.1.2.12 Object.is ( value1, value2 )
#### 19.1.2.13 Object.isExtensible ( O )
#### 19.1.2.14 Object.isFrozen ( O )
#### 19.1.2.15 Object.isSealed ( O )
#### 19.1.2.16 Object.keys ( O )
#### 19.1.2.17 Object.preventExtensions ( O )
#### 19.1.2.18 Object.prototype
#### 19.1.2.19 Object.seal ( O )
#### 19.1.2.20 Object.setPrototypeOf ( O, proto )
#### 19.1.2.21 Object.values ( O )
### 19.1.3 Properties of the Object Prototype Object
#### 19.1.3.1 Object.prototype.constructor
#### 19.1.3.2 Object.prototype.hasOwnProperty ( V )
#### 19.1.3.3 Object.prototype.isPrototypeOf ( V )
#### 19.1.3.4 Object.prototype.propertyIsEnumerable ( V )
#### 19.1.3.5 Object.prototype.toLocaleString ( [ reserved1 [ , reserved2 ] ] )
#### 19.1.3.6 Object.prototype.toString ( )
#### 19.1.3.7 Object.prototype.valueOf ( )
### 19.1.4 Properties of Object Instances
## 19.2 Function Objects
### 19.2.1 The Function Constructor
#### 19.2.1.1 Function ( p1, p2, … , pn, body )
##### 19.2.1.1.1 RS: CreateDynamicFunction( constructor, newTarget, kind, args )
### 19.2.2 Properties of the Function Constructor
#### 19.2.2.1 Function.length
#### 19.2.2.2 Function.prototype
### 19.2.3 Properties of the Function Prototype Object
#### 19.2.3.1 Function.prototype.apply ( thisArg, argArray )
#### 19.2.3.2 Function.prototype.bind ( thisArg, ...args )
#### 19.2.3.3 Function.prototype.call ( thisArg, ...args )
#### 19.2.3.4 Function.prototype.constructor
#### 19.2.3.5 Function.prototype.toString ( )
#### 19.2.3.6 Function.prototype [ @@hasInstance ] ( V )
### 19.2.4 Function Instances
#### 19.2.4.1 length
#### 19.2.4.2 name
#### 19.2.4.3 prototype
## 19.3 Boolean Objects
### 19.3.1 The Boolean Constructor
#### 19.3.1.1 Boolean ( value )
### 19.3.2 Properties of the Boolean Constructor
#### 19.3.2.1 Boolean.prototype
### 19.3.3 Properties of the Boolean Prototype Object
#### 19.3.3.1 Boolean.prototype.constructor
#### 19.3.3.2 Boolean.prototype.toString ( )
#### 19.3.3.3 Boolean.prototype.valueOf ( )
### 19.3.4 Properties of Boolean Instances
## 19.4 Symbol Objects
### 19.4.1 The Symbol Constructor
#### 19.4.1.1 Symbol ( [ description ] )
### 19.4.2 Properties of the Symbol Constructor
#### 19.4.2.1 Symbol.for ( key )
#### 19.4.2.2 Symbol.hasInstance
#### 19.4.2.3 Symbol.isConcatSpreadable
#### 19.4.2.4 Symbol.iterator
#### 19.4.2.5 Symbol.keyFor ( sym )
#### 19.4.2.6 Symbol.match
#### 19.4.2.7 Symbol.prototype
#### 19.4.2.8 Symbol.replace
#### 19.4.2.9 Symbol.search
#### 19.4.2.10 Symbol.species
#### 19.4.2.11 Symbol.split
#### 19.4.2.12 Symbol.toPrimitive
#### 19.4.2.13 Symbol.toStringTag
#### 19.4.2.14 Symbol.unscopables
### 19.4.3 Properties of the Symbol Prototype Object
#### 19.4.3.1 Symbol.prototype.constructor
#### 19.4.3.2 Symbol.prototype.toString ( )
##### 19.4.3.2.1 RS: SymbolDescriptiveString ( sym )
#### 19.4.3.3 Symbol.prototype.valueOf ( )
#### 19.4.3.4 Symbol.prototype [ @@toPrimitive ] ( hint )
#### 19.4.3.5 Symbol.prototype [ @@toStringTag ]
### 19.4.4 Properties of Symbol Instances
## 19.5 Error Objects
### 19.5.1 The Error Constructor
#### 19.5.1.1 Error ( message )
### 19.5.2 Properties of the Error Constructor
#### 19.5.2.1 Error.prototype
### 19.5.3 Properties of the Error Prototype Object
#### 19.5.3.1 Error.prototype.constructor
#### 19.5.3.2 Error.prototype.message
#### 19.5.3.3 Error.prototype.name
#### 19.5.3.4 Error.prototype.toString ( )
### 19.5.4 Properties of Error Instances
### 19.5.5 Native Error Types Used in This Standard
#### 19.5.5.1 EvalError
#### 19.5.5.2 RangeError
#### 19.5.5.3 ReferenceError
#### 19.5.5.4 SyntaxError
#### 19.5.5.5 TypeError
#### 19.5.5.6 URIError
### 19.5.6 NativeError Object Structure
#### 19.5.6.1 NativeError Constructors
#### 19.5.6.2 Properties of the NativeError Constructors
#### 19.5.6.3 Properties of the NativeError Prototype Objects
#### 19.5.6.4 Properties of NativeError Instances
# 20 Numbers and Dates
## 20.1 Number Objects
### 20.1.1 The Number Constructor
#### 20.1.1.1 Number ( value )
### 20.1.2 Properties of the Number Constructor
#### 20.1.2.1 Number.EPSILON
#### 20.1.2.2 Number.isFinite ( number )
#### 20.1.2.3 Number.isInteger ( number )
#### 20.1.2.4 Number.isNaN ( number )
#### 20.1.2.5 Number.isSafeInteger ( number )
#### 20.1.2.6 Number.MAX_SAFE_INTEGER
#### 20.1.2.7 Number.MAX_VALUE
#### 20.1.2.8 Number.MIN_SAFE_INTEGER
#### 20.1.2.9 Number.MIN_VALUE
#### 20.1.2.10 Number.NaN
#### 20.1.2.11 Number.NEGATIVE_INFINITY
#### 20.1.2.12 Number.parseFloat ( string )
#### 20.1.2.13 Number.parseInt ( string, radix )
#### 20.1.2.14 Number.POSITIVE_INFINITY
#### 20.1.2.15 Number.prototype
### 20.1.3 Properties of the Number Prototype Object
#### 20.1.3.1 Number.prototype.constructor
#### 20.1.3.2 Number.prototype.toExponential ( fractionDigits )
#### 20.1.3.3 Number.prototype.toFixed ( fractionDigits )
#### 20.1.3.4 Number.prototype.toLocaleString ( [ reserved1 [ , reserved2 ] ] )
#### 20.1.3.5 Number.prototype.toPrecision ( precision )
#### 20.1.3.6 Number.prototype.toString ( [ radix ] )
#### 20.1.3.7 Number.prototype.valueOf ( )
### 20.1.4 Properties of Number Instances
## 20.2 The Math Object
### 20.2.1 Value Properties of the Math Object
#### 20.2.1.1 Math.E
#### 20.2.1.2 Math.LN10
#### 20.2.1.3 Math.LN2
#### 20.2.1.4 Math.LOG10E
#### 20.2.1.5 Math.LOG2E
#### 20.2.1.6 Math.PI
#### 20.2.1.7 Math.SQRT1_2
#### 20.2.1.8 Math.SQRT2
#### 20.2.1.9 Math [ @@toStringTag ]
### 20.2.2 Function Properties of the Math Object
#### 20.2.2.1 Math.abs ( x )
#### 20.2.2.2 Math.acos ( x )
#### 20.2.2.3 Math.acosh ( x )
#### 20.2.2.4 Math.asin ( x )
#### 20.2.2.5 Math.asinh ( x )
#### 20.2.2.6 Math.atan ( x )
#### 20.2.2.7 Math.atanh ( x )
#### 20.2.2.8 Math.atan2 ( y, x )
#### 20.2.2.9 Math.cbrt ( x )
#### 20.2.2.10 Math.ceil ( x )
#### 20.2.2.11 Math.clz32 ( x )
#### 20.2.2.12 Math.cos ( x )
#### 20.2.2.13 Math.cosh ( x )
#### 20.2.2.14 Math.exp ( x )
#### 20.2.2.15 Math.expm1 ( x )
#### 20.2.2.16 Math.floor ( x )
#### 20.2.2.17 Math.fround ( x )
#### 20.2.2.18 Math.hypot ( value1, value2, ...values )
#### 20.2.2.19 Math.imul ( x, y )
#### 20.2.2.20 Math.log ( x )
#### 20.2.2.21 Math.log1p ( x )
#### 20.2.2.22 Math.log10 ( x )
#### 20.2.2.23 Math.log2 ( x )
#### 20.2.2.24 Math.max ( value1, value2, ...values )
#### 20.2.2.25 Math.min ( value1, value2, ...values )
#### 20.2.2.26 Math.pow ( base, exponent )
#### 20.2.2.27 Math.random ( )
#### 20.2.2.28 Math.round ( x )
#### 20.2.2.29 Math.sign ( x )
#### 20.2.2.30 Math.sin ( x )
#### 20.2.2.31 Math.sinh ( x )
#### 20.2.2.32 Math.sqrt ( x )
#### 20.2.2.33 Math.tan ( x )
#### 20.2.2.34 Math.tanh ( x )
#### 20.2.2.35 Math.trunc ( x )
## 20.3 Date Objects
### 20.3.1 Overview of Date Objects and Definitions of Abstract Operations
#### 20.3.1.1 Time Values and Time Range
#### 20.3.1.2 Day Number and Time within Day
#### 20.3.1.3 Year Number
#### 20.3.1.4 Month Number
#### 20.3.1.5 Date Number
#### 20.3.1.6 Week Day
#### 20.3.1.7 Local Time Zone Adjustment
#### 20.3.1.8 Daylight Saving Time Adjustment
#### 20.3.1.9 LocalTime ( t )
#### 20.3.1.10 UTC ( t )
#### 20.3.1.11 Hours, Minutes, Second, and Milliseconds
#### 20.3.1.12 MakeTime ( hour, min, sec, ms )
#### 20.3.1.13 MakeDay ( year, month, date )
#### 20.3.1.14 MakeDate ( day, time )
#### 20.3.1.15 TimeClip ( time )
#### 20.3.1.16 Date Time String Format
#### 20.3.1.16.1 Extended Years
### 20.3.2 The Date Constructor
#### 20.3.2.1 Date ( year, month [ , date [ , hours [ , minutes [ , seconds [ , ms ] ] ] ] ] )
#### 20.3.2.2 Date ( value )
#### 20.3.2.3 Date ( )
### 20.3.3 Properties of the Date Constructor
#### 20.3.3.1 Date.now ( )
#### 20.3.3.2 Date.parse ( string )
#### 20.3.3.3 Date.prototype
#### 20.3.3.4 Date.UTC ( year [ , month [ , date [ , hours [ , minutes [ , seconds [ , ms ] ] ] ] ] ] )
### 20.3.4 Properties of the Date Prototype Object
#### 20.3.4.1 Date.prototype.constructor
#### 20.3.4.2 Date.prototype.getDate ( )
#### 20.3.4.3 Date.prototype.getDay ( )
#### 20.3.4.4 Date.prototype.getFullYear ( )
#### 20.3.4.5 Date.prototype.getHours ( )
#### 20.3.4.6 Date.prototype.getMilliseconds ( )
#### 20.3.4.7 Date.prototype.getMinutes ( )
#### 20.3.4.8 Date.prototype.getMonth ( )
#### 20.3.4.9 Date.prototype.getSeconds ( )
#### 20.3.4.10 Date.prototype.getTime ( )
#### 20.3.4.11 Date.prototype.getTimezoneOffset ( )
#### 20.3.4.12 Date.prototype.getUTCDate ( )
#### 20.3.4.13 Date.prototype.getUTCDay ( )
#### 20.3.4.14 Date.prototype.getUTCFullYear ( )
#### 20.3.4.15 Date.prototype.getUTCHours ( )
#### 20.3.4.16 Date.prototype.getUTCMilliseconds ( )
#### 20.3.4.17 Date.prototype.getUTCMinutes ( )
#### 20.3.4.18 Date.prototype.getUTCMonth ( )
#### 20.3.4.19 Date.prototype.getUTCSeconds ( )
#### 20.3.4.20 Date.prototype.setDate ( date )
#### 20.3.4.21 Date.prototype.setFullYear ( year [ , month [ , date ] ] )
#### 20.3.4.22 Date.prototype.setHours ( hour [ , min [ , sec [ , ms ] ] ] )
#### 20.3.4.23 Date.prototype.setMilliseconds ( ms )
#### 20.3.4.24 Date.prototype.setMinutes ( min [ , sec [ , ms ] ] )
#### 20.3.4.25 Date.prototype.setMonth ( month [ , date ] )
#### 20.3.4.26 Date.prototype.setSeconds ( sec [ , ms ] )
#### 20.3.4.27 Date.prototype.setTime ( time )
#### 20.3.4.28 Date.prototype.setUTCDate ( date )
#### 20.3.4.29 Date.prototype.setUTCFullYear ( year [ , month [ , date ] ] )
#### 20.3.4.30 Date.prototype.setUTCHours ( hour [ , min [ , sec [ , ms ] ] ] )
#### 20.3.4.31 Date.prototype.setUTCMilliseconds ( ms )
#### 20.3.4.32 Date.prototype.setUTCMinutes ( min [ , sec [ , ms ] ] )
#### 20.3.4.33 Date.prototype.setUTCMonth ( month [ , date ] )
#### 20.3.4.34 Date.prototype.setUTCSeconds ( sec [ , ms ] )
#### 20.3.4.35 Date.prototype.toDateString ( )
#### 20.3.4.36 Date.prototype.toISOString ( )
#### 20.3.4.37 Date.prototype.toJSON ( key )
#### 20.3.4.38 Date.prototype.toLocaleDateString ( [ reserved1 [ , reserved2 ] ] )
#### 20.3.4.39 Date.prototype.toLocaleString ( [ reserved1 [ , reserved2 ] ] )
#### 20.3.4.40 Date.prototype.toLocaleTimeString ( [ reserved1 [ , reserved2 ] ] )
#### 20.3.4.41 Date.prototype.toString ( )
#### 20.3.4.41.1 RS: ToDateString( tv )
#### 20.3.4.42 Date.prototype.toTimeString ( )
#### 20.3.4.43 Date.prototype.toUTCString ( )
#### 20.3.4.44 Date.prototype.valueOf ( )
#### 20.3.4.45 Date.prototype [ @@toPrimitive ] ( hint )
### 20.3.5 Properties of Date Instances


# 21. Procesado de texto
# 22. Colecciones indexadas
# 23. Colecciones con clave
# 24. Datos estructurados
# 25. Objetos para Control de abstracciones
# 26. Reflexión
# 27. Modelo de memoria
# A. Sumario de gramática
# B. Características adicionales de ECMAScript para Navegadores Web
# C. El Modo Estricto de ECMAScript
# D. Correcciones y aclaraciones en ECMAScript2015 con posible impacto en la compatibilidad
# E. Adiciones y cambios que introducen incompatibilidades con ediciones anteriores
# F. Bibliografía
# G. Derechos de autor y licencia de software