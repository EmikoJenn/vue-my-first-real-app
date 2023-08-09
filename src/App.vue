<template>
  <indecision />
</template>

<script>
import Indecision from "./components/Indecision.vue";

export default {
  name: "App",
  components: {
    Indecision,
  },
};
</script>

<style>
html,
body {
  background-color: black;
}
body {
  text-align: center;
  padding: 10rem;
}
</style>
