<template>
    <li>
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

</style>