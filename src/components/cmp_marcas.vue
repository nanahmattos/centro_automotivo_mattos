<template>
  <div class="q-pa-md">
    <div class="container">
      <p class="text-center">Trabalhamos com peças de primeira linha</p>

      <div class="carousel-wrapper">
        <div class="carousel-track">
          <div v-for="(imagem, index) in imagensDuplicadas" :key="index" class="carousel-item">
            <q-img
              :src="imagem.img"
              fit="contain"
              :alt="imagem.alt"
              style="height: 60px; width: 100px"
            />
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue'
import img_bosch from 'src/assets/images/marcas/bosch.png'
import img_mahle from 'src/assets/images/marcas/mahle.png'
import img_cobreq from 'src/assets/images/marcas/cobreq.png'
import img_cofap from 'src/assets/images/marcas/cofap.png'
import img_controil from 'src/assets/images/marcas/controil.png'
import img_frasle from 'src/assets/images/marcas/frasle.png'
import img_fremax from 'src/assets/images/marcas/fremax.png'
import img_hipper_freios from 'src/assets/images/marcas/hipper_freios.png'
import img_kyb from 'src/assets/images/marcas/kyb.png'
import img_magneti_marelli from 'src/assets/images/marcas/magneti_marelli.png'
import img_man_filter from 'src/assets/images/marcas/man_filter.png'
import img_monroe from 'src/assets/images/marcas/monroe.png'
import img_nakata from 'src/assets/images/marcas/nakata.png'
import img_tecfil from 'src/assets/images/marcas/tecfil.png'
import img_trw from 'src/assets/images/marcas/trw.png'

const imagens = ref([
  { img: img_mahle, alt: 'Mahle' },
  { img: img_bosch, alt: 'Bosch' },
  { img: img_cobreq, alt: 'Cobreq' },
  { img: img_cofap, alt: 'Cofap' },
  { img: img_controil, alt: 'Controil' },
  { img: img_frasle, alt: 'Frasle' },
  { img: img_fremax, alt: 'Fremax' },
  { img: img_hipper_freios, alt: 'Hipper Freios' },
  { img: img_kyb, alt: 'Kyb' },
  { img: img_magneti_marelli, alt: 'Magneti Marelli' },
  { img: img_man_filter, alt: 'Man Filter' },
  { img: img_monroe, alt: 'Monroe' },
  { img: img_nakata, alt: 'Nakata' },
  { img: img_tecfil, alt: 'Tecfil' },
  { img: img_trw, alt: 'Trw' },
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
