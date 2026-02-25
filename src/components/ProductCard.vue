<template>
  <div class="card">
    <BaseBadge 
      v-if="product.isEco" 
      label="100% Eco" 
      variant="success" 
    />
    
    <h3>{{ product.name }}</h3>
    <p class="price">${{ product.price }}</p>
    
    <button @click="$emit('add-to-cart', product.id)">
      Agregar al Carrito
    </button>
  </div>
</template>

<script setup>
import BaseBadge from './BaseBadge.vue';

// Recibe datos del padre
defineProps({
  product: {
    type: Object,
    required: true
  }
});

// Define el evento que enviará al padre
defineEmits(['add-to-cart']);
</script>

<style scoped>
.card {
  border: 1px solid #e5e7eb;
  padding: 1rem;
  border-radius: 8px;
  text-align: center;
  transition: transform 0.2s;
}
.card:hover {
  transform: translateY(-5px);
}
.price {
  font-size: 1.25rem;
  font-weight: bold;
  color: #2563eb;
  margin: 0.5rem 0;
}
button {
  background-color: #10b981;
  color: white;
  border: none;
  padding: 0.5rem 1rem;
  border-radius: 4px;
  cursor: pointer;
}
button:hover {
  background-color: #059669;
}
</style>