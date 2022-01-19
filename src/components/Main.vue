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
import axios from 'axios';
import Search from "./Search.vue"
export default {
    name: 'Main',
    //metto elemento figlio
    components: {
        Search,
    },
    data () {
        return {
            cardFilm: null,
            filmName: 'no',
            queryPath: 'https://api.themoviedb.org/3/search/movie?api_key=c84442c7cda19b672849e1f2bfc0459d',
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
            axios
            .get(this.queryPath, {
                params: {
                    query: this.filmName
                }
            })
            .then((response) => {
                this.cardFilm = response.data.results;
                console.log(this.cardFilm);
            })
            .catch(function (error) {
                console.log(error);
            });
        }
    }
}
</script>

<style lang="scss" scoped>
@import "../assets/scss/partials/_variables.scss";
@import "../assets/scss/partials/_commons.scss";
</style>