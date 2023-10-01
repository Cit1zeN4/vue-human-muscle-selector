<template>
  <div id="app">
    <MuscleSelector
      outer-color="#212121"
      body-color="#607D8B"
      muscle-color="#455A64"
      select-color="#CDDC39"
    />
  </div>
</template>

<script>
import MuscleSelector from "./components/MuscleSelector.vue";

export default {
  name: "App",
  components: {
    MuscleSelector,
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
