<template>
    <li class="col-xl-3 col-lg-4 col-md-5 col-sm-6 mb-5">
        <img class="front-img"
        :src="srcImg"
        :alt="altImg">
        <h1> {{ title }} </h1>
        <h2> {{ originalTitle }} </h2>
        <div class="div">
            <i class="fas fa-star yellow" v-for="(i, index) in  vote" :key="index+originalTitle"></i>
            <i class="fas fa-star grey" v-for="(i, index) in  (5-vote)" :key="index+originalTitle+i"></i>
        </div>
        <img class="flag-image"
        :src="src"
        :alt="alt">
    </li>
</template>

<script>
export default {
    name: "MainFilmSerie",
    props: ['src', 'alt', 'title', 'originalTitle', 'language', 'vote', 'srcImg', 'altImg'],
    data() {
        return {

        }
    }
}
</script>

<style lang="scss" scoped>
li {
    height: 350px;
    h1 {
        font-size: 1.5em;
    }
    h2 {
        font-size: 1em;
    }
    h3 {
        font-size: 0.8em;
    }
    h4 {
        font-size: 0.8em;
    }
    h1, h2, h3, h4 {
        color: white;
    }
    .yellow {
        color: yellow;
    }
    .grey {
        color: grey;
    }
}
.flag-image {
    width: 40px;
}
.front-img {
    width: 100%;
    color: white;
}
</style>