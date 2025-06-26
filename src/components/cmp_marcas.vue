<template>
  <div class="q-pa-md">
    <div class="container">
      <p class="text-center">Trabalhamos com peças de primeira linha</p>

      <div class="carousel-wrapper">
        <div class="carousel-track">
          <div v-for="(imagem, index) in imagensDuplicadas" :key="index" class="carousel-item">
            <q-img :src="imagem.img" fit="contain" :alt="imagem.alt" style="height: 60px; width: 100px" />
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue'
import mahle from '../assets/images/mahle.svg'
const imagens = ref([
  { img: mahle, alt: 'Mahle' },
  { img: mahle, alt: 'Mahle' },
  { img: mahle, alt: 'Mahle' },
  { img: mahle, alt: 'Mahle' },
  { img: mahle, alt: 'Mahle' },
])

// Duplicar as imagens para o loop infinito parecer contínuo
const imagensDuplicadas = computed(() => [...imagens.value, ...imagens.value])

</script>

<style scoped>
.carousel-wrapper {
  overflow: hidden;
  width: 100%;
  position: relative;
}

.carousel-track {
  display: flex;
  width: fit-content;
  animation: scroll 20s linear infinite;
}

.carousel-item {
  flex-shrink: 0;
  padding: 0 20px;
}

@keyframes scroll {
  0% {
    transform: translateX(0);
  }
  100% {
    transform: translateX(-50%);
  }
}
</style>
