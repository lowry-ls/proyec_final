<template>
  <Header
    :carritoCount="carrito.length"
    @buscar="filtrarProductos"
    @carritoClick="mostrarCarrito = true"
  />
  <Carrusel />
  <Filtro @filtrar="filtrarProductos" />
  <Productos
    :productos="productosFiltrados"
    @verDetalle="productoSeleccionado = $event"
    @agregarCarrito="agregarAlCarrito"
  />
  <DetalleProducto
    v-if="productoSeleccionado"
    :producto="productoSeleccionado"
    @cerrar="productoSeleccionado = null"
  />
  <Carrito
    v-if="mostrarCarrito"
    :carrito="carrito"
    @cerrar="mostrarCarrito = false"
    @eliminar="eliminarDelCarrito"
  />
  <Footer />
</template>

<script>
import Header from './Header.vue'
import Carrusel from './Carrusel.vue'
import Productos from './Productos.vue'
import DetalleProducto from './DetalleProducto.vue'
import Carrito from './Carrito.vue'
import Footer from './Footer.vue'
import Filtro from './Filtro.vue'

import ps4 from './assets/ps4.png'
import ps3 from './assets/ps3.jpg'
import mandoGamer from './assets/mando_gamer.jpg'
import play5 from './assets/play_5.jpg'
import mandoGamer2 from './assets/mando_gamer2.jpg'
import iconoPixel from './assets/icono_pixel.png'

export default {
  name: 'App',
  components: { Header, Carrusel, Productos, DetalleProducto, Carrito, Footer, Filtro },
  data() {
    return {
      productos: [
        { id: 1, nombre: "PlayStation 4", descripcion: "Consola Sony PS4, 1TB.", imagen: ps4, precio: 3200 },
        { id: 2, nombre: "PlayStation 3", descripcion: "Consola Sony PS3, 500GB.", imagen: ps3, precio: 2100 },
        { id: 3, nombre: "Mando Gamer", descripcion: "Control inalámbrico PS4/PC.", imagen: mandoGamer, precio: 350 },
        { id: 4, nombre: "PlayStation 5", descripcion: "Nueva generación Sony.", imagen: play5, precio: 4500 },
        { id: 5, nombre: "Mando Gamer 2", descripcion: "Control edición especial.", imagen: mandoGamer2, precio: 400 },
        { id: 6, nombre: "Pixel Gamer Icon", descripcion: "Musepat Logo Pixel Gamer.", imagen: iconoPixel, precio: 50 }
      ],
      productosFiltrados: [],
      carrito: [],
      productoSeleccionado: null,
      mostrarCarrito: false
    }
  },
  created() {
    this.productosFiltrados = this.productos
  },
  methods: {
    filtrarProductos(busqueda) {
      if (!busqueda) {
        this.productosFiltrados = this.productos
      } else {
        const texto = busqueda.toLowerCase()
        this.productosFiltrados = this.productos.filter(p =>
          p.nombre.toLowerCase().includes(texto) ||
          p.descripcion.toLowerCase().includes(texto)
        )
      }
    },
    agregarAlCarrito(producto) {
      this.carrito.push(producto)
    },
    eliminarDelCarrito(producto) {
      this.carrito = this.carrito.filter(p => p.id !== producto.id)
    }
  }
}
</script>