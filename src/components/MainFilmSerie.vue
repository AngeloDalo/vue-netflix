<template>
    <li class="col-xl-3 col-lg-4 col-md-5 col-sm-6 mb-5">
        <div class="container-card">
            <div class="div imgFilm">
                <img class="front-img"
                :src="srcImg"
                :alt="altImg">
            </div>
            <div class="div imgHover text-start p-2">
                <h1>Titolo: {{ title }} </h1>
                <h2>Titolo originale: {{ originalTitle }} </h2>
                <div class="voto">
                    Voto:
                    <i class="fas fa-star yellow" v-for="(i, index) in  vote" :key="index+title"></i>
                    <i class="fas fa-star grey" v-for="(i, index) in  (5-vote)" :key="index+title+i"></i>
                </div>
                <img class="flag-image"
                :src="src"
                :alt="alt">
                <p class="overview">Overview: {{ overview }} </p>
            </div>
        </div>
    </li>
</template>

<script>
export default {
    name: "MainFilmSerie",
    props: ['src', 'alt', 'title', 'originalTitle', 'language', 'vote', 'srcImg', 'altImg', 'overview'],
    data() {
        return {

        }
    }
}
</script>

<style lang="scss" scoped>
@import "../assets/scss/partials/_filmSerie.scss";
li {
    @include li;
}
</style>