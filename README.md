# 🛒 Análisis de Caso: EcoMarket - Prototipo Vue 3

![Estado del Proyecto](https://img.shields.io/badge/Estado-Finalizado-yellow)
![Stack](https://img.shields.io/badge/Stack-Vue.js_3_%7C_Vue_Router_%7C_Vite_%7C_CSS-blue)

---

## 📖 Descripción del Proyecto

**Unidad solicitante: EcoMarket**

La empresa EcoMarket, dedicada a la venta online de productos ecológicos y sostenibles, se encuentra en pleno proceso de rediseño de su aplicación web. El equipo de desarrollo ha decidido migrar su plataforma a **Vue.js** para mejorar la mantenibilidad del código, la escalabilidad del sistema y la velocidad de implementación de nuevas funcionalidades.

Anteriormente, la aplicación presentaba vistas repetidas y elementos duplicados, lo que dificultaba el mantenimiento y la consistencia visual. Este prototipo reorganiza la interfaz actual basándose en **componentes reutilizables**, garantizando una arquitectura más limpia, una comunicación fluida entre componentes y una gestión eficiente del ciclo de vida.

---

## 🎯 Objetivo

El objetivo principal es la reestructuración de la interfaz actual utilizando componentes en Vue.js, aplicando buenas prácticas de componentización y aprovechando los hooks del ciclo de vida para gestionar correctamente el comportamiento de la aplicación.

Como parte del análisis, se identificaron las secciones del sitio que pueden convertirse en componentes, definiendo cómo deben comunicarse entre ellos (props, eventos, slots) y determinando los momentos críticos para la ejecución de tareas, como llamadas a API o limpieza de recursos.

---

## 🔍 Análisis Inicial y Propuesta de Solución

Debido a que la aplicación de EcoMarket contenía múltiples vistas repetidas y elementos redundantes en HTML —lo cual dificultaba el mantenimiento y la aplicación de actualizaciones visuales consistentes— se concluyó que era necesaria una reestructuración integral. Esta transformación busca mejorar tanto la experiencia del usuario como la calidad del código, aplicando los principios de la componentización y aprovechando el sistema de hooks de Vue.js para una gestión óptima del ciclo de vida.

Por lo anterior, se propone la siguiente solución técnica:

### 1. Jerarquía de Componentes

Se ha diseñado una arquitectura modular y escalable para el catálogo de productos:

- **`ShopView.vue` (Padre/Vista)**: Orquesta el estado global (productos, carga, carrito).
  - **`ProductList.vue` (Hijo)**: Recibe la prop `products` (Array) y emite el evento `add-to-cart`.
    - **`ProductCard.vue` (Nieto)**: Recibe la prop `product` (Objeto) y emite el evento `add-to-cart` (ID del producto).
      - **`BaseBadge.vue` (Hijo de Card)**: Recibe props `label` y `variant` para estados visuales.
- **`BaseModal.vue` (Padre Genérico)**: Controlado desde `ShopView` para mostrar el carrito o detalles.
- **`ProductDetails.vue` (Hijo de ShopView)**: Contenedor independiente para información extendida del producto.

### 2. Uso de Slots y Componentes Dinámicos

- **Slots (`BaseModal.vue`)**: Se utilizan **Named Slots** (`#header`, `#footer`) y un slot por defecto. Esto permite que el mismo modal sirva para mostrar el carrito o alertas de confirmación, inyectando contenido dinámico sin duplicar la lógica estructural.
- **Componentes Dinámicos (`ProductDetails.vue`)**: Utiliza `<component :is="currentTab" />` para alternar entre **Descripción** e **Impacto Eco** de forma fluida, optimizado con `<KeepAlive>` para mantener el estado entre pestañas.

### 3. Aplicación del Ciclo de Vida

Se han implementado los siguientes hooks clave:

- **`onMounted`**: Se ejecuta al insertar la vista principal (`ShopView`) en el DOM para realizar la carga inicial de datos (simulada con un retardo de 1.5s), asegurando una transición suave para el usuario.
- **`onUnmounted`**: Utilizado para la limpieza de recursos, como la destrucción de listeners globales o temporizadores, previniendo posibles fugas de memoria (_Memory Leaks_).

### 4. Buenas Prácticas de Estilo

- **Class Binding (`:class`)**: Aplicado para gestionar estados dinámicos en badges y pestañas activas.
- **Style Binding (`:style`)**: Utilizado para valores calculados en tiempo real según el estado de la aplicación.
- **`scoped`**: El uso de `<style scoped>` en todos los componentes garantiza un diseño modular y evita colisiones de estilos globales.

---

## 🛠️ Requerimientos Técnicos

Este proyecto cumple con los criterios exigidos en el análisis de caso:

1. **Jerarquía de Componentes**: Arquitectura modular con flujo de datos descendente (props) y ascendente (emits).
2. **Slots y Componentes Dinámicos**: Implementación de contenedores adaptables y renderizado dinámico eficiente.
3. **Ciclo de Vida**: Uso estratégico de hooks para la gestión reactiva de datos y recursos.
4. **Buenas Prácticas de Estilo**: Uso de bindings dinámicos y encapsulamiento estricto de CSS.

---

## 📂 Documentación Técnica

### 1. 🚀 Stack Tecnológico

- **Vue 3**: Composition API y `<script setup>`.
- **Vite**: Entorno de desarrollo y empaquetado de alto rendimiento.
- **CSS3 Scoped**: Estilos modernos y modulares.
- **Git/GitHub**: Gestión del código fuente.

### 2. Estructura del Proyecto

```text
m7_analisis-de-caso_ecomarket-vue/
│
├── index.html
├── README.md
├── package.json
├── vite.config.js
│
└── src/
    ├── main.js                   # Punto de entrada
    ├── App.vue                   # Componente raíz
    │
    ├── views/
    │   └── ShopView.vue          # Vista principal / Catálogo
    │
    └── components/
        ├── BaseBadge.vue         # Etiqueta visual reutilizable
        ├── BaseModal.vue         # Modal genérico con Slots
        ├── ProductCard.vue       # Tarjeta de producto
        ├── ProductList.vue       # Grilla iteradora
        ├── ProductDetails.vue    # Contenedor de Tabs Dinámicos
        ├── TabDescription.vue    # Pestaña de Descripción
        └── TabImpact.vue         # Pestaña de Impacto Ecológico
```

### 3. Arquitectura y Responsabilidades

- **`ShopView.vue`**: Centraliza el estado reactivo (`products`, `cartCount`) y controla la visibilidad de los componentes modulares.
- **`ProductCard.vue`**: Encargado de la representación visual del producto y de notificar acciones al padre.
- **`BaseModal.vue`**: Provee una estructura base versátil para diálogos mediante el uso de slots.
- **`ProductDetails.vue`**: Gestiona la navegación interna de detalles sin sobrecargar el DOM.

---

## 🚀 Como ejecutar el proyecto

### 1. Clonar e Instalar

```bash
git clone https://github.com/jltamayocabello-droid/m7_analisis-de-caso_ecomarket-vue.git
cd m7_analisis-de-caso_ecomarket-vue
npm install
```

### 2. Ejecución en Desarrollo

```bash
npm run dev
```

---

## 📱 Uso de la Aplicación

- **Catálogo Dinámico**: Explora la lista de productos sustentables (con retardo de carga inicial para simular API).
- **Gestión del Carrito**: Añade productos y observa cómo el contador se actualiza en tiempo real.
- **Detalles y Modales**: Visualiza información extendida mediante pestañas dinámicas y revisa tu selección en el modal de carrito.

---

## 🌐 Despliegue (Demo)

- **Repositorio GitHub**:

  > 🔗 [https://github.com/jltamayocabello-droid/m7_analisis-de-caso_ecomarket-vue](https://github.com/jltamayocabello-droid/m7_analisis-de-caso_ecomarket-vue)

- **Deploy del proyecto**:
  > 🔗 [https://jltamayocabello-droid.github.io/m7_analisis-de-caso_ecomarket-vue/](https://jltamayocabello-droid.github.io/m7_analisis-de-caso_ecomarket-vue/)

---

## 🤔 Reflexión Final

#### ¿Qué ventajas trae la componentización en comparación con una interfaz monolítica?

La componentización aplica el principio de responsabilidad única, permitiendo que cada parte de la interfaz sea independiente. Esto facilita el reuso de código (DRY), permite aislar errores de forma quirúrgica y simplifica enormemente las pruebas unitarias y el escalamiento.

#### ¿Cómo mejora el mantenimiento y la colaboración en equipo?

A nivel de equipo, mejora la productividad al permitir que múltiples desarrolladores trabajen en distintas piezas (filtros, carrito, modales) simultáneamente sin generar conflictos de código constantes, logrando un flujo de trabajo más ágil y un mantenimiento mucho más sencillo.

---

## ✒️ Autor

**Jorge Tamayo Cabello**
_Estudiante de Desarrollo Front-End Trainee — SENCE_

---

## 📄 Licencia

Este proyecto es de uso académico y educativo para el programa SENCE.
