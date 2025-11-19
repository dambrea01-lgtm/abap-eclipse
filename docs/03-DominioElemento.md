# 📘 Capítulo 3: Dominios y Elementos de Datos en SAP ABAP Cloud

| [⬅️ Ir al Capítulo 2](../docs/02-HolaMundoABAP.md) | [↩️ Volver al inicio del proyecto](../README.md) |
| :------------------------------------------------: | :----------------------------------------------: |

<br/>
<hr/>
<br/>

> En este capítulo aprenderás a crear **dominios** y **elementos de datos** en SAP ABAP Cloud desde Eclipse. Estos objetos son fundamentales dentro del **Diccionario de Datos** (Data Dictionary), ya que definen cómo se almacena y manipula la información en el sistema SAP Cloud.

<br/>
<hr/>
<br/>

## 📚 Índice del Capítulo

| Sección                                                                                                     | Descripción                                                                                  |
| :---------------------------------------------------------------------------------------------------------- | :------------------------------------------------------------------------------------------- |
| [1. 🧭 ¿Qué es el Diccionario de Datos?](#1--qué-es-el-diccionario-de-datos)                                | Aprende qué papel cumple el Data Dictionary en ABAP Cloud y por qué es tan importante.       |
| [2. 🧩 Creación de un Dominio en Eclipse](#2--creación-de-un-dominio-en-eclipse)                            | Paso a paso para crear un dominio que defina las propiedades técnicas de tus campos.         |
| [3. ⚙️ Configuración del Dominio](#3-️-configuración-del-dominio)                                           | Explicación de los parámetros técnicos del dominio: tipo de dato, longitud y valores.        |
| [4. 🧱 Creación de un Elemento de Datos](#4--creación-de-un-elemento-de-datos)                              | Aprende a crear un elemento de datos que use tu dominio o un tipo predefinido.               |
| [5. 📐 Configurar un Elemento de Datos en ABAP Cloud](#5--configurar-un-elemento-de-datos-en-abap-cloud)    | Configura las propiedades técnicas y semánticas de un elemento de datos paso a paso.         |
| [6. 🎯 Diferencias Clave: Dominio vs Elemento de Datos](#6--diferencias-clave-dominio-vs-elemento-de-datos) | Tabla resumida de las diferencias fundamentales entre dominios y elementos de datos.         |
| [7. 📝Ejercicios Propuestos](#7-ejercicios-propuestos)                                                      | Ejercicios propuestos y resueltos de diferentes niveles sobre dominios y elementos de datos. |

<br/>
<hr/>
<br/>

## [1. 🧭 ¿Qué es el Diccionario de Datos?](#-índice-del-capítulo)

El **Data Dictionary** es el lugar donde SAP almacena todos los objetos relacionados con los datos:

🌐 **Dominios** → Definen las propiedades técnicas de los campos (tipo, longitud, formato, valores permitidos).

🧩 **Elementos de datos** → Definen el significado y las propiedades semánticas de un campo.

📊 **Tablas y vistas** → Estructuras donde se guardan los datos propiamente dichos.

💡 En resumen, los dominios definen la “forma” del dato, y los elementos de datos definen su “significado”.

<br/>
<hr/>
<br/>

## [2. 🧩 Creación de un Dominio en Eclipse](#-índice-del-capítulo)

Te muestro a continuación, como crear un dominio en tu proyecto ABAP SAP Cloud. Por ejemplo, yo voy a usar el paquete donde trabajamos el "Hola Mundo" del capitulo 2 (ZBREA_TUTORIAL)

![Paquete ZBREA_TUTORIAL](assets/tema-03/img-01.png)

👉 Nos posicionamos con el cursor encima de nuestro paquete y hacemos click boton derecho y seleccionamos: New > Other ABAP Repository Object

![Other ABAP Repository Object](assets/tema-03/img-02.png)

👉 Busca Domain 🔍 y haz Clic en Next

![Domain](assets/tema-03/img-03.png)

👉 Escribe un nombre y una descripción, por ejmplo ZBREA_DOM_URL – Dominio para URLs "es muy recomendable que uses siempre tus iniciales Z(tus iniciales) para cuando tengas que buscar algo creado por ti, lo encuentres rápido, ya que estamos en el modo de prueba".

![Domain](assets/tema-03/img-04.png)

👉 En ABAP Cloud (Eclipse, entorno BTP) los objetos no se transportan con órdenes de transporte clásicas como en los sistemas on-premise (SAP ECC o S/4HANA local). Es decir, las órdenes de transporte no existen en el modelo Cloud, ya que los objetos se guardan directamente en el paquete del software component o del namespace asignado a tu espacio de desarrollo.

Por eso sale vacio estos campos, solo haz clic en finalizar (finish)

![Domain](assets/tema-03/img-05.png)

👉Podemos ver en la raiz de nuestro proyecto, como se ha generado el dominio que acabamos de crear:

![dominio en la raiz del proyecto](assets/tema-03/img-15.png)

👉 Y listo ya tenemos el dominio creado a la espera de una configuración.

![Domain](assets/tema-03/img-06.png)

<br/>
<hr/>
<br/>

## [3. ⚙️ Configuración del Dominio](#-índice-del-capítulo)

> Es importante desde mi punto de vista, conocer bien, como se configura un dominio en ABAP SAP. Analizo campo por campo:

👇
| Propiedad | Descripción | Ejemplo práctico |
| :------------ | :----------------------------------------------------------------------------------------------------------- | :---------------------------------------------------------------------------------------------------------------------------- |
| **Data Type** | Tipo de dato físico en base de datos (ej. `CHAR`, `NUMC`, `DEC`, `INT`). Define cómo se guarda internamente. | `CHAR` para texto, `NUMC` para números almacenados como caracteres (p. ej. códigos), `DEC` para valores decimales monetarios. |

![data type](assets/tema-03/img-07.png)

👇
| Propiedad | Descripción | Ejemplo práctico |
| :--------- | :------------------------------------------------------------------------------------------------ | :----------------------------------------------------------- |
| **Length** | Longitud máxima del campo (nº de caracteres o posiciones). Es el tamaño real en la base de datos. | `URL`: 255 &nbsp;&nbsp;•&nbsp;&nbsp; `Código país (NUMC)`: 3 |

![length](assets/tema-03/img-08.png)

👇
| Propiedad | Descripción | Ejemplo práctico |
| :---------------- | :----------------------------------------------------------------------------------------- | :------------------------------------------------------------------------------------ |
| **Output Length** | Longitud que se mostrará en pantallas o formularios. Puede ser menor o igual a **Length**. | Si `Length = 20` y `Output Length = 15`, solo se mostrarán 15 caracteres en pantalla. |

![output length](assets/tema-03/img-09.png)

👇
| Propiedad | Descripción | Ejemplo práctico |
| :----------------- | :----------------------------------------------------------------------------------------------------------------- | :--------------------------------------------------------------------------------------------------------------- |
| **Decimal Places** | Número de decimales que almacena el campo; define la posición del punto decimal. Solo aplicable a campos tipo DEC. | Importe en euros: 2 decimales. Si `Length = 13` y `Decimals = 2`, acepta hasta 11 dígitos enteros + 2 decimales. |

![decimal places](assets/tema-03/img-10.png)

👇
| Propiedad | Descripción | Ejemplo práctico |
| :----------------- | :------------------------------------------------------------------------------ | :------------------------------------------------------------------------------------------------------- |
| **Case Sensitive** | Indica si el campo distingue entre mayúsculas y minúsculas al comparar (A ≠ a). | URL: normalmente no sensible; códigos tipo AB12 pueden ser case-sensitive si se necesita diferenciarlos. |

![case sensitive](assets/tema-03/img-11.png)

👇
| Propiedad | Descripción | Ejemplo práctico |
| :--------------- | :----------------------------------------------------------------------------------- | :------------------------------------------------ |
| **Fixed Values** | Lista de valores permitidos; si se completa, solo se podrán introducir esos valores. | Estados: A = Activo, I = Inactivo, B = Bloqueado. |

![fixed values](assets/tema-03/img-12.png)

👇
| Propiedad | Descripción | Ejemplo práctico |
| :---------------------------- | :------------------------------------------------------- | :------------------------------------------ |
| **Value Table / Check Table** | Referencia a una tabla para validar valores, si procede. | T005 (países) para validar códigos de país. |

![value table](assets/tema-03/img-13.png)

👇
Nuestro ejemplo usaremos CHAR, con length 255, con output length 100, no case-sensitive

![ejemplo final](assets/tema-03/img-14.png)

Para finalizar activamos nuestro dominio, haciendo clic en el icono (que parece una cerilla) o pulstamos ctrl + F3

![activamos](assets/tema-03/img-16.png)

<br/>
<hr/>
<br/>

## [4. 🧱 Creación de un Elemento de Datos](#-índice-del-capítulo)

> ⚠️ **Nota importante**: Los **dominios** no se usan directamente en programas, clases o tablas. Solo pueden ser utilizados a través de los **elementos de datos**.

👉 Por lo tanto, vamos a crear un elemento que use nuestro dominio ZBREA_DOM_URL. Vamos a nuestra raiz del proyecto.

![raiz proyecto](assets/tema-03/img-17.png)

👉 Podemos crear nuestro elemento de datos de la misma forma que hicimos al crear nuestro dominio: New > Other ABAP Repository Object y buscamos Data Element.

Pero tambien podemos crearlo haciando clic sobre la carpeta dictionary: new > data element

![creando desde dictionary](assets/tema-03/img-18.png)

👉 Ponemos un nombre a nuesto data element, por ejemplo ZBREA_ELEM_URL y una descripción - Elemento para almacenar URLs. Y pulsumanos next.

![data element](assets/tema-03/img-19.png)

👉 Las órdenes de transporte no existen en el modelo Cloud, lo dejamos vacio y le damos a finalizar.

![transport](assets/tema-03/img-23.png)

👉 Listo, ya nos aparece el Data Element en nuestra carpeta Dictionary del proyecto.

![raiz data element](assets/tema-03/img-21.png)

👉 Solo falta configuarar nuestro Data Element

![data element plantilla](assets/tema-03/img-22.png)

<br/>
<hr/>
<br/>

## [5. 📐 Configurar un Elemento de Datos en ABAP Cloud](#-índice-del-capítulo)

> Los **elementos de datos** son objetos que definen **características técnicas y semánticas** de un campo, variable o parámetro en ABAP Cloud. Pueden crearse a partir de un **dominio** o de un **tipo predefinido**. Vamos a verlo paso a paso.

### 🔹 Elemento de Datos Basado en un Dominio

👉 Cuando usamos un dominio, el elemento de datos hereda automáticamente las propiedades técnicas definidas allí (tipo de dato, longitud, decimales, etc.), lo que ayuda a mantener **consistencia y reutilización**.

En el campo **Domain**, escribe el nombre del dominio que creaste antes, en mi caso:  
 `ZBREA_DOM_URL` y veras como se cargan automáticamente sus propiedades.

![asignando dominio al elemento de dato](assets/tema-03/img-24.png)

👉 Define las propiedades **semánticas**: En mi caso de ejemplo lo escribo todo URL

![semantica del elemento de dato](assets/tema-03/img-25.png)

👉 Activa el elemento de datos haciendo clic en **Activate** o pulsando ctrl + F3.

![activamos elemento de datos](assets/tema-03/img-16.png)

> 🧩 Este tipo de elemento **hereda las propiedades técnicas del dominio**, asegurando consistencia y facilidad de mantenimiento.

<br/>
<hr/>
<br/>

### 🔹 Elemento de Datos con Tipo Predefinido

> Tenemos otra forma, si prefieres un método más rápido o no necesitas un dominio, puedes definir directamente el tipo de dato en el elemento:

👉 Tenemos que seleccionar **Predefined Type** en lugar de Domain.

![seleccionando predefined type](assets/tema-03/img-26.png)

👉 Define el tipo de dato directamente: por ejemplo `CHAR` con longitud `255` para nuestra URL.

![datos de predefined type](assets/tema-03/img-27.png)

👉 Esto es igual que el otro método, agrega la descripción y otros textos semánticos si lo deseas. Para finalizar activa el elemento de datos con ctrl + F3 o pulsando al icono en forma de cerilla.

> 💡 Este método es más rápido, pero **no aprovecha la reutilización ni la consistencia** que ofrecen los dominios.

### 🔹 Diferencias Clave

| Característica              | Basado en Dominio | Tipo Predefinido |
| --------------------------- | ----------------- | ---------------- |
| Reutilización               | ✅ Sí             | ❌ No            |
| Consistencia                | ✅ Alta           | ⚠️ Limitada      |
| Tiempo de creación          | ⚠️ Mayor          | ✅ Más rápido    |
| Hereda propiedades técnicas | ✅ Sí             | ❌ No            |

👉 Anotar que ambos metodos tienen propiedades adicionales, que ahora mismo no nos hace falta aprender, pero es bueno que lo veas

![datos de predefined type](assets/tema-03/img-28.png)

Ahora sabes cómo crear elementos de datos en ABAP Cloud y cuándo conviene usar un dominio frente a un tipo predefinido.

> 💡 **Tip:** A diferencia de los dominios, los **Elementos de Datos** sí se pueden usar directamente en tus objetos ABAP Cloud, como **clases**, **tablas**, **vistas**, **variables** y **parámetros de métodos**. Esto los hace mucho más flexibles para tus desarrollos.

<br/>
<hr/>
<br/>

## [6. 🎯 Diferencias Clave: Dominio vs Elemento de Datos](#-índice-del-capítulo)

Antes de mostrar la comparación, es importante entender que tanto los **dominios** como los **elementos de datos** son piezas fundamentales del Diccionario de Datos en ABAP Cloud.

Mientras que los dominios se enfocan en la **definición técnica** de un campo, los elementos de datos agregan un **significado semántico** y permiten que esos campos sean utilizados directamente en tablas, clases y otros objetos del sistema.

La siguiente tabla resume las diferencias clave entre ambos:

| Característica               | Dominio 🌐 | Elemento de Datos 🧩 |
| ---------------------------- | ---------- | -------------------- |
| Define tipo técnico          | ✅         | ✅ (si usa dominio)  |
| Define significado semántico | ❌         | ✅                   |
| Se usa en tablas y clases    | ❌         | ✅                   |
| Tiene valores fijos          | ✅         | ❌ (solo los hereda) |

<br/>
<hr/>
<br/>

## [7. 📝Ejercicios Propuestos](#-índice-del-capítulo)

👉 **Ejercicio 1 — Nivel Básico: Crear un Dominio y un Elemento de Datos para almacenar un código de país**

**🎯 Objetivo:** Aprender a crear un dominio simple y un elemento de datos que lo utilice.

**📘 Enunciado**: Crea un dominio llamado ZBREA_DOM_PAIS que almacene códigos de país de 3 caracteres. Luego, crea un elemento de datos llamado ZBREA_ELEM_PAIS que use este dominio.

**💡 Pistas**: - Usa tipo de dato CHAR con longitud 3. - No hace falta usar valores fijos. - El elemento de datos debe usar el dominio.

> [🔗 Enlace de ejercicio 1 resuelto paso a paso](../ejercicios/capitulo-03/ejercicio-01.md)

<hr/>

👉 **Ejercicio 2 — Nivel Intermedio: Crear un Dominio con valores fijos y un Elemento de Datos que los herede**

**🎯 Objetivo:** Aprender a usar valores fijos en un dominio y ver cómo los hereda un elemento de datos.

**📘 Enunciado:** Crea un dominio llamado ZBREA_DOM_ESTADO para almacenar un estado simple de un registro: A = Activo - I = Inactivo - B = Bloqueado. Luego crea un elemento de datos ZBREA_ELEM_ESTADO que utilice este dominio.

**💡 Pistas:** - Usa tipo CHAR(1) - Agrega los valores fijos en la sección Fixed Values - El elemento de datos los heredará automáticamente

<hr/>

👉 **Ejercicio 3 — Nivel Avanzado: Optimización semántica**

**🎯 Objetivo:** Crear un elemento de datos con una semántica avanzada y comprender cómo influye en herramientas SAP sin necesidad de tablas.

**📘 Enunciado:** Crea un dominio ZBREA_DOM_CODAPP, pensado para almacenar un "Código interno de una aplicación". Debe ser case-sensitive. Debe permitir valores entre 5 y 10 caracteres (longitud fija 10). No uses valores fijos. Luego crea un elemento de datos ZBREA_ELEM_CODAPP con las siguientes condiciones: Hereda el dominio. Define textos semánticos completos (Short, Medium, Long). En Heading debe aparecer "Código App". En Documentation agrega una descripción útil para otros desarrolladores.

**Pregunta avanzada:** Explica por qué sería mejor usar dominio en este caso y no un tipo predefinido.

<br/>
<hr/>
<br/>

| [⬅️ Ir al Capítulo 2](../docs/02-HolaMundoABAP.md) | [⬆️ Ir al inicio del capítulo](#-capítulo-3-dominios-y-elementos-de-datos-en-sap-abap-cloud) | [↩️ Volver al inicio del proyecto](../README.md) |
| :------------------------------------------------: | :------------------------------------------------------------------------------------------: | :----------------------------------------------: |
