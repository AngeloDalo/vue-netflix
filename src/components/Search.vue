<template>
  <div class="search">
    <input 
        type="text"
        name="search"
        v-model="inputText"
        id="search"
    >
    <button
      class="btn btn-primary"
      type="submit"
      @click="$emit('searchFilm', inputText)"
    >
        Cerca Film
    </button>
  </div>
</template>

<script>
export default {
  name: 'Search',
  data() {
    return {
      inputText: '',
    };
  },
};
</script>

<style>

</style>