<template>
  <div class="bg-grey-9 q-py-md">
    <p class="text-center title-primary text-white">Principais Serviços</p>
    <div class="card-container container row">
      <q-card v-for="(item, id) in servicos" :key="id" class="card items-center">
        <q-card-section class="justify-center flex q-pa-none">           
            <q-img :src="item.icon" fit="cover" class="card-img" />
          <div class="content">
            <p class="title-secondary text-white">{{ item.title }}</p>
            <p class="texto-primary text-white">{{ item.texto }}</p>
          </div>
        </q-card-section>
      </q-card>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import cambio from 'src/assets/images/servicos/cambio.png'
//import susp from 'src/assets/images/servicos/suspensao_freio.png'
import ar from 'src/assets/images/servicos/ar.png'
import embreagem from 'src/assets/images/servicos/embreagem.png'
import scanner from 'src/assets/images/servicos/scanner.png'
import motor from 'src/assets/images/servicos/motor.png'
import freio from 'src/assets/images/servicos/freio.png'
import suspensao from 'src/assets/images/servicos/suspensao.png'
import arrefecimento from 'src/assets/images/servicos/arrefecimento.png'

const servicos = ref([
  {
    id: 0,
    title: 'Motor',
    texto: 'Diagnóstico, troca de óleo, reparos e manuntenção preventiva do motor',
    icon: motor,
  },
  {
    id: 1,
    title: 'Câmbio Automático',
    texto: 'Troca técnica de óleo e revisão do câmbio automático e manual.',
    icon: cambio,
  },
  {
    id: 2,
    title: 'Embreagem',
    texto: 'Avaliação do sistema e substituição do kit de embreagem para uma troca suave e eficiente de marchas.',
    icon: embreagem,
  },
  {
    id: 3,
    title: 'Injeção Eletrônica',
    texto: 'Leitura via scanner, limpeza e correções da injeção eletônica.',
    icon: scanner,
  },
  {
    id: 4,
    title: 'Freios',
    texto: 'Troca de pastilhas, discos, fluido e revisão completa do sistema de freio.',
    icon: freio,
  },

  {
    id: 5,
    title: 'Suspensão',
    texto: 'Manutenção de amortecedores, molas, bandejas e buchas para garantir estabilidade.',
    icon: suspensao,
  },
  {
    id: 6,
    title: 'Sistema de Arrefecimento',
    texto: 'Limpeza do sistema, troca de aditivo, revisão do radiador e verificação de vazamentos.',
    icon: arrefecimento,
  },

  {
    id: 7,
    title: 'Ar-condicionado Automotivo',
    texto: 'Revisão do sistema de ar-condicionado com recarga de gás, limpeza e inspeção técnica.',
    icon: ar,
  },
])
</script>
<style scoped lang="scss">
.card {
  max-width: 300px;
  width: 100%;
  background-color: $primary;
  cursor: pointer;
  margin: 10px;
  display: flex;
  flex-direction: column;
  border-radius: 25px;
  text-align: center;
  overflow: hidden;

  .card-img {
    width: 100%;
    height: 200px;
    object-fit: cover;
  }

  .content {
    padding: 10px; 
    
  }
}
</style>
