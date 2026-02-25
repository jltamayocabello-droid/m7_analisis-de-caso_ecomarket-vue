Análisis de Caso
Lección 1: Componentes y su ciclo de vida en vue componentización
Situación inicial 📍
La empresa EcoMarket, dedicada a la venta online de productos ecológicos y
sostenibles, se encuentra en pleno proceso de rediseño de su aplicación web. El
equipo de desarrollo ha decidido migrar su plataforma a Vue.js para mejorar la
mantenibilidad del código, la escalabilidad del sistema y la velocidad de
implementación de nuevas funcionalidades.
Actualmente, la aplicación tiene muchas vistas repetidas y elementos duplicados
en HTML, lo que genera dificultades para mantener el código y aplicar
actualizaciones visuales de forma consistente. No se utilizan componentes
reutilizables ni estructuras modulares, y no hay una estrategia clara para
gestionar el ciclo de vida de cada parte de la interfaz.
El desafío es reorganizar la interfaz actual en base a componentes reutilizables,
garantizando una arquitectura más limpia y flexible. La empresa necesita
además que los componentes puedan comunicarse correctamente entre sí,
responder a eventos, adaptarse visualmente a distintas condiciones y ser
fácilmente escalables a futuro.
Descripción del Caso 🔎
Asumirás el rol de desarrollador/a front-end dentro del equipo técnico de
EcoMarket. Tu responsabilidad será liderar la reestructuración de la interfaz
actual utilizando componentes en Vue.js, aplicando buenas prácticas de
componentización y aprovechando los hooks del ciclo de vida para gestionar
correctamente el comportamiento de la aplicación.
Como parte del análisis, deberás identificar qué secciones del sitio pueden
convertirse en componentes, cómo deben comunicarse entre ellos (props,
eventos, slots), y en qué momentos del ciclo de vida se deben ejecutar tareas
críticas como llamadas a API o limpieza de recursos.
También deberás definir una estructura clara para los componentes (jerarquía
padre-hijo), aplicar estilos encapsulados con scoped, y asegurar que la nueva
arquitectura facilite futuras expansiones del sitio.

Instrucciones 💡
Tu análisis y propuesta deben abordar los siguientes puntos:
1. Identificación de componentes reutilizables
○ Detecta al menos tres secciones de la tienda actual que puedan
transformarse en componentes reutilizables.
○ Justifica por qué cada sección debe convertirse en un componente.
2. Diseño de la jerarquía de componentes
○ Establece qué componentes serán padres y cuáles hijos.
○ Define qué props deberá recibir cada hijo y qué eventos emitirá.
3. Uso de slots y componentes dinámicos
○ Propón un componente que utilice slots para adaptarse a diferentes
contextos.
○ Describe una situación donde sería útil aplicar un componente
dinámico con :is.
4. Aplicación del ciclo de vida
○ Elige al menos dos hooks del ciclo de vida y explica cómo los usarías
en el contexto de la aplicación (ej. carga de datos, suscripciones,
animaciones).
5. Buenas prácticas de estilo
○ Explica cómo usarías class binding, style binding y el
atributo scoped para lograr una interfaz clara y mantenible.

6. Reflexión final
○ ¿Qué ventajas trae la componentización en comparación con una
interfaz monolítica?

○ ¿Cómo mejora el mantenimiento y la colaboración en equipo?