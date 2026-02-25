<template>
  <div class="details-container">
    <nav class="tabs">
      <button 
        :class="{ active: currentTab === TabDescription }" 
        @click="currentTab = TabDescription"
      >
        Descripción
      </button>
      <button 
        :class="{ active: currentTab === TabImpact }" 
        @click="currentTab = TabImpact"
      >
        Impacto Eco
      </button>
    </nav>

    <KeepAlive>
      <component :is="currentTab" />
    </KeepAlive>
  </div>
</template>

<script setup>
import { shallowRef } from 'vue';
import TabDescription from './TabDescription.vue';
import TabImpact from './TabImpact.vue';

// shallowRef es la mejor práctica en Vue 3 para almacenar componentes reactivos
const currentTab = shallowRef(TabDescription);
</script>

<style scoped>
.details-container { margin-top: 2rem; border-top: 1px solid #e5e7eb; padding-top: 1rem; }
.tabs button {
  background: none; border: none; padding: 0.5rem 1rem; cursor: pointer;
  font-weight: bold; color: #6b7280; border-bottom: 2px solid transparent;
}
.tabs button.active { color: #10b981; border-bottom-color: #10b981; }
</style>