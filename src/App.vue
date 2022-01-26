<template>
  <div class="app container text-center">
    <the-header></the-header>
    <the-home></the-home>
  </div>
</template>

<script>
import TheHeader from "./components/TheHeader.vue";
import TheHome from "./components/TheHome.vue";
export default {
  name: "App",
  components: {
    TheHeader,
    TheHome,
  },
};
</script>

<style scoped>
.app {
  height: 100vh;
}
.container {
  max-width: 1040px;
}
</style>
