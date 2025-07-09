<template>
  <q-layout>
    <q-header :class="{ 'solid-background': scrolled }" class="header container">
      <q-toolbar class="justify-between">
        <div class="row items-center">
          <!-- logo -->
          <div>
            <q-btn
              flat
              no-caps
              @click="router.push('/')"
              
              style="padding-left: 0"
              @click.prevent="backHome()"
            >
              <q-img
                :src="logo2"
                style="width: 50px"
                :class="scrolled ? 'logo-filter-white' : 'logo-normal'"
              />
            </q-btn>
          </div>

          <!-- desktop -->
          <div v-if="!$q.screen.xs">
            <q-btn-toggle
              v-model="tab"
              :toggle-color="toggleColor"
              flat
              stretch
              style="gap: 5px"
              dense
              no-caps
              :options="options"
              @click="scrollToSection(tab)"
            />
          </div>

          <!-- mobile -->
          <div v-else>
            <q-btn
              :class="[
                'active-button',
                { 
                  'home-button': $route.name === 'home',
                  scrolled: scrolled,
                },
              ]"
              no-caps
              flat
            >
              Menu
              <q-icon name="arrow_drop_down" />
              <q-menu>
                <q-list dense>
                  <q-item clickable v-close-popup no-caps  @click="router.push('/')">
                    <q-item-section> Ínicio </q-item-section>
                  </q-item>
                  <q-item clickable v-close-popup no-caps @click="scrollToSection('servicos')">
                    <q-item-section> Serviços </q-item-section>
                  </q-item>
                  <q-item clickable v-close-popup no-caps @click="scrollToSection('contato')">
                    <q-item-section> Contato</q-item-section>
                  </q-item>
                </q-list>
              </q-menu>
            </q-btn>
          </div>
        </div>
        <div>
          <q-btn
            no-caps
            class="button-primary"
            :class="
              scrolled || $route.name === 'home' ? 'bg-primary text-white' : 'bg-white text-dark'
            "
            @click="openWhatsApp"
            label="Falar conosco"
          />
        </div>
      </q-toolbar>
    </q-header>

    <q-page-container style="padding: 0">
      <router-view />
    </q-page-container>
  </q-layout>

  <footer id="contato" class="footer">
    <div class="row col-xs-12">
      <div class="col-xs-12 col-sm-6">
        <h5>Navegação</h5>
        <ul>
          <li v-for="(item, index) in options" :key="index">
            <a class="text-white" @click="scrollToSection(item.value)">{{ item.label }}</a>
          </li>
        </ul>
        <h5>Sobre</h5>
        <p class="q-ma-none">Joana Eni de Mattos - Oficina Mecanica</p>
        <p>CNPJ: 34.231.646/0001-00</p>
      </div>
      <div class="col-xs-12 col-sm-6 footer-item">
        <h5>Contato</h5>
        <p>
          Rua José Rosa, 289
          <br />
          Bairro Belo Horizonte, Campo Grande - MS, 79090-201
        </p>
        <p>centroautomotivomattos@gmail.com</p>
        <div class="row items-center">
          <q-img  class="white-filter" :src="icon_wpp" style="width: 20px" fit="contain" />
          <p class="q-ma-none q-pl-xs">(67) 3351-6211</p>
        </div>
        <div class="q-mt-sm row items-center">
          <q-img  class="white-filter" :src="icon_insta" style="width: 20px" fit="contain" />
          <a class="text-white q-pl-xs" href="https://www.instagram.com/mattos.centroautomotivo/" target="_blank">mattos.centroautomotivo</a>
          
        </div>
      </div>
    </div>
    <div class="text-center q-mt-lg" style="font-size: 12px">
      <p class="q-ma-none">
        {{ anoAtual }} &copy;Centro Automotivo Mattos - Todos os direitos reservados
      </p>
    </div>
  </footer>
  <span v-if="scrolled">
    <div class="button-voltar">
      <q-btn icon="north" round color="primary" @click.prevent="backHome()" />
    </div>
  </span>
  <span v-if="scrolled">
    <div class="button-whats">
      <q-btn round color="green" @click="openWhatsApp">
        <q-img class="white-filter" :src="icon_wpp" style="width: 20px" fit="contain" />
      </q-btn>
    </div>
  </span>
