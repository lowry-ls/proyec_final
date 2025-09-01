<!-- filepath: e:\workspace-vscode\proyec\Pixel_Gamer\src\Carrito.vue -->
<template>
  <div class="carrito position-fixed top-0 end-0 bg-white shadow p-3" style="width:320px; z-index:2000;">
    <div class="d-flex justify-content-between align-items-center mb-3">
      <h5><i class="fas fa-shopping-cart"></i> Carrito</h5>
      <button class="btn btn-sm btn-danger" @click="$emit('cerrar')">Cerrar</button>
    </div>
    <div v-if="carrito.length === 0" class="text-center text-muted">
      <p>El carrito está vacío.</p>
    </div>
    <ul v-else class="list-group mb-3">
      <li v-for="(producto, idx) in carrito" :key="idx" class="list-group-item d-flex justify-content-between align-items-center">
        <div>
          <strong>{{ producto.nombre }}</strong>
          <br>
          <span class="text-muted">Bs {{ producto.precio }}</span>
        </div>
        <button class="btn btn-sm btn-outline-danger" @click="eliminar(idx)">
          <i class="fas fa-trash"></i>
        </button>
      </li>
    </ul>
    <div v-if="carrito.length > 0" class="text-end fw-bold">
      Total: Bs {{ total }}
    </div>
  </div>
</template>

<script setup>
const props = defineProps({
  carrito: Array
})
const emit = defineEmits(['cerrar', 'eliminar'])

function eliminar(idx) {
  emit('eliminar', idx)
}

const total = computed(() => props.carrito.reduce((sum, p) => sum + p.precio, 0))
</script>