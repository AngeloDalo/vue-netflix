<template>
  <main>
      <div class="container-fluid">
          <div class="row mt-5">
              <div class="col-12 d-flex justify-content-center">
                  <Search
                        @searchFilm="searchFilmSerie($event)"
                   />
              </div>
          </div>
          <div class="container mt-5 text-center">
                <img src="../assets/img/Film.png" alt="">
                <ul class="row mt-5">
                    <MainFilmSerie
                    v-for="(cardFilm, index) in cardFilms"
                    :key="index+cardFilms"
                    :srcImg = "imgFilm[index]"
                    :altImg = "cardFilm.title"
                    :title = "cardFilm.title"
                    :originalTitle = "cardFilm.original_title"
                    :language = "cardFilm.original_language"
                    :vote = "cardFilm.vote_average"
                    :i = 1
                    :src = "flagFilm[index]"
                    :alt = "cardFilm.original_language"
                    :overview = "cardFilm.overview"
                    />
                </ul>
                <img src="../assets/img/Serietv.png" alt="">
                <ul class="row mt-5">
                    <MainFilmSerie
                    v-for="(cardSerie, index) in cardSeries"
                    :key="index+cardSeries"       
                    :srcImg = "imgSerie[index]"
                    :altImg = "cardSerie.title"                               
                    :title = "cardSerie.name"
                    :originalTitle = "cardSerie.original_name"
                    :language = "cardSerie.original_language"
                    :vote = "cardSerie.vote_average"
                    :i = 1
                    :src = "flagSerie[index]"
                    :alt = "cardSerie.original_language"
                    :overview = "cardSerie.overview"
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
            imgFilm: [], //immagini dei film
            imgSerie: [], //immagini delle serie
            cardFilms: null, //contiene tutte le carte dei film
            cardSeries: null, //contiene tutte le carte per le serie
            filmSerieName: '', //film o serie inserito nell'input
            api: 'c84442c7cda19b672849e1f2bfc0459d',
            queryPathFILM: 'https://api.themoviedb.org/3/search/movie?',
            queryPathTV: 'https://api.themoviedb.org/3/search/tv?',
            baseImg: 'https://image.tmdb.org/t/p/',
            smallSize: 'w342/',
            mediumSize: 'w1000/',
            bigSize: 'w1920/',
            //ESEMPIO: https://image.tmdb.org/t/p/w342/wwemzKWzjKYJFfCeiB57q3r4Bcm.png
        }
    },
    computed: {
    },
    created() {
    },
    methods: {
        searchFilmSerie(event) {
            //al filmSerieName andrà il valore inserito nell'input (event)
            this.filmSerieName  = event;
            axios
            .get(this.queryPathFILM, {
                params: {
                    //parametro dinamico del link
                    api_key: this.api,
                    query: this.filmSerieName
                }
            })
            .then((response) => {
                ///riempire le carte dei film con valori presi dal sito
                this.cardFilms = response.data.results;
                //per determinate lingue bisogna modificare il nome per trovare la bandiera
                for (let i=0; i < this.cardFilms.length; i++) {
                    if (this.cardFilms[i].original_language == 'en') {
                        this.cardFilms[i].original_language = 'us';
                    }
                    if (this.cardFilms[i].original_language == 'ja') {
                        this.cardFilms[i].original_language = 'jp';
                    }
                    //nel fleg film andranno le iniziali della lingua
                    //creato un link dinamico per inserire la bandiera e l'immagine
                    this.cardFilms[i].vote_average = Math.round(this.cardFilms[i].vote_average / 2);
                    this.flagFilm[i] = "https://www.bandiere-mondo.it/data/flags/w580/" + this.cardFilms[i].original_language + ".png" 
                    this.imgFilm[i] = this.baseImg + this.smallSize + this.cardFilms[i].backdrop_path;
                    if (this.cardFilms[i].backdrop_path == null) {
                        this.imgFilm[i] = 'https://www.salonlfc.com/wp-content/uploads/2018/01/image-not-found-scaled-1150x647.png';
                    }
                }
            })
            .catch(function (error) {
                console.log(error);
            });
            
            //stessa cosa dei film fatta ora per le serie
            axios
            .get(this.queryPathTV, {
                params: {
                    api_key: this.api,
                    query: this.filmSerieName
                }
            })
            .then((response) => {
                this.cardSeries = response.data.results;
                for (let i=0; i < this.cardSeries.length; i++) {
                    if (this.cardSeries[i].original_language == 'en') {
                        this.cardSeries[i].original_language = 'us';
                    }
                    if (this.cardSeries[i].original_language == 'ja') {
                        this.cardSeries[i].original_language = 'jp';
                    }     
                    this.cardSeries[i].vote_average = Math.round(this.cardSeries[i].vote_average / 2);
                    this.flagSerie[i] = "https://www.bandiere-mondo.it/data/flags/w580/" + this.cardSeries[i].original_language + ".png" 
                    this.imgSerie[i] = this.baseImg + this.smallSize + this.cardSeries[i].backdrop_path;
                    if (this.cardSeries[i].backdrop_path == null) {
                        this.imgSerie[i] = 'https://www.salonlfc.com/wp-content/uploads/2018/01/image-not-found-scaled-1150x647.png';
                    }
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
@import "../assets/scss/partials/_main.scss";
.container-fluid {
    @include main;
}
</style>