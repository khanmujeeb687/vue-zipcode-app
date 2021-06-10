<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png" />
    <Zip_Details msg="Welcome to Your city finder App" />
  </div>
</template>

<script>
import Zip_Details from "./components/Zip-Details.vue";

export default {
  name: "App",
  components: {
    Zip_Details,
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
