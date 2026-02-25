<template>
  <div class="shop-container">
    <header>
      <h1>EcoMarket 🌱</h1>
      <div class="cart-badge">Carrito: {{ cartCount }}</div>
    </header>
    
    <main>
      <p v-if="isLoading" class="loading">Cargando productos ecológicos...</p>
      
      <ProductList 
        v-else
        :products="products" 
        @add-to-cart="handleAddToCart"
      />
    </main>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue';
import ProductList from '../components/ProductList.vue';

// Estado Reactivo (State)
const products = ref([]);
const isLoading = ref(true);
const cartCount = ref(0);

// Ciclo de Vida: onMounted para simular carga de datos (Punto 4 del informe)
onMounted(() => {
  console.log('Componente montado. Simulando fetch a la API...');
  
  setTimeout(() => {
    products.value = [
      { id: 1, name: 'Cepillo de Bambú', price: 5.99, isEco: true },
      { id: 2, name: 'Bolsa de Algodón', price: 3.50, isEco: true },
      { id: 3, name: 'Termo Acero Inox', price: 15.00, isEco: false },
      { id: 4, name: 'Jabón Artesanal', price: 4.20, isEco: true }
    ];
    isLoading.value = false;
  }, 1500); // Simula 1.5s de red
});

// Manejador del evento emitido por el hijo
const handleAddToCart = (productId) => {
  cartCount.value++;
  console.log(`Lógica de negocio: Producto ${productId} agregado.`);
};
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

.cart-badge {
  background-color: #2563eb;
  color: white;
  padding: 0.5rem 1rem;
  border-radius: 8px;
  font-weight: bold;
}

.loading {
  text-align: center;
  font-size: 1.2rem;
  color: #6b7280;
}
</style>