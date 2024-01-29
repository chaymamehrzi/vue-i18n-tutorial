<template>
  <div id="app" class="container">
    <div class="jumbotron">
      <h1 class="display-4">Vue Internationalization App</h1>
    </div>
    <HelloI18n />
  </div>
</template>

<script>
import HelloI18n from "./components/HelloI18n.vue";

export default {
  name: "App",

  components: {
    HelloI18n,
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
