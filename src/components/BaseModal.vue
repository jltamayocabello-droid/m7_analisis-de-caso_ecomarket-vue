<template>
  <div class="modal-overlay" @click.self="$emit('close')">
    <div class="modal-content">
      <header class="modal-header">
        <slot name="header">
          <h2>Título por defecto</h2>
        </slot>
      </header>

      <main class="modal-body">
        <slot>
          <p>Contenido principal del modal.</p>
        </slot>
      </main>

      <footer class="modal-footer">
        <slot name="footer">
          <button @click="$emit('close')" class="btn-close">Cerrar</button>
        </slot>
      </footer>
    </div>
  </div>
</template>

<script setup>
defineEmits(['close']);
</script>

<style scoped>
.modal-overlay {
  position: fixed;
  top: 0; left: 0; width: 100vw; height: 100vh;
  background: rgba(0, 0, 0, 0.5);
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 1000;
}

.modal-content {
  background: white;
  padding: 1.5rem;
  border-radius: 8px;
  width: 90%;
  max-width: 500px;
  box-shadow: 0 4px 6px rgba(0,0,0,0.1);
}

.modal-header {
  border-bottom: 1px solid #e5e7eb;
  padding-bottom: 0.5rem;
  margin-bottom: 1rem;
}

.modal-footer {
  margin-top: 1rem;
  display: flex;
  justify-content: flex-end;
}

.btn-close {
  background: #ef4444;
  color: white;
  border: none;
  padding: 0.5rem 1rem;
  border-radius: 4px;
  cursor: pointer;
}
</style>