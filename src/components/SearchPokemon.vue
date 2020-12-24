<template>
  <b-col>
    <h3>SEARCH POKEMON</h3>
    <input v-model="query" />
    <button @click="search">Search</button>
    <button @click="resetForm">Reset</button>
  </b-col>
</template>

<script>
export default {
  name: "SearchPokemon",
  data() {
    return {
        query: '',
    };
  },
  methods: {
      resetForm() {
          this.query = '';
      },
      search() {
          this.$emit('new-search-query', this.query);
      }
  }
};
</script>

<style>
</style>