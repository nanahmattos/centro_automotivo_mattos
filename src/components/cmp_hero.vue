<template>
  <div class="bg-hero" >
    <div style="position: relative;"></div>
  </div>
</template>

<script setup></script>
<style lang="scss" scoped>
.bg-hero {
  //padding: 20px;
  //background-size: cover;
  //background-position: center;
  //background-repeat: no-repeat;
  position: relative;
  //display: flex;
  //align-items: flex-end;
  //justify-content: center;
  //opacity: 0.9;
  //width: 100vw;
  min-height: 350px;
  height: auto;
}
.bg-hero::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: $dark;
  z-index: 1;
  pointer-events: none;
}
</style>
