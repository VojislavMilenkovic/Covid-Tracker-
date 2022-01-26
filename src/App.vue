<template>
  <the-header></the-header>
  <the-home></the-home>
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

<style>
#app {
}
</style>
