<template>
  <q-page class="column" style="min-height: auto">
    <section id="hero" class="full-width">
      <Hero />
    </section>
    <section id="servicos" class="full-width">
      <Servicos />
    </section>
  </q-page>
</template>

<script setup>
//
import Hero from '../components/cmp_hero.vue'
import Servicos from '../components/cmp_servicos.vue'
</script>
