<template>
    <li class="col-3 mb-5">
        <img class="front-img"
        :src="srcImg"
        :alt="altImg">
        <h1> {{ title }} </h1>
        <h2> {{ originalTitle }} </h2>
        <h4> {{ vote }} </h4>
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
    overflow: hidden;
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
}
.flag-image {
    width: 40px;
}
.front-img {
    width: 100%;
}
</style>