<template>
  <div class="bg-hero">
    <div class="row container text-white justify-start items-center full-height margin-header">
      <div class="col-xs-12 col-sm-4 flex column items-start q-pa-md">
        <div class="row items-center">
          <div style="width: 20px; height: 1px" class="bg-primary q-mr-sm" />
          <span class="text-primary bebas-font">DESDE 1998</span>
        </div>
        <p class="column title-primary bebas-font">
          <span> MAIS DE 25 ANOS </span>
          <span class="text-primary"> DE CONFIANÇA </span>
          <span> NO SEU VEÍCULO </span>
        </p>
        <p class="subtitle-primary">
          Serviços de qualidade com transparência e compromisso. Atendemos
          <b class="texto-verde">Carros, SUVs</b> e <b class="texto-verde">Picapes</b> com uma
          equipe experiente e dedicada, sempre priorizando o melhor atendimento para nossos
          clientes.

          <!-- Serviços de qualidade com transparência e compromisso. Atendemos carros, SUVs e picapes com uma equipe experiente e dedicada. -->
        </p>
        <q-btn
          icon-right="arrow_forward"
          class="button-primary"
          color="primary"
          no-caps
          @click="openWhatsApp"
          label="Solicitar Orçamento"
        />
      </div>
    </div>
  </div>
</template>

<script setup>
const openWhatsApp = () => {
  if (typeof window !== 'undefined') {
    window.open('https://wa.me/556733516211', '_blank')
  }
}
</script>
<style lang="scss" scoped>
.texto-verde {
  color: $primary;
  // font-size: 18px;
}
.bg-hero {
  background-image: url('src/assets/images/bg-hero.png');
  width: 100%;
  background-color: $dark;
  min-height: 700px;
  display: flex;
  align-items: center;
}

.vidro-efeito {
  background: rgba(255, 255, 255, 0.1);
  padding: 1.5rem;
  border-radius: 8px;
  backdrop-filter: blur(6px);
}
@media (max-width: 600px) {
  .margin-header {
    margin-top: 70px;
  }
}
</style>
