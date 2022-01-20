<template>
  <div id="app">
    <Header />
    <Main />
  </div>
</template>

<script>
import Main from "./components/Main.vue";
import Header from "./components/Header.vue";

export default {
  name: "App",
  components: {
    Main,
    Header
  },
};
</script>

<style lang="scss">
@import "~bootstrap/scss/bootstrap";
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  background-color: rgb(59, 59, 59);
}
</style>
