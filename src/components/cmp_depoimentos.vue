<template>
  <div class="bg-grey-9">
    <!-- <div class="row justify-between items-center">
      <div class="q-gutter-sm">
        <q-btn
          flat
          class="nav-arrow"
          @click="prevSlide"
          :disabled="currentIndex === 0"
          aria-label="Slide anterior"
          icon="keyboard_arrow_left"
        />
        <q-btn
          flat
          class="nav-arrow"
          @click="nextSlide"
          aria-label="Slide anterior"
          icon="keyboard_arrow_right"
          :disabled="currentIndex === totalSlides - 1"
        />
      </div>
    </div> -->
    <p class="text-center title-primary text-white">Serviços</p>

    <q-carousel
      v-model="slide"
      swipeable
      animated
      class="bg-grey-9"
      transition-prev="scale"
      transition-next="scale"
      padding
      arrows
      control-color="white"
      navigation
      height="auto"
    >
      <q-carousel-slide
        v-for="(group, index) in chunkedItems"
        :key="index"
        :name="index"
        class="row col-12 no-wrap"
        style="width: 100%"
      >
        <q-card v-for="(item, id) in group" :key="id" class="card items-center">
          <div class="q-pa-sm">
            <q-img :src="item.icon" style="width: 100px" fit="contain" />
          </div>
          <div class="content">
            <p class="title-secondary text-white">{{ item.title }}</p>
            <p class="texto-primary text-white">{{ item.texto }}</p>
          </div>
        </q-card>
      </q-carousel-slide>
    </q-carousel>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue'
import { useQuasar } from 'quasar'
import { useRoute } from 'vue-router'
import icon_susp from '../assets/images/suspensao.svg'
const route = useRoute()
const $q = useQuasar()

const servicos = ref([
  {
    id: 1,
    title: 'Serviço 1',
    texto:
      'Lorem ipsum dolor sit amet consectetur adipisicing elit. Quas cupiditate laboriosam fugiat.',
    icon: icon_susp,
  },
  {
    id: 2,
    title: 'Serviço 2',
    texto:
      'Lorem ipsum dolor sit amet consectetur adipisicing elit. Quas cupiditate laboriosam fugiat.',
    icon: icon_susp,
  },

  {
    id: 3,
    title: 'Serviço 3',
    texto:
      'Lorem ipsum dolor sit amet consectetur adipisicing elit. Quas cupiditate laboriosam fugiat.',
    icon: icon_susp,
  },
  {
    id: 4,
    title: 'Serviço 4',
    texto:
      'Lorem ipsum dolor sit amet consectetur adipisicing elit. Quas cupiditate laboriosam fugiat.',
    icon: icon_susp,
  },
])

const slide = ref(0)
const filteredItems = computed(() => servicos.value.filter((item) => item.name !== route.name))

const chunkSize = computed(() => {
  if ($q.screen.xs) return 1 // até ~599px
  if ($q.screen.sm) return 2 // 600px a 1023px
  if ($q.screen.md) return 3 // 1024px a 1439px
  return 4 // lg e xl
})
function chunk(array, size) {
  const result = []
  for (let i = 0; i < array.length; i += size) {
    result.push(array.slice(i, i + size))
  }
  return result
}

const chunkedItems = computed(() => chunk(filteredItems.value, chunkSize.value))
// const totalSlides = computed(() => chunkedItems.value.length)
// const currentIndex = computed(() => slide.value)

// const nextSlide = () => {
//   if (currentIndex.value < totalSlides.value - 1) {
//     slide.value++
//   }
// }

// const prevSlide = () => {
//   if (currentIndex.value > 0) {
//     slide.value--
//   }
// }
</script>
<style scoped lang="scss">
.card {
  max-width: 400px;
  width: 100%;
  background-color: $primary;
  cursor: pointer;
  margin: 10px;
  display: flex;
  border-radius: 25px;
  flex-direction: column;
  text-align: center;
  overflow: hidden;

  .image {
    max-width: 100px;
    max-height: 200px;
    height: 100%;
    width: 100%;
  }

  .content {
    padding: 10px;
  }
}
</style>
