<template>
  <main>
      <div class="container">
          <div class="row">
              <div class="col-12">
                  <Search
                        @searchFilm="searchFilm($event)"
                   />
              </div>
          </div>
          <div class="row mt-5">
              film
          </div>
      </div>
  </main>
</template>

<script>
//import axios from 'axios';
import Search from "./Search.vue"
export default {
    name: 'Main',
    //metto elemento figlio
    components: {
        Search,
    },
    data () {
        return {
            filmName: null,
        }
    },
    computed: {
    },
    created() {

    },
    methods: {
        searchFilm(event) {
            this.filmName  = event;
            console.log(this.filmName);
        }
    }
}
</script>

<style lang="scss" scoped>
@import "../assets/scss/partials/_variables.scss";
@import "../assets/scss/partials/_commons.scss";
</style>