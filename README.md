# 🛒 EcoMarket - Prototipo Vue 3 (M7 L1 Análisis de Caso)

Prototipo de prueba para evaluar la reestructuración de interfaces monolíticas hacia una arquitectura escalable basada en componentes reutilizables utilizando el framework Vue 3.

### 1. Stack Tecnológico

* **Vue 3**: Composition API y `<script setup>`.
* **Vite**: Entorno de desarrollo ultrarrápido y empaquetador.
* **CSS3**: Variables CSS y encapsulamiento (`<style scoped>`).
* **Git/GitHub**: Control de versiones.

### 2. Estructura del Proyecto

```text
ecomarket-vue/
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
    │   └── ShopView.vue          # Vista principal / Catálogo de la tienda
    │
    └── components/
        ├── BaseBadge.vue         # Etiqueta visual reutilizable
        ├── BaseModal.vue         # Modal reutilizable con Slots
        ├── ProductCard.vue       # Tarjeta individual de producto
        ├── ProductList.vue       # Grilla iteradora de productos
        ├── ProductDetails.vue    # Contenedor de pestañas dinámicas
        ├── TabDescription.vue    # Pestaña: Descripción del producto
        └── TabImpact.vue         # Pestaña: Impacto ecológico
3. Arquitectura de Componentes
Componente ShopView.vue (Vista Principal / Smart Component)
Fragmento de código
// Maneja el ref() de products, cartCount e isModalOpen.
// Utiliza onMounted() para simular la petición de datos.

@add-to-cart="handleAddToCart"
Responsabilidades:

Orquestar la obtención de datos y pasarlos hacia abajo.

Manejar el estado del carrito de compras.

Controlar la apertura y cierre del modal.

Componente ProductCard.vue
Fragmento de código
defineProps({ product: Object })

defineEmits(['add-to-cart'])
Responsabilidades:

Mostrar nombre, precio y utilizar el sub-componente BaseBadge según el estado ecológico.

Emitir el evento de agregar al carrito al componente contenedor.

Componente BaseModal.vue
Fragmento de código
<slot name="header"></slot>
<slot></slot> <slot name="footer"></slot>

defineEmits(['close'])
Responsabilidades:

Proveer una estructura UI base para ventanas emergentes.

Recibir inyección de HTML dinámico del padre sin acoplarse a un caso de uso específico.

Componente ProductDetails.vue
Fragmento de código
<component :is="currentTab" />
<KeepAlive>
Responsabilidades:

Alternar dinámicamente entre los componentes TabDescription y TabImpact sin recargar ni usar múltiples v-if.

4. Características Implementadas
🌱 Catálogo Dinámico y Ciclo de Vida
Uso del hook onMounted para simular un retraso de red (1.5s) y mostrar un estado de "Cargando..." antes de renderizar la grilla de productos.

🏗️ Comunicación Bidireccional
Flujo de datos descendente (State -> Props) desde la vista a las tarjetas.

Flujo de acciones ascendente (Emits -> Handlers) para actualizar el contador del carrito.

🧩 Slots y Componentes Dinámicos
Implementación de Named Slots en BaseModal para adaptar su contenido como un carrito de compras.

Implementación de Dynamic Components (<component :is>) para el sistema de pestañas de detalles, optimizado con <KeepAlive> para mantener el estado.

🎨 Estilos Encapsulados
Uso estricto de <style scoped> para evitar colisión de CSS entre componentes y clases de binding dinámico (:class) para componentes interactivos.