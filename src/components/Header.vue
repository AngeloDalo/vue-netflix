<template>
  <header>
      <img src="../assets/img/Boolflix.png" alt="">
  </header>
</template>

<script>
export default {
    name: 'Header',
    data () {
        return {

        }
    }
}
</script>

<style lang="scss" scoped>
@import "../assets/scss/partials/_variables.scss";
@import "../assets/scss/partials/_commons.scss";
header {
    display: flex;
    align-items: center;
    padding-left: 2em;
    background-color: black;
    height: 100px;
}
</style>