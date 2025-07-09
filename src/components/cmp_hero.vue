<template>
  <div class="bg-hero">
    <div class="row container text-white justify-around items-center full-height full-width margin-header">
      <div class="col-xs-12 col-sm-4 flex column items-start q-pa-md">
        <p class="title-secondary">Mais de 25 anos no mercado</p>
        <p class="">
          Estamos no mercado desde 1998, oferecendo serviços de qualidade com transparência e
          compromisso. Atendemos <b class="texto-verde">Carros, SUVs</b> e
          <b class="texto-verde">Picapes</b> com uma equipe experiente e dedicada, sempre
          priorizando o melhor atendimento para nossos clientes.
        </p>
      </div>

      <div class="col-xs-12 col-sm-4 q-pa-md">
        <div class="vidro-efeito">
          <p class="title-secondary">Faça seu orçamento agora!</p>
          <p class="">
            Solicite seu orçamento sem compromisso. Nossa equipe está pronta para ajudar você!
          </p>
          <q-btn icon-right="arrow_forward" class="button-primary   q-mt-sm">Solicitar orçamento</q-btn>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup></script>
<style lang="scss" scoped>
.texto-verde {
  color: $primary;
  font-size: 18px;
}
.bg-hero {
  background-image: url('src/assets/images/bg-hero.png');
  width: 100%;
  background-color: $dark;
  min-height: 400px; // ocupa a altura da tela inteira
  display: flex;
  align-items: center;
}

.vidro-efeito {
  background: rgba(255, 255, 255, 0.1);
  padding: 1.5rem;
  border-radius: 8px;
  backdrop-filter: blur(6px);
}
@media(max-width: 600px) {
  .margin-header {
    margin-top: 70px;
  }
}
</style>
