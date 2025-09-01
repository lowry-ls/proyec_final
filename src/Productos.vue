<template>
  <section id="productos">
    <h2>Productos Destacados</h2>
    <div class="row row-cols-1 row-cols-md-3 g-4">
      <ProductoCard
        v-for="producto in productos"
        :key="producto.id"
        :producto="producto"
        @verDetalle="emitVerDetalle"
      />
    </div>
  </section>
</template>

<script setup>
import ProductoCard from './ProductoCard.vue'
const props = defineProps({
  productos: Array
})
const emit = defineEmits(['verDetalle'])

function emitVerDetalle(producto) {
  emit('verDetalle', producto)
}
</script>