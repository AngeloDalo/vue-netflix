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
@import "../assets/scss/partials/_header.scss";
header {
    @include header;
}
</style>