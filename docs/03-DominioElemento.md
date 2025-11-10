# 📘 Capítulo 3: Dominios y Elementos de Datos en SAP ABAP Cloud

| [⬅️ Ir al Capítulo 2](../docs/02-HolaMundoABAP.md) | [↩️ Volver al inicio del proyecto](../README.md) |
| :------------------------------------------------: | :----------------------------------------------: |

---

> En este capítulo aprenderás a crear **dominios** y **elementos de datos** en SAP ABAP Cloud desde Eclipse. Estos objetos son fundamentales dentro del **Diccionario de Datos** (Data Dictionary), ya que definen cómo se almacena y manipula la información en el sistema SAP Cloud.

---

## 📚 Índice del Capítulo

| Sección                                                                         | Descripción                                                                            |
| :------------------------------------------------------------------------------ | :------------------------------------------------------------------------------------- |
| [🧭 ¿Qué es el Diccionario de Datos?](#-qué-es-el-diccionario-de-datos)         | Aprende qué papel cumple el Data Dictionary en ABAP Cloud y por qué es tan importante. |
| [🧩 Creación de un Dominio en Eclipse](#-creación-de-un-dominio-en-eclipse)     | Paso a paso para crear un dominio que defina las propiedades técnicas de tus campos.   |
| [⚙️ Configuración del Dominio (🛠️ desarrollando)](#️-configuración-del-dominio) | Explicación de los parámetros técnicos del dominio: tipo de dato, longitud y valores.  |

---

## 🧭 ¿Qué es el Diccionario de Datos?

El **Data Dictionary** es el lugar donde SAP almacena todos los objetos relacionados con los datos:

🌐 **Dominios** → Definen las propiedades técnicas de los campos (tipo, longitud, formato, valores permitidos).

🧩 **Elementos de datos** → Definen el significado y las propiedades semánticas de un campo.

📊 **Tablas y vistas** → Estructuras donde se guardan los datos propiamente dichos.

💡 En resumen, los dominios definen la “forma” del dato, y los elementos de datos definen su “significado”.

---

## 🧩 Creación de un Dominio en Eclipse

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

---

## ⚙️ Configuración del Dominio

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

---

## 🧱 Creación de un Elemento de Datos

> ⚠️ **Nota importante**: Los **dominios** no se usan directamente en programas, clases o tablas. Solo pueden ser utilizados a través de los **elementos de datos**.

👉 Por lo tanto, vamos a crear un elemento que use nuestro dominio ZBREA_DOM_URL. Vamos a nuestra raiz del proyecto.

![raiz proyecto](assets/tema-03/img-17.png)

👉 Podemos crear nuestro elemento de datos de la misma forma que hicimos al crear nuestro dominio: New > Other ABAP Repository Object y buscamos Data Element.

Pero tambien podemos crearlo haciando clic sobre la carpeta dictionary: new > data element

![creando desde dictionary](assets/tema-03/img-18.png)

👉 Ponemos un nombre a nuesto data element, por ejemplo ZBREA_ELEM_URL y una descripción - Elemento para almacenar URLs. Y pulsumanos next.

![data element](assets/tema-03/img-19.png)

👉 Las órdenes de transporte no existen en el modelo Cloud, lo dejamos vacio y le damos a finalizar.

![transport](assets/tema-03/img-20.png)

👉 Listo, ya nos aparece el Data Element en nuestra carpeta Dictionary del proyecto.

![raiz data element](assets/tema-03/img-21.png)

👉 Solo falta configuarar nuestro Data Element

![data element plantilla](assets/tema-03/img-22.png)

---

## 📐 Configurar un Elemento de Datos en ABAP Cloud


---

[ 🛠️ desarrollando ...]

---

| [⬅️ Ir al Capítulo 2](../docs/02-HolaMundoABAP.md) | [⬆️ Ir al inicio del capítulo](#-capítulo-3-dominios-y-elementos-de-datos-en-sap-abap-cloud) | [↩️ Volver al inicio del proyecto](../README.md) |
| :------------------------------------------------: | :------------------------------------------------------------------------------------------: | :----------------------------------------------: |
