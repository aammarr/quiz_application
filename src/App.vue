<script setup>
import "./assets/css/index.css";
import { RouterLink, RouterView } from "vue-router";
</script>

<template>
  <RouterView />
</template>

<style lang="scss">
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: "Nunito";
}
@font-face {
  font-family: "Nunito";
  src: url("./assets/fonts/Nunito/static/Nunito-Regular.ttf");
}
@font-face {
  font-family: "Rubik";
  src: url("./assets/fonts/Rubik/static/Rubik-Regular.ttf");
}

.mdc-button {
  font-family: "Nunito" !important;
  text-transform: capitalize !important;
}
</style>
