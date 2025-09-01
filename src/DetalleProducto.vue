<template>
  <div class="modal fade show d-block" tabindex="-1" style="background:rgba(0,0,0,0.5)" @click.self="$emit('cerrar')">
    <div class="modal-dialog">
      <div class="modal-content">
        <div class="modal-header">
          <h5 class="modal-title">{{ producto.nombre }}</h5>
          <button type="button" class="btn-close" @click="$emit('cerrar')"></button>
        </div>
        <div class="modal-body">
          <img :src="producto.imagen" class="img-fluid mb-3" :alt="producto.nombre">
          <p>{{ producto.descripcion }}</p>
          <p class="fw-bold">Precio: Bs {{ producto.precio }}</p>
        </div>
        <div class="modal-footer">
          <button class="btn btn-secondary" @click="$emit('cerrar')">Cerrar</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
const props = defineProps({
  producto: Object
})
</script>