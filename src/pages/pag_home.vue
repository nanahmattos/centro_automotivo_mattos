<template>
  <q-page class="column" style="min-height: auto">
    <section id="hero" class="full-width">
      <Hero />
    </section>
    <section id="servicos" class="full-width">
      <Servicos />
    </section>
    <section class="full-width">
      <Marcas />
    </section>
    <section class="full-width">
      <Mapa />
    </section>
    <section class="full-width">
      <Depoimentos />
    </section>
  </q-page>
</template>

<script setup>
import Hero from '../components/cmp_hero.vue'
import Servicos from '../components/cmp_servicos.vue'
import Marcas from '../components/cmp_marcas.vue'
import Mapa from '../components/cmp_mapa.vue'
import Depoimentos from '../components/cmp_depoimentos.vue'
</script>