</template>

<script setup>
import { ref, onMounted, onBeforeUnmount } from 'vue'
import { useRouter } from 'vue-router'
//import logo1 from 'src/assets/images/logo/logo_cam_1.png'
import logo2 from 'src/assets/images/logo/logo_cam_2.png'
import icon_wpp from 'src/assets/images/icons/icon_wpp.webp'
import icon_insta from 'src/assets/images/icons/instagram.png'

const toggleColor = ref('white')
const router = useRouter()
const anoAtual = ref(new Date().getFullYear())
const scrolled = ref(false)
const tab = ref('home')
const options = [
  { label: 'Ínicio', value: 'hero' },
  { label: 'Serviços', value: 'servicos' },
  { label: 'Contato', value: 'contato' },
]
onMounted(() => {
  window.addEventListener('scroll', handleScroll)
})

onBeforeUnmount(() => {
  window.removeEventListener('scroll', handleScroll)
})

const scrollToSection = (id) => {
  if (['contato'].includes(id)) {
    scrollToElement(id)
  }

  if (['home', 'servicos'].includes(id)) {
    if (router.currentRoute.value.path !== '/') {
      router.push('/').then(() => {
        scrollToElement(id)
      })
    } else {
      scrollToElement(id)
    }
  } else {
    scrollToElement(id)
  }
}

const scrollToElement = (id) => {
  const section = document.getElementById(id)
  const headerOffset = 70 // Altura da header ou o deslocamento desejado
  if (section) {
    const elementPosition = section.getBoundingClientRect().top + window.scrollY // Posição do elemento
    const offsetPosition = elementPosition - headerOffset // Ajusta para o deslocamento
    window.scrollTo({
      top: offsetPosition,
      behavior: 'smooth',
    })
  }
}
const handleScroll = () => {
  scrolled.value = window.scrollY > 50
  toggleColor.value = scrolled.value ? '#0d1a33' : '#fff'
}
const openWhatsApp = () => {
  if (typeof window !== 'undefined') {
    window.open('https://wa.me/5567984113872', '_blank')
  }
}
const backHome = () => {
  window.scrollTo({
    top: 0,
    behavior: 'smooth',
  })
}
</script>
<style lang="scss" scoped>
.logo-filter-white {
  filter: brightness(1) invert(1); // deixa a imagem branca
  transition: filter 0.3s ease;
}

.logo-normal {
  filter: none;
  transition: filter 0.3s ease;
}

.header {
  position: fixed;
  top: 10px;
  left: 0;
  //border: 1px solid #fff;
  background-color: transparent;
  width: 100%;
  max-width: 1200px;
  margin: 0 auto;
  color: #fff;
  transition: background-color 0.3s ease;

  &.solid-background {
    border-radius: 15px;
    border: none;
    background-color: #fff;
    box-shadow: 0 2px 8px rgba(0, 0, 0, 0.3);
    color: $dark;
  }
  &.home-header {
    color: $dark;
  }
}

.active-button {
  color: #fff;
  border: 1px solid #fff;
  border-radius: 25px;

  &.scrolled {
    color: $primary;
    border-color: $primary;
  }
  &.home-button {
    border-color: $primary;
    background-color: #fff;
    color: $primary;
  }
}
.footer {
  display: block;
  color: #fff;
  background: $dark;
  padding: 0 15vw;
  h5 {
    font-weight: bold;
    font-size: 18px;
    color: #fff;
    padding: 0;
    margin: 20px 0;
  }
  ul {
    list-style: none;
    padding: 0;
    margin: 0;
    li {
      margin: 10px 0;
      a {
        color: #fff;
        text-decoration: none;
        cursor: pointer;
        &:hover {
          color: $accent;
        }
      }
    }
  }
}

.button-whats {
  position: fixed;
  z-index: 1;
  right: 20px;
  bottom: 20px;
}
.button-voltar {
  position: fixed;
  z-index: 1;
  right: 20px;
  bottom: 70px;
}
.white-filter {
  width: 20px;
  filter: brightness(0) invert(1);
}
</style>
