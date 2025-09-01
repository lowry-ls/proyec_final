<template>
  <header>
    <nav class="navbar navbar-expand-lg navbar-dark bg-dark fixed-top">
      <div class="container-fluid">
        <img :src="imgLogo" alt="Pixel Gamer Logo" style="height:40px;" class="me-2" />
        <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbar">
          <span class="navbar-toggler-icon"></span>
        </button>
        <div class="collapse navbar-collapse" id="navbar">
          <ul class="navbar-nav me-auto mb-2 mb-lg-0">
            <li class="nav-item"><a class="nav-link" href="#">Inicio</a></li>
            <li class="nav-item"><a class="nav-link" href="#productos">Productos</a></li>
            <li class="nav-item"><a class="nav-link" href="#">Contacto</a></li>
          </ul>
          <form class="d-flex me-2" @submit.prevent="buscarProducto">
            <input
              v-model="busqueda"
              class="form-control form-control-sm"
              type="search"
              placeholder="Buscar"
              aria-label="Buscar"
              style="width:120px;"
            />
            <button class="btn btn-sm btn-outline-info ms-2" type="submit">
              <i class="fas fa-search"></i>
            </button>
          </form>
          <button class="btn btn-sm btn-outline-warning me-2 position-relative" title="Carrito" @click="abrirCarrito">
            <i class="fas fa-shopping-cart"></i>
            <span v-if="carritoCount > 0" class="position-absolute top-0 start-100 translate-middle badge rounded-pill bg-danger">
              {{ carritoCount }}
            </span>
          </button>
          <button @click="toggleDark" class="btn btn-outline-light ms-2" title="Modo oscuro">
            <i class="fas fa-moon"></i>
          </button>
          <!-- Botón Login/Registro -->
          <button class="btn btn-sm btn-outline-primary ms-2" @click="mostrarLogin = true">
            <i class="fas fa-user"></i>
          </button>
        </div>
      </div>
    </nav>
    <!-- Modal Login/Registro -->
    <div v-if="mostrarLogin" class="login-modal">
      <div class="login-container">
        <div class="d-flex justify-content-between mb-3">
          <button
            class="btn btn-sm"
            :class="tab === 'login' ? 'btn-primary' : 'btn-outline-primary'"
            @click="tab = 'login'"
          >Login</button>
          <button
            class="btn btn-sm"
            :class="tab === 'registro' ? 'btn-primary' : 'btn-outline-primary'"
            @click="tab = 'registro'"
          >Registro</button>
        </div>
        <form v-if="tab === 'login'" @submit.prevent="login">
          <h5 class="mb-3">Iniciar sesión</h5>
          <input v-model="usuario" type="text" class="form-control mb-2" placeholder="Usuario" required />
          <input v-model="clave" type="password" class="form-control mb-2" placeholder="Contraseña" required />
          <div class="d-flex justify-content-end">
            <button type="button" class="btn btn-secondary btn-sm me-2" @click="cerrarModal">Cancelar</button>
            <button type="submit" class="btn btn-primary btn-sm">Entrar</button>
          </div>
        </form>
        <form v-else @submit.prevent="registro">
          <h5 class="mb-3">Registro</h5>
          <input v-model="nuevoUsuario" type="text" class="form-control mb-2" placeholder="Usuario" required />
          <input v-model="nuevoCorreo" type="email" class="form-control mb-2" placeholder="Correo" required />
          <input v-model="nuevaClave" type="password" class="form-control mb-2" placeholder="Contraseña" required />
          <div class="d-flex justify-content-end">
            <button type="button" class="btn btn-secondary btn-sm me-2" @click="cerrarModal">Cancelar</button>
            <button type="submit" class="btn btn-primary btn-sm">Registrar</button>
          </div>
        </form>
      </div>
      <div class="login-backdrop" @click="cerrarModal"></div>
    </div>
  </header>
</template>

<script>
import imgLogo from './assets/icono_pixel.png'
import './assets/login.css'

export default {
  name: 'Header',
  props: {
    carritoCount: {
      type: Number,
      default: 0
    }
  },
  data() {
    return {
      imgLogo,
      busqueda: '',
      mostrarLogin: false,
      tab: 'login',
      usuario: '',
      clave: '',
      nuevoUsuario: '',
      nuevoCorreo: '',
      nuevaClave: ''
    }
  },
  methods: {
    toggleDark() {
      document.body.classList.toggle('dark-mode')
    },
    buscarProducto() {
      this.$emit('buscar', this.busqueda)
      this.busqueda = ''
    },
    abrirCarrito() {
      this.$emit('carritoClick')
    },
    cerrarModal() {
      this.mostrarLogin = false
      this.tab = 'login'
      this.usuario = ''
      this.clave = ''
      this.nuevoUsuario = ''
      this.nuevoCorreo = ''
      this.nuevaClave = ''
    },
    login() {
      // Lógica de login
      alert(`Bienvenido, ${this.usuario}!`)
      this.cerrarModal()
    },
    registro() {
      // Lógica de registro
      alert(`Usuario registrado: ${this.nuevoUsuario}`)
      this.cerrarModal()
    }
  }
}
</script>

<style>
.login-modal {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  display: flex;
  align-items: center;
  justify-content: center;
  z-index: 1050;
}

.login-container {
  background-color: white;
  padding: 2rem;
  border-radius: 0.5rem;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
  width: 300px;
  position: relative;
}

.login-backdrop {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-color: rgba(0, 0, 0, 0.7);
  z-index: -1;
}
</style>