<template>
  <div id="carrusel" class="carousel slide carousel-fade mb-4" data-bs-ride="carousel">
    <div class="carousel-inner">
      <div class="carousel-item active">
        <img :src="img1" class="d-block w-100" alt="Mando Gamer">
      </div>
      <div class="carousel-item">
        <img :src="img2" class="d-block w-100" alt="Mando Gamer 2">
      </div>
      <div class="carousel-item">
        <img :src="img3" class="d-block w-100" alt="Play 4">
      </div>
      <div class="carousel-item">
        <img :src="img4" class="d-block w-100" alt="Play 5">
      </div>
      <div class="carousel-item">
        <img :src="img5" class="d-block w-100" alt="Switch">
      </div>
      <div class="carousel-item">
        <img :src="img6" class="d-block w-100" alt="Teclado RGB">
      </div>
    </div>
    <button class="carousel-control-prev" type="button" data-bs-target="#carrusel" data-bs-slide="prev">
      <span class="carousel-control-prev-icon" aria-hidden="true"></span>
      <span class="visually-hidden">Anterior</span>
    </button>
    <button class="carousel-control-next" type="button" data-bs-target="#carrusel" data-bs-slide="next">
      <span class="carousel-control-next-icon" aria-hidden="true"></span>
      <span class="visually-hidden">Siguiente</span>
    </button>
  </div>
</template>

<script>
import img1 from './assets/mando_gamer.jpg'
import img2 from './assets/mando_gamer2.jpg'
import img3 from './assets/play_4.jpg'
import img4 from './assets/play_5.jpg'
import img5 from './assets/Switch1.jpeg'
import img6 from './assets/teclado_rgb.jpeg'

export default {
  name: 'Carrusel',
  data() {
    return {
      img1,
      img2,
      img3,
      img4,
      img5,
      img6
    }
  }
}
</script>