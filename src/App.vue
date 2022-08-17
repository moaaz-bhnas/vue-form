<template>
  <HunterForm />
</template>

<script>
import HunterForm from "./components/HunterForm.vue";

export default {
  name: "App",
  components: {
    HunterForm,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
