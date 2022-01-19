<template>
  <main>
      <div class="container-fluid">
          <div class="row mt-5">
              <div class="col-12">
                  <Search
                        @searchFilm="searchFilm($event)"
                   />
              </div>
          </div>
          <div class="container mt-5 text-center">
                <h1>FILM</h1>
                <ul class="row mt-5">
                    <MainFilmSerie
                    v-for="(cardFilm, index) in cardFilms"
                    :key="index"
                    :title = "cardFilm.title"
                    :originalTitle = "cardFilm.original_title"
                    :language = "cardFilm.original_language"
                    :vote = "cardFilm.vote_average"
                    :src = "flagFilm[index]"
                    :alt = "cardFilm.original_language"
                    />
                </ul>
                <h1>SERIE TV</h1>
                <ul class="row mt-5">
                    <MainFilmSerie
                    v-for="(cardSerie, index) in cardSeries"
                    :key="index"
                    :title = "cardSerie.name"
                    :originalTitle = "cardSerie.original_name"
                    :language = "cardSerie.original_language"
                    :vote = "cardSerie.vote_average"
                    :src = "flagSerie[index]"
                    :alt = "cardSerie.original_language"
                    />
                </ul>
          </div>
      </div>
  </main>
</template>

<script>
import axios from 'axios';
import Search from "./Search.vue"
import MainFilmSerie from "./MainFilmSerie.vue"
export default {
    name: 'Main',
    //metto elemento figlio
    components: {
        Search,
        MainFilmSerie,
    },
    data () {
        return {
            flagFilm: [], //link della bandiera per i film
            flagSerie: [],  //link della bandiera per le serie
            cardFilms: null, //contiene tutte le carte dei film
            cardSeries: null, //contiene tutte le carte per le serie
            filmSerieName: '', //film o serie inserito nell'input
            queryPathFILM: 'https://api.themoviedb.org/3/search/movie?api_key=c84442c7cda19b672849e1f2bfc0459d',
            queryPathTV: 'https://api.themoviedb.org/3/search/tv?api_key=c84442c7cda19b672849e1f2bfc0459d&query='
        }
    },
    computed: {
    },
    created() {
    },
    methods: {
        searchFilm(event) {
            //al filmSerieName andrà il valore inserito nell'input (event)
            this.filmSerieName  = event;
            axios
            .get(this.queryPathFILM, {
                params: {
                    //parametro dinamico del link
                    query: this.filmSerieName
                }
            })
            .then((response) => {
                ///riempire le carte dei film con valori presi dal sito
                this.cardFilms = response.data.results;
                //per determinate lingue bisogna modificare il nome per trovare la bandiera
                for (let i=0; i < this.cardFilms.length; i++) {
                    if (this.cardFilms[i].original_language == 'en') {
                        this.cardFilms[i].original_language = 'gb';
                    }
                    if (this.cardFilms[i].original_language == 'ja') {
                        this.cardFilms[i].original_language = 'jp';
                    }
                    //nel fleg film andranno le iniziali della lingua
                    this.flagFilm.push(this.cardFilms[i].original_language);
                    //creato un link dinamico per inserire la bandiera
                    this.flagFilm[i] = "https://www.bandiere-mondo.it/data/flags/w580/" + this.cardFilms[i].original_language + ".png" 
                }
            })
            .catch(function (error) {
                console.log(error);
            });
            
            //stessa cosa dei film fatta ora per le serie
            axios
            .get(this.queryPathTV, {
                params: {
                    query: this.filmSerieName
                }
            })
            .then((response) => {
                this.cardSeries = response.data.results;
                for (let i=0; i < this.cardSeries.length; i++) {
                    if (this.cardSeries[i].original_language == 'en') {
                        this.cardSeries[i].original_language = 'gb';
                    }
                    if (this.cardSeries[i].original_language == 'ja') {
                        this.cardSeries[i].original_language = 'jp';
                    }
                    this.flagSerie.push(this.cardSeries[i].original_language);
                    this.flagSerie[i] = "https://www.bandiere-mondo.it/data/flags/w580/" + this.cardSeries[i].original_language + ".png" 
                }
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