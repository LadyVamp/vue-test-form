<template>
  <div class="container">
    <app-document-card></app-document-card>
  </div>
</template>

<script>
import AppDocumentCard from "./components/AppDocumentCard.vue";

export default {
  name: "App",
  components: {
    AppDocumentCard,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
