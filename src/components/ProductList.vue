<template>
  <div class="product-grid">
    <ProductCard 
      v-for="product in products" 
      :key="product.id" 
      :product="product"
      @add-to-cart="$emit('add-to-cart', $event)"
    />
  </div>
</template>

<script setup>
import ProductCard from './ProductCard.vue';

// Recibe la lista completa de productos
defineProps({
  products: {
    type: Array,
    required: true
  }
});

// Actúa como puente para que el evento llegue a ShopView
defineEmits(['add-to-cart']);
</script>

<style scoped>
/* Sistema de grilla responsiva moderna sin media queries complejas */
.product-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 1.5rem;
  padding: 1rem 0;
}
</style>