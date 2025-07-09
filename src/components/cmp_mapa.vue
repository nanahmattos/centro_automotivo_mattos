<template>
  <div class="container">
    <div class="row items-stretch  q-pt-md">
      <div class="col-xs-12 col-sm-6">
        <div style="position: relative" class="same-height">
          <q-img src="../assets/images/image_portao.webp" />

          <div class="overlay-content text-white">
            

              <!-- <p class="title-secondary">Horário de Atendimento</p>
              <p class="texto-primary "><b>Segunda a Quinta:</b> 7h30 às 11h30 e 13h às 18h</p>
              <p class="texto-primary"><b>Sexta-feira:</b> 7h30 às 11h30 e 13h às 17h</p> -->
            
          </div>
        </div>
      </div>

      <div class="col-xs-12 col-sm-6">
        <div class="map-wrapper same-height">
          <iframe
            src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3737.711032708049!2d-54.64892658925972!3d-20.47705848095874!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x9486e743ec358fbf%3A0x7c8ce09b0459d03c!2sCENTRO%20AUTOMOTIVO%20MATTOS%20-%20C.A.M.!5e0!3m2!1spt-BR!2sbr!4v1750970767617!5m2!1spt-BR!2sbr"
            allowfullscreen
            loading="lazy"
            referrerpolicy="no-referrer-when-downgrade"
          ></iframe>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup></script>
<style scoped lang="scss">
.same-height {
  height: 300px;
  display: flex;
}
.map-wrapper iframe {
  width: 100%;
  height: 100%;
  border: 0;
}

.overlay-content {
  position: absolute;
  top: 0;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.2);
  width: 100%;
  padding: 1rem;
  color: white;
}
</style>
