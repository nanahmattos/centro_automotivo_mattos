<template>
  <div>
    <p class="text-center">O que estão dizendo ?</p>
    <div class="card-container row">
      <q-card v-for="(depoimento, index) in depoimentos" :key="index" class="card items-center">
        <q-card-section>
          <p>{{ depoimento.title }}</p>
          <p>
            {{ depoimento.texto }}
          </p>
        </q-card-section>
      </q-card>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const depoimentos = ref([
  {
    id: 1,
    title: 'Cliente 1',
    texto:
      'Lorem ipsum dolor sit amet consectetur adipisicing elit. Quas cupiditate laboriosam fugiat.',
    icon: '',
  },
  {
    id: 2,
    title: 'Cliente 2',
    texto:
      'Lorem ipsum dolor sit amet consectetur adipisicing elit. Quas cupiditate laboriosam fugiat.',
    icon: '',
  },

  {
    id: 3,
    title: 'Cliente 3',
    texto:
      'Lorem ipsum dolor sit amet consectetur adipisicing elit. Quas cupiditate laboriosam fugiat.',
    icon: '',
  },
  {
    id: 4,
    title: 'Cliente 4',
    texto:
      'Lorem ipsum dolor sit amet consectetur adipisicing elit. Quas cupiditate laboriosam fugiat.',
    icon: '',
  },
])
</script>
<style scoped lang="scss">
.card-container {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
}
.card {
  max-width: 200px;
  width: 100%;
  margin: 10px;
  align-items: stretch;
  border-radius: 25px;
  text-align: center;

  .image {
    max-width: 100px;
    max-height: 200px;
    height: 100%;
    width: 100%;
  }
}
</style>
