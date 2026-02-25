<template>
  <div class="shop-container">
    <header>
      <h1>EcoMarket 🌱</h1>
      <button class="cart-btn" @click="isModalOpen = true">Carrito: {{ cartCount }}</button>
    </header>

    <main>
      <p v-if="isLoading" class="loading">Cargando productos ecológicos...</p>
      <ProductList v-else :products="products" @add-to-cart="handleAddToCart" />
    </main>

    <Teleport to="body">
      <BaseModal v-if="isModalOpen" @close="isModalOpen = false">
        <template #header>
          <h2>Tu Carrito Eco 🛒</h2>
        </template>

        <p v-if="cartCount === 0">Tu carrito está vacío. ¡Suma productos sustentables!</p>
        <p v-else>
          Tienes <strong>{{ cartCount }}</strong> artículos en tu pedido.
        </p>

        <template #footer>
          <button class="btn-cancel" @click="isModalOpen = false">Cerrar</button>
          <button class="btn-checkout" v-if="cartCount > 0">Ir al Pago</button>
        </template>
      </BaseModal>
    </Teleport>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import ProductList from '../components/ProductList.vue'
import BaseModal from '../components/BaseModal.vue' // Importamos el modal

const products = ref([])
const isLoading = ref(true)
const cartCount = ref(0)

// Estado para controlar la visibilidad del modal
const isModalOpen = ref(false)

onMounted(() => {
  setTimeout(() => {
    products.value = [
      { id: 1, name: 'Cepillo de Bambú', price: 5.99, isEco: true },
      { id: 2, name: 'Bolsa de Algodón', price: 3.5, isEco: true },
      { id: 3, name: 'Termo Acero Inox', price: 15.0, isEco: false },
      { id: 4, name: 'Jabón Artesanal', price: 4.2, isEco: true },
    ]
    isLoading.value = false
  }, 1500)
})

const handleAddToCart = (productId) => {
  cartCount.value++
}
</script>

<style scoped>
.shop-container {
  max-width: 1000px;
  margin: 0 auto;
  padding: 2rem;
  font-family: sans-serif;
}
header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  border-bottom: 2px solid #e5e7eb;
  margin-bottom: 2rem;
  padding-bottom: 1rem;
}
.loading {
  text-align: center;
  font-size: 1.2rem;
  color: #6b7280;
}

/* Estilos de botones */
.cart-btn {
  background-color: #2563eb;
  color: white;
  padding: 0.5rem 1rem;
  border-radius: 8px;
  font-weight: bold;
  border: none;
  cursor: pointer;
}
.cart-btn:hover {
  background-color: #1d4ed8;
}
.btn-cancel {
  background: white;
  color: #374151;
  border: 1px solid #d1d5db;
  padding: 0.5rem 1rem;
  border-radius: 4px;
  cursor: pointer;
  margin-right: 0.5rem;
}
.btn-checkout {
  background: #10b981;
  color: white;
  border: none;
  padding: 0.5rem 1rem;
  border-radius: 4px;
  cursor: pointer;
}
</style>
