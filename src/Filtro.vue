<!-- filepath: e:\workspace-vscode\proyec\Pixel_Gamer\src\Filtro.vue -->
<template>
  <form @submit.prevent="emitirFiltro" class="mb-3">
    <input
      v-model="texto"
      class="form-control form-control-sm"
      placeholder="Filtrar productos..."
    />
    <button class="btn btn-sm btn-primary mt-2" type="submit">Filtrar</button>
  </form>
</template>

<script setup>
import { ref } from 'vue'
const texto = ref('')
const emit = defineEmits(['filtrar'])
function emitirFiltro() {
  emit('filtrar', texto.value)
}
</script>