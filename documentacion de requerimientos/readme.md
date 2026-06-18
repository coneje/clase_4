# Manual de Supervivencia: Ingeniería de Requerimientos

Este documento resume la realidad de la gestión de requerimientos, dejando de lado la burocracia innecesaria para enfocarse en lo que realmente importa: sobrevivir en el mundo del desarrollo de software sin problemas graves de comunicación o pérdidas de información.

---

## 1. El gran mito de "Lo tengo en la cabeza"

Es común caer en la trampa de pensar que escribir es una pérdida de tiempo. Sin embargo, en el desarrollo de software la memoria falla, el personal rota y los clientes olvidan lo que prometieron o solicitaron originalmente.

* **Si no lo escribes, no existe:** Documentar no es burocracia; es un respaldo indispensable cuando el cliente afirma no haber solicitado una característica específica, o cuando el programador principal renuncia dejando un código difícil de interpretar.
* **Las 5 funciones clave de un documento:**
    1. **Acuerdo:** El contrato real con el cliente sobre el alcance del proyecto.
    2. **Guía:** El mapa técnico para que los desarrolladores no tengan que adivinar las reglas de negocio.
    3. **Verificación:** El libreto que utilizan los encargados de pruebas (testers) para validar el sistema.
    4. **Conocimiento:** La memoria del proyecto que sobrevive a la rotación de personal.
    5. **Respaldo Legal:** La defensa ante auditorías, revisiones fiscales o disputas contractuales.

---

## 2. El SRS (IEEE 830): El plano de la casa

Construir un software sin documentación es equivalente a construir una casa solo hablando con el albañil de forma verbal. El SRS (Software Requirements Specification) funciona como el plano oficial. El estándar IEEE 830 proporciona una estructura prediseñada para asegurar que no se omitan aspectos clave durante el levantamiento de información.

### Estructura base del estándar
* **1. Introducción:** Propósito del software, alcance del proyecto y normativas o leyes aplicables que se deben cumplir.
* **2. Descripción general:** Contexto del producto, perfiles de los usuarios que interactuarán con el sistema (usuarios casuales, administradores) y restricciones de tiempo o presupuesto.
* **3. Requisitos específicos:** El núcleo técnico del documento, dividido en:
    * **Requerimientos Funcionales (RF):** Lo que el software debe hacer (acciones, botones, flujos de pantallas).
    * **Requerimientos No Funcionales (RNF):** Cómo se debe comportar el software (velocidad, seguridad, estabilidad, disponibilidad).

---

## 3. Casos de Uso: Contar la historia completa

Mientras que un requerimiento funcional define una acción puntual ("El sistema debe permitir iniciar sesión"), el Caso de Uso funciona como el libreto de dicha acción. Narra de forma secuencial los pasos exactos que realiza el usuario (Actor) y cómo responde el software (Sistema).

### Componentes clave
* **Flujo principal (Camino feliz):** La secuencia de pasos cuando todo sale de forma correcta al primer intento.
* **Excepciones y flujos alternos:** Los escenarios donde el usuario introduce datos erróneos, se pierde la conexión a internet o el recurso solicitado no está disponible. Si no se diseñan estos escenarios, el sistema presentará fallas críticas en producción.
* **Relaciones en diagramas (UML):**
    * **Include (Incluye):** Un flujo que obligatoriamente ocurre dentro de otro (por ejemplo, "Reservar libro" incluye de forma mandatoria "Iniciar sesión").
    * **Extend (Extiende):** Un comportamiento opcional que se ejecuta únicamente bajo ciertas condiciones (por ejemplo, "Reservar libro" se extiende a "Pagar multa" si el usuario registra una deuda pendiente).

---

## 4. La revisión cruzada: Validación objetiva

Tras trabajar de forma prolongada en la redacción de un documento, el autor suele desarrollar fatiga visual o sesgos conceptuales. Contar con un compañero analista que revise el SRS antes de presentarlo al cliente previene errores de diseño costosos.

### Antipatrones y errores a detectar:
* **Ambigüedades:** Uso de palabras subjetivas que quedan abiertas a la libre interpretación del lector.
* **Falta de atomicidad:** Agrupar múltiples funciones independientes dentro de un mismo enunciado (por ejemplo: "El sistema permite borrar usuarios, mandar SMS y generar reportes"). Los requerimientos deben desglosarse de forma individual con un ID único para cada función.
* **Exceso de jerga técnica frente al cliente:** Al usuario final o cliente no le corresponde validar detalles de implementación como "header Authorization Bearer JWT". La jerga técnica se reserva para las especificaciones de arquitectura y el código, no para los requerimientos que el cliente debe firmar como aceptados.
* **Contradicciones internas:** Declarar en una sección que la base de datos es de acceso público y en otra exigir restricciones severas de autenticación para consultar la misma información.