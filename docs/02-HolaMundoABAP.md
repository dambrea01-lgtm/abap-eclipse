# 🚀 Capítulo 2: ¡Hola Mundo! Soy ABAP 🌍

| [⬅️ Ir al Capítulo 1](../docs/01-Introduccion.md) | [↩️ Volver al inicio del proyecto](../README.md) |
| :-----------------------------------------------: | :----------------------------------------------: |

---

En este capítulo vamos a dar nuestros primeros pasos reales en ABAP Cloud. Después de haber instalado Eclipse y conectado nuestro entorno en SAP BTP, ahora aprenderemos a entender el entorno de trabajo (el famoso Project Explorer) y crearemos nuestro primer programa ABAP: “¡Hola Mundo! Soy ABAP”.

---

## 🧭 Explorando Eclipse y el Project Explorer

Antes de programar nada, veamos qué tenemos en pantalla cuando abrimos nuestro entorno ABAP en Eclipse. Después de haber configurado todo en el Capítulo 1, ahora deberías ver algo así en el panel izquierdo 👇

![Project Explorer](assets/tema-02/img-tema02-00.png)

- 🧩 **¿Qué es todo esto?**

Cuando conectas tu Eclipse con tu cuenta SAP BTP ABAP Cloud trial, SAP automáticamente crea una conexión al sistema TRL (Trial). No te preocupes, tú no creaste nada manualmente: esto viene preconfigurado para que puedas empezar a practicar sin tocar objetos del sistema.

| **Elemento**                            | **Qué es**                               | **Lo creaste tú** | **Para qué sirve**                                                     |
| :-------------------------------------- | :--------------------------------------- | :---------------: | :--------------------------------------------------------------------- |
| **TRL_EN [TRL, 100, CB9980002564, EN]** | Tu conexión activa a **ABAP Cloud**      |       ❌ No       | Es tu entorno Cloud, conectado con **SAP BTP**.                        |
| **Favorite Packages (42629)**           | Todos los **paquetes del sistema**       |       ❌ No       | Contiene el **código base estándar** de SAP.                           |
| **Favorite Objects (0)**                | Tu **lista personal de favoritos**       | ⚙️ Tú los añades  | Permite tener **acceso rápido** a tus programas y clases.              |
| **Released Objects (6309)**             | Objetos públicos **“liberados” por SAP** |       ❌ No       | Son las **APIs disponibles** que puedes usar libremente en ABAP Cloud. |

> 💡 Dato curioso: En ABAP Cloud solo puedes usar objetos liberados. Esto garantiza que todo tu código sea compatible con el entorno cloud y no dependa de funciones internas del sistema.

---

( desarrollando ... )

---

| [⬅️ Ir al Capítulo 1](../docs/01-Introduccion.md) | [↩️ Volver al inicio del proyecto](../README.md) |
| :-----------------------------------------------: | :----------------------------------------------: |
