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
        Cerca Film o Serie TV
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

<style lang="scss" scoped>
.search {
    input {
      border: 2px solid black;
    }
    button {
        margin-left: 2em;
    }
}
</style>