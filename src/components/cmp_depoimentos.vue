<template>
  <div>
    <p class="text-center">O que estão dizendo ?</p>
    <div class="card-container row">
      <q-card v-for="(depoimento, index) in depoimentos" :key="index" class="card items-center">
        <q-card-section class="justify-center flex">
          <span class="row q-pa-sm" >
            <q-icon name="star" color="yellow" size="xs" />
            <q-icon name="star" color="yellow" size="xs" />
            <q-icon name="star" color="yellow" size="xs" />
            <q-icon name="star" color="yellow" size="xs" />
            <q-icon name="star" color="yellow" size="xs" />
          </span>
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
    id: 0,
    title: 'PÉDDY GÁS',
    texto:
      'Serviço autamente efciciente, preço justo, oficina 100% confiável, equipe de profissional super educados e prestativos. Este RECOMENDO....PARABÉNS!!!',
    icon: '',
  },
  {
    id: 1,
    title: 'João Araujo',
    texto:
      'Atendimento excelente, profissionalismo e compromisso com o cliente. Super indico para quem procura um serviço de qualidade e preço justo!! Grato',
    icon: '',
  },

  {
    id: 2,
    title: 'Júnior Benites',
    texto:
      'Profissionais muito corretos nos diagnósticos automotivos....top',
    icon: '',
  },
  {
    id: 3,
    title: 'Rodiney Lima',
    texto:
      'Ótima reputação, o proprietário Claudiney é um profissional muito sério e honesto!',
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
