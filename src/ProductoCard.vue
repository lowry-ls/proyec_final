<template>
  <div class="col">
    <div class="card h-100">
      <img :src="getImagen(producto.imagen)" class="card-img-top" :alt="producto.nombre">
      <div class="card-body">
        <h5 class="card-title">{{ producto.nombre }}</h5>
        <p class="card-text">{{ producto.descripcion }}</p>
        <p class="card-text fw-bold">Bs {{ producto.precio }}</p>
        <button class="btn btn-primary" @click="$emit('verDetalle', producto)">Ver detalle</button>
      </div>
    </div>
  </div>
</template>

<script setup>
const props = defineProps({
  producto: Object
})

// Función para obtener la ruta correcta de la imagen
function getImagen(imagen) {
  // Si la ruta ya es un import, la retorna tal cual
  if (imagen.startsWith('data:') || imagen.startsWith('http')) return imagen
  // Si la imagen está en assets, usa la ruta relativa para Vite
  return new URL(`./assets/${imagen.split('/').pop()}`, import.meta.url).href
}
</script>