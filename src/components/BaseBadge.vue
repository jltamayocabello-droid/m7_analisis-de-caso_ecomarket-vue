<template>
  <span :class="['badge', `badge-${variant}`]">
    {{ label }}
  </span>
</template>

<script setup>
// Definición de Props modernas con validación
defineProps({
  label: {
    type: String,
    required: true
  },
  variant: {
    type: String,
    default: 'success' // Opciones esperadas: 'success', 'warning'
  }
});
</script>

<style scoped>
/* Estilos encapsulados solo para este componente */
.badge {
  padding: 0.25rem 0.5rem;
  border-radius: 9999px; /* Pill shape */
  font-size: 0.75rem;
  font-weight: bold;
  text-transform: uppercase;
}

.badge-success {
  background-color: #d1fae5;
  color: #065f46;
}

.badge-warning {
  background-color: #fef3c7;
  color: #92400e;
}
</style>