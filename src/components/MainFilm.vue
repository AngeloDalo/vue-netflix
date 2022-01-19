<template>
    <li class="col-4 mb-5">
        <h1> {{ title }} </h1>
        <h2> {{ originalTitle }} </h2>
        <h3> {{ language }} </h3>
        <h4> {{ vote }} </h4>
    </li>
</template>

<script>
export default {
    name: "MainFilm",
    props: ['title', 'originalTitle', 'language', 'vote'],
    data() {
        return {

        }
    }
}
</script>

<style lang="scss" scoped>
li {
    h1 {
        font-size: 2em;
    }
    h2 {
        font-size: 1.5em;
    }
    h3 {
        font-size: 1em;
    }
    h4 {
        font-size: 0.8em;
    }
}
</style>